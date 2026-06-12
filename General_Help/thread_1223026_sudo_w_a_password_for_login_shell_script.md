---
title: "sudo w/ a password for login shell script?"
date: 2009-07-25
forum: General Help
---

### Post by bjdonhauser on 2009-07-25
I'd like to have a shell script run at login which calls "sudo". But "sudo" requires my login password. What should I do?

---

### Post by sisco311 on 2009-07-25
[s]you should seek a better option. :)

or edit the sudoers file.[/s]

Could you please elaborate your question so we can give you an adequate answer?

Btw, welcome to the forums!

---

### Post by bacil on 2009-07-25
what is your script supposed to do ? you can use setuidbit and run it with root rights.

---

### Post by mikewhatever on 2009-07-25
Do you want to run the script as root? If yes, you don't need sudo for that. Can you elaborate on what you want to do.

---

### Post by sisco311 on 2009-07-25
> **bacil said:**
> you can use setuidbit and run it with root rights.

that's the last resort.

> **mikewhatever said:**
> Can you elaborate on what you want to do.
+1

---

### Post by ajgreeny on 2009-07-25
I think you can just ignore the need for sudo in the command, ie, leave it out completely, even if that command usually needs it, add the script to */etc/init.d* folder, then run the command ```
sudo /etc/init.d/scriptname start
```which will need the password, of course.  This will mean it is running for all users, however, which may not be what you want.

---

### Post by Crunchy the Headcrab on 2009-07-25
or just add the command to the end of /etc/rc.local 

This has the same problem that ajgreeny mentioned.

---

### Post by bjdonhauser on 2009-07-25
I'm running Ubuntu 9.04 as a VM via Sun's VirtualBox on a Vista machine. I'd like to be able to share a folder between the host (Vista) and guest (Ubuntu). I mostly followed the instructions [here]("http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/"). I created a folder "shared-windows" in my home folder on Ubuntu. I created a folder "shared-ubuntu" on the host machine. I instructed the VM where the shared folder was. I wrote the following "share-folders" script:


#!/bin/bash

sudo mount -t vboxsf shared-ubuntu ~/shared-windows

I then made this script executable:

$ chmod +x share-folders

When I run this script from the terminal sudo prompts me for my password. I supply it. Everything works great. So, I then tried throwing "~/share-folders" script in my ~/.profile. And it didn't work, not surprisingly, because I had no way of supplying the password. 

I really don't want to be running this as the root. Is there no way to run this script locally, automatically at login? It seems like there should be some way to do this

Thanks for the help so far everyone

---

### Post by Crunchy the Headcrab on 2009-07-25
edit /etc/rc.local

add:> mount -t vboxsf shared-ubuntu ~/shared-windowsafter the last line.  (reboot)
Let me know if it works.  I have some commands in mine that make my laptop play nice with linux.

When you say you don't want to run as root does this mean you don't want every user to have this happen automatically?  Because it is very easy to do system wide by doing it the way I recommended, but if you only want to do it on a per user basis then it gets a bit more complicated.

---

### Post by sisco311 on 2009-07-26
add
```
shared-ubuntu    **/home/username**/shared-windows    vboxsf    defaults    0    0
```
at the end of the /etc/fstab file.

To edit the file press Alt+F2 and type:
```
gksu gedit /etc/fstab
```

The /etc/rc.local file is handy for quick and dirty fixes, but there is almost always a better way to accomplish the same task.

NOTE: You have to use the full path to the mount point.

HTH

---

### Post by bjdonhauser on 2009-07-26
@sisco311: I tried your method first and it worked wonderfully. Thank you. Really clear explanation. 

Since I'm a noob and very curious, I wanted to know what the /etc/fstab file was. I found a clear and useful explanation [here]("http://www.tuxfiles.org/linuxhelp/fstab.html"). 

So I take it that this is NOT a system-wide mount. Honestly, the system-wide vs. local deal doesn't matter a whole lot to me on THIS particular issue. But, since I'm new I figured I'd try and start using best practices right away :)

What I really like about this thread is it provides me segue into my next problem: a cdrom being mounted at each login even after I've "ejected volume" AND even after I've gone into the /etc/fstab file and commented out the:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

which is causing the mounting. Something weird is going on here...but that's for another thread :) Thanks again everyone. Playing around with Ubuntu is a lot of fun.

---

