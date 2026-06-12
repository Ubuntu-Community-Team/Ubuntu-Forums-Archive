---
title: "Ubuntu 9.10 Grub2 Menu"
date: 2009-12-05
forum: General Help
---

### Post by beekr on 2009-12-05
So I'm trying to clean up my grub2 boot menu, you know the story - three different version etc etc. I've read most of the posts for doing so; i.e modifying the 10_linux or 40_custom file. When I open the 10_linux, it is one big script and 40_custom is perty much blank. Could anyone post how they cleaned up their's ? Thanks in advance,

Beekr

---

### Post by Herman on 2009-12-05
One idea, especially for those of us who are multi-booting, is to create a 'Dedicated GRUB2 Partition' and chmod the grub.cfg in it 777. It will be outside the control of operating system programs, so you can just edit it yourself any way you like. 
Probably just one chainloader entry for each operating system would be nice and tidy.

Of course you will still have GRUB 2 again in your operating system, or in some cases GRUB Legacy or LiLo, or even some non-Linux boot loader.
GRUB 2 doesn't really like being installed in a boot sector, it will protest but it will do it if you use the -f flag.
Booting from one boot loader to another may slow down your booting a little bit unless you configure your operating system boot loaders to not show the menu and have very little or no timeout. 
I'm not in a hurry, so I like to see all my menus and have them wait forever until I make a decision, but that's probably not for everyone.


Another idea is to change your boot-up resolution from 640x480 or whatever it is to whatever your monitor and video card normally run at. 
That way the text in your GRUB menu will appear relatively smaller so you can see a lot more of it at once, so you won't need to scroll as much. 
You can also fit a much nicer splashimage in that way too.

---

### Post by beekr on 2009-12-08
Ok, maybe I worded that wrong. Can anyone post how they modified 10_linux to show the latest version or their own 40_custom file ? 

Thanks,

Beekr

---

### Post by beekr on 2009-12-08
Found this thread: [http://ubuntuforums.org/showthread.php?t=1195275&highlight=40_custom](http://ubuntuforums.org/showthread.php?t=1195275&highlight=40_custom)

Search down where it says: "Building a Totally Customized Menu" explains it all right there.

---

