---
title: "folders missing after rebooting system"
date: 2011-07-12
forum: General Help
---

### Post by divyabdasar on 2011-07-12
[LEFT]Hi All,

i am using Ubuntu 9.10 - the Karmic Koala
I was playing songs in movie player 2.28. Due to some issue i just used command 

$ sudo reboot

With the player on. 

After machine got restarted the songs folder is missing. but when i check Recent Documents i am able to see previously played songs. and able to play them again. But i am unable to locate my music folder. 

Please some body help me to recover my collections of songs. 
:(:(:(:(:(:???::neutral:
Awaiting for reply.


[/LEFT]

---

### Post by divyabdasar on 2011-07-12
Hi All,

i am using Ubuntu 9.10 - the Karmic Koala
I was playing songs in movie player 2.28. Due to some issue i just used command 

$ sudo reboot

With the player on. 

After machine got restarted the songs folder is missing. but when i  check Recent Documents i am able to see previously played songs. and  able to play them again. But i am unable to locate my music folder. 

Please some body help me to recover my collections of songs. 
:sad::sad::sad::sad::sad::???::neutral:
Awaiting for reply.

---

### Post by uRock on 2011-07-12
Duplicate post here [http://ubuntuforums.org/showthread.php?t=1803188](http://ubuntuforums.org/showthread.php?t=1803188)

Thread Closed.

---

### Post by cariboo on 2011-07-12
It seems I merged the threads while Urock closed one. :)

---

### Post by JedMeister on 2011-07-12
If it is NTFS then I suggest doing a chkdsk from Windows. I have had strange behaviour similar to this after shutting down a system without first unmounting NTFS filesystems (ie hard reset/power failure/etc). chkdsk fixed it for me.

---

### Post by Mark Phelps on 2011-07-13
If the folder was actually deleted, unless Movie Player actually saves a copy of the files, the files would be gone, too.

But, you've given us little to work with to solve this.

What filesystem was used to store the folder? NTFS? Ext4?

Is this a folder that's local to your PC? Or were you mounting a folder from a network drive? Or, mounting it from another PC on the local network (i.e., using SAMBA)?

If the files are local, and stored in a Linux filesystem, you could try doing a "find" command.  That will give you the full pathname of the file -- telling you where is it now being stored.

---

