---
title: "Startup screen"
date: 2010-07-07
forum: General Help
---

### Post by diego_pmc on 2010-07-07
I've been having the pretty common problem with proprietary Nvidia drivers that cause the startup screen to display at a very low resolution. I've fixed the problem by following the instruction found in the forum and on other sites. What I did was to give the [FONT=Lucida Console]GRUB_CMDLINE_LINUX_DEFAULT[/FONT] parameter in [FONT=Lucida Console]etc/default/grub[/FONT] the following value ([as suggested on Softpedia]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")): 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
```That fixed the resolution, but a small problem still persisted. Both before and after I changed that parameter value a small vertical black band of about 1 cm in width ran across the right side of my screen, as if the whole screen was off-centered. I tried pressing the "Auto" button on the monitor which readjusts the position of the screen but nothing happened.

How can I fix this?

---

### Post by diego_pmc on 2010-07-07
*(bump)*

---

### Post by Meneer Jansen on 2010-07-07
Maybe modify the 
mode_option=1280x1024-24
to 
mode_option=800x600-1
[FONT=monospace]
BTW: bump after 1,5 hours???

[/FONT]

---

