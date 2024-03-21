1.Control Structures and Loops in PHP Bank Transaction
Coding:
<html>
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Bank Transactions</title>
</head>
<body>
<h2>Bank Transactions</h2>
<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
   <label for="initialBalance">Initial Balance:</label>
   <input type="number" name="initialBalance" required><br><br>
   <label for="numTransactions">Number of Transactions:</label>
   <input type="number" name="numTransactions" required><br><br>
   <label for="transactionType">Transaction Type:</label>
   <select name="transactionType" required>
       <option value="deposit">Deposit</option>
       <option value="withdraw">Withdraw</option>
   </select><br><br>
   <label for="amount">Amount:</label>
   <input type="number" name="amount" required><br><br>
   <input type="submit" value="Perform Transactions">
</form>
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
   $iBalance = $_POST["initialBalance"];
   $numT = $_POST["numTransactions"];
   $tranType = $_POST["transactionType"];
   $amt = $_POST["amount"];
   echo "<h3>Transaction Results:</h3>";
   echo "<p>Initial Balance: $iBalance</p>";
   for ($i = 1; $i<= $numT; $i++) {
       echo "<p>Transaction $i:</p>";
       switch ($tranType) {
           case "deposit":
               $iBalance += $amt;
               echo "<p>Deposit: +$amt</p>";
               break;
           case "withdraw":
               if ($amt <= $iBalance) {
                   $iBalance -= $amt;
                   echo "<p>Withdrawal: -$amt</p>";
               } else {
                   echo "<p style='color: red;'>Insufficient funds for withdrawal!</p>";
               }
 break;
           default:
               echo "<p style='color: red;'>Invalid transaction type!</p>";
       }
   }
   echo "<p>Final Balance: $iBalance</p>";
}
?>
</body></html>
 OUTPUT SCREEN:












2.GET AND POST METHODS IN PHP


HTML CODE:

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Student Course Selection</title>
</head>
<body>
<h1><b><center>Course Registration</center></b></h1>
<form  action="REGISTRATION.php" method="get">
<Table align="center">
<tr><th>Name</th>
<td><input type="text" name="name"></td></tr>
<tr><th>SSLC Mark </th>
<td><input type="number" name="sslcmrk"></td>
</tr>
<tr><th>HSC Mark </th><td><input type="number" name="hscmrk"></td></tr>
<tr>
<th>Courses</th><td><select name="course">
<option value="Computer Science">Computer Science</option>                        	
<option value="Computer Science with Cognitive Systems">Computer Science with Cognitive Systems</option>
<option value="Computer Science with Artificial Intelligence">Computer Science with Artificial Intelligence</option>
<option value="Information Technology">Information Technology</option>
<option value="B.Sc CS with cyber security">B.Sc CS with cyber security</option></td></tr>
<tr><td><input type="submit" name="submit"></td></tr>
</Table></form></body></html>



PHP CODE:


<?php
$name=$_GET["name"];
$sslc=$_GET["sslcmrk"];
$hsc=$_GET["hscmrk"];
$course=$_GET["course"];
echo "<b>NAME:</b>".$name."<br>";
echo "<b>SSLC MARK:</b>".$sslc."<br>";
echo "<b>HSC MARK:</b>".$hsc."<br>";
echo "<b>COURSE SELECTED:</b>".$course."<br>";
?>

OUTPUT SCREEN:
















3. ARRAY AND FUNCTIONS IN PHP
CODING:
 
