---
title: "Citrix xen app"
date: 2011-05-12
forum: General Help
---

### Post by agemini68 on 2011-05-12
I am trying to access my work website and I have to use a citrix xen app to get there. I found the linux version of the app, but when I hit the inside.healthsouth logo, I get a client error message. Just look at the screenshot in the attachment.  Is there a way to fix it?

---

### Post by noah++ on 2011-05-12
[This?]("http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex") (via the Googles)

---

### Post by agemini68 on 2011-05-12
None of those seem to be working in ubunto 10.10.

I tried the solutions in the above post and I can't seem to get it to work. I'm using 10.10. Copy of my terminal:

```
donna@donna-HP-dx2000-MT-DR547AV:~$ CERTINSTALLDIR="/usr/lib/ICAClient/keystore/cacerts"
donna@donna-HP-dx2000-MT-DR547AV:~$ STARTDIR=$PWD
donna@donna-HP-dx2000-MT-DR547AV:~$ #echo $CERTINSTALLDIR
donna@donna-HP-dx2000-MT-DR547AV:~$ #exit
donna@donna-HP-dx2000-MT-DR547AV:~$ echo Current directory is: $STARTDIR
Current directory is: /home/donna
donna@donna-HP-dx2000-MT-DR547AV:~$ echo Creating temp download dir in $STARTDIR...
Creating temp download dir in /home/donna...
donna@donna-HP-dx2000-MT-DR547AV:~$ mkdir cert_download
donna@donna-HP-dx2000-MT-DR547AV:~$ cd cert_download
donna@donna-HP-dx2000-MT-DR547AV:~/cert_download$ echo Fetching Thawte Root Certs...
Fetching Thawte Root Certs...
donna@donna-HP-dx2000-MT-DR547AV:~/cert_download$ wget [https://www.verisign.com/support/thawte-roots.zip](https://www.verisign.com/support/thawte-roots.zip)
--2011-05-12 13:18:04--  [https://www.verisign.com/support/thawte-roots.zip](https://www.verisign.com/support/thawte-roots.zip)
Resolving [www.verisign.com](www.verisign.com)... 69.58.181.89
Connecting to [www.verisign.com|69.58.181.89|:443](www.verisign.com|69.58.181.89|:443)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30539 (30K) [application/zip]
Saving to: `thawte-roots.zip'

100%[======================================>] 30,539       196K/s   in 0.2s    

2011-05-12 13:18:05 (196 KB/s) - `thawte-roots.zip' saved [30539/30539]
```

