---
title: "So I built this upload script...."
date: 2010-10-31
forum: General Help
---

### Post by YungKris15 on 2010-10-31
But I need some help. I built part of this script off a tut, and did the rest myself however, I want it so it send the information into a database. 

What I want is, once a user uploads an image, it can also be deleted by that user with the code given.
I have made the html, bbcode & direct link. I want an option for a box where it shows Delete link....

here's my FULL php upload script.

> 
<?php
define ("MAX_SIZE","100000"); 
function getExtension($str) {
$i = strrpos($str,".");
if (!$i) { return ""; }
$l = strlen($str) - $i;
$ext = substr($str,$i+1,$l);
return $ext;
}
$errors=0;
if(isset($_POST['Submit'])) 
{
$image=stripslashes($_FILES['image']['name']);
if ($image) 
{
$filename = stripslashes($_FILES['image']['name']);
$extension = getExtension($filename);
$extension = strtolower($extension);
if (($extension != "jpg") && ($extension != "jpeg") && ($extension != "mov") && ($extension !="PNG") && ($extension !="bmp") && ($extension != "png") && ($extension != "gif")) 
{

echo '<font color="red"><b>Extension not allowed</b></font><br>';
$errors=1;
}
else
{
$size=filesize($_FILES['image']['tmp_name']);


if ($size > MAX_SIZE*100000)
{
echo 'You have exceeded the size limit!';
$errors=1;
}

$image_name=time().'.'.$extension;

$newname="images/".$image_name;

$fullname="http://www.maniaupload.net/".$newname;



$copied = copy($_FILES['image']['tmp_name'], $newname);
if (!$copied) 
{
echo '<font color=\"red\"><b>Upload Unsuccessful! Try Again?</b></font>';
$errors=1;
}}}}

if(isset($_POST['Submit']) && !$errors) 
{
echo "File Uploaded Successfully! <br /><br /> <img src=\"$newname\" /> <br /><br /> 

<b>Direct Image Link:</b><br/><table width=\"338\" border=\"0\" cellpadding=\"0\" cellspacing=\"0\" id=\"Table1\">
<tr>
<td align=\"center\" valign=\"middle\"><textarea readonly name=\"message\" rows=\"1\" cols=\"50\">$fullname</textarea></td>
</tr>
</table></center><br>

<b>HTML Code:</b><br/><table width=\"338\" border=\"0\" cellpadding=\"0\" cellspacing=\"0\" id=\"Table1\">
<tr>
<td align=\"center\" valign=\"middle\"><textarea readonly name=\"message\" rows=\"1\" cols=\"50\">
<a href=\"$fullname\" target=\"_blank\"><img border=\"0\" src=\"$fullname\"></a>
</textarea></td>
</tr>
</table><br>

<b>BBCode <font color=\"red\">*NEW*</font></b><br>
<table width=\"338\" border=\"0\" cellpadding=\"0\" cellspacing=\"0\" id=\"Table1\">
<tr>
<td align=\"center\" valign=\"middle\">
<textarea readonly name=\"message\" rows=\"1\" cols=\"50\">
[IMG] $fullname [/IMG]
</textarea></td>
</tr>
</table><br>
";
}

?>

I think it involves MYSQL, I'm still learning. Would anyone happen to know how to do this? or show me a tut or something. I just need this thing. 

I have more code but its not needed, its outside of the php tags. But can anyone help please. It's just adding a delete link so users can delete it if they choose.

Thanks.

---

