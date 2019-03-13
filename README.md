# LatihanPHPModul7
RONA KAMILIA 34 X RPL 4
 JAWABAN
1. <?php

$host = "localhost";
$db = "db_universitas";
$uname = "root";
$pass = "";

$connect = mysqli_connect($host, $uname, $pass, $db);

if(!$connect)
{
    echo"Koneksi ke database gagal : " . mysqli_connect_error();
}
?>


2. Membuat langsung di PHPmyadmin




3. <?php

include '../connect.php';

$query = "SELECT * FROM dosen";
$result = mysqli_query($connect, $query);
$num = mysqli_num_rows($result);

?>
<!DOCTYPE html>
<html>
<head>
<title></title>
</head>
<body>
    <table border='1'>
    <h2>Data Dosen</h2>
    <tr>
        <th>No.</th>
        <th>Nama Dosen</th>
        <th>Telepon</th>
        <th>Aksi</th>
    </tr>
        <?php
            if($num > 0)
           {
               $no = 1;
               while($data = mysqli_fetch_assoc($result))
               {
                   echo "<tr>";
                   echo "<td>" . $no . "</td>";
                   echo "<td>" . $data['nama_dosen'] . "</td>";
                   echo "<td>" . $data['telp'] . "</td>";
                   echo "<td><a href='form-update.php?id_dosen=" . $data['id_dosen'] . "'>Edit</a> | ";
                   echo "<td><a href='delete.php?id_dosen=" . $data['id_dosen'] . "' onclick='return confirm(\"Apakah Anda yakin ingin menghapus data?\")'>Hapus</a></td>";
                   echo "</tr>";
                   $no++;
               }
           } 
           else
           {
               echo "<td colspan='3'>Tidak ada data</td>";
           }
        ?>
    </table>
</body>
</html>


4. <?php

include '../connect.php';

$id_dosen = $_POST['id_dosen'];
$nama_dosen = $_POST['nama_dosen'];
$telp = $_POST['telp'];

$query = "UPDATE dosen SET nama_dosen = '$nama_dosen', telp = '$telp' WHERE id_dosen = $id_dosen";

$result = mysqli_query($connect, $query);

$num = mysqli_affected_rows($connect);

if($num > 0)
{
    echo "Berhasil update data <br>";
} else {
    echo "Gagal update data <br>";
}
echo "<a href = 'read.php'>Lihat Data</a>";
?>


5.
<?php

include '../connect.php';

$id_dosen = $_GET['id_dosen'];

$query = "DELETE FROM dosen WHERE id_dosen = $id_dosen";

$result = mysqli_query($connect,$query);

$num = mysqli_affected_rows($connect);

    if ($num > 0)
    {
        echo "Berhasil hapus data<br>";
    } else {
        echo "Gagal hapus data<br>";
    }

    echo "<a  href='read.php'>Lihat Data</a>";

?>



SCREENSHOTS
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Tambah%20data%201.png)
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Tambah%20data%202.png)
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Berhasil%20tambah%201.png)
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Tampilan%20data%201.png)
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Tampilan%20data%202.png)
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Update%20data%201.png)
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Update%20data.png)
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Hasil%20update.png)
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Hapus%20data%201.png)
![alt text](https://github.com/ronakamilia27rpl/LatihanPHPModul7/blob/master/Berhasil%20hapus%20data%20.png)





