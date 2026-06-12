---
title: "Mount Window Folder Shared."
date: 2012-03-21
forum: General Help
---

### Post by mbm1234 on 2012-03-21
Hello, actually I can mount Windows folder shared but in the graphical environment, this folder only I can see from the graphical environment, In the graphical environment when I start up the Libre Office or other program and I try to open a file from the Windows folder shared I can not because Libre Office and other programs can not see a Windows folder shared, in windows I can see the folder shared of Linux and Windows from any program and I can open the file from the folder shared from any program, I want to mount Windows folder shared, this way I can see from any program and also from the console, please help me, if it is possible to do this, thanks in advance.

---

### Post by HiImTye on 2012-03-21
if you mean folders you mounted from the network, from inside the 'File Browser' (nautilus) they are in '~/.gvfs/<Share> on <Computer>'

---

### Post by mbm1234 on 2012-03-21
Hello HiImTye, thankyou for reply, I have mount a Windows folder shared but I can not find this path "~/.gvfs/" in my Linux computer.

---

### Post by mbm1234 on 2012-03-21
I found but I can not still see the Windows folder shared from any program, I found in this path "usr/share/gvfs".

---

### Post by jerome1232 on 2012-03-21
not /usr, ~/, that means inside your home folder, hit ctrl+h to see hidden files

---

### Post by mbm1234 on 2012-03-21
Hello jerome1232, I found the folder in my Home folder and now I can see the Windwos folder shared, thankyou.

---

### Post by jerome1232 on 2012-03-21
> **mbm1234 said:**
> Hello jerome1232, I found the folder in my Home folder and now I can see the Windwos folder shared, thankyou.

If it is any consolation, I hate Libre Offices' file browser with a passion. Why it can't just call the system default browser like most applications do is beyond me. It does the same crap on Windows if I remember right.

---

### Post by redmk2 on 2012-03-21
> **jerome1232 said:**
> If it is any consolation, I hate Libre Offices' file browser with a passion. Why it can't just call the system default browser like most applications do is beyond me. It does the same crap on Windows if I remember right.

I believe that it's because of the *manner *Nautilus mounts the share that you (and I) have problems.  The mount needs the option **nobrl** to be added and nautilus doesn't use that option.

Try mounting the share from the CLI with something like this```
sudo mount -t cifs //server_or_IP/share_name/ /media/mount_point user,username=login uid=1000,gid=1000,iocharset,nobrl
```

This will allow you to open LO documents (or any others) from the share, manipulate them and save back to the share.

I use this in a script that mount the share for the user (the mount needs to be listed in fstab) and also un-mounts the share when the user is done.  If you use zenity prompts, the user can be notified that the share has been successfully mounted and dismounted via the GUI.

If you want to see what Nautilus does, then mount the share via the GUI, then use the *mount *command from the CLI.

---

