---
title: "Super ubuntu noob looking for the trash can xD"
date: 2009-08-06
forum: General Help
---

### Post by Whiteblooded on 2009-08-06
Hey, I'm very new to ubuntu.. I can barely do anything with it yet. I'm using ubuntu 9.04

I was looking for the trash can. It's not in /home/rob/.trash, and I've also looked for it in the /root/.trash, but it tells me that "the folder contents could not be displayed", which is very worrying as I'm the only user on the system (which kind of leads me on to believe that I probably have other things to fix before I even DREAM of finding the trash can lol)

Anyone have any ideas? I will warn you that it took me about half an hour to find the terminal xD

---

### Post by TMAN 1 on 2009-08-06
> **Whiteblooded said:**
> Hey, I'm very new to ubuntu.. I can barely do anything with it yet. I'm using ubuntu 9.04

I was looking for the trash can. It's not in /home/rob/.trash, and I've also looked for it in the /root/.trash, but it tells me that "the folder contents could not be displayed", which is very worrying as I'm the only user on the system (which kind of leads me on to believe that I probably have other things to fix before I even DREAM of finding the trash can lol)

Anyone have any ideas? I will warn you that it took me about half an hour to find the terminal xD
You shouldn't have to install it.
It shouls be in one of the corners of your screen,depending on your page layout,most likely on the bottom right hand corner.
You can also find it under Places>Home folder.

---

### Post by Whiteblooded on 2009-08-06
Yep.. It was in the bottom corner. Still though, shouldn't I be able to access teh /root/ folder? I'm guessing I've not set this user up correctly.

---

### Post by jocko on 2009-08-06
> **Whiteblooded said:**
> Yep.. It was in the bottom corner. Still though, shouldn't I be able to access teh /root/ folder? I'm guessing I've not set this user up correctly.
No, the /root folder should *not* be accessible to you as a normal user. Only root have access to /root.

---

### Post by muteXe on 2009-08-06
If you're doing stuff outside your home folder you have to use sudo before commands.
[http://ubuntuforums.org/showthread.php?t=261204](http://ubuntuforums.org/showthread.php?t=261204)

---

### Post by geirha on 2009-08-06
/root should only be accessible by the root user. You can run commands as root with the sudo command. E.g. "sudo ls /root" instead of "ls /root" will list the content of /root. Only users that are members of the admin group are allowed to use sudo.

In earlier releases of Ubuntu, trash was located in a folder ".Trash" in your homefolder. In later releases though, this has changed to ".local/share/Trash/".

---

### Post by Whiteblooded on 2009-08-06
Okay, thanks for that.. that was a lot of help :)

---

### Post by Whiteblooded on 2009-08-06
Darn.

I just realised that I can't move anything out of the recycle bin because I don't have the permission :confused: I figure I'll have to use something with sudo? Surely I should at least have permission to just click and drag the files out of the bin? 

Any ideas?

---

### Post by RED Lemming on 2009-08-06
I hope this is what you want....

Right click on the trash can.

Click "Open the Wastebasket"

Find the file you are looking for.

Right click on said file.

And (dangerously if logically) just below "Delete Permanently" there is a "Restore" option that should shove the offending file back from whence it came....

I hope that helped :-)

EDIT: Sorry I just read your last post :-/ chances are is you don't have permission, yes you will probably have to do it as root.... 
Although I'd like to know what user type you are logged in as?

---