<?php
if(isset($_POST['disp']))
{
	$s=$_POST['s'];
	$ch=$_POST['ch'];
	switch($ch)
	{
    	case 'STRING LENGTH':
        	$res= strlen($s);
        	break;
    	case 'WORD COUNT':
        	$res= str_word_count($s);
        	break;
    	case 'STRING REVERSE':
        	$res=strrev($s);
        	break;
    	case 'POSITION OF A CHARACTER':
        	$res=strpos($s,"a");
        	break;
        case 'STRING REPLACE':
            $res=str_replace($s,"hello","world");
        	break;
    	case 'STRING SPLIT':
        	$res=str_split($s,1);
        	break;
    	case 'PASSWORD GENERATOR':
        	$data="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
        	$res= substr(str_shuffle($data),0,7);
        	break;}
}
?>
<html>
<body bgcolor="cyan">
<form action="" method="post">
<table align="center" border="3" width="20%"><br><br>
<tr bgcolor="forestgreen"><td align="center" colspan="2">
<font color="white" face="arial black" size="5">STRING HANDLING</font></td></tr>
<tr><td><input type="button" value="Enter String"></td>
<td><input type="text" name="s"></td></tr>
<tr><td><input type="button" value="Select Your Choice"></td>
<td><center><select name="ch">
<option>STRING LENGTH</option>
<option>WORD COUNT</option>
<option>STRING REVERSE</option>
<option>POSITION OF A CHARACTER</option>
<option>STRING REPLACE</option>
<option>STRING SPLIT</option>
<option>PASSWORD GENERATOR</option>
</center></select></td></tr>
<tr><td><input type="submit" value=" RESULT " name="disp"></td>
<td><input type="text" value="<?php echo @$res; ?>" readonly="true"/>
</td></tr></table>
</body></html>

OUTPUT SCREEN:










4.Using Arrays and Functions – Quiz Application
CODING:
<!DOCTYPE html>
<html>
<head>
<title>Quiz Application</title>
</head>
<body>
<h1>Quiz Application</h1>
<form method="post">
<p>Question 1: Full form for WDD?</p>
<input type="radio" name="q1" value="Web Design Development " required> Web Design Development <br>
<input type="radio" name="q1" value=" Web Deploy Development "> Web Deploy Development <br>
<input type="radio" name="q1" value="None of the above"> None of the above <br>
<p>Question 2: All variable names are case sensitive: </p>
<input type="radio" name="TRUE" value="3"> 3<br>
<input type="radio" name="q2" value="FALSE" required> 4<br>
<input type="submit" name="submit" value="Submit">
</form>
<?php
	// Function to check quiz answers and calculate the score
	function checkAnswers($userAnswers) {
    	$correctAnswers = array('q1' => ' Web Design Development ', 'q2' => 'TRUE');
    	$score = 0;
        foreach ($userAnswers as $question => $userAnswer) {
        	if (isset($correctAnswers[$question]) && $correctAnswers[$question] === $userAnswer) {
                $score++;
        	}}
    	return $score;
	}
	// Check if the form has been submitted
	if (isset($_POST['submit'])) {
        $userAnswers = array(
            'q1' => $_POST['q1'],
            'q2' => $_POST['q2']
    	);
$score = checkAnswers($userAnswers);
    	echo "<h2>Quiz Results:</h2>";
    	echo "<p>Your Score: $score out of 2</p>";
	}
	?>
</body>
</html>

OUTPUT SCREEN:












5. Regular Expressions in PHP
Code:
<html>
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Regular Expressions</title>
</head>
<body>
<h2>Regular Expression</h2>
<form method="post" action="">
   <label for="input_text">Enter Text:</label>
   <input type="text" name="input_text" id="input_text" required>
   <button type="submit">Submit</button>
</form>




<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
   $userInput = $_POST["input_text"];


   // Regular expression to match only letters and numbers
   $pattern = '/^[a-zA-Z0-9]+$/';
   echo "<h3>Applied Regular Expressions:</h3>";


   // Check if the input matches the pattern


   if (preg_match($pattern, $userInput)) {
       echo "<p>Input contains only letters and numbers.</p>";
   } else {
       echo "<p>Input contains characters other than letters and numbers.</p>";
   }
   // Find all matches of letters in the input


   preg_match_all('/[a-zA-Z]/', $userInput, $matches);
   echo "<p>Letters found: " . implode(", ", $matches[0]) . "</p>";


   // Replace spaces with underscores
   $modifiedText = preg_replace('/\s/', '_', $userInput);
   echo "<p>Spaces replaced with underscores: $modifiedText</p>";


   // Split the input into an array using commas as delimiters
   $splitText = preg_split('//', $userInput);
   echo "<p>Split input using commas: " . implode(", ", $splitText) . "</p>";
}




?>
</body>
</html>


