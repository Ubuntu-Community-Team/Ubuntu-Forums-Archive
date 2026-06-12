---
title: "Right click on desktop disabled and no icons"
date: 2009-07-09
forum: General Help
---

### Post by budgemook on 2009-07-09
Hi,

I recently installed Ubuntu 9.04 on my acer aspire netbook. I decided to donwload the netbook remix version from the ubuntu website so i didn't have to deal with getting the wireless / mic / sound etc working again, and then change it so it's like a regular ubuntu install, but now i reckon i've spent longer trying to get my desktop sorted :-)

The problem is I cannot see the desktop icons or I can't right click on the desktop. The only way I can get it working is to launch nautilus from the command line. When i close the window and stop nautilus the icons are gone again and i cant right click again.

So far i have tried clicking show desktop in gconf-editor but it didn't change anything. I believe if it wasn't clicked then my desktop wouldn't show when i run nautilus.

I read another post about running nautilus from the command line, then going to sessions and then setting the order to 40 or something like that but the sessions tab isn't there on 9.04 and the startup programs doesn't have any options to change order or save changes or really anything that he described.

Please help, it's bugging the hell out of me :-D

---

### Post by JohnsShadow on 2009-07-09
see if this works

in terminal

```
gconftool-2 --set /apps/nautilus/preferences/show_desktop --type bool 1
```

the code is sposed to turn on desktop drawing in gnome

---

### Post by budgemook on 2009-07-09
No that didn't work i'm afraid. 
typed it into the command line but nothing at all happened. no output whatsoever. Any other ideas?

---

### Post by budgemook on 2009-07-21
Sorry for bumping but I still haven't figured this out. Can anyone help?

---

### Post by drfox on 2009-07-22
Here's what you need to do to get your panels back:
Get a terminal session, either by logging on to a terminal session or by pressing Alt-F2 from your desktop and then typing "xterm"

Remove these folders:
.gconfd
.gconf
.gnome2
.gnome2_private
.config

by using the command: rm -r foldername

Once they are removed, reboot using the command: sudo shutdown -r now

Your panels will be back. 

HTH  Larry

---

### Post by masux594 on 2009-07-22
This problem were resolved by restarting X [from [this thread]("http://ubuntuforums.org/showthread.php?t=849089")].. Have u tried that?

Sysc, A

---

### Post by budgemook on 2009-07-22
Hi,

drfox - By panels you mean the regular gnome panels right? There is no problem with those. I have one on top and one on the bottom and they are working fine. It's what's in between - The desktop - That "isn't working". I can see the background image, i just cant see any files I have saved in the desktop folder and I can't right click on the desktop - No menu appears

masux - When i restart my computer doesn't that restart X? I will have a look this evening when i get home and see if that sorts it out.

Thanks for the reply guys.

Just read through that thread masux, I did start nautilus but without the ampersand to run it in the background and it did work but it's a bit annoying having to do that every time. I also put nautilus in the startup programs but that didn't work. Maybe i'll try put nautilus & in my bashrc or something.

Cheers,

A

---

### Post by masux594 on 2009-07-22
Yes, but, it "Start", not "Restart".. I know that means that start again, but, maybe shutting down and start X is different.. ..Hmm, tell us if you find the main reason of this error.. in the last weeks, many user encounter this problem..

Sysc, A

---

### Post by drfox on 2009-07-22
> **budgemook said:**
> Hi,

drfox - By panels you mean the regular gnome panels right? There is no problem with those. I have one on top and one on the bottom and they are working fine. It's what's in between - The desktop - That "isn't working". I can see the background image, i just cant see any files I have saved in the desktop folder and I can't right click on the desktop - No menu appears


A

If you follow my directions, you should be able to see and work with your desktop again. To start without an x session, when your computer reboots, select the recovery mode (the 2nd item in your grub menu) and you'll be able to start a terminal session to delete those directories.

Larry

---

### Post by raronson on 2009-07-22
Over the years, I've had to resort to 

Press Alt-F2 (Gnome's run dialogue) and type "killall nautilus", which exits the problematic instance of it.

Then bring up Alt-F2 again and type "nautilus" to restart it (and fork it into the background).

Sometimes Nautilus makes a quiet exit.  Hasn't been fixed for years and years.  Ah, don't get me started...

---

