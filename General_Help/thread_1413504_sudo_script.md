---
title: "sudo script"
date: 2010-02-22
forum: General Help
---

### Post by Jpenguin on 2010-02-22
I have a UDF *.iso image, but found a way to mount it--

[http://www.notes2self.info/2009/06/easily-mount-iso-files-as-virtual.html]("http://www.notes2self.info/2009/06/easily-mount-iso-files-as-virtual.html")

The only prob is that I have to enter my password each time I mount ab ISO.  Is the a way to include my password in the script?  I do not want to edit my sudoers file and make my entire account able to sudo w/o a password.

---

### Post by doas777 on 2010-02-22
well, you could use gksu instead of sudo, so it prompts you via gnome. I prefer that when running scripts off launchers.

I believe there is a way to mount image files via gvfs in userspace so no need for sudo/gksu. you;ll have to look it up to get the details though.

---

### Post by bodhi.zazen on 2010-02-22
If all you want to do is mount an iso you have several options. You can try any of the graphical tools, not sure if they require root access or not.

Even easier is to simply make a mount point and add a line in fstab. In the options column use the option user or users.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Your other option is to modify sudoers :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

If you want to script it, look at expect.

[http://www.linux-mag.com/id/699](http://www.linux-mag.com/id/699)

---

### Post by tom4everitt on 2010-02-22
> **bodhi.zazen said:**
> 

Your other option is to modify sudoers :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)


I think its worth to point out that you can edit the sudoers file to just let you run a single command without typing password. Check the NOPASSWD section in the link.

Or just use this example:

ray    rushmore = NOPASSWD: /bin/kill, /bin/ls, /usr/bin/lprm

which will allows user ray to (on machine rushmore) run /bin/kill and /usr/bin/lprm without typing password.

---

### Post by Jpenguin on 2010-02-22
> **bodhi.zazen said:**
> If all you want to do is mount an iso you have several options. You can try any of the graphical tools, not sure if they require root access or not.

I have tried the GUI tools

[QUOTE=Notes2Self]The biggest flaw in Gmount-iso, AcetoneIso ,Furius ISO Mount and mount.sh scripts is that THEY CANNOT MOUNT ISO IMAGES USING THE UDF FORMAT.[//QUOTE]

---

### Post by Jpenguin on 2010-02-22
echo "password" | sudo -S command

---

### Post by tom4everitt on 2010-02-23
> **Jpenguin said:**
> echo "password" | sudo -S command

Wow, thats brilliant!!! Had no idea it could be that easy. Thanks!!

---

### Post by doas777 on 2010-02-23
just make sure you keep your script safe. having passwords in cleartext just gives me the willies.

---

### Post by tom4everitt on 2010-02-23
Of course its by no means a safe way to do it :)

---