OUTPUT SCREEN:






6.Form Handling in PHP– Conference Registration
Code:
<!DOCTYPE html>
<html>
<head>
    <title>Conference Registration</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #FFEBF5; /* Light pink background */
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
 
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            width: 80%;
            max-width: 400px;
        }
 
        h1 {
            color: #FF69B4; /* Darker pink for headings */
            margin-bottom: 20px;
            text-align: center;
        }
 
        label {
            display: block;
            margin-bottom: 8px;
            color: #FF69B4; /* Pink for labels */
        }
 
        input[type="text"],
        input[type="email"],
        select {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #FF69B4; /* Pink border for input fields */
            border-radius: 4px;
        }
 
        select {
            height: 100px;
        }
 
        input[type="submit"] {
            background-color: #FF69B4;
            color: #fff;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            display: block;
            margin: 0 auto;
        }
 
        input[type="submit"]:hover {
            background-color: #E85C9E;
        }
 
        h2 {
            color: #FF69B4;
            margin-bottom: 10px;
            text-align: center;
        }
 
        ul {
            margin-left: 20px;
        }
 
        li {
            margin-bottom: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Conference Registration</h1>
        <form method="post">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
            <label for="organization">Organization:</label>
            <input type="text" id="organization" name="organization" required>
            <label for="sessions">Select Sessions:</label>
            <select id="sessions" name="sessions[]" multiple required>
                <option value="session1">Session 1 - Topic 1</option>
                <option value="session2">Session 2 - Topic 2</option>
                <option value="session3">Session 3 - Topic 3</option>
            </select>
            <input type="submit" name="submit" value="Register">
        </form>
        
        <?php
        // Check if the form has been submitted
        if (isset($_POST['submit'])) {
            $name = $_POST['name'];
            $email = $_POST['email'];
            $organization = $_POST['organization'];
            $selectedSessions = $_POST['sessions'];
 
            // Display the registration details
            echo "<h2>Registration Details:</h2>";
            echo "<p>Name: $name</p>";
            echo "<p>Email: $email</p>";
            echo "<p>Organization: $organization</p>";
            echo "<p>Selected Sessions:</p>";
            echo "<ul>";
            foreach ($selectedSessions as $session) {
                echo "<li>$session</li>";
            }
            echo "</ul>";
        }
        ?>
    </div>
</body>
</html>
OUTPUT SCREEN: 








Program 7 – Server Link Validation 
Coding : 
<?php 
if(isset($_POST['Submit'])){ 
$emp_name=trim($_POST["emp_name"]); 
$emp_number=trim($_POST["emp_number"]); 
$emp_email=trim($_POST["emp_email"]); 
if(!isset($emp_name) || $emp_name==""){ 
$errorMsg= "error: You did not enter a name."; 
$code="1"; 
} 
elseif($emp_number==""){ 
$errorMsg= "error: Please enter number."; 
$code="2"; 
} 
elseif(is_numeric(trim($emp_number))== false) { 
$errorMsg= "error: Please enter numeric value."; 
$code="2"; 
} 
elseif(strlen($emp_number)<10){ 
$errorMsg= "error: Number should be ten digits."; 
$code="2"; 
} 
elseif($emp_email==""){ 
$errorMsg= "error: You did not enter a email."; 
$code="3"; 
} 
elseif(!preg_match("/^[0-9a-zA-Z-]+@([0-9a-zA-Z][0-9a-zA-Z-]+\.)+[a-zA-Z]{2,6}$/i",  $emp_email)){ 
$errorMsg='error: You did not enter a valid email.';
$code="3"; 
} 
else{ 
echo "Success"; 
} 
} 
?> 
<html> 
<head> 
<meta charset="utf-8"> 
<title>Employee Information Sample HTML Form</title> 
<style type="text/css"> 
.errorMsg {border:1px solid red; } 
.message {color: red; font-weight:bold;} 
</style> 
</head> 
<body> 
<?php 
if (isset($errorMsg)) 
{ 
echo "<p class='message'>" .$errorMsg. "</p>"; 
} 
?> 
<form name="registration" id="registration" method="post" action=""> <table width="400" border="0" align="center" cellpadding= "4" cellspacing="1"> <tr> 
<td>Employee Name:</td> 
<td><input name="emp_name" type="text" id="emp_name" value="<?php  if(isset($emp_name)) {echo $emp_name;} ?>" 
<?php if(isset($code) && $code ==1) { echo "class=errorMsg" ;} ?>></td> </tr>
<tr> 
<td>Contact No.: </td> 
<td><input name="emp_number" type="text" id="emp_number" value="<?php  if(isset($emp_number)) {echo $emp_number;} ?>" 
<?php if(isset($code) && $code== 2) { echo "class=errorMsg";}?>></td> </tr> 
<tr> 
<td> Personal Email: </td> 
<td><input name="emp_email" type="text" id="emp_email" value="<?php  if(isset($emp_email)) {echo $emp_email; } ?>" 
<?php if(isset($code) && $code == 3) { echo "class=errorMsg" ;} ?>></td> </tr> 
<tr> 
<td></td> 
<td><input type="submit" name="Submit" value="Submit"></td> </tr> 
</table> 
</form> 
</body> 
</html>
OUTPUT SCREEN:


Program 8 – Cookies 
Coding : 
<?php 
if(!isset($_COOKIE['visits']))$_COOKIE['visits']=0; 
$visits=$_COOKIE['visits']+1; 
setcookie('visits',$visits,time()+3600*24*365); 
?> 
<html> 
<head><style type="text/css"> 
div{font-size:20pt;color:navy;font-family:arial black;width:50%;background-color:white} p{font-size:18pt;color:lime;font-weight:bold;text-align:center;font-family:bauhus93} .groove{border-style:groove} 
.dotted{border-style:dotted} 
</style></head><body bgcolor="salmon"> 
<?php  
echo'<br><br><center><div class="groove">HIT COUNTER USING  COOKIES</div><br>'; 
echo'<div class="dotted">'; 
if($visits>1){ 
 echo"<p>This is visit number $visits</p>";} 
 else { 
 echo'<p>Welcome to my Website! Click here for a tour!</p>';}  echo"<br></center></div>"; 
?></body></html>
OUTPUT SCREEN:




9.FILE READING AND WRITING IN PHP
CODING:

<!DOCTYPE html>
<html>
<head>
   <title>Read and Write File</title>
</head>
<body>
<?php
   // Specify the path to the file in your Downloads directory
   $filename = 'C:\Users\3bcc27\RKS\t.txt';
  
   // Check if the file exists
   if (!file_exists($filename)) {
       echo "File '$filename' does not exist.";
       exit();
   }
  
   // Reading from file
   $file = fopen($filename, "r");
   if ($file == false) {
       echo ("Error in opening file");
       exit();
   }
  
   $filesize = filesize($filename);
   $filetext = fread($file, $filesize);
   fclose($file);
  
   echo ("File size: $filesize bytes <br>");
   echo ("<pre>$filetext</pre>");
  
   // Writing to file
   $file = fopen($filename, "w");
   if ($file == false) {
       echo ("Error in opening file for writing");
       exit();
   }
  
   $text_to_write = "This is a simple test";
   fwrite($file, $text_to_write);
   fclose($file);
  
   // Reading from the same file again to display changes
   $file = fopen($filename, "r");
   if ($file == false) {
       echo ("Error in opening file for reading");
       exit();
   }
  
   $filesize = filesize($filename);
   $filetext = fread($file, $filesize);
   fclose($file);
  
   echo ("<br> File size after writing: $filesize bytes <br>");
   echo ("Content after writing: $filetext");
   echo ("<br> File name: $filename");
?>
</body>
</html>

OUTPUT:













                                      10.File / Image uploading in PHP

CODING:

Upload.html

<!DOCTYPE html>
<html>
<head>
<title>File Upload</title>
</head>
<body>
<h2>Upload a File</h2>
<form action="upload.php" method="post" enctype="multipart/form-data">
<input type="file" name="fileToUpload" id="fileToUpload">
<input type="submit" value="Upload File" name="submit">
</form>
</body>
</html>



Upload.php

<?php
$targetDir = "C:\21BCC027"; // Specify the directory where uploaded files will be stored
$targetFile = $targetDir . basename($_FILES["fileToUpload"]["name"]);
$uploadOk = 1; // Flag to check if upload is successful
// Check if the file is an actual image or fake image
if(isset($_POST["submit"])) {
$check = getimagesize($_FILES["fileToUpload"]["tmp_name"]);
if($check !== false) {
echo "File is an image - " . $check["mime"] . ".";
$uploadOk = 1;
} else {
echo "File is not an image.";
$uploadOk = 0;
}
}
// Check if the file already exists
if (file_exists($targetFile)) {
echo "Sorry, file already exists.";
$uploadOk = 0;
}
// Check file size
if ($_FILES["fileToUpload"]["size"] > 500000) { // You can adjust the file size limit
echo "Sorry, your file is too large.";
$uploadOk = 0;
}
// Allow only certain file formats
$allowedExtensions = array("jpg", "jpeg", "png", "gif");
$fileExtension = strtolower(pathinfo($targetFile, PATHINFO_EXTENSION));
if (!in_array($fileExtension, $allowedExtensions)) {
echo "Sorry, only JPG, JPEG, PNG & GIF files are allowed.";
$uploadOk = 0;
}
// Check if $uploadOk is set to 0 by an error
if ($uploadOk == 0) {
echo "Sorry, your file was not uploaded.";
// If everything is ok, try to upload file
} else {
if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $targetFile)) {
echo "The file ".
htmlspecialchars(basename($_FILES["fileToUpload"]["name"])) . " has been uploaded.";
} else {
    echo "Sorry, there was an error uploading your file.";
}
}
?>

