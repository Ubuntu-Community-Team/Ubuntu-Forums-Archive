---
title: "After first instlation"
date: 2010-07-24
forum: General Help
---

### Post by al7ussein on 2010-07-24
dear all
its my first time to install Linux 
its pretty cool and i really like it
but i had 3 problems as anew user i don't know how to deal with them
1st
ctrl+shift don't work when i want to change writing language
2nd
after update now i have 6 Linux choices the was only 4 so i want to know how i can edit at the boot loader
3rd
every time i open the laptop its asking me for default password so i create it after that every time i open the laptop and it going to connect to the network asking me for it
it will be great if any one help me with these problems

---

### Post by PaulReaver on 2010-07-24
I don't know about the 1st and the 3rd questions but I can answer the 2nd

if you remove the extra old kernels using the synaptic package manager it should update the grub boot menu automatically.  Just be careful not to remove the latest kernel.

---

### Post by agnes on 2010-07-24
3rd question: it's 'gnome-keyring-daemon' that asks the password? If so you can disable it this way:
Go to System->Preferences->Startup Applications. Deselect gnome-keyring-daemon from the list. 
Then open the File Manager, press Ctrl+H to show hidden files. Go to the directory /home/your-name/.gnome2/keyrings. Delete the .keyring files.
Reboot. Gnome-keyring-daemon should not pop up anymore.
If it still does (I only tested this with 10.04), just leave the password blank.

---

