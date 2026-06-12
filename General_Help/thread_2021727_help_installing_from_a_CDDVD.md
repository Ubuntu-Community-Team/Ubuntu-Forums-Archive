---
title: "help installing from a CD/DVD"
date: 2012-07-09
forum: General Help
---

### Post by Firewalker572 on 2012-07-09
I am very new to linux and have been asked to build a small server for my company.  I have a AMD semperon 2600 (1.8 ghz), 2g RAM and 40g HD  i am running 32bit server (believe its 10.x).  I am trying to install a program from a cd but I dont know the exact name of the software and i dont know how to navigate to a cd from the command line.  I installed gnome gui but it kept locking up the computer so not looking to go down that path again.  Any help is appreciated.

---

### Post by foxmulder881 on 2012-07-09
Is there any reason that you can't install the software from the repositories?

---

### Post by Firewalker572 on 2012-07-09
yes, the software I am trying to install i dont believe it is in the repositories.  its a large database manipulation software.  Best i could describe it, im not entirely sure what it is, sorry.

---

### Post by ronnysingh on 2012-07-09
Read Ubuntu server guide :

[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

---

### Post by Firewalker572 on 2012-07-10
Ronny i have looked through that server guide and it doesnt specifically address installing software from a CD from the CLI

---

### Post by Cheesemill on 2012-07-10
To mount the CD:
```
sudo mkdir /mnt/cdrom
sudo mount /dev/cdrom /mnt/cdrom
```

To move to the directory and list the contents:
```
cd /mnt/cdrom
ls -lh
```

If you post back with the output of the last command we can take it from there.

---

### Post by Firewalker572 on 2012-07-10
it gave me an error "mount: no medium found on dev/sr1"
I verified that something is on the CD, windows doesnt recognize the type of file.
Is it possible that a CD driver is being loaded instead of a DVD driver?

---

### Post by Cheesemill on 2012-07-10
Try:
```
sudo mount /dev/sr0 /mnt/cdrom
```

---

### Post by Firewalker572 on 2012-07-10
that worked!!
"total 2.3G
-r-xr-xr-x 1 4294967295 4294967295 2.3G Jun 26 15:43 MSTR_921m_GA_Linux.tar.gz" (last part is in liime green)

---

### Post by Cheesemill on 2012-07-10
What's the output of:
```
ls -lh /dev/cd*
```

---

### Post by Firewalker572 on 2012-07-10
lrwxrwxrwx 1 root 3 Jul 10 12:34 /dev/cdrom -> sr1
lrwxrwxrwx 1 root 3 Jul 10 12:04 /dev/cdrom1 -> sr0
lrwxrwxrwx 1 root 3 Jul 10 12:34 /dev/cdrw -> sr1

---

### Post by Cheesemill on 2012-07-10
Sorry, I missed the part where it worked!

---

### Post by Cheesemill on 2012-07-10
OK then. MSTR_921m_GA_Linux.tar.gz is a compressed file which we first need to extract:
```
cd ~
mkdir MSTR
cd MSTR
tar -xvzf /mnt/cdrom/MSTR_921m_GA_Linux.tar.gz
```

Then can you post back the output of:
```
ls -lh
```

If you select the output you are posting and then click on # it will appear in a code box which makes it easier to read (like the code I've posted).

---

### Post by Firewalker572 on 2012-07-10
total 68k
drwxr-xr-x 13 jasond jasond  12k Dec 14 2011 Documentation
drwxr-xr-x  4 jasond jasond 4.0k Dec 14 2011 Installations
-rwxr-xr-x 1 jasond jasond 5.5k Dec 14 2011 pvcystmt.html
-rwxr-xr-x 1 jasond jasond 8.0k Dec 14 2011 readme.htm
drwxr-xr-x 4 jasond jasond 20k Dec 14 2011 ReleaseNotes

---

### Post by Cheesemill on 2012-07-10
As far as I can tell from the instructions MicroStrategy 9 is only supported on Red Hat or SUSE Linux. You are likely to come across problems trying to install it on Ubuntu.

If you want a free OS to install it on then you could use CentOS (a free version of Red Hat).

You *have* read the 600 page installation guide haven't you?
[http://www.microstrategy.com/producthelp/manuals/9.2.1/en/InstallationConfig.pdf](http://www.microstrategy.com/producthelp/manuals/9.2.1/en/InstallationConfig.pdf)

---

### Post by Firewalker572 on 2012-07-10
ARGGH!!  I think im going to shoot myself.....thanks for your help.
Guessing CentOS commands would be the same as what you have told me?

---

### Post by Cheesemill on 2012-07-10
The commands to mount the DVD and extract the files will be the same, but you probably wont need them.

Red Hat / CentOS has a GUI so the DVD should automount and you can extract the files using a graphical application.

Make sure you install a version of CentOS that is listed as certified in the software requirements (it uses the same version numbering as Red Hat).

---

### Post by Firewalker572 on 2012-07-13
Cheese can you recommend a book, or some other type of media, that would teach me how to use Ubuntu server in the CLI?  Or Linux in general...

---

### Post by Cheesemill on 2012-07-13
Your first stop would be the CLI Learning Resources page on the Ubuntu Wiki.

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by Firewalker572 on 2012-07-13
Thank you sir/ma'am

---

### Post by Cheesemill on 2012-07-13
Sir :)

---

### Post by Firewalker572 on 2012-07-13
Thats what i figured but didnt want to assume.  Thank you sir

---

### Post by Cheesemill on 2012-07-13
How's the MicroStrategy install going?

---

### Post by Firewalker572 on 2012-07-13
I'm thinking it would be easier if I just quit my job. Lol. Microstrategy doesn't install easily on anything. I tried win7, 2k server and XP. I'm thinking about telling the boss to find something else and free doesn't always mean its a good deal.

---

