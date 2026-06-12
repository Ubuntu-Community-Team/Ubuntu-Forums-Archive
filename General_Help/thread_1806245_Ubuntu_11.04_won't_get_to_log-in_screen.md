---
title: "Ubuntu 11.04 won't get to log-in screen"
date: 2011-07-17
forum: General Help
---

### Post by mizushinzui on 2011-07-17
Hello guys, I was hoping you could help me with this.

Basically I was using my computer quite normally and all of a sudden something goes haywire, so I perform a safe shutdown from the shutdown/log off menu (which incidentally was displayed as squares instead of text) and restarted my computer. 

However every time I tried to turn it back on it won't get as far as the log on screen, it just sort of turns on (as the screen is still lit, but black) and sits there waiting. There is no log-on sound and I don't seem to be able to do anything. 

I made a seperate partition on the hard drive and re-installed an older version of ubuntu (10.10) and that's what I am currently using. I would usually just upgrade to 11.04 and use this new install instead. But I can't recover any of my files because every time I mount the other partition I can't access it. If I click on the 745GB file system (that's the other partition) it just disappears. 

If you can help me either recover my files from the other partition, or just help me boot my 11.04 sector again. 

Thanks in advance people :)

---

### Post by mmsmc on 2011-07-17
when you boot up are you able to get into the grub? if so boot into safe mode. if not boot into a live cd and see if that works

---

### Post by mizushinzui on 2011-07-17
I can get to grub and boot into what I assume is ubuntu's version of safe mode, recovery mode. I tried this before and I have tried most of the options that where available. 

I've updated grub, attempted to self repair packages and booted in failsafe graphic mode, and none of these things appear to have worked.

I do have an update on my other partition though,

I can now see all of the folders in the media folder of my current filesystem (folders like bin, home etc) however they are not showing up as folders. They are showing up as unkown files. I tried to open them with file browser but that didn't work. I managed to gain access to the folders through another program but since it was just looking for a inf file for my dongle I couldn't copy any of the files to my current partition. 

Hope this info helps.

EDIT: I managed to access my files using the gksudo nautilus command, I've deleted my old partition now that I have what I wanted, just thought I'd let you know that the error was never actually fixed in the end though.

---

