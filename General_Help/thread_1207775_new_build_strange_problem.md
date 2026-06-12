---
title: "new build strange problem"
date: 2009-07-08
forum: General Help
---

### Post by aadra on 2009-07-08
ok so here's the thing. my dad and i finsihed putting together a new comp but for some reason ubuntu is installed already on the hard drive. i know that the hard drive was returned to the store from where i bought it so its not a stretch to assume that it was left over from the previous owner. all i want to do is format the hard drive , delete ubuntu and install windows xp. just i dont know the password needed to access the application manager to install the app that will allow me to partition and format the hard drive. any kind of help will be greatly appreciated. :confused:

---

### Post by cariboo on 2009-07-08
Just boot from your Windows install disk, when you get to the partitoning section, just delete the ext3 partions, and create your own partitions. I just did this the other day and it works with zero problems.

Select the partion using the arrow keys, the press **D**, then press **L** when asked. Do the same for the rest of the partitons. Windows will overwrite the mbr and grub will be removed.

---

### Post by aadra on 2009-07-08
the other thing is that the disk that i am using is being read by ubuntu but whenever i try to run either the setup it says that it cannot open it because its not a zip file and when i try the auto run it says that there is no application to run it :confused:

---

### Post by rbishop on 2009-07-08
Reboot your computer with the XP disk in the CDRom drive and away you go.....

---

### Post by aadra on 2009-07-08
yea that doesnt work either......

---

### Post by aadra on 2009-07-08
alright heres another thing. so when i my dad and i built a new comp we got a used hitachi deskstar hard drive from fry's. when we set up the bios and everything we booted it up and for some reason ubuntu was already installed as the OS under the user hal2001. what we want to do is install windows xp on it except the thing is we dont know the password for this user and we dont know how to access the /etc directory to see what the password is. plesae please any kind of help would be greatly appreciated thank you :D

---

### Post by t4thfavor on 2009-07-10
Just install XP over top of the Ubuntu partition if you really want to. I bet the password is dave, or hal2001 though. It appears that the person who installed it  was a 2001 a space odessy fan :)

if there is no password, and the session logs in, you can open up a commandline by clicking Applications -> Accessories-> and Terminal. Then type

sudo passwd hal2001
then type in any password. then your done.

---

### Post by jocko on 2009-07-10
> **aadra said:**
> alright heres another thing. so when i my dad and i built a new comp we got a used hitachi deskstar hard drive from fry's. when we set up the bios and everything we booted it up and for some reason ubuntu was already installed as the OS under the user hal2001. what we want to do is install windows xp on it except the thing is we dont know the password for this user and we dont know how to access the /etc directory to see what the password is. plesae please any kind of help would be greatly appreciated thank you :D
You don't need to do anything in ubuntu if you don't want to keep it. The windows installer will not run in ubuntu, so just boot from your windows cd (i.e set the cd/dvd first in the boot order in bios), and let the windows installer format the hard drive and install.
You would not be able to see the password even if you knew how to access the /etc/ directory. It would probably be a little bit too easy to make viruses/trojans/malware that could gain full system access even in linux if the password could simply be read from an unencrypted file in your file system.

---

