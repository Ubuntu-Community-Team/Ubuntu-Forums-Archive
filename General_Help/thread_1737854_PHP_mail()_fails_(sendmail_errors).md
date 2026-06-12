---
title: "PHP mail() fails (sendmail errors)"
date: 2011-04-24
forum: General Help
---

### Post by Chesamo on 2011-04-24
I have an application form (it's currently residing at [http://sublevel21.tk/minecraft/whitelist.html](http://sublevel21.tk/minecraft/whitelist.html) ) that needs to send an email to me. I've installed sendmail and enabled it in /etc/php5/apache2/php.ini using the ```
sendmail_path=/usr/sbin/sendmail -t -i
``` parameter. On my web pages, the PHP mail succeeds; however, the mail is never sent and stalls in mailq. When I run mailq, I get errors such as ```
p3O2qDv1003455       92 Sat Apr 23 22:52 <www-data@watson.home>
                 (Deferred: Connection timed out with mx0.gmx.com.)
                                         <chesamo@engineer.com>
``` sendmail is flat-out refusing to work on external domains. How the heck can I get this working?

The PHP is below.

```
<?php

// Email address to send to
$myemail="chesamo@engineer.com";

// email subject
$emailsubject="SCG Minecraft Whitelist Request";

// Mail priority (for lulz)
$priority="3"; 

// Message displayed after a sucessful send
$thanksmessage="Request sent! You should hear from us soon.";

// Message to be shown when **** goes wrong.
$formphail="Something went wrong... Send your application directly to chesamo@engineer.com and tell him this form stopped working.";

//Keep haxxors from passing headers

function clean_msg($key) {
	$key=str_replace("\r", "", $key);
	$key=str_replace("\n", "", $key);
	$find=array(
		"/bcc\:/i",
		"/Content\-Type\:/i",
		"/Mime\-Type\:/i",
		"/cc\:/i",
		"/to\:/i"
	);
  $key=preg_replace($find, "", $key);
  return $key;
}

// GOGO VARIABLES
$error="";
$sent_mail=false;

$yourname = $_POST['title'];
$yourvoucher = $_POST['voucher'];
$youremail = $_POST['email'];
$yourmessage = $_POST['extra'];

		// Check the form for errors
		If(trim($yourname)=="") { 
			$error.="You did not enter your name!<br />";
		}
		
		If(trim($youremail)=="") { 
			$error.="You did not enter your email address!<br />";
		} Elseif(!preg_match("/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,})+$/", $youremail)) {
			$error.="Invalid email address.<br />";
		}

		If(trim($yourvoucher)=="") { 
			$error.="You forgot to tell us who sent you!<br />";
		}
		

	if($error) {
	
		$display_message=$error;
		echo $error;
		exit("<a href='whitelist.html'>Go Back</a>");
		

	} else {
		
		$boundary=md5(uniqid(time()));
		
		//Headers
		$headers="Return-Path: <".clean_msg($youremail).">\n";
		$headers.="From: ".clean_msg($yourname)." <do-not-reply@sublevel21.tk>\n";
		$headers.="X-Mailer: PHP/".phpversion()."\n";
		$headers.="X-Sender: ".$_SERVER['REMOTE_ADDR']."\n";
		$headers.="X-Priority: ".$priority."\n"; 
		$headers.="MIME-Version: 1.0\n";
		$headers.="Content-Type: text/plain; charset=\"iso-8859-1\"\n";
		$headers.="Content-Transfer-Encoding: 7bit\n";
		//Message

		$message.="\r\n";
		$message.="From MC User: ".$yourname."\r\n";
		$message.="Voucher: ".$yourvoucher."\r\n";
		$message.="Email Address: ".$youremail."\r\n";
		$message.="Message: \r\n".$yourmessage."\r\n";
		// End the message
		// Send the completed message
		If(!mail($myemail, clean_msg($emailsubject), $message, $headers)) {
			
			Exit($formphail."\n");
			?>
			<script type="text/javascript">
			window.location = "whitelist_phail.html"
			</script>
			
	<?	} Else {	?>
		
			<script type="text/javascript">
			window.location = "whitelist_success.html"
			</script>
			<?
		}

	} // Else
?>

```

---

### Post by mörgæs on 2011-04-24
Have you tried this forum?
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

