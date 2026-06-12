---
title: "Deleted home folder trying to fix .ICEauthority"
date: 2010-08-29
forum: General Help
---

### Post by Ctrl-Alt-Eject on 2010-08-29
On startup in 10.04 I was getting this message before the desktop would load: "Could not update ICEauthority file /home/user/.ICEauthority"

So, I did this:
```
sudo chown user:user /home/user/.ICEauthority
sudo chmod 644 /home/user/.ICEauthority
exit
```where user=username

Then, I restarted and got the following errors: "Could not update ICEauthority file /home/user/.ICEauthority" 

and "There is a problem with the configuration server. (/usr/lib/libconfig-2-4/gconf/sanity-check-2 exited with status 256)"

and "Nautilus could not create the following required folders: /home/user/Desktop, /home/user/Nautilus. Before running nautilus, please create these folders, or set permissions such that Nautilus can create them."

After this point I could no longer boot to the desktop. I was ready to do a clean install so I booted from the livecd to backup files and found my /home/user was empty. :D  I do not have a backup of this stuff.

What happened? Is there any chance of recovering my home directory? I am new to GNU/Linux so I do not know what I am doing.

---

### Post by scorp123 on 2010-08-29
> **Ctrl-Alt-Eject said:**
>  I booted from the livecd to backup files and found my /home/user was empty. :D  I do not have a backup of this stuff.  Are you sure the correct disk was mounted?? If you have your /home on a separate disk, but from the Live CD you only mounted the harddisk the OS was installed on ... then yes, it will show up empty. Simply because there's nothing mounted underneath /home yet.

The commands you used up there only manipulate the permissions ... they should not delete your entire home directory in any way, they are not "deadly" per se. If you really really lost your entire home then I imagine there must be something wrong with your disk then. :confused:

---

### Post by Ctrl-Alt-Eject on 2010-08-29
> **scorp123 said:**
> Are you sure the correct disk was mounted?? If you have your /home on a separate disk, but from the Live CD you only mounted the harddisk the OS was installed on ... then yes, it will show up empty. Simply because there's nothing mounted underneath /home yet.

The commands you used up there only manipulate the permissions ... they should not delete your entire home directory in any way, they are not "deadly" per se. If you really really lost your entire home then I imagine there must be something wrong with your disk then. :confused:
Yes, I am sure I mounted the correct disk. /home is on the same partition as the OS. As far as the disk being bad, I have never had problems with data disappearing before and disk utility says the disk is healthy.

Thanks for the reply.

---

### Post by David Andersson on 2010-08-29
1) Normally you should be able to look into /media/xxx/home from a live cd, but if read permissions somehow have been changed, you might need to be root on the live cd to see it.

2) Do you remember approximately the size of the content in home, or the size of the whole file system? If you check the current size, does it suggest approximately the size of home is missing, or not?

---

### Post by peptobismal on 2010-08-30
If you can get some forensic hard drive restoration discs, maybe. I dunno, seems like at this point if your home folder is deleted it's gone no matter what you do, you know? I mean you're probably best off starting all over.

---

### Post by Ctrl-Alt-Eject on 2010-08-31
> **David Andersson said:**
> 1) Normally you should be able to look into /media/xxx/home from a live cd, but if read permissions somehow have been changed, you might need to be root on the live cd to see it.

2) Do you remember approximately the size of the content in home, or the size of the whole file system? If you check the current size, does it suggest approximately the size of home is missing, or not?

David, you were right about permission. I don't know if I should have suspected that since I am a newb. I am not sure if this is the best way but, I did "sudo nautilus" and opened /home and everything was there which was hidden without root. Thanks very much David and everyone who responded. This helped me out allot.

---

### Post by David Andersson on 2010-08-31
The symptoms suggest the permissions and/or owner/group in /home/yourname is not what they normally should be. So the problem still has to be fixed. It could be done from a live-cd, from a fail-safe login if that is possible, and from a boot into recovery mode. The alternatives have different complications. If fail-safe login is possible, I think that is easiest.

Another option is to save all files, including hidden files, from /home/yourname to an external harddisk or usb-stick, then re-install ubuntu, and then copy all files back into the new /home/yourname. If you choose that route, make two copies, just for sure. Copy back as your new yourself, not as root. If the copy was on fat or ntfs, after copying back the files, you should selectively reset their execute-permissions.

Right now I think re-install is overkill. Does fail-safe login work?

---

