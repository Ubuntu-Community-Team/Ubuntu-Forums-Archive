---
title: "run .sh file ( denied permission)"
date: 2012-07-30
forum: General Help
---

### Post by Spgt on 2012-07-30
I have tried to execute a file that ends with .sh
I tried the following methods but NO LUCK!

[EMAIL="sgharagoz@ubuntu:%7E/Cadence_iso/IC610_lnx86.Base"]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/EMAIL]/CDROM1$ sh SETUP.sh
sh: 0: Can't open SETUP.sh

[EMAIL="sgharagoz@ubuntu:%7E/Cadence_iso/IC610_lnx86.Base"]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/EMAIL]/CDROM1$ chmod +x SETUP.SH
chmod: changing permissions of `SETUP.SH': Function not implemented

[EMAIL="sgharagoz@ubuntu:%7E/Cadence_iso/IC610_lnx86.Base"]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/EMAIL]/CDROM1$ ./SETUP.SH
bash: ./SETUP.SH: /bin/sh: bad interpreter: Permission denied

PLEASE REMEMBER THAT I HAVE NO EXPERIENCE WITH LINUX.

THANKS

---

### Post by BkkBonanza on 2012-07-30
Post output of 

ls -lsa SETUP.sh
ls -lsa /bin/sh

---

### Post by westie457 on 2012-07-30
Hi at least one of those commands and probably all of them need sudo at the front. 

'Sudo' is used to give you temporary privileges to change/install things in the / (root) folder.

---

### Post by Spgt on 2012-07-30
Thank you for replying quickly.

[email]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/email]/CDROM1$ ls -lsa SETUP.sh
ls: cannot access SETUP.sh: No such file or directory

[email]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/email]/CDROM1$ ls -lsa /bin/sh
0 lrwxrwxrwx 1 root root 4 Jul 30 14:59 /bin/sh -> dash

Just could  you explain to me what am I exactly doing? 

Cheers

---

### Post by Spgt on 2012-07-30
Hey Westie,

I tried both of them but no luck I have:

[email]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/email]/CDROM1$ sudo chmod +x SETUP.SH
chmod: cannot access `SETUP.SH': Permission denied

[email]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/email]/CDROM1$ sudo sh SETUP.SH
sh: 0: Can't open SETUP.SH

Cheers

---

### Post by BkkBonanza on 2012-07-30
Those commands just list the attributes of the files.
It seems your'e on a cdrom but that SETUP.sh isn't even present. Maybe post output of,

pwd
ls -lsa
ls -lsa /Cadence_iso/IC610_lnx86.Base

these commands just give a bit more info about your "persent working directory" and what's in the location given. ls is just the "list" command.

Regarding your other commands.
chmod won't work on a cdrom as the file is readonly. Cannot change file. Any setup script ought to me executable anyway but if using the sh in front it doesn't need to be. The problem here is that the file you want either doesn't exist or is spelled wrong.

The sh command is linked to the dash shell on your system. Likely not a real problem though.

---

### Post by Spgt on 2012-07-30
Okay I've what you asked and I have:

[email]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/email]/CDROM1$ pwd
/home/sgharagoz/Cadence_iso/IC610_lnx86.Base/CDROM1

[email]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/email]/CDROM1$ ls -lsa
total 367
  1 dr-xr-xr-x 1 root root   2048 Jun 26  2007 .
  1 dr-xr-xr-x 1 root root   2048 Jun 26  2007 ..
 90 -r--r--r-- 1 root root 369203 Oct 20  2006 Base_IC610_lnx86.sdx
  0 -r--r--r-- 1 root root    419 Oct 20  2006 ic_index.sdx
  1 dr-xr-xr-x 1 root root   4096 Jun 26  2007 IMAGES.DIR
 26 -r--r--r-- 1 root root 106279 Mar 31  2006 INSTALL.HTML
  0 -r--r--r-- 1 root root     88 Oct 20  2006 .kpsource
  0 -r--r--r-- 1 root root     97 Oct 20  2006 MEDIA1.TXT
  3 -r--r--r-- 1 root root  11089 Oct 20  2006 README
  1 dr-xr-xr-x 1 root root   2048 Jun 26  2007 READMES
  6 -r--r--r-- 1 root root  25120 Oct 20  2006 SETUP.SH
