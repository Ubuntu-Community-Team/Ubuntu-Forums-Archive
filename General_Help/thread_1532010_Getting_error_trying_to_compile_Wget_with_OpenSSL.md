---
title: "Getting error trying to compile Wget with OpenSSL"
date: 2010-07-15
forum: General Help
---

### Post by rollin on 2010-07-15
Howdy,

I'm trying to compile wget with openssl. Unfortunately I can't seem to find much on Google for doing this, the closest so far has been: [http://ubuntuforums.org/showthread.php?t=134822](http://ubuntuforums.org/showthread.php?t=134822)
Following the steps, I've downloaded the source package version 1.12 and tried the following code:

```
./configure --with-ssl
```But I'm getting the error:

```
configure: error: --with-ssl was given, but SSL is not available.
```I'm not an expert by any means with security / ssl etc but it seems I already have openssl installed:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
```Any help you can give to suggest a method of completing the installation with ssl would be great!

---

### Post by rollin on 2010-07-23
Bump!

Still googling this but no luck so far! I'm still hoping someone has managed to do this and could give some advice please ?!

---

### Post by Bachstelze on 2010-07-23
Why do you want to compile wget?  I'm pretty sure the version in the repos has SSL support.

---

### Post by rollin on 2010-07-23
> **Bachstelze said:**
> Why do you want to compile wget?  I'm pretty sure the version in the repos has SSL support.

Oh right that's embaressing! To explain better I'm trying to get wget to run on port 993 for IMAP over SSL. I'm running the gmail.py script from here: [http://ubuntuforums.org/showthread.php?t=680265](http://ubuntuforums.org/showthread.php?t=680265)

The command in the script is: wget -O - https:// etc and having run sudo netstat -antp I can see it is running on port 443. Which I appreciate is the https default port.

I had a look at the wget manual though: [http://www.gnu.org/software/wget/manual/html_node/HTTPS-_0028SSL_002fTLS_0029-Options.html](http://www.gnu.org/software/wget/manual/html_node/HTTPS-_0028SSL_002fTLS_0029-Options.html) and wanted to add an option such as --secure-protocol=SSLv2 but the script stops working!

So am I just approaching it the wrong way or is there a way to test what protocol it is adopting without specifying one? 

Sorry if it's a bit random!

---

