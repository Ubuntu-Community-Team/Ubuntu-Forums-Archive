---
title: "Increase the upload limit from 2GB to 5GB"
date: 2012-10-10
forum: General Help
---

### Post by neo_one2199 on 2012-10-10
Hi

I'm currently running Ubuntu Server 12.04 64bit and I setup Apache 2.2 web server. I set my php.ini 'upload_max_filesize' 'post_max_size' to 5000M but when I try to upload a file with 2.8GB size I get error!

I checked my apache error log file and I have this: 
```
Invalid Content-Length, referer: http://mydomain.com/examples/
```I also google this and some people say that "You have to set LimitRequestBody 0 in httpd.conf" so I did that also but still same error.

When I upload anything less than 2GB exact there is** no **problem!

Any idea, what am I missing?? :-k

---

### Post by spjackson on 2012-10-10
What sort of filesystem are you uploading to? It isn't FAT is it?

---

### Post by neo_one2199 on 2012-10-10
it's ext4

---

### Post by spjackson on 2012-10-11
The documentation entry for [LimitRequestBody]("http://httpd.apache.org/docs/2.2/mod/core.html#limitrequestbody") says:
> 
This directive specifies the number of bytes from 0 (meaning unlimited) to 2147483647 (2GB) that are allowed in a request body.
It sounds like "unlimited" might mean 2GB in practice.

---

### Post by jwbrase on 2012-10-11
Is the file you're trying to upload compressed or uncompressed?

If it's uncompressed, try compressing it to see if you can get it below 2GB.

If it's compressed, try using "split" on it before uploading, then piecing it back together with "cat" on the server. Zip archives can also be split by "zip" (with the s option).

---

### Post by plucky on 2012-10-11
I interpreted that statement to mean that if you set the value to 0,you will get unlimited uploads.

I could be wrong

Good luck

---

### Post by spjackson on 2012-10-11
> **plucky said:**
> I interpreted that statement to mean that if you set the value to 0,you will get unlimited uploads.

I could be wrong

Interesting, that is a natural way to read it. However, "unlimited" cannot possibly mean infinite. Apache cannot store a file bigger than the filespace available, for example, or larger than what is supported by the host filesystem type. The question arises why can't you specify a limit of 2.1GB or 3GB or 1TB or...?

[http://httpd.apache.org/docs/2.2/new_features_2_2.html]("http://httpd.apache.org/docs/2.2/new_features_2_2.html") "Large File Support. httpd is now built with support for files larger than 2GB on modern 32-bit Unix systems. Support for handling >2GB request bodies has also been added."

Someone has successfully set a limit > 2GB, so that might be worth a try. See [http://ubuntuforums.org/showthread.php?t=1385890]("http://ubuntuforums.org/showthread.php?t=1385890") but then hit timeout errors.

Is http really the ideal protocol for transferring files larger than 2GB?

---

### Post by neo_one2199 on 2012-10-11
Hi,

Thanks for your replies!

I changed the LimitRequestBody to 5368709120 (5GB) Also I install [PECL Upload Progress]("http://pecl.php.net/package/uploadprogress") to check the uploading progress and used their Example php files to do a test upload.

On my Google Chrome The Upload Starts but it's saying -1% -2% -3% -4% and ....

On Firefox I get the Connection Was reset. and no progress details!

I don't want to compress my files that wouldn't help me.

---

### Post by neo_one2199 on 2012-10-11
> 
Someone has successfully set a limit > 2GB, so that might be worth a try. See [http://ubuntuforums.org/showthread.php?t=1385890](http://ubuntuforums.org/showthread.php?t=1385890) but then hit timeout errors.

this was the first thing I found when I googled this problem and didn't work for me! ](*,)

---

### Post by spjackson on 2012-10-11
Well it could be the client that is setting an invalid length (e.g. negative) if the size is >2GB. What client are you using?

As a diagnostic tool (not for production) you could enable the log_forensic module and configure a log file for forensic logging. This will enable you to see the content-length that is being sent by the client.

---

### Post by neo_one2199 on 2012-10-11
Hi spjackson,

Thanks for your reply. I will try that.

I also found out if you upload more than than your limit using [PECL Upload Progress]("http://pecl.php.net/package/uploadprogress") will give you negative result.

Also I tried their example PHP file on Safari and this is the result  "[COLOR=#000000][FONT=Times New Roman]Infinity% done".
[/FONT][/COLOR]

---

### Post by neo_one2199 on 2012-10-11
I also read this article about httpd.conf on ubuntu [http://ubuntugods.com/httpd-conf-location-ubuntu](http://ubuntugods.com/httpd-conf-location-ubuntu) since Main configuration of Apache is apache2.conf. Shall I put the LimitRequestBody in my "apache2.conf"?

------------------------

here is my php.ini:
upload_max_filesize = 10240M
max_execution_time = 7200
max_input_time = 7200
memory_limit = 20480M
post_max_size = 10240M

---

### Post by shreepads on 2012-10-11
Stupid question, did you restart or reload httpd after changing httpd.conf?

---

### Post by neo_one2199 on 2012-10-11
LOL

Yep I did! No Result!

---