241 -r--r--r-- 1 root root 985657 Oct 20  2006 sl2iswrap.zip

[email]sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base[/email]/CDROM1$ ls -lsa /Cadence_iso/IC610_lnx86.Base
ls: cannot access /Cadence_iso/IC610_lnx86.Base: No such file or directory

Just a bit of info about the file itself. I have ISO file and I mounted the file using Furious ISO Mount.
I have the ISO file on DVD as well as my Desktop as well and I mounted somewhere in my Document folder.

Cheeers

---

### Post by HiImTye on 2012-07-30
you'll likely need to copy the files to a separate folder, change the file permissions and then create a new iso to fix the problem as I don't know of a reliable way to mount an iso rw

---

### Post by BkkBonanza on 2012-07-30
Given info above,

sudo sh SETUP.SH

should work. You might try it will the full path. 

sudo sh /home/sgharagoz/Cadence_iso/IC610_lnx86.Base/CDROM1/SETUP.SH

(case is important so don't use lower case there).
If that doesn't work then perhaps something is wrong with how it's mounted or maybe something with "dash". You could try using bash if it's there.

eg. first,
ls -las /bin/bash
to see what's there, then

sudo /bin/bash SETUP.SH

---

### Post by steeldriver on 2012-07-30
a couple of things:

1. Linux filenames are case sensitive - so if the file is called SETUP.SH then SETUP.sh, Setup.SH, setup.SH etc won't work

2.  /Cadence_iso/IC610_lnx86.Base is NOT the same as **~**/Cadence_iso/IC610_lnx86.Base - the first one starts at the root of the filesystem (/) whereas the second one starts at your home directory (~) - this is why  your command ```
ls -lsa /Cadence_iso/IC610_lnx86.Base 

``` didn't work

3. if you have COPIED (not 'mounted') the contents of the iso to **~**/Cadence_iso/IC610_lnx86.Base then there should be no problem making the COPIED SH file executable:

```
chmod +x SETUP.SH
```or (if your pwd is not ~/Cadence_iso/IC610_lnx86.Base)

```
chmod +x ~/Cadence_iso/IC610_lnx86.Base/SETUP.SH 
```

---

### Post by Spgt on 2012-07-30
@Bkk I have tried sh and the full path but it didn't work

sgharagoz@ubuntu:~/Cadence_iso/IC610_lnx86.Base/CDROM1$ sudo sh /home/sgharagoz/Cadence_iso/IC610_lnx86.Base/CDROM1/SETUP.SH
sh: 0: Can't open /home/sgharagoz/Cadence_iso/IC610_lnx86.Base/CDROM1/SETUP.SH

@steeldriver
" if you have COPIED (not 'mounted') the contents of the iso to **~**/Cadence_iso/IC610_lnx86.Base then there should be no problem making the COPIED SH file executable:"
How Can I do it? Should I extract it using Archive manager?

Cheers

---

### Post by Spgt on 2012-07-30
I used Archvie manager and copied all the files in a folder.But for some reason I have ;1 in front of all the file!!!
I rename SETUP.SH;1 to SETUP.SH and then I right clicked on SETUP.SH , clicked on the permission tab and tick the " allow executing files as program" and it did something!!

How do I remove those " ;1 "???
there are to many files!!!

Cheers

---

### Post by raja.genupula on 2012-07-30
open your terminal and cd to that directory . then type this command 

```
for i in *.SH;1; do mv "$i" "${i/.SH;1}".SH; done
```

---

### Post by BkkBonanza on 2012-07-30
This is sounding more like some weird mounting problem. Can you post the output of the **mount** command. 

If you have an ISO file you should be able to mount it as a loop device easily. I don't know what Furious ISO Mount is but maybe it's doing something odd.

eg. this ought to work, ( but you'd have to umount what you have now first ),

sudo mount -o loop path/to/dvdfile.iso /mnt
ls -lsa /mnt

---

