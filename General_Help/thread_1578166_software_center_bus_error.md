---
title: "software center bus error"
date: 2010-09-20
forum: General Help
---

### Post by Dave2081 on 2010-09-20
Hello 
I am running Ubuntu 10.04 LTS on an HP Pavilion dv6000 and am having trouble with software center. When I try to open it in the GUI menu it never loads after about 6-10 seconds of the cursor counter going, and from the command line it says bus error. 

Fairly new to linux any help would be appreciated.

Thanks,
Dave

---

### Post by robsoles on 2010-09-20
Please post back output of following in terminal (command line)
```
sudo apt-get update
```
(Please use copy and paste, please catch all output.)

---

### Post by Dave2081 on 2010-09-21
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,049B]                       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release        
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [77.1kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [299kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [27.9kB]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [38.9kB]   
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [9,810B]     
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,869B]  
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [656B]     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,270B] 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [120kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,439B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [118kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [47.6kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [3,651B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [1,739B]
Fetched 838kB in 3s (278kB/s)                       
Reading package lists... Done

---

### Post by robsoles on 2010-09-21
Ok, nice. Let's take any updates that are available:

```
sudo apt-get upgrade
```

If errors occur then post output of command here, if not then proceed:

Let's just blindly uninstall and reinstall Ubuntu Software Center (BUT don't do it if errors from preceeding command!)
```
sudo apt-get remove software-center
```
(again about errors...)
```
sudo apt-get -f install software-center
```
(one last time, post output of command here if errors occur please)

If you reached this point with no errors (or errors that don't sound like they stopped too much from working) then please try to open "Applications"->"Ubuntu Software Center" and post back how good or bad that goes for you this time.

---

### Post by Dave2081 on 2010-09-23
Hello again,
I tried running all three commands. Software center is still doing what it was doing before. 


d@d-laptop:~$ sudo apt-get upgrade
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  fglrx-modaliases libssl0.9.8 openssl
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,401kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? y   
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libssl0.9.8 0.9.8k-7ubuntu8.1 [979kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main openssl 0.9.8k-7ubuntu8.1 [406kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main fglrx-modaliases 2:8.723.1-0ubuntu5 [15.1kB]
Fetched 1,401kB in 2s (491kB/s)           
Preconfiguring packages ...
(Reading database ... 124439 files and directories currently installed.)
Preparing to replace libssl0.9.8 0.9.8k-7ubuntu8 (using .../libssl0.9.8_0.9.8k-7ubuntu8.1_amd64.deb) ...
Unpacking replacement libssl0.9.8 ...
Setting up libssl0.9.8 (0.9.8k-7ubuntu8.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 124439 files and directories currently installed.)
Preparing to replace openssl 0.9.8k-7ubuntu8 (using .../openssl_0.9.8k-7ubuntu8.1_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace fglrx-modaliases 2:8.723.1-0ubuntu4 (using .../fglrx-modaliases_2%3a8.723.1-0ubuntu5_amd64.deb) ...
Unpacking replacement fglrx-modaliases ...
Processing triggers for man-db ...
/usr/bin/mandb: can't read from /var/cache/man/index.db: Input/output error
Setting up openssl (0.9.8k-7ubuntu8.1) ...

Setting up fglrx-modaliases (2:8.723.1-0ubuntu5) ...









_____________ REMOVE COMMAND _____________________
d@d-laptop:~$ sudo apt-get remove software-center 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,720kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124435 files and directories currently installed.)
Removing software-center ...
Processing triggers for man-db ...
/usr/bin/mandb: can't read from /var/cache/man/index.db: Input/output error
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
d@d-laptop:~$ 


___________REINSTALL ______________________
d@d-laptop:~$ sudo apt-get -f install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  software-center
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/279kB of archives.
After this operation, 1,720kB of additional disk space will be used.
Selecting previously deselected package software-center.
(Reading database ... 124318 files and directories currently installed.)
Unpacking software-center (from .../software-center_2.0.7_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
/usr/bin/mandb: can't read from /var/cache/man/index.db: Input/output error
Processing triggers for python-support ...
Setting up software-center (2.0.7) ...

Processing triggers for python-central ...
d@d-laptop:~$

---

### Post by robsoles on 2010-09-24
Open a terminal and issue command
```
tail -f /var/log/system
```

Take note of where logging gets up to.

Try to open software-center

Please show us lines that appear in the log when you try to open software-center.

---

### Post by Dave2081 on 2010-10-03
It doesn't look like the tail command did much. I tried running it before and after opening software-center and it did the same thing. Hopefully your still subscribed to this thread. Was outta town for a week and didn't have access to this lap top. Thanks for your help

d@d-laptop:~$ tail -f /var/log/system
tail: cannot open `/var/log/system' for reading: No such file or directory
tail: no files remaining
d@d-laptop:~$ tail -f /var/log/system
tail: cannot open `/var/log/system' for reading: No such file or directory
tail: no files remaining
d@d-laptop:~$ software-center
Bus error
d@d-laptop:~$ tail -f /var/log/system
tail: cannot open `/var/log/system' for reading: No such file or directory
tail: no files remaining
d@d-laptop:~$

---

### Post by robsoles on 2010-10-03
Sorry, my error - dunno what my malfunction was!

```
tail -f /var/log/messages
```

Is the log I was actually after at first but I should probably point out logs in /var/log/apt as well.

The 'tail' command with the '-f' flag should 'follow' a log and show new entries as they are made, I am hoping to see entries from the log relevant to what is happening with your software center.

---

### Post by Dave2081 on 2010-10-03
One quick question: I installed ubuntu on this laptop using a cd drive that is kinda faulty. but it either works or it doesn't so I thought I would try and i eventually got it to work. Is it possible that, that's where this problem is coming from? I would try to reinstall using a USB drive but I don't have that option as a bootable device in the BIOS. 

typed in the first command and then tried to open software-center on the desktop.

d@d-laptop:~$ tail -f /var/log/messages
Oct  3 06:56:56 d-laptop kernel: [11177.619880] ata3.00: configured for UDMA/100
Oct  3 06:56:56 d-laptop kernel: [11177.619903] sd 2:0:0:0: [sda] Unhandled sense code
Oct  3 06:56:56 d-laptop kernel: [11177.619907] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  3 06:56:56 d-laptop kernel: [11177.619915] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Oct  3 06:56:56 d-laptop kernel: [11177.619925] Descriptor sense data with sense descriptors (in hex):
Oct  3 06:56:56 d-laptop kernel: [11177.619929]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  3 06:56:56 d-laptop kernel: [11177.619948]         00 05 61 3a 
Oct  3 06:56:56 d-laptop kernel: [11177.619957] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Oct  3 06:56:56 d-laptop kernel: [11177.619966] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 05 61 38 00 00 08 00
Oct  3 06:56:56 d-laptop kernel: [11177.620067] ata3: EH complete
Oct  3 06:57:50 d-laptop kernel: [11231.084642] ata3.00: configured for UDMA/100
Oct  3 06:57:50 d-laptop kernel: [11231.084657] ata3: EH complete
Oct  3 06:57:52 d-laptop kernel: [11233.249886] ata3.00: configured for UDMA/100
Oct  3 06:57:52 d-laptop kernel: [11233.249905] ata3: EH complete
Oct  3 06:57:54 d-laptop kernel: [11235.415302] ata3.00: configured for UDMA/100
Oct  3 06:57:54 d-laptop kernel: [11235.415326] ata3: EH complete
Oct  3 06:57:56 d-laptop kernel: [11237.580365] ata3.00: configured for UDMA/100
Oct  3 06:57:56 d-laptop kernel: [11237.580385] ata3: EH complete
Oct  3 06:57:58 d-laptop kernel: [11239.745709] ata3.00: configured for UDMA/100
Oct  3 06:57:58 d-laptop kernel: [11239.745732] ata3: EH complete
Oct  3 06:58:00 d-laptop kernel: [11241.910867] ata3.00: configured for UDMA/100
Oct  3 06:58:00 d-laptop kernel: [11241.910893] sd 2:0:0:0: [sda] Unhandled sense code
Oct  3 06:58:00 d-laptop kernel: [11241.910897] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  3 06:58:00 d-laptop kernel: [11241.910905] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Oct  3 06:58:00 d-laptop kernel: [11241.910915] Descriptor sense data with sense descriptors (in hex):
Oct  3 06:58:00 d-laptop kernel: [11241.910919]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  3 06:58:00 d-laptop kernel: [11241.910939]         00 05 61 3a 
Oct  3 06:58:00 d-laptop kernel: [11241.910947] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Oct  3 06:58:00 d-laptop kernel: [11241.910956] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 05 61 38 00 00 08 00
Oct  3 06:58:00 d-laptop kernel: [11241.911013] ata3: EH complete



___________________________



d@d-laptop:~$ tail -f /var/log/apt
tail: error reading `/var/log/apt': Is a directory
tail: /var/log/apt: cannot follow end of this type of file; giving up on this name
tail: no files remaining

---

### Post by Dave2081 on 2010-10-16
Can anyone see this thread anymore? Should I repost it somewhere

---

### Post by robsoles on 2010-10-16
Every time anyone posts to the thread it goes back to the top of the  list and anyone subscribed to it gets notification, no need to repost.

I apologise, must have clicked my notification at work, not had time to post and then not remembered later at home.

The log entries above give me an idea that your drive controller is  failing. Can you use an alternative computer to make a bootable USB of  10.04 and try it on the pavilion? The BIOS may just list the USB drive  in 'bootable devices'/'boot order' if it is started with a bootable USB  inserted.

I could be entirely wrong but with dodgy CD-ROM access and the  impression your posts give me, maybe both the hard drive and the  DVD/CD-ROM drive are failing. How old is your pavilion?

---

### Post by Dave2081 on 2010-10-18
its about four years old. I'll make a bootable USB on my main laptop and try it on the HP. its always worked ok. I doubt I'd buy an internal harddrive for it if, if the hard drive is failing in anyway. 

thanks,
Dave

---

### Post by Dave2081 on 2010-10-18
thanks for the help. I reinstalled as I can install from a USB. so far it seems to work. 
Thanks!

---

