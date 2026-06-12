---
title: "DVD image file size only 46.1 MB?!"
date: 2011-05-30
forum: General Help
---

### Post by tlc8126 on 2011-05-30
Hello!

I am new to the forums.  Please excuse me if this isn't the correct place for posting this information/question.

After screwing up an update to Ubuntu 11.04 I decided to do a clean install.  I tried downloading the AMD64 DVD image of 11.04 but I have found that some of the files cannot be downloaded and appear to have bad file size.  In several mirrors and repositories I found the image size to be only 46.1 MB!  (Yes, thats "Mega"-bytes, not Giga-bytes.  I ftp'd to the repositories/mirror sites and confirmed this.)  Yet in many of the HTTP pages it shows as 4.0 GB.

I  can't believe that the true size is 46.1 MB as the i386 DVD image is over 3 GB.  4.0 GB sound right, but doesn't match the actual file size.  :(So, how long until it gets updated?  

Thanks.

---

### Post by WorMzy on 2011-05-30
Where are you downloading from? Download from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Btw, the normal install CD iso is about 700MB.

---

### Post by crispy_420 on 2011-05-30
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/natty/release/ubuntu-11.04-dvd-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/natty/release/ubuntu-11.04-dvd-i386.iso)

My guess: corrupt download or wrong item downloaded.

---

### Post by Metaxa on 2011-05-30
I have encountered the same problem when trying to make an ISO from a DVD of a friends wedding. Don't know what the deal was.

---

### Post by dFlyer on 2011-05-30
> **tlc8126 said:**
> Hello!

I am new to the forums.  Please excuse me if this isn't the correct place for posting this information/question.

After screwing up an update to Ubuntu 11.04 I decided to do a clean install.  I tried downloading the AMD64 DVD image of 11.04 but I have found that some of the files cannot be downloaded and appear to have bad file size.  In several mirrors and repositories I found the image size to be only 46.1 MB!  (Yes, thats "Mega"-bytes, not Giga-bytes.  I ftp'd to the repositories/mirror sites and confirmed this.)  Yet in many of the HTTP pages it shows as 4.0 GB.

I  can't believe that the true size is 46.1 MB as the i386 DVD image is over 3 GB.  4.0 GB sound right, but doesn't match the actual file size.  :(So, how long until it gets updated?  

Thanks.

Download from: [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/11.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/11.04/release/)

The file size is 4 gig for the AMD64

---

### Post by tlc8126 on 2011-05-31
Thanks for all your replies.

I had tried the "mirror.anl.gov" HTTP site, and still I could only get 46.1 MB.  

Since I want the amd64 DVD ISO image using the normal download from the "http://www.ubuntu.com/download/ubuntu/download" link on the downloads web page wouldn't suit me.

I again logged on to the 'cdimage.ubuntu.com' site via anonymous FTP and can confirm that the file is > 4.34 GB (See FTP listing below).  So, I can assume this is now a software problem.  Either the server is responding with the wrong file size, or my WGET, FTP, and HTTP download programs are having problems. ](*,)

ftp> ls
229 Entering Extended Passive Mode (|||28279|).
150 Here comes the directory listing.
-rw-rw-r--    1 1000     1000           27 Apr 28 09:18 FOOTER.html
-rw-rw-r--    1 1000     1000         5333 Apr 28 09:18 HEADER.html
-rw-rw-r--    1 1000     1000          609 Apr 28 09:18 MD5SUMS
-rw-rw-r--    1 1000     1000          281 Apr 28 09:18 MD5SUMS-metalink
-rw-rw-r--    1 1000     1000          198 Apr 28 09:18 MD5SUMS-metalink.gpg
-rw-rw-r--    1 1000     1000          198 Apr 28 09:18 MD5SUMS.gpg
-rw-rw-r--    1 1000     1000          673 Apr 28 09:18 SHA1SUMS
-rw-rw-r--    1 1000     1000          198 Apr 28 09:18 SHA1SUMS.gpg
-rw-rw-r--    1 1000     1000          865 Apr 28 09:18 SHA256SUMS
-rw-rw-r--    1 1000     1000          198 Apr 28 09:18 SHA256SUMS.gpg
drwxrwsr-x    2 1000     1000         4096 Apr 28 08:46 source
-rw-rw-r--    1 1000     1000     731273216 Apr 26 12:59 ubuntu-11.04-alternate-amd64+mac.iso
-rw-rw-r--    1 1000     1000        28131 Apr 28 09:17 ubuntu-11.04-alternate-amd64+mac.iso.torrent
-rw-rw-r--    1 1000     1000      1428516 Apr 28 09:17 ubuntu-11.04-alternate-amd64+mac.iso.zsync
-rw-rw-r--    1 1000     1000       155707 Apr 28 09:17 ubuntu-11.04-alternate-amd64+mac.jigdo
-rw-rw-r--    1 1000     1000       111255 Apr 26 12:59 ubuntu-11.04-alternate-amd64+mac.list
-rw-rw-r--    1 1000     1000         1039 Apr 28 09:18 ubuntu-11.04-alternate-amd64+mac.metalink
-rw-rw-r--    1 1000     1000      2904637 Apr 26 12:59 ubuntu-11.04-alternate-amd64+mac.template
-rw-rw-r--    1 1000     1000     727494656 Apr 27 17:06 ubuntu-11.04-desktop-amd64+mac.iso
-rw-rw-r--    1 1000     1000        27989 Apr 28 09:18 ubuntu-11.04-desktop-amd64+mac.iso.torrent
-rw-rw-r--    1 1000     1000      1421128 Apr 28 09:18 ubuntu-11.04-desktop-amd64+mac.iso.zsync
-rw-rw-r--    1 1000     1000         4148 Apr 27 17:06 ubuntu-11.04-desktop-amd64+mac.list
-rw-rw-r--    1 1000     1000        41370 Apr 25 23:10 ubuntu-11.04-desktop-amd64+mac.manifest
-rw-rw-r--    1 1000     1000         1033 Apr 28 09:18 ubuntu-11.04-desktop-amd64+mac.metalink
-rw-rw-r--    1 1000     1000     4343263232 Apr 27 10:53 ubuntu-11.04-dvd-amd64.iso    " <== I want this one. "
-rw-rw-r--    1 1000     1000        83083 Apr 28 08:28 ubuntu-11.04-dvd-amd64.iso.torrent
-rw-rw-r--    1 1000     1000      8483161 Apr 28 08:26 ubuntu-11.04-dvd-amd64.iso.zsync
-rw-rw-r--    1 1000     1000       203876 Apr 27 10:54 ubuntu-11.04-dvd-amd64.list
-rw-rw-r--    1 1000     1000        74512 Apr 26 02:36 ubuntu-11.04-dvd-amd64.manifest
-rw-rw-r--    1 1000     1000         1010 Apr 28 09:18 ubuntu-11.04-dvd-amd64.metalink
-rw-rw-r--    1 1000     1000     4217223168 Apr 27 11:02 ubuntu-11.04-dvd-i386.iso
-rw-rw-r--    1 1000     1000        80662 Apr 28 08:28 ubuntu-11.04-dvd-i386.iso.torrent
-rw-rw-r--    1 1000     1000      8236991 Apr 28 08:27 ubuntu-11.04-dvd-i386.iso.zsync
-rw-rw-r--    1 1000     1000       206014 Apr 27 11:02 ubuntu-11.04-dvd-i386.list
-rw-rw-r--    1 1000     1000        74620 Apr 26 02:35 ubuntu-11.04-dvd-i386.manifest
-rw-rw-r--    1 1000     1000         1007 Apr 28 09:18 ubuntu-11.04-dvd-i386.metalink
-rw-rw-r--    1 1000     1000     213526225 Apr 26 17:34 ubuntu-11.04-preinstalled-headless-armel+omap.img.gz
-rw-rw-r--    1 1000     1000     38569605 Apr 28 08:36 ubuntu-11.04-preinstalled-headless-armel+omap.img.gz.zsync
-rw-rw-r--    1 1000     1000     206297958 Apr 26 05:51 ubuntu-11.04-preinstalled-headless-armel+omap4.img.gz
-rw-rw-r--    1 1000     1000     38502774 Apr 28 08:36 ubuntu-11.04-preinstalled-headless-armel+omap4.img.gz.zsync
-rw-rw-r--    1 1000     1000     565388235 Apr 26 19:32 ubuntu-11.04-preinstalled-netbook-armel+omap.img.gz
-rw-rw-r--    1 1000     1000     50172252 Apr 28 08:34 ubuntu-11.04-preinstalled-netbook-armel+omap.img.gz.zsync
-rw-rw-r--    1 1000     1000     558112546 Apr 26 05:36 ubuntu-11.04-preinstalled-netbook-armel+omap4.img.gz
-rw-rw-r--    1 1000     1000     50027285 Apr 28 08:32 ubuntu-11.04-preinstalled-netbook-armel+omap4.img.gz.zsync
226 Directory send OK.
ftp> 


I have seen this kind of download issue before with older FTP programs, but haven't had problems with the Ubuntu/Canonical files before...

Thanks for all your help, I post if I find anything useful to others.

---

### Post by tlc8126 on 2011-05-31
I guess I'm not as smart as I think I am!  :oops:

I finally got past the 46MB mark using anonymous FTP, and WGET seems to have no problem  continuing the download (FTP resume function working normally).

Sorry for the confusion.  The problem seems to be particular to HTTP downloads.  I can't say this is not my software, but FTP has no problem and I'm now at over 110 MB! (Anyone know of any download bugs in HTTP?)

Thanks again for your posts!

---