```
donna@donna-HP-dx2000-MT-DR547AV:~/cert_download$ echo Unzipping Thawte Root Certs...
Unzipping Thawte Root Certs...
donna@donna-HP-dx2000-MT-DR547AV:~/cert_download$ unzip thawte-roots.zip
Archive:  thawte-roots.zip
   creating: Thawte Root Certificates/Thawte Timestamping CA/
  inflating: Thawte Root Certificates/Thawte Timestamping CA/Thawte Timestamping CA.cer  
  inflating: Thawte Root Certificates/Thawte Timestamping CA/Thawte Timestamping CA.pem  
  inflating: Thawte Root Certificates/Thawte Timestamping CA/Thawte Timestamping CA.txt  
   creating: Thawte Root Certificates/thawte SGC Root CA/
  inflating: Thawte Root Certificates/thawte SGC Root CA/Class 3 Public Primary Certification Authority.cer  
  inflating: Thawte Root Certificates/thawte SGC Root CA/Class 3 Public Primary Certification Authority.pem  
  inflating: Thawte Root Certificates/thawte SGC Root CA/Class 3 Public Primary Certification Authority.txt  
   creating: Thawte Root Certificates/thawte Server CA/
 extracting: Thawte Root Certificates/thawte Server CA/Notes - Thawte Server CA.txt  
  inflating: Thawte Root Certificates/thawte Server CA/Thawte Server CA.cer  
  inflating: Thawte Root Certificates/thawte Server CA/Thawte Server CA.pem  
  inflating: Thawte Root Certificates/thawte Server CA/Thawte Server CA.txt  
   creating: Thawte Root Certificates/thawte Primary Root CA - G3 (SHA256)/
   creating: Thawte Root Certificates/thawte Primary Root CA - G2 (ECC)/
  inflating: Thawte Root Certificates/thawte Primary Root CA - G2 (ECC)/Notes - thawte Primary Root CA - G2.txt  
  inflating: Thawte Root Certificates/thawte Primary Root CA - G2 (ECC)/thawte Primary Root CA - G2_ECC.cer  
  inflating: Thawte Root Certificates/thawte Primary Root CA - G2 (ECC)/thawte Primary Root CA - G2_ECC.pem  
  inflating: Thawte Root Certificates/thawte Primary Root CA - G2 (ECC)/thawte Primary Root CA - G2_ECC.txt  
   creating: Thawte Root Certificates/thawte Primary Root CA - G1 (EV)/
  inflating: Thawte Root Certificates/thawte Primary Root CA - G1 (EV)/Notes - thawte_Primary_Root_CA.txt  
  inflating: Thawte Root Certificates/thawte Primary Root CA - G1 (EV)/thawte_Primary_Root_CA.cer  
  inflating: Thawte Root Certificates/thawte Primary Root CA - G1 (EV)/thawte_Primary_Root_CA.pem  
  inflating: Thawte Root Certificates/thawte Primary Root CA - G1 (EV)/thawte_Primary_Root_CA.txt  
   creating: Thawte Root Certificates/thawte Premium Server CA/
  inflating: Thawte Root Certificates/thawte Premium Server CA/Notes - Thawte Premium Server CA.txt  
  inflating: Thawte Root Certificates/thawte Premium Server CA/Thawte Premium Server CA.cer  
  inflating: Thawte Root Certificates/thawte Premium Server CA/Thawte Premium Server CA.pem  
  inflating: Thawte Root Certificates/thawte Premium Server CA/Thawte Premium Server CA.txt  
   creating: Thawte Root Certificates/Thawte Personal Premium CA/
  inflating: Thawte Root Certificates/Thawte Personal Premium CA/Thawte Personal Premium CA.cer  
  inflating: Thawte Root Certificates/Thawte Personal Premium CA/Thawte Personal Premium CA.pem  
  inflating: Thawte Root Certificates/Thawte Personal Premium CA/Thawte Personal Premium CA.txt  
 extracting: Thawte Root Certificates/Thawte Personal Premium CA/Notes - Thawte Personal Premium CA.txt  
   creating: Thawte Root Certificates/Thawte Personal Freemail CA/
  inflating: Thawte Root Certificates/Thawte Personal Freemail CA/Notes - Thawte Personal Freemail CA.txt  
  inflating: Thawte Root Certificates/Thawte Personal Freemail CA/Thawte Personal Freemail CA.cer  
  inflating: Thawte Root Certificates/Thawte Personal Freemail CA/Thawte Personal Freemail CA.pem  
  inflating: Thawte Root Certificates/Thawte Personal Freemail CA/Thawte Personal Freemail CA.txt  
   creating: Thawte Root Certificates/Thawte Personal Basic CA/
  inflating: Thawte Root Certificates/Thawte Personal Basic CA/Thawte Personal Basic CA.cer  
  inflating: Thawte Root Certificates/Thawte Personal Basic CA/Thawte Personal Basic CA.pem  
  inflating: Thawte Root Certificates/Thawte Personal Basic CA/Thawte Personal Basic CA.txt  
 extracting: Thawte Root Certificates/Thawte Personal Basic CA/Notes - Thawte Personal Basic CA.txt  
donna@donna-HP-dx2000-MT-DR547AV:~/cert_download$ echo Copying Thawte Root Certs to $CERTINSTALLDIR and renaming them...
Copying Thawte Root Certs to /usr/lib/ICAClient/keystore/cacerts and renaming them...
```
```
donna@donna-HP-dx2000-MT-DR547AV:~/cert_download$ sudo cp "Thawte SSLWeb Server Roots/thawte Premium Server CA/Thawte Premium Server CA.cer"
[sudo] password for donna: 
Sorry, try again.
[sudo] password for donna: 
cp: missing destination file operand after `Thawte SSLWeb Server Roots/thawte Premium Server CA/Thawte Premium Server CA.cer'
Try `cp --help' for more information.
```

---

### Post by noah++ on 2011-05-14
The argument **$CERTINSTALLDIR** is missing from the end of this command, and that's why it failed.

> donna@donna-HP-dx2000-MT-DR547AV:~/cert_download$ sudo cp "Thawte SSLWeb  Server Roots/thawte Premium Server CA/Thawte Premium Server CA.cer"

---

### Post by agemini68 on 2011-05-14
I can't seem to get that one to work either. Ok, I'm a newbie, is there a simple fix for this?

A big Thank You to Peter Dyson who has been working for the last couple of weeks to fix this problem for me. Here is what worked for me. Oh, I'm running Ubunto 10.10, 32 bit version with all the latest updates installed. 

Download the X86 Deb package here: [http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323](http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323)

(It's the third one down on the list)

Install the package.

After you install the package, run this command in the terminal:
sudo cp -n /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/

You will need to enter your password. One other thing, after I ran the command, there wasn't a response. Just go into the Citrix Client and see if that stops the error message. I hope this helps someone else.

---

