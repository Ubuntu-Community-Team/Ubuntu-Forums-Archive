---
title: "su trash"
date: 2010-05-31
forum: General Help
---

### Post by styleruk on 2010-05-31
Hi

I have to fire up Kino as SU for another reason I won't go into now, however, I use sudo nautilus to manage the files because they were written as su.  In doing that I have deleted 12gb video file as su and don't know where it is.  I can't access the trash as su it won't let me and it's not in the normal trash.
Can anyone tell where it has gone and how I can clear the space on my drive?

Si

---

### Post by harrismh777 on 2010-05-31
Your Trash is in  /home/youruserid/.local/share/Trash

Assuming your root did not actually completely remove the file... and I suspect it did actually remove it, perhaps the file is in  /root/.local/share/Trash.  I have not actually tried this mind you... 

Every account has its own trash can; however, not everything goes into the trash... it is possible to rm (remove) a file directly in a terminal and its gone... no trash can recovery. If you used nautilus to remove the file as root, check to see if it placed it in roots Trash folder... but I doubt it.

---

### Post by styleruk on 2010-05-31
I've tried both them directories and the files are not in there?

---

### Post by harrismh777 on 2010-05-31
try running this command:   its safe, but takes a while:

sudo  find  /  -name  filename*  -print

Run from a terminal, the command will search the entire disk from / till it finds the
filename.  This takes time on large systems or slow processors.

---

### Post by styleruk on 2010-05-31
That did not return the file.
There is a hidden folder called trash on the drive that I'm deleting from and the contents are unreadable.

---

### Post by styleruk on 2010-05-31
Mind you I searched for *.avi and it did not find any either?

---

### Post by harrismh777 on 2010-05-31
Are you game for removing the hidden Trash folder?

What do you mean its unreadable?

---

### Post by styleruk on 2010-06-01
Can't remove the trash file, has a cross on it.

Solved it by finding places to put the files I wanted to keep and format the drive.  It's a 74GB drive and I only had 15GB left on it!  Now it's formated and back to normal.  Trouble is I keep getting issues where I have to run as sudo and therefore can't empty the bin.
Take kino for instance, will not recognize the firewire video camera without sudo.
Also my iPod, I use it to keep files on and transfer to and from work, can't do that unless I sudo nautilus.  Have to be real carefull deleting stuff off of this, I rely on windows at work to do the deleting otherwise they will be hidden somewhere on the device. have run sudo chmod -R etc... but still won't let me paste files into it.

Anyway, problem solved, maybe one day I'll start another thread.

Thanks for your help
Si

---

