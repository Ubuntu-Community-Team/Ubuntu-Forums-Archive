---
title: "PHP script, Upload and submit script not working."
date: 2011-08-02
forum: General Help
---

### Post by scottykal12 on 2011-08-02
Can some one please explain why this script does not work?

I think the problem comes from somewhere at the TMP name because I cannot  even get it to echo the TMP info.

```
<?php

$filename = $_FILES['file']['name'];
//$filesize = $_FILES['file']['size'];
//$filetype= $_FILES['file']['type'];
$tmp_name = $FILES['file']['tmp_name'];
 


if (isset($filename)) {
    if(!empty($filename)){
    
    $location = 'Scott/';
    
    if (move_uploaded_file ($tmp_name, $location.$filename)) {
     echo 'Beer served!';
    }
    
    } else{
     echo 'Please choose file.';
    }
}

?>
<form action ="upload.php" method="POST" enctype="multipart/form-data">
    <input type="file" name="file">
    <input type="submit" value="Serve">
</form>

<html>
<a href=Scott> My Fridge</a>
<html>
```I know this is not secure so no need to tell me.

---

### Post by scottykal12 on 2011-08-02
More info: I can get it to echo the file name size and type but not the tmp_name.... think it is not saving to the tmp file maybe? I'm using Ubuntu 11.04 if it helps.

---

### Post by toniknik1982 on 2011-10-19
Does apache have write-access to your Document-Root Folder? Link could help you...

[http://superuser.com/questions/19318/how-can-i-give-write-access-of-a-folder-to-all-users-in-linux](http://superuser.com/questions/19318/how-can-i-give-write-access-of-a-folder-to-all-users-in-linux)

---