OUTPUT SCREEN:







11.EXCEPTIONS IN PHP
CODE:
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Division Form</title>
</head>
<body>
    <form method="post">
        <label for="dividend">Enter dividend:</label>
        <input type="number" id="dividend" name="dividend" required><br><br>
        <label for="divisor">Enter divisor:</label>
        <input type="number" id="divisor" name="divisor" required><br><br>
        <button type="submit">Divide</button>
    </form>

    <?php
    class DivideByZeroException extends Exception { }  
    class DivideByNegativeNoException extends Exception { }  

    function checkdivisor($dividend, $divisor){  
        // Throw exception if divisor is zero or negative  
        try {  
            if ($divisor == 0) {  
                throw new DivideByZeroException;  
            }   
            else if ($divisor < 0) {  
                throw new DivideByNegativeNoException;   
            }   
            else {  
                $result = $dividend / $divisor;  
                echo "Result of division = $result </br>";  
            }  
        }  
        catch (DivideByZeroException $dze) {  
            echo "Divide by Zero Exception! </br>";  
        }  
        catch (DivideByNegativeNoException $dnne) {  
            echo "Divide by Negative Number Exception </br>";  
        }  
        catch (Exception $ex) {  
            echo "Unknown Exception";  
        }  
    }  

    // Check if form is submitted
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $dividend = $_POST["dividend"];
        $divisor = $_POST["divisor"];
        checkdivisor($dividend, $divisor);
    }
    ?>
