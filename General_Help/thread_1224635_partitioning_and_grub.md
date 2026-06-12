---
title: "partitioning and grub"
date: 2009-07-27
forum: General Help
---

### Post by thundaraptor on 2009-07-27
Greetings,

I have just installed a new system.  Took a 1 TB hdd and partitioned a 25gb section.  On the large 975 gb partition I have Jaunty Jackelop 9.04 installed and on the smaller 25 gb section I have hardy heron installed.  When I boot, I get the grub screen with the 9 second countdown to load...

How do I change which OS is at the top of the screen?  It currently has Hardy Heron in the top slot and I want Jaunty to be up there as basically I use the small partition just to play around with other systems.  

Thanks,

TR

---

### Post by oldfred on 2009-07-27
It sounds like the grub/menu.lst from Hardy is your boot configuration. If you have a kernel update in Jaunty your grub entry in hardy will not be updated and you will keep booting the old kernel. 
You may want to reinstall Grub so it points to your Jaunty's /boot/grub and menu.lst. You then can add a chainboot back to Hardy 
This is my entry, you would have to adjust the (hd2,0):
title       Ubuntu 9.04 64 bit @ sdc1
root        (hd2,0)
chainloader +1
Mine is set up on a different hard drive with grub installed everywhere.
More info on multiboot:
[http://members.iinet.net/~herman546/]("http://members.iinet.net/%7Eherman546/")
and chain boot 145 systems:
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
The advantage of chain booting is that updates get automatically included in the local menu.lst. The disadvantage is you have layered boot menus.

---

### Post by thundaraptor on 2009-07-27
How do I tell the grub to look for the jaunty kernal first and not the hardy?  is there a gui, is this a command line entry?  I am relatively unsophisticated user so I mostly learn via the cut 'n paste method or asking tons of questions.

---

### Post by thundaraptor on 2009-07-27
Looking at [http://www.gnu.org/software/grub/manual/html_node/root.html#root](http://www.gnu.org/software/grub/manual/html_node/root.html#root)

I think that if I enter the command line in grub while it is booting, I should be able to enter "root device (x,x)" where x,x is the different portion of drive to look at but when I do this I get the error message using the command "root device (0,0)" unrecognized device string.  Am I completely misunderstandin this?

---

### Post by thundaraptor on 2009-07-27
I went in and edited the grub in the 8.04 version and got it set straight.  now, how does the system know which grub menu.lst file to look at?  Is it picking the 8.04 because that partition appears before the full size partition that has jaunty on it?

---

### Post by louieb on 2009-07-27
Bet you installed Hardy last. Last OS installed will put its boot loader code in the MBR.  

anyway for a temporary fix  boot hardy fix press alt+f2 to bring up the run dialog. enter
```
gksudo gedit /boot/grub/menu.lst
```

find the Jaunty entry and copy or move it between these lines.

```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

```

Its temporary because you will have to change it next Jaunty has a kernel update.

For a better fix look at [IDBS GRUB Page]("http://members.iinet.net.au/%7Eherman546/p15.html")  in particular  search and check out the **configfile** option, or how to **chainload **one Linux install from another Linux installs grub menu. and what I do when I have more that 1 OS  [IDBS make a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")

---

### Post by bark50 on 2009-07-27
Can't thundaraptor just install Startup Manager from Synaptic and change the Default Operating System under the Boot Options tab to Jaunty?  For this to work, I think you would have to install Startup Manager in your Hardy partition since that was the last operating system you installed.

---

### Post by oldfred on 2009-07-28
It is the install of grub to the MBR that points to the copy of menu.lst and the operating system. If you reinstall GRUB it will run from Jaunty.

See this web site for more detail:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub+livecd](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub+livecd)

from above link see link for explainations

using live CD terminal session

[COLOR=DarkRed]sudo grub[/COLOR]
[COLOR=DarkRed]find /boot/grub/menu.lst[/COLOR]   *you will get two answers one for Jaunty and one for Hardy check your partitioning to know which is which.
[COLOR=DarkRed]root (hd?,?)[/COLOR]  where hd?,? is the jaunty location from above.
[COLOR=DarkRed]setup (hd0)[/COLOR]  if you are booting from your first hard drive
[COLOR=DarkRed]quit[/COLOR] 
When you reboot it should use the jaunty menu.lst Edit it like I said in my earlier comment as the last entry.

[COLOR=DarkRed]title       Ubuntu Hardy on sda2 [COLOR=Black]or where it is in fdisk -l[/COLOR]
root        (hd0,1) [COLOR=Black]from find above the hardy entry[/COLOR]
chainloader +1[/COLOR]

---

### Post by thundaraptor on 2009-07-28
Cool great posts.  I made the change to the menu.lst file inside the hardy partition.  I still get a messy initial grub screen but at least jaunty is the default boot.  I might try to redo the grub but since things are working now and I have other fish to fry, like proper dual dispaly i might hold off any further.  anyways, the problem is essentially fixed and I am continuing to learn about the os.  thanks.

---

