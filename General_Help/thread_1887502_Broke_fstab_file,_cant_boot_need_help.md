---
title: "Broke fstab file, cant boot need help"
date: 2011-11-27
forum: General Help
---

### Post by bennettg on 2011-11-27
Hello.  I am a noob who broke the ubuntu.

I researched the boards to try to permanently mount a external hard drive and followed the instructions which involved:


1. Determining the /dev address of the USB drive (partition, really, I guess): sudo fdisk -l. In my case, the address was /dev/sdb
2. Adding a mount point for the partition: sudo mkdir /media/externalhd. 
3. Editing fstab: sudo gedit /etc/fstab.
4. Adding the following 2 lines to fstab: 
         /dev/sdb1 /media/media auto rw,auto,user
         umask=000     

the umask=000 command was to allow read/write access to the external drive from other machines on my home network.

*******now i can no longer boot the computer.  i ran the recovery and it told me that there was an error in the fstab file.  

can anyone tell me how i can open the fstab file during the recovery and remove the edits i made above?  or some other way to fix it without losing everything?

thanks in advance.

---

### Post by Elfy on 2011-11-27
Use nano 

You might need to use the remount option in the recovery menu first - then once done - root prompt

nano /etc/fstab

do the change - then Ctrl+X - yes - enter to save

Edit - you could actually try this - open the file to edit it - _then make this 1 line not 2_ which is the problem with the file. 


/dev/sdb1 /media/externalhd auto rw,auto,user,umask=000 0 0

Then save - then try 

mount -a 

if it still fails then comment the line out with a #

---

### Post by WorMzy on 2011-11-27
> **forestpiskie said:**
> Edit - you could actually try this - open the file to edit it - _then make this 1 line not 2_ which is the problem with the file. 


/dev/sdb1 /media/media auto rw,auto,user umask=000

Almost there. That space between user and umask should be a comma, otherwise mount will think that "umask=000" is the desired value of fs_freq/dump. Also, the mount point the user created, and the mount point stated in the fstab line differ.

```
/dev/sdb1 /media/externalhd auto rw,auto,user,umask=000 0 0
```

would be a better written line.

Also, bennettg, don't use "sudo" when launching graphical applications as root. Use "gksudo" instead.

---

### Post by Elfy on 2011-11-27
Thanks wormzy ... 

should have just left it before the edit :p- changed mine now ...

---

### Post by bennettg on 2011-11-27
> **forestpiskie said:**
> Use nano 

You might need to use the mount option in the recovery menu first - then once done - root prompt

nano /etc/fstab

do the change - then Ctrl+X - yes - enter to save

Edit - you could actually try this - open the file to edit it - _then make this 1 line not 2_ which is the problem with the file. 


/dev/sdb1 /media/externalhd auto rw,auto,user,umask=000 0 0

Then save - then try 

y.

mount -a 

if it still fails then comment the line out with a #

thanks....getting close.  i did the nano /etc/fstab and i can see the file, but it tells me i can read only....i do not have write permissions.  

what do i do to get write permissions?

thanks in advance, your assistance is appreciated greatl

---

### Post by Elfy on 2011-11-27
You need to do the remount command from the recovery menu first the press enter when prompted - seems to be a new thing - caught me out once or twice till I caught on ... then you can edit the file.

---

### Post by bennettg on 2011-11-27
> **forestpiskie said:**
> You need to do the remount command from the recovery menu first the press enter when prompted - seems to be a new thing - caught me out once or twice till I caught on ... then you can edit the file.

no luck, still wont allow me to have write access.  any other ideas?

---

### Post by gordintoronto on 2011-11-27
use sudo nano ....

---

### Post by bennettg on 2011-11-27
> **gordintoronto said:**
> use sudo nano ....

nope.  thanks anyway.

can anyone else help?

---

### Post by Elfy on 2011-11-28
Boot a livecd - mount the partition - edit the file in there.

---