</body>
</html>




OUTPUT:



12

<?php
$host = "localhost";
$username = "root";
$password = "";
$database = "php_student_registration";

$conn = new mysqli($host, $username, $password, $database);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Check if the form is submitted for registering a student
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = $_POST['name'];
    $email = $_POST['email'];
    $phone = $_POST['phone'];
    $address = $_POST['address'];
    $gender = $_POST['gender'];
    $department = $_POST['department'];
    $parttime = isset($_POST['parttime']) ? 1 : 0;
    $joinedDate = $_POST['joined_date'];

    $sql = "INSERT INTO students (name, email, phone, address, 
            gender, department, parttime, joined_date) 
            VALUES ('$name', '$email', '$phone', '$address', 
            '$gender', '$department', $parttime, '$joinedDate')";

    if ($conn->query($sql) === TRUE) {
        echo "Student registered successfully!";
    } else {
        echo "Error: " . $sql . "<br>" . $conn->error;
    }
}

// Fetch and display registered students
$sql = "SELECT * FROM students";
$result = $conn->query($sql);
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Registration</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">

</head>
<body >
    <div class="container-fluid" >
        <div class="row bg-dark p-2">
            <h3 class="text-white">PHP Project</h3>
        </div>
        <div class="row bg-info">
            <div class="col-6">
                <h2>Student Registration</h2>
                <form action="" method="post">
                    <label for="name">Student Name:</label>
                    <input type="text" name="name" required><br>
        
                    <label for="email">Student Email:</label>
                    <input type="email" name="email" required><br>
        
                    <label for="phone">Phone:</label>
                    <input type="tel" name="phone" required><br>
        
                    <label for="address">Address:</label>
                    <textarea name="address" rows="3" required></textarea><br>
        
                    <label for="gender">Gender:</label>
                    <select name="gender" required>
                        <option value="Male">Male</option>
                        <option value="Female">Female</option>
                        <option value="Other">Other</option>
                    </select><br>
        
                    <label for="department">Department:</label>
                    <input type="text" name="department" required><br>
        
                    <label for="parttime">Part-time Student:</label>
                    <input type="checkbox" name="parttime"><br>
        
                    <label for="joined_date">Joined Date:</label>
                    <input type="date" name="joined_date" required><br>
        
                    <button type="submit">Register Student</button>
                </form>
            </div>
            <div class="col-6">
            <h3>Registered Students</h3>
            <?php
                if ($result->num_rows > 0) {
                    echo "<ul>";
                    while ($row = $result->fetch_assoc()) {
                        echo "<li>{$row['name']} - {$row['email']} ({$row['joined_date']})</li>";
                    }
                    echo "</ul>";
                } else {
                    echo "No students registered.";
                }
                $conn->close();
            ?>
            </div>
        </div>
    </div>
