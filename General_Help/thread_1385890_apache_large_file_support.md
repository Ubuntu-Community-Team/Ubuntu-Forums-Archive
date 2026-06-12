---
title: "apache large file support"
date: 2010-01-20
forum: General Help
---

### Post by al_mic on 2010-01-20
hello,

i read about how apache knows about large file support (>2GB) from version 2.2
but from what i searched, i found only how to make this by compiling apache from sources.

do you know if this large file support is enabled when installing apache with apt-get?
or if is any way to activate it if it was installed with apt?
in my httpd.conf or other files i did not found any such value being set.

links:
[http://httpd.apache.org/docs/2.2/new_features_2_2.html](http://httpd.apache.org/docs/2.2/new_features_2_2.html)
[http://beranger.org/index.php?article=1410&page=3k](http://beranger.org/index.php?article=1410&page=3k)

thanks!

---

### Post by amsterdamharu on 2010-01-20
Is it not working?

[http://beranger.org/index.php?article=1410&page=3k](http://beranger.org/index.php?article=1410&page=3k)
Says:
"...recent 2.4.x or 2.6.x kernel"
My Ubuntu 8.04 uses kernel 2.6.24-26-generic so should not be a problem.
[http://httpd.apache.org/docs/2.2/new_features_2_2.html](http://httpd.apache.org/docs/2.2/new_features_2_2.html)
"[httpd]("http://httpd.apache.org/docs/2.2/programs/httpd.html") is now built with support for files larger           than 2GB on modern 32-bit Unix systems.  Support for handling           >2GB request bodies has also been added."
My synaptic package manager says that apache version 2.2.8 is available.

I gues the httpd.conf might have a file size limit (for uploads) and php.ini as well (for uploads).

---

### Post by al_mic on 2010-01-20
i see it does not.

on a 32 bit server i was first receiving these errors:
[Wed Jan 20 12:10:04 2010] [error] [client ] PHP Warning:  POST Content-Length of 2147483647 bytes exceeds the limit of 1073741824 bytes in Unknown on line 0, referer: 

[Wed Jan 20 12:10:04 2010] [error] [client ] Requested content-length of 4135698643 is larger than the configured limit of 2147483647, referer: 

but then i've placed in the httpd.conf:
LimitRequestBody 4147483647  #in apche docs max is 2GB so.. i'm surprised it worked.

and this helped me solve the apache error message, but is still receive the php warning
[Wed Jan 20 13:44:33 2010] [error] [client ] PHP Warning:  POST Content-Length of 2147483647 bytes exceeds the limit of 1073741824 bytes in Unknown on line 0, referer: 

i don't know if is from php, because i have:
upload_max_filesize    5120M    
 post_max_size    5120M
in php.ini


in the end, i tried intalling apache on a 64 bit ubuntu
this time i got no errors in my error.log but after about 30 second the connection is lost:
Error 101 (net::ERR_CONNECTION_RESET): Unknown error.  (Chrome say)
but in php.ini i have:
max_execution_time = 7200 

so .. what could be?
how to make apache and php work with large file support?

---

### Post by al_mic on 2010-01-20
this is the php script that i use to upload:
 (/mnt/upload dir is owned by apache user)
upload.php

<?php
if(!empty($_FILES['video']['name'])) {
        move_uploaded_file($_FILES['video']['tmp_name'], '/mnt/upload/' . $_FILES['video']['name']);
        echo 'done';
        exit();
}
?>
<html>
<head>
</head>

<body>
        <form method="POST" enctype="multipart/form-data" action="upload.php">
        <input type="file" name="video" />
        <input type="submit" value="Save" />
        </form>
</body>
</html>

---

