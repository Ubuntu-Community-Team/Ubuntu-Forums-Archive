---
title: "Filesharing"
date: 2006-02-10
forum: General Help
---

### Post by kdxrider9262 on 2006-02-10
Hello,

My name is steve and im a n00bie when it comes to linux so far. I have ubuntu 5.10 64 bit running. Im trying to share a folder on my desktop called shared with my windows machines. I have it set up under the shared folders application. When i try to access the folder on my windoes machines. I go to the workgroup and double click the serer. It then asks me for a user name and password. I type in the one i use to log onto my server but that doesnt work. Is there anyway i can get it to not even ask for a user name and/or password? Please help.

Thanks,
Steve

---

### Post by Jason_25 on 2006-02-10
Check [this]("http://www.ubuntuforums.org/showthread.php?t=122837&highlight=smb.conf") thread out.  On post 12 I post my smb.conf for anonymous read/write access.  BTW, not that it matters but my pc with the samba server happens to be running breezy 64 too.

---

### Post by kdxrider9262 on 2006-02-10
I am not able to modify the samba.conf that is listed in the etc/samba folder. It is set to read only and i am not able to check otherwise. Any suggestions?

---

### Post by Zeroangel on 2006-02-10
First enable the 'run' dialogue box:
1) Right click in the empty space in your top panel
2) Select 'Add to panel' from the context menu
3) Drag and drop the 'Run Application...' icon onto the panel

4) open the terminal using the command 'gnome-terminal'
5) type in 'sudo gedit /etc/samba/smb.conf'

---

### Post by kdxrider9262 on 2006-02-15
I implented the samba.conf you supplied and I am now able to acces it but I am not able to create any new files or new folders.

---

### Post by kdxrider9262 on 2006-02-18
i wish there were easier ways to share files lol. Im debating whether or not to go back to server 2003 for my file sharing. Please dont yell at me LOL!!! Im still gonna use linux for all of my other server features.

---

