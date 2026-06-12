---
title: "Recover Data From Crashed Kernal"
date: 2009-10-02
forum: General Help
---

### Post by ID_ on 2009-10-02
Hey guys. Here is the deal i have been using ubuntu since gusty and i am stumped. 9.04 freaked out on me and i need to recover data off the drive. I am currently running live off the 9.04 disk and have read everything on how to access my old home folder to transfer the data. Any way I try to get to it it says permission denied. Is there a way that i can login to the drive with my old login and password? What do i need to do?

---

### Post by ID_ on 2009-10-02
made some progress.

in terminal 

gksudo nautilus

allowed me to access home folder but showed two files
Readme.txt      Access-Your-Private-Data.desktop

i opened the readme file and it tells you to type this in the command line

ecryptfs-mount-private

---

### Post by ID_ on 2009-10-02
Then it says Encrypted Private is not setup properly. or when i try to launch the .desktop file in nautilus, terminal tells me "Failed to contact the GConf daemon; exiting"

---

### Post by ID_ on 2009-10-02
now i am stuck went through gksudo nautilus to change permissions on the drive and it shows the same two files in the home folder.

---

### Post by ID_ on 2009-10-02
i am gonna call it a night. check back in the morning.

---

### Post by Spaceman9 on 2009-10-02
Get a copy of Puppy Linux [http://www.puppylinux.com/](http://www.puppylinux.com/) it runs in root all the time. Burn it to a CD as an .iso and make it a multisession CD. 

Because Puppy will see all your hard drives, floppy drives and USB drives including USB sticks and because it runs as root you can move or copy files to where ever you want to. It's saved my life more than once when a distro has crashed and I have no other way to recover data files.

Also although I use Gnome I installed Krusader because it's way better then Gnome Commander and Nautilus for changing permissions. To run Krusader in Gnome press Alt+F2 and type gksudo krusader and hit Enter.

---

### Post by ID_ on 2009-10-02
If that works your a godsend. Thanks for the help. I am going to try that right now.

---

### Post by ID_ on 2009-10-02
well i got puppy up but how did you say you get to krusader? BTW i got Puppy 4.3.

---

### Post by ID_ on 2009-10-02
well here is what it has came down to. I drive is encrypted and i do not know a passphrase to access it. Is there a way to find the passphrase?

---

### Post by Mi*6d@# on 2009-10-02
> **ID_ said:**
> well here is what it has came down to. I drive is encrypted and i do not know a passphrase to access it. Is there a way to find the passphrase?
The only way to get it is to remember it. Otherwise you can say goodbye to the data on the drive, sorry.

---

### Post by ID_ on 2009-10-02
thanks man. ubuntu set up the encrytion. I never created a passphrase so i am going to dig through the files and see if i can dig it out.

---

