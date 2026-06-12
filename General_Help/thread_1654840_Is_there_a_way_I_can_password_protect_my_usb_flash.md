---
title: "Is there a way I can password protect my usb flash drive."
date: 2010-12-28
forum: General Help
---

### Post by Mindswap1 on 2010-12-28
Hi guys! I was wondering is there was a way I could make it so that to access my usb flash drive you would need a password. It would really help me out a bunch. Thanks In advance!

---

### Post by wilee-nilee on 2010-12-28
Can't guarantee anything but here is a link.
[http://www.liberiangeek.net/2010/09/encrypt-thumb-drives-ubuntu-10-10-maverick-meerkat-truecrypt/](http://www.liberiangeek.net/2010/09/encrypt-thumb-drives-ubuntu-10-10-maverick-meerkat-truecrypt/)

---

### Post by mikewhatever on 2010-12-28
Encryption. Try truecrypt. It's maltiplatform and relatively easy to use.
[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by Mindswap1 on 2010-12-29
If I were to use Windows Bitlocker, to encrypt my flash drive, would it still be detected and work in linux ubuntu?

---

### Post by endotherm on 2010-12-29
I really recommend truecrypt, since it is cross-platform, open source, and a good implementation of modern cryptographic standards.

no bitlocker will not work with linux.

---

### Post by Kirboosy on 2010-12-29
> **Mindswap1 said:**
> If I were to use Windows Bitlocker, to encrypt my flash drive, would it still be detected and work in linux ubuntu?

I'm not sure if Bitlocker is even a good encryption, but I know it won't work.

Truecrypt is good and its multiplatform.  Just make sure you keep your flash drive in FAT or FAT32 format that way any computer can read it. 

If you really wanted to get fancy you could have a dual partition setup on your drive. The small partition can be like 25 Mb if you wish. Keep the big one encrypted but on the small one store a Windows copy of Truecrypt. That way you can always unlock your drive on any Windows computer even if they don't have it installed. :)

Truecrypt is a easy install process in Ubuntu

---

### Post by karthick87 on 2010-12-29
Encryption is the best way.Try truecrypt..

---

### Post by Mindswap1 on 2010-12-30
Could someone help me install truecrypt? I can't seem to figure it out. I downloaded both the truecrypt.tar.gz file, and the signature file. What do I do after that tho? I'm fairly new to to Ubuntu so forgive my ignorance.

---

### Post by karthick87 on 2010-12-30
Download truecrypt from this [**[COLOR=DarkRed]site[/COLOR]**]("http://www.truecrypt.org/downloads").For example If you have your *.tar.gz file in your desktop then type the following in your terminal..
```
cd Desktop
``````
tar -xzvf truecrypt-7.0a-linux-x86.tar.gz
``````
./truecrypt-7.0a-setup-x86
```

After installation you access truecrypt from Applications &#8594; Accessories &#8594; Truecrypt

---

### Post by Kirboosy on 2010-12-30
> **karthick87 said:**
> Download truecrypt from this [**[COLOR=DarkRed]site[/COLOR]**]("http://www.truecrypt.org/downloads").For example If you have your *.tar.gz file in your desktop then type the following in your terminal..
```
cd Desktop
``````
tar -xzvf truecrypt-7.0a-linux-x86.tar.gz
``````
./truecrypt-7.0a-setup-x86
```After installation you access truecrypt from Applications &#8594; Accessories &#8594; Truecrypt

Ok everything he said is correct. Here is the GUI way you can install everything.

1. Download the standard version from the website listed above.

2. Open up your download folder, and right click on the truecrypt-7.0a-linux-x86.tar.gz then click Extract Here.

3. Double click on the new file that appears (truecrypt-7.0a-setup-x86)

4. Next Click 'Run in Terminal'. Another window will appear and simply click Install Truecrypt. The rest should explain itself


Since you are new to Ubuntu (and probably Linux in general) I will try to explain exactly what you are doing in the terminal.


**cd = change directory --** Seems fairly self explanatory. All you need to know is the file structure of your computer. 
A simple way to grasp exactly what we are doing is Opening Places-->Computer-->File System. This will allow you to explore your file structure through the GUI.

**ls = list files --** I know he didn't mention this but it makes it easier to work in your terminal. ls simply displays the files that are in the directory. You can even view contents of another folder without having to move folders.

**tar = tape archive --** It is both a file type and a program to handle compressed files. When tar is used in the file sense it is generally called a tarball. -xzvf are commands for the tar program to run. This will change according to the files that you are trying to use. If you aren't sure what you need just type in the terminal **tar --help**

**./ = execute the file/script**

Hopefully this helps :)

---

### Post by karthick87 on 2010-12-31
+1 on post #10

---

### Post by Kirboosy on 2010-12-31
> **karthick87 said:**
> +1 on post #10

Thank you. :)

I know it can be intimidating when you switch to Ubuntu or Linux in general. Especially when you have never had to use a command line in Windows. I remember when I first tried using Ubuntu (Ubuntu 8.10 :D) I was totally lost for the first month. Then one day it just clicked and I ditched Windows altogether and ran just Ubuntu because its so much better for me.

Now I just try to help others catch on faster. That way they will enjoy using Linux more and possibly get others to start using Linux too!

---

### Post by Kirboosy on 2010-12-31
Oops it double posted. Sorry.

---

### Post by Mindswap1 on 2010-12-31
Thank You so much [Caboose885]("http://ubuntuforums.org/member.php?u=900617") You rock :) It works perfectly. Can't thank you enough! Once again thanks :).

---

