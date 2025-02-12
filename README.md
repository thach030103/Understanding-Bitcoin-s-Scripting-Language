# Understanding-Bitcoin-s-Scripting-Language
<p>Số lượng SV thực hiện : 5</p>
<p>Tên SV: Nguyễn Bửu Thạch</p>
<p>Công việc: Developer</p>
<h3>1. Tạo script P2PKH (task1)</h3>
<h4>a. Viết hàm tạo tập lệnh P2PKH:</h4>
<ul>
  <li> Chọn tham số cho testnet </li>
  <li> Sinh khoá riêng (private key): Dùng CbitcoinSecret để tạo khoá cá riêng ngẫu nhiên </li>
  <li> Tạo khoá công khai (public key) từ private key</li>
  <li> Tạo địa chỉ P2PKH trên testnet</li>
</ul>
<h4>b. Nhận testnet BTC với địa chỉ Bitcoin đã tạo từ Bitcoin Faucet:</h4>
<ul>
  <li>Sử dụng faucet Testnet ( https://coinfaucet.eu/en/btc-testnet/ ) để gửi testnet BTC đến địa chỉ vừa tạo.</li>
</ul>
<h4>c. Viết hàm tạo khoá quỹ vào địa chỉ đã tạo:</h4>
<ul>
  <li>Sử dụng P2PKH (Pay-to-PubKey-Hash) để khóa quỹ vào một địa chỉ Bitcoin đã tạo.
  <li>Tạo ScriptPubKey (Khóa Quỹ): 
     <ul>
        <li>OP_DUP: Sao chép khóa công khai vào ngăn xếp.
        <li>OP_HASH160: Tính giá băm băm (Hash160) của giá trị trên đỉnh ngăn xếp.
        <li>public_key_hash : Đưa giá trị băm của khóa công khai (public_key) vào tập lệnh dùng hàm Hash160
        <li>OP_EQUALVERIFY: So sánh giá trị băm vừa tính được từ OP_HASH160 với giá trị đã lưu (public_key_hash)
        <li>OP_CHECKSIG: Xác minh chữ ký số với khóa công khai được cung cấp. Nếu chữ ký hợp lệ, giao dịch sẽ được chấp nhận 
     </ul>
</ul>
<h4>d. Viết hàm chí tiêu số tiền bị khoá bằng giao dịch đã ký:</h4>
<ul>
  <li>Xác đinh đầu vào và đầu ra:</li>
     <ul>
        <li>Đầu vào (UTXO) tham chiếu đến giao dịch đã nhận tiền.</li>
        <li>Đầu ra là địa chỉ người nhận và số tiền cần gửi.</li>
     </ul>
  <li>Tạo giao dịch</li>
  <li>Ký giao dịch</li>
     <ul>
        <li>Tính Hash: Sử dụng SignatureHash để băm giao dịch với script_pubkey.</li>
        <li>Ký Số: Dùng khóa riêng để ký vào hash, tạo chữ ký bí mật.</li>
        <li>Tạo ScriptSig (Mở Khóa Quỹ): Kết hợp chữ ký và khóa công khai vào tập lệnh mở khóa.</li>
     </ul>
</ul>
<h4>e. Viết hàm phát sóng giao dịch :</h4>
<ul>
  <li>Chuyển đổi giao dịch thành chuỗi hex và gửi đến API để phát sóng lên Testnet.</li>
</ul>
<h3>2. Tạo Script 2-of-2 Multisig (task2)</h3>
