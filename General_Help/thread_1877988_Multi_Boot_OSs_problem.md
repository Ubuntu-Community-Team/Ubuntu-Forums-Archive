---
title: "Multi Boot OSs problem"
date: 2011-11-09
forum: General Help
---

### Post by Legend_Xeon on 2011-11-09
I have windows 7 installed on my PC. I also installed ubuntu later from wubi-installer.
Now i want to install ubuntu on its own partition along with other OSs.
The list goes like this:-
1. Windows 7
2. Windows XP
3. Ubuntu
4. Slackware
5. Backtrack 5
6. FreeBSD

I heard that there are many things to consider like 4 primary partitions limit, the sequence etc..

I am not sure if there is a  very similar thread that goes on to explaining step by step details of what to do to achieve this. If there is any just link me to it.

Thanks in advance.

---

### Post by saltsprung on 2011-11-09
I'm wondering the same thing and found this:

[http://www.linuxbsdos.com/2011/05/31/how-to-triple-boot-fedora-15-ubuntu-11-04-and-windows-7/](http://www.linuxbsdos.com/2011/05/31/how-to-triple-boot-fedora-15-ubuntu-11-04-and-windows-7/)

and this:

[http://ubuntuforums.org/tags.php?tag=triple+boot](http://ubuntuforums.org/tags.php?tag=triple+boot)

I'd really like to learn how to do this...

---

### Post by Mark Phelps on 2011-11-09
So, of the six, which ones are already installed?

If it were me, I would have the first two OSs each in their own primary partition, then I would create an Extended partition for the remainder of the drive, and create Logical partitions inside that for each of the other OSs.

And actually, if you plan to SHARE date amongst the OS, then create a Logical NTFS partition inside the Extended partition -- and use that to share data.

---

