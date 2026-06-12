---
title: "Can no longer boot"
date: 2009-11-06
forum: General Help
---

### Post by kaelonlloyd on 2009-11-06
I was using ubuntu 9.10 as normal but when i tried to turn it on just now grub2 didn't appear, only a termninal type screen came up. My windows boots fine, but windows isn't the best of OS's.

i used wubi to install ubuntu 9.10 if that changes anything, and i didn't do a hard reboot, which i know can corrupt data.

Does any one what heppened?

---

### Post by jbrown96 on 2009-11-06
Could you elaborate on "the terminal" screen that appears? Is it a Ubuntu terminal? Are there any options? Any error messages, or anything about busybox?

---

### Post by kaelonlloyd on 2009-11-06
I just tried boting again, i get taken into the grub 1.97~beta4, which says something about TAB (I didn't understand)

I typed 'help' in and list of commands came up

I then tried 'Boot' and it said 'error : No selected Kernel'

Before this comes up something flashes about NTFS but it goes too quick to piece together.

Could it be caused by a program?, i recently installed 2 HTML editors through software center before shutting down.

Edit: i also done some updates as well

---

### Post by jbrown96 on 2009-11-06
When you get to the Grub2 secreen, there's usually a list of kernels that you can choose to boot. Are they there, or is it blank? You may need to hold the Shift key during boot to get this window. Try the kernel at the top. If that doesn't work, then try the next non-recovery entry.

---

### Post by pqwoerituytrueiwoq on 2009-11-06
TAB probably means press the tab key
not trying to say you are an idiot
i use the old grub new one lags for me 
how does a text iu lag?

---

### Post by kaelonlloyd on 2009-11-06
> **pqwoerituytrueiwoq said:**
> TAB probably means press the tab key
not trying to say you are an idiot
i use the old grub new one lags for me 
how does a text iu lag?

Don't worry i have a brain and so tried the TAB button, but no luck.

I done some research though and came across this
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)

It turns out i'm in CLI mode, i don't know how, but i do know when. 

Anyways, can anyone help me fix this problem now that you know what i limited too.

Oh and the ESC button doesnt take me to menu mode like the page says, and that part that says press ESC doesnt show up for me

Edit: i've gon into C:\ubuntu\disks\boot\grub on my windows partition an theres is no file, if it matters

---

### Post by jbrown96 on 2009-11-06
> **pqwoerituytrueiwoq said:**
> TAB probably means press the tab key
not trying to say you are an idiot
i use the old grub new one lags for me 
how does a text iu lag?

Grub1 had a file at /boot/grub/menu.lst that contained all the bootable system and preferences. 
Grub2 dynamically creates the entries at boot, so it takes a little time to scan everything. I'm not a huge fan of grub2, but it does have some cool features. I put fedora on a flash, and I missed pressing F12 in the BIOS to boot from it. However, it showed up as an entry in Grub, which is pretty spectacular. It also removed the entry on the next boot. 

Please don't insinuate (even if say you are not trying to) that a new user is an idiot. It's unwelcoming.

---

### Post by P4man on 2009-11-06
Im no expert in wubi installs (all I know is that one should avoid them), but does a wubi install even use grub? I thought it used the windows bootloader, or is the windows bootloader used to  chainload grub? And if so where is the grub folder, on the host ntfs partition or inside the virtual partition? Can anyone with more experience with wubi enlighten me?

Anyway, to the OP. Since a wubi install is dependant on the file system of the host OS (windows) I suggest you do a thorough check of your filesystem to start with.

---

### Post by kaelonlloyd on 2009-11-06
> **P4man said:**
> Im no expert in wubi installs (all I know is that one should avoid them), but does a wubi install even use grub? I thought it used the windows bootloader, or is the windows bootloader used to  chainload grub? And if so where is the grub folder, on the host ntfs partition or inside the virtual partition? Can anyone with more experience with wubi enlighten me?

Anyway, to the OP. Since a wubi install is dependant on the file system of the host OS (windows) I suggest you do a thorough check of your filesystem to start with.

As far as i know the windows boot loader boots into grub

---

### Post by kaelonlloyd on 2009-11-06
Looking around i've found out that pressiing tab after a bracket will show a list of bootable partitions, but there is only 1, which is 'loop0' this i take is something to do with wubi due to a prior problem with wubi being unable to end loop0(this problem was fixed with a clean install)

So i know that loop0 is my only partition in grub if that helps?

---

