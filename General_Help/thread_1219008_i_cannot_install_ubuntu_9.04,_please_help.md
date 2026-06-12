---
title: "i cannot install ubuntu 9.04, please help"
date: 2009-07-21
forum: General Help
---

### Post by Armaggedon89 on 2009-07-21
hi to all you friends,

i have a problem with the installation of ubuntu 9.04 on my pc... i get the error that installation cannot continue, and that i should view the log. i have the log, and if anyone want to try to help me, i can upload the txt file, or to copy some part of it in post... please, help me :)

PC:

32bit Windows
ATI x600 pro
1Gb RAM


and i want to install it with my windows xp sp2, because my sister will work on windows and i will work on linux :)

---

### Post by bacil on 2009-07-21
can you attach the log ? to analyze

---

### Post by Armaggedon89 on 2009-07-21
[http://www.mediafire.com/?1b4rjdwytmy](http://www.mediafire.com/?1b4rjdwytmy)

here's the log file :) i hope it's possible to fix...

---

### Post by adam_kimber on 2009-07-21
Glad to see you are trying out Ubuntu! Wubi is a great way to have a fully fledged Ubuntu without the hassle of dual booting. If you want to dual boot, back up data first.

Back to your Wubi problem. The log has this in it (a few times)
07-21 14:35 ERROR  root: [Errno 13] Permission denied

It looks like it is trying to copy some files over and cannot. Therefore it fails to install. Do you have administrative rights for your XP installation? If not this is a possibility. Make sure you are not logged in as a limited account.

[IMG]http://teamtutorials.com/wp-content/uploads/2007/05/add-users-windows-xp-tutorial-06.jpg[/IMG]

---

### Post by bacil on 2009-07-21
right i see you using some autoinstall on top of windows and dont have permissons to its files

```

07-21 14:35 ERROR  TaskList: [Errno 13] Permission denied
07-21 14:35 ERROR  root: [Errno 13] Permission denied

```

it refers to 

```

07-21 14:32 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Stefan\LOCALS~1\Temp\pyl30.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-21 14:32 DEBUG  TaskList: ## Finished copy_installation_files
07-21 14:32 DEBUG  TaskList: ## Running get_iso...
07-21 14:32 DEBUG  TaskList: New task copy_file
07-21 14:32 DEBUG  TaskList: ### Running copy_file...
07-21 14:35 DEBUG  TaskList: ### Finished copy_file
07-21 14:35 ERROR  TaskList: [Errno 13] Permission denied

```

and from this i guess it is your typo because you are looking for iso file but you have called your downloaded one Ubunto.ico < thats my guess

---

### Post by Armaggedon89 on 2009-07-21
@adam_kimber
yes, i am administrator of this system :) 
@bacil
so, what should i do?

---

### Post by bacil on 2009-07-21
i would start with renaming Ubuntu.ico to Ubuntu.iso if that helps.

I cant advice on wubi since i dont know anything about it at all.

---

### Post by Armaggedon89 on 2009-07-21
@bacil

what do u mean? i downloaded wubi from it's site, and it was *.iso. i recorded iso on cd-r and i tried to install it from cd-r... i dont get it... where is that ubuntu.ico/.iso?

p.s. sorry for my bad english, it's not my mother language :)

---

### Post by bacil on 2009-07-21
That file (based on your log) is here :

C:\DOCUME~1\Stefan\LOCALS~1\Temp\pyl30.tmp\data\images\Ubuntu.ico

so i would start looking there . and i have no clue about wubi will probably have test go with it on my windows machine when i can go roudit and reimage it back after latest crash :-)

---

### Post by Armaggedon89 on 2009-07-21
no, that doesn't work... im still getting the same message that i should view log... can anyone else help me...

what should i do? this is what i have found:

installation gave me same message, but i have the ubuntu folder on my C:\
there are some files, here is the ss... maybe that can help? should i try to restart pc and try to boot into ubuntu setup?
[[IMG]http://img361.imageshack.us/img361/3505/75986398.th.jpg[/IMG]]("http://img361.imageshack.us/my.php?image=75986398.jpg")

---

### Post by sikandarnoori on 2009-07-21
hi
i had same problem as well, i download the .iso file and wrote it on cd, but no chance to install inside windows, for me the only successful way was to use the original free cd i gottrough shipmen t, i think you know how to register and request for free cd,
have a nice time

---

### Post by bacil on 2009-07-21
I will test this today ... will be back

---

### Post by Armaggedon89 on 2009-07-21
thanks for the answers... i will try to order free cd, but i think it's not possible for the cd to get here, in my country :)
but i will try anyway :)
thanks again, and if someone knows how can i resolve my problem, please help, i would really appreciate it...

---

### Post by bacil on 2009-07-21
ok the wubi is installed and now testing different distros.  now trying to download iso through it and will see then

---

### Post by Armaggedon89 on 2009-07-21
thanks mate... i installed 8.04 and will try to upgrade it to 8.10 and then to 9.04... i think that this might work :) wish me luck :)

---

### Post by Lisheo on 2009-07-21
I'm having the same problem; also admin, so permission denied seems a little odd.
I've tried installing on both drives, to no avail, same problem.

---

### Post by bacil on 2009-07-21
ISO is coming my way. about 1:30 remaining.

i got some other iso already here and i will be testing with them as soon as this firstone finishes.

---

### Post by Lisheo on 2009-07-21
Anything?

---

### Post by bacil on 2009-07-21
16 min 50s remaining :-)

---

### Post by Lisheo on 2009-07-21
It appears my disc was corrupted/broken/whatever.
damn ubuntu. Wanted to make it simple, but I'll just install from the iso as I have ****** up four other discs trying to make a copy lol

---

### Post by bacil on 2009-07-21
Right here we come:

i have installed wubi used this to download mythbuntu and install mythbuntu on my windows laptop. whole operation took over 4 hours (due my internet speed)

after the installation (successfull one) my windows rebooted and have now dual boot with mythbuntu (using gparted) to shrink my windows partiton and get me the disksize i wanted for my mythbuntu.

Then usual strugle with wireless dirvers and graphic card and all is up ad running now (i dindt haveto burn cd or anything) assuming wubi used virtual cdrom and mounted dowladed iso.

Now iam booting back to widows to have look through install log, from first glance this is what is happening:

1. wubi set torent and downlaod iso of selected distro
2. create directory c:\ubuntu where all its files are stored
3. in there it copies iso after successful downlaod
4. in there create disk, install and winboot directroy
5. redirect winboot to c:\ubuntu\winboot
6. create virtual disk and swap disk
7. mount iso as virtual cdrom and boot live cd
8. launch install from live cd
9. reboot and have "virtual dual boot"

that is what happenened in mine please see attached install log

now back to your problem. i will try to replicate this issue i will download ubuntu.iso it might be that there is bug in downaloader

for you i suggest you have access right to wherever you isntalling ubuntu and that those files and directories are created

---

