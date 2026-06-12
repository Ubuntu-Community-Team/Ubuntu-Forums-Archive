---
title: "How do I change labels on GRUB menu"
date: 2010-05-04
forum: General Help
---

### Post by blindape on 2010-05-04
Hi after upgrading to lucid lynx on my computer which dual boots to Ubuntu and Win Vista, the grub menu has changed the label for accessing vista from "Windows Vista (loader)" to "Windows Recovery (loader)".  At first I had major thinking that I had lost access to windows altogether, but when testing out the menu entries found that what was labelled as windows recovery was actually booting up Vista as normal.  So panic over, but I would like to change the label so that it actually reads Windows Vista and not Recovery.

Also I have a lot of entries on Grub relating to older versions of the linux kernel and I have to scroll down off screen to get to the windows entry.  How do I remove these old linux entries?

Cheers,

John Curwood

---

### Post by fooey on 2010-05-04
IIRC, you can just edit the cfg file to adjust menu entries. i suggest 2 things. 1 make a backup of it first then only adjust the text in the quotes for each menu entry.

sudo gedit /boot/grub/grub.cfg

---

### Post by fooey on 2010-05-04
err, well now that i think of it. it'll probably get overwritten frequently when an update-grub cmd is executed

good read/info on grub & grub2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by MrPok on 2010-05-05
> **blindape said:**
> ..after upgrading to lucid lynx ..

[INDENT]I can't tell from your first post which version of GRUB you are using. 
Depending on the version of GRUB, there is a slight difference in the way you update/edit.[/INDENT]

Which version are you using?
In terminal/commandline type:  ***grub-install -v***
Mine says "grub-install (GNU GRUB 0.97)", which indicates that I am using version 1.

If *grub-install -v* returns a higher version number you are using GRUB2, then pls stop reading here and read the excellent:
[QUOTE=fooey]good read/info on grub & grub2:

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")[/QUOTE]

--

If you are running version 1, then you need to edit the file 
/boot/grub/**menu.lst**

ALWAYS backup the file first, by making a copy with a different name. 
In /boot/grub/:  ***cp menu.lst BACKUP--menu.lst***

-- 
[INDENT]For removing old entries of the Linux kernels from GRUB there are a number of ways to do this, yet I propose you simply remove the old kernels except for say, the one you are using and the previous kernel you used (that didn't give you any trouble).
  GRUB automatically shows all kernels that are on your system, and keeping an older one is a way that you can alway revert back to an older one if a new kernel update unstabilizes your system.[/INDENT]

Which kernel are you using?
In terminal/commandline type:  ***uname -r***

To remove the unwanted kernels:
Go to System >> Administration >> Synaptic Package Manager, and type "linux-image" in the Quick search.
Then you can just right-click on any unwanted kernel and choose "Mark for removal". After you're done selecting/marking just choose Apply in the top bar.


Hope this helps!

---

### Post by blindape on 2010-05-07
Hi,

my Grub version is (GNU GRUB 1.98-1ubuntu6)
so I've been reading the suggested thread. It seems like a lot of work just to change a name on the menu, But I am still reading and will probably attempt something in the next day or two.  As a general question, does anyone know why the automated OS search would now name Vista as Windows Recovery Environment when on Karmic it was called Vista?

uname -r gave me 2.6.32-22-generic, so all I need to do is use synaptic package manage to remove the old kernels except for the previous kernel that gave no trouble?

Cheers,

John

---

### Post by MrPok on 2010-05-07
> **blindape said:**
> Hi,

my Grub version is (GNU GRUB 1.98-1ubuntu6)
so I've been reading the suggested thread. It seems like a lot of work just to change a name on the menu, But I am still reading and will probably attempt something in the next day or two.  As a general question, does anyone know why the automated OS search would now name Vista as Windows Recovery Environment when on Karmic it was called Vista?
Sorry I am not running GRUB2, so I can't help you there. Good luck though! ;)

> **blindape said:**
> 
uname -r gave me 2.6.32-22-generic, so all I need to do is use synaptic package manage to remove the old kernels except for the previous kernel that gave no trouble? ..
Correct. The first time you do a thing like this it is still a scary procedure (*"removing a kernel"* sounds like hefty stuff 8-[), but it is really very easy to do, so you'll do fine. Just keep one or two older kernels in case the newest one gives you problems.

Cheers,
p a u l

---

