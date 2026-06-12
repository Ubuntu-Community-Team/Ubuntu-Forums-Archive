---
title: "Grub errors (can't boot Windows)"
date: 2006-06-01
forum: General Help
---

### Post by Adanufgail on 2006-06-01
I had a power outage which messed up my boot, so I used my windows setup disk and used fixmbr. That let me boot to Windows. I then used the Ubuntu Setup disk to install grub, and that worked fine, except now I can't boot to Windows.

Here is my Windows GRUB config:
```

title 		Windows XP
root   		(hd0,0)
makeactive
chainloader +
boot 
```

```

Here is the error message:

root     (hd0,0)
 Filesystem is fat, partition type 0xc
makeactive
chainloader +

Error 1: Filename must either be an absolute pathname or blocklist.
```

ANY help is apreciated.

---

### Post by Sutekh on 2006-06-02
[quote=Adanufgail]
Here is my Windows GRUB config:
```

title         Windows XP
root           (hd0,0)
makeactive
chainloader +
boot 
```[/quote] Can you try this alternative GRUB entry.  You can edit by selecting the Windows entry in the GRUB menu and pressing 'e'.  The you can edit the line again using 'e' to make the change (in bold)   ```

title         Windows XP
root           (hd0,0)
makeactive
chainloader + **1**
boot 
```Use 'b' to boot Windows.  

If this works then you can make the change permanent the next time you use Ubuntu.

