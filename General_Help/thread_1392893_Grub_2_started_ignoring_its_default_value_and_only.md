---
title: "Grub 2 started ignoring its default value and only starts at linux"
date: 2010-01-28
forum: General Help
---

### Post by foolfoolz on 2010-01-28
I have karmic (with all updates) and windows 7 (with all updates). I boot with grub2. I recently made a change to my grub menu, I added a new entry on top of the menu that boots windows 7. Ever since then, my default menu selection setting (which is set to 'saved') is ignored. Every time the system boots it default highlights linux. Here is a list of my /etc/grub.d/ folder:
```
00_header
05_debian_theme
06_Windows7
10_Linux
11_
20_memtest86+
30_os-prober
40_custom
```the 11_ is just a blank so there is a space in the menu. It has the exact same contents as the 06_Windows7 aside from the display name.

So i just added the Windows7 a few days ago and had this problem. Before that there was no file for loading windows. There was a menu option below all the others that said ```
Windows 7 (loader on /hd/sda2)
``` I couldnt move this menu entry around, i still dont know how it shows up there but it does.

So anyone have any ideas of something I might have done wrong to mess this up? This is what i put in my 06_Windows7 file:
```

#! /bin/sh -e
echo "Adding Windows 7" >&2
cat << EOF
menuentry "Windows 7" {
set root=(hd0,2)
chainloader +1
}
EOF
```It loads windows 7 fine never had any problems booting the os.

---

### Post by quixote on 2010-01-29
What do you have in 40_custom?  I believe that's where all the added menu entries should go, such as the Win7 you added.  ?? (Not sure.  Just starting with Grub2.)

In any case (from [Grub2 Ubuntu Community Docs]("https://help.ubuntu.com/community/Grub2#Initial%20Default")):> The default entry is determined by the DEFAULT=  setting in /etc/default/grub; the first "menuentry" is has a value of "0". So, if let's say Win7 was the fourth entry, and you wanted it as the default, it would say "DEFAULT=3".

Hope that helps.  As I say, I'm just learning grub2.

---

### Post by foolfoolz on 2010-01-31
well i figured out the windows 7 was being added the the os-prober. So i deleted my 06_windows file and renamed os-prober to 06_os-prober to move windows up the list. Everything works again.

---

### Post by quixote on 2010-01-31
Glad to hear it!  That's an interesting solution that I don't think I've seen before.

---

