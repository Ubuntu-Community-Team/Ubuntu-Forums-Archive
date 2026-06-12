---
title: "Panic, cant start session!!!"
date: 2010-06-16
forum: General Help
---

### Post by komitaltrade on 2010-06-16
After update in Lucid, cant start the session. As only critical part was Nautilus (on 2.31), how to fix it?

I don't have in GDM any session option and no way to approach to terminal and start any session. 

Only way can be somehow before GDM (Lucid by default don't have Grub) or via Live USB (but how?).

---

### Post by komitaltrade on 2010-06-16
At least somebody know how to mount live USB on hard drive existent file-system, or

how to copy file on existent file-system?

---

### Post by Procrat on 2010-06-16
I'm having the same problem. I tried everything... Now I'm reinstalling Lucid with the LiveCD.
For information on LiveUSB: [Click here]("https://help.ubuntu.com/community/Installation/FromUSBStick")

By the way, you can still approach the terminal hitting Ctrl+Alt+F1/F2/F3/F4/F5/F6.

---

### Post by komitaltrade on 2010-06-16
You are genius, I have access via terminal.

Now, idea is to copy user s, install new Lucid and copy back user s, because of setting.

Drive is /media/Samsung   (users are /home/xxx)

I done 

cp -avr /home/xxx/ /media Samsung

and it work's.

Question is

Can I do it like I planned?

What files to avoid to copy back (to avoid problem s)?

---

### Post by Procrat on 2010-06-16
I'm about to do the same thing. I think it would be best to only copy your home folder, and reinstall all the rest. :)

Although there are some hidden files (starting with a '.') in the home folder concerning the configuration of Gnome (which in my case might cause problems)... So I'll leave those out.

Good luck. ;-)

---

### Post by komitaltrade on 2010-06-16
Personally, I don't think how you should to avoid hidden files and folders (it can be problem) and I didn't notice any problem with copy (any sign of some error).

Moreover, here is nice tutorial, but I still want to know can I expect the problem s with user s.

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by dino99 on 2010-06-16
[http://manpages.ubuntu.com/manpages/lucid/en/man8/adduser.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/adduser.8.html)

---

### Post by komitaltrade on 2010-06-16
Sorry Dino99, I don't get the point.

It is not problem with users (I dont need new users), problem is with Nautilus (I cant start any user).

Question is what method can be best to clean Nautilus completely and install it again (and to not touch users settings, it mean without Gnome re-installation, just Nautilus related)?

Repositores are OK (and Internet connection), so I can try via command line to do it.

I will start with purge (if it is nobody with better idea).

---

### Post by komitaltrade on 2010-06-16
Finally, everything is broken by Nautilus Elementary!!!

I purged nautilus and reinstalled ubuntu desktop (this is what enabled gui login), but after I ppa purged elementary repository. 

In any case, now I still cant open file browser Nautilus and I have some strange messages, so I will now create separate partition and copied users there, than new install.

---