Open a Terminal window (Applications -> Accessories Menu) and use these commands to backup and edit the GRUB menu
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` When the editor opens you can make the change.

---

### Post by Adanufgail on 2006-06-02
Nope, same error.

---

### Post by Adanufgail on 2006-06-02
bump. Any ideas?

---

### Post by Adanufgail on 2006-06-03
I tried running Windows Setup, going to the console and typing fixmbr. I rebooted, and the GRUB bootloader still came up, and Windows still didn't work.

---

### Post by Sutekh on 2006-06-03
Do you have Windows and Ubuntu on separate hard discs?

---

### Post by Adanufgail on 2006-06-04
Yes. Here is how I partitioned things.

Disk 1:
Windows

Disk 2:
NTFS
Ubuntu
SWAP

---

### Post by Sutekh on 2006-06-04
So which hard drive is the first booted device?  The first or second disc?

---

### Post by Adanufgail on 2006-06-04
By the BIOS? The first...

Under GRUB, I've tried putting Windows first, last, and 2nd in menu.lst. Still won't boot.

---

### Post by Sutekh on 2006-06-04
[quote=Adanufgail]By the BIOS? The first...

Under GRUB, I've tried putting Windows first, last, and 2nd in menu.lst. Still won't boot.[/quote]
Yep by the BIOS.

So the disc with Windows is booted first?  GRUB loads from this disc?

---

### Post by Adanufgail on 2006-06-04
I believe so.
I think I installed GRUB on the first disk over the Windows Bootloader.

---

### Post by Sutekh on 2006-06-04
And the Windows fixmbr didn't replace GRUB?  Thats wierd..

There a couple of things you can try, probably the easiest right now, is to reinstall GRUB.

Try this Wiki link

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Adanufgail on 2006-06-04
Would re-installing GRUB wipe my menu.lst file? Because when I rebooted...It was the same.


[EDIT]
And...My 2nd hard drive's first partition is not comming up...

---

### Post by Adanufgail on 2006-06-05
Any ideas?

---

### Post by Sutekh on 2006-06-05
[quote=Adanufgail]Would re-installing GRUB wipe my menu.lst file? Because when I rebooted...It was the same.[/quote]Yes it should have replaced the menu.lst.  

When you installed GRUB did it detect your Windows installation as [shown in this install step??](http://users.bigpond.net.au/hermanzone/p3/34ntfs.gif)

[quote=Adanufgail]
[EDIT]
And...My 2nd hard drive's first partition is not comming up...[/quote]What do you mean?  Not showing in the GRUB menu?

---

### Post by Adanufgail on 2006-06-05
No, that Windows Screen isn't coming up...

And my NTFS partition on my 2nd HD won't mount.

---

### Post by Adanufgail on 2006-06-05
No, that Windows Screen isn't coming up...

And my NTFS partition on my 2nd HD won't mount. That's because rather than type grub-install /dev/hda I typed grub-install /dev/hdb1 (hdb1 is my NTFS partition)

---

### Post by Sutekh on 2006-06-06
[quote=Adanufgail]No, that Windows Screen isn't coming up...

And my NTFS partition on my 2nd HD won't mount. That's because rather than type grub-install /dev/hda I typed grub-install /dev/hdb1 (hdb1 is my NTFS partition)[/quote] Oh, you used grub-install on /dev/hdb1?  I see.  Ok you may need to fix the Windows bootloader on *that (/dev/hdb1) *partition too.  When you ran fixmbr before, it would have been on the first disc, /dev/hda1.  Did Windows on the first disc work after using fixmbr?

If you check out [Microsoft's page on fixmbr]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true") you can specify which hard drive the fixmbr command works on.  


Due to the nature of the relationship between NTLDR (**NT** Loa**D**e**R**) and GRUB, I think you should get the NTLDR on both Windows partitions fixed *first*.  See if you can get both Windows partitions booting then try the grub-install, making sure you do it on the correct partition.


One more thing, when you said that you accidently used grub-install on /dev/hdb1, at that stage what OS's could you boot?  What ones could you boot afterwards?

Actually it'd be helpful to also know **when you could boot each OS**, and **what processes you tried** and then **what OS's you could boot after trying them**.  Do this first.

Hope this gets you somewhere...

---

### Post by Adanufgail on 2006-06-06
tried fixmbr \Device\HardDisk0 and fixmbr \Device\HardDisk1

Grub still came up :(



Anyway, when I acciedntily ran grub-install /dev/dhb1 I could boot Ubuntu. It ran fine except the NTFS drive (/dev/hdb1) wasn't mounting.

I made another thread to fix this and they said to run fixboot from Windows Setup...and that screwed everything up as now I go straight to the GRUB console and can't boot anything. I'm using a Live CD now and can only mount /dev/hda1 (nothing on /dev/hdb mounts)

---

### Post by Sutekh on 2006-06-06
[quote=Adanufgail]tried fixmbr \Device\HardDisk0 and fixmbr \Device\HardDisk1

Grub still came up :(

[/quote] This I still find really strange.  The fixmbr should remove GRUB from the disc MBR replacing it with the NTLDR instead.

I can but think of one explanation, perhaps when you instaled GRUB using the *grub-install* command, it installed GRUB on the ***root*** partition ofWindows ***not the MBR***.

Check out the [GRUB manual on using grub-install]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall") and see if I'm making any sense.

So if I'm reading this correct, the correct command is
```
grub-install /dev/hdb
``` Which writes GRUB to the MBR of the second hard disc.  *However, the command you used*
```
grub-install /dev/hdb1
```*I think writes GRUB to the Windows partition* *not the MBR*. I think this is why using fixmbr didn't remove the GRUB and allow you to boot Windows, because it wasn't on the MBR (/dev/hdb) but on the /dev/hdb**1** partition.  

What do you think?  Does that make sense?


There must be someway to repair the root partition of the Windows install, maybe thats what the fixboot command does??

The other thing to check from the Live CD is the GRUB menu and device map
```
cat /boot/grub/menu.lst
cat /boot/grub/device.map
``` 
[quote=Adanufgail]
Anyway, when I acciedntily ran grub-install /dev/dhb1 I could boot Ubuntu. It ran fine except the NTFS drive (/dev/hdb1) wasn't mounting.

I made another thread to fix this and they said to run fixboot from Windows Setup...and that screwed everything up as now I go straight to the GRUB console and can't boot anything. I'm using a Live CD now and can only mount /dev/hda1 (nothing on /dev/hdb mounts)[/quote] At this point I'd be more concerned with mounting the /dev/hda1 and /dev/hdb1 partitions.

Whats the problem with your /dev/hdb1 partition?  I'll check out the other thread.

---

### Post by Adanufgail on 2006-06-07
I'm not sure where /boot/ is located, but I think it's drive 2 (from which I can mount nothing).

---