</body>
</html>

sql:
USE php_student_registration;

-- Create a table for students
CREATE TABLE IF NOT EXISTS students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    phone VARCHAR(20) NOT NULL,
    address VARCHAR(255) NOT NULL,
    gender ENUM('Male', 'Female', 'Other') NOT NULL,
    department VARCHAR(50) NOT NULL,
    parttime BOOLEAN NOT NULL,
    joined_date DATE NOT NULL
);

Program 13 – MySQL Functions 
Coding : 
<?php 
$host = "localhost"; 
$username = "root"; 
$password = ""; 
$database = "mydatabase"; 
// Connect to the MySQL database 
$cn = mysqli_connect($host, $username, $password, $database); if ($cn->connect_error) { 
 die("Connection failed: " . $cn->connect_error); 
} 
// Check if the form has been submitted 
if (isset($_POST['submit'])) { 
 // Get the input values from the form 
 $user_input_fullname = $_POST['fullname']; 
 $user_input_id = $_POST['id']; 
 // Use prepared statements to prevent SQL injection attacks 
 $stmt = $cn->prepare("INSERT INTO test_table (fullname, id) VALUES (?, ?)");  $stmt->bind_param("si", $user_input_fullname, $user_input_id);  if ($stmt->execute()) { 
 echo "Thank you for registering. Your registration ID is: " . $user_input_id;  } else { 
 echo "Error: " . $stmt->error; 
 } 
 $stmt->close(); 
} 
?> 
<html> 
 <body> 
 <h1>Registration</h1> 
 <form action="" method="post"> 
 Your full name:<br> 
 <input type="text" name="fullname"><br> 
 Your ID:<br> 
 <input type="text" name="id"><br> 
 <input type="submit" name="submit" value="Register">  </form> 
 </body> 
</html>


14.Laravel
cmd
composser -v
php -v
path:
D:-learn - workspace any folder

cmd
composser create-project laravel/laravel student-reg
for error
c->zamp -> php folder-> php.ini file drag into the vs code in line 892 
go to line 962 remove the ; infront of the extension
cd student-reg
php artisan serve


vs code:
vapp
web.php
.env
migration:

php artisan make:controller studentcontroller
php artisan make:model student
php artisan make:migration create_-students_-table
extension:
student-reg.blade.php
in html code add @csrf in line 58
