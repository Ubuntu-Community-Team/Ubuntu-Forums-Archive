---
title: "FTP problem"
date: 2009-09-16
forum: General Help
---

### Post by Strega on 2009-09-16
Hello,

I've a problem with my FTP.
I made a user with the useradd command and set a password.
Everything goes well, I can login and download files from the server, but I can't upload files to it.
This is the error on a single file upload :
```
WD  
257 "/home/strega/public_html/img"  
TYPE A  
200 Switching to ASCII mode.  
PASV  
227 Entering Passive Mode (188,40,79,137,62,71)  
STOR index.php  
Connect socket #824 to 188.40.79.137, port 15943...
553 Could not create file.  
index.php - 0 bytes transferred  
PASV  
227 Entering Passive Mode (188,40,79,137,210,149)  
LIST  
Connect socket #828 to 188.40.79.137, port 53909...
150 Here comes the directory listing.  
226 Directory send OK.  
TYPE A  
200 Switching to ASCII mode.  
PASV  
227 Entering Passive Mode (188,40,79,137,152,150)  
STOR index.php  
Connect socket #824 to 188.40.79.137, port 39062...
553 Could not create file.  
index.php - 0 bytes transferred  
PASV  
227 Entering Passive Mode (188,40,79,137,245,21)  
LIST  
Connect socket #828 to 188.40.79.137, port 62741...
150 Here comes the directory listing.  
226 Directory send OK.  
TYPE A  
200 Switching to ASCII mode.  
PASV  
227 Entering Passive Mode (188,40,79,137,239,104)  
STOR index.php  
Connect socket #824 to 188.40.79.137, port 61288...
553 Could not create file.  
index.php - 0 bytes transferred  
PASV  
227 Entering Passive Mode (188,40,79,137,106,140)  
LIST  
Connect socket #828 to 188.40.79.137, port 27276...
150 Here comes the directory listing.  
226 Directory send OK.  
TYPE A  
200 Switching to ASCII mode.  
PASV  
227 Entering Passive Mode (188,40,79,137,110,167)  
STOR index.php  
Connect socket #824 to 188.40.79.137, port 28327...
553 Could not create file.  
index.php - 0 bytes transferred  
PASV  
227 Entering Passive Mode (188,40,79,137,51,117)  
LIST  
Connect socket #828 to 188.40.79.137, port 13173...
150 Here comes the directory listing.  
226 Directory send OK.  
TYPE A  
200 Switching to ASCII mode.  
PASV  
227 Entering Passive Mode (188,40,79,137,100,232)  
STOR index.php  
Connect socket #824 to 188.40.79.137, port 25832...
553 Could not create file.  
index.php - 0 bytes transferred  
PASV  
Transfer time: 00:00:01  
227 Entering Passive Mode (188,40,79,137,35,205)  
LIST  
Connect socket #852 to 188.40.79.137, port 9165...
150 Here comes the directory listing.  
226 Directory send OK.  
Transferred 64 bytes in 0.001 seconds  
```
Does anybody know what the problem is and how to solve it ?

Regards, Strega

---

### Post by dandnsmith on 2009-09-16
I think, subject to correction, that it may be the combination of passive mode and password with a requirement to upload which is killing you.
I believe that passive mode is only used for download from a server (as you can see, the directory listing works)

---

### Post by ChumleyEX on 2009-09-16
What ftp server are you using and is there a place in the .config file to allow uploading?

---

