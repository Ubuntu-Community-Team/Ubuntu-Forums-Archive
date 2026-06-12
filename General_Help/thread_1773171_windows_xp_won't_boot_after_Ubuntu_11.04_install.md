---
title: "windows xp won't boot after Ubuntu 11.04 install"
date: 2011-06-01
forum: General Help
---

### Post by altomang on 2011-06-01
Hi,
 
Super busy at work, won't check back for about 4 hours. Sorry if stuff doesn't make sense, typing really quickly.. Also kind of a newbie. Used to know my stuff but then got out of touch for a long time before I started to reminisce about linux. 
 
 
I installed ubuntu 11.04 as dual boot with windows xp but it failed after partially installing. The failed install took up the alloted partition space I gave. Windows XP is still working at this point and the computer just booted directly to windows with no grub. I redownloaded Ubuntu and re-installed over the failed installation and now I can use Ubuntu. However, when I first turn on my comptuer and get to the menu and choose to boot XP, it will just go to the next screen as if it is going to XP for 1 second and then it will go back to the menu. My computer will only run Ubuntu. Looks like I need an XP cd which I don't have since it's a dell laptop with factory restore which happens to have an error. Nice! I have an idea of what to do but since the last time I used linux was like 3 years ago I'm not sure. Help?
 
I really should just get a new laptop but Ubuntu is extending its lifetime since its so much more simple and fast but I still need to use windows sometimes...

---

### Post by mike555 on 2011-06-01
Sounds like you installed Ubuntu inside Windows (Wubi install) , but if not just go into ubuntu and in terminal type "  sudo update-grub  " without the quotes.
 if you used a Wubi install you will need to edit the Windows boot menu , search this forum for instructions.

---

### Post by bcbc on 2011-06-01
It sounds like you might have set the Timeout for the windows boot manager to zero, and set Ubuntu as the default OS to boot. So it transfers control to Ubuntu's Grub menu. Selecting Windows from there, just loops back to Grub. If this is not the case, ignore the rest of this post.

Since it's XP, you should be able to locate and edit the C:\boot.ini (from Ubuntu it will be either /host/boot.ini if you installed Wubi on C: or you have to find and mount the partition that represents C: )

1. Before editing make a copy.
```
cp /host/boot.ini /host/boot.ini.copy
```
2. Be careful not to add line breaks as windows uses different line ending control characters and this can stop windows booting (and probably also prevent access to wubi)
3. Locate the line specifying the Timeout and change it to 15

PS I haven't personally modified the boot.ini from Ubuntu before and I can't guarantee that the line ending control characters won't be changed, depending on the editor you use. You should probably obtain a live CD or windows repair CD just in case - prior to applying the edits)

---

### Post by altomang on 2011-06-02
neither worked, looks like my cpu is fubar'd until i get my hands on a win xp cd to reinstall

---

### Post by bcbc on 2011-06-02
> **altomang said:**
> neither worked, looks like my cpu is fubar'd until i get my hands on a win xp cd to reinstall

Why don't you download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That might help show what's going on.

---

### Post by mike555 on 2011-06-02
I would only reinstall XP as a last resort , it will probably not come with drivers for things like sound and video or even maybe ethernet card..... 
   you might try a live boot cd like "plop live"  from; [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)  , just burn the live.iso to a cd , then reboot off the cd , it will let you boot whatever operating systems you have (even usb drives).

---

