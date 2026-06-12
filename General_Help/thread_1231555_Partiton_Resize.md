---
title: "Partiton Resize?"
date: 2009-08-04
forum: General Help
---

### Post by fleamour on 2009-08-04
If I resize Linux partition & move to the left also moving Linux swap, will Xubuntu cope?

---

### Post by cholericfun on 2009-08-04
maybe

save your data and be ready for a days work,
that said it might do just fine - i think -
i never did it myself

---

### Post by CatKiller on 2009-08-04
You'll be fine. At worst you'll need to amend /etc/fstab to reflect any changes in the swap partition.

Backup anything important, though, just in case.

---

### Post by fleamour on 2009-08-04
I am using G-Parted, I guess it'll cope automatically without intervention on my part.  Win2k has put up with all my abuse!

> At worst you'll need to amend /etc/fstab to reflect any changes in the swap partition.


Not sure what that means but maybe I should Google it.

EDIT:  Sounds complicated!

---

### Post by CatKiller on 2009-08-04
> **fleamour said:**
>  Not sure what that means but maybe I should Google it.

EDIT:  Sounds complicated!

Nah. fstab (the filesystem table) is a list of filesystems that you want mounted. Each line contains a reference to a partition. It's possible that moving the swap partition will change its reference, in which case you would update fstab to reflect the change. But I don't think you'll need to.

---

### Post by fleamour on 2009-08-04
I guess if swap moved & not reflected in fstab then it wont hibernate properly.

---

### Post by fleamour on 2009-08-04
As I thought it refuses to hibernate stating cannot find swap file.  Other than that it boots OK.  Where can I find the fstab file & edit its contents?  Also what new info should replace the current info?

---

### Post by Glyndwr on 2009-08-04
fstab file is /etc/fstab.  There should be a line for swap there already, just change it to use the correct partition.

---

### Post by fleamour on 2009-08-04
I guess I can ascertain the correct partition by using G-Parted?  Also Xubuntu boots verbosely with white writing on a black backround.  I'm sure it did not do this before.  Is there a way round this without a full reinstall? Maybe fstab needs editing to correct this as well?

---

### Post by merlinus on 2009-08-04
Try adding quiet to the end of the kernel line and in a new line after initrd in /boot/grub/menu.lst.

---

### Post by Glyndwr on 2009-08-04
Im pretty sure the boot text thing is a setting in menu.lst

/boot/grub/menu.lst

Look for the words quiet or splash in the kernel line.  I'm pretty sure its one of those that you need, just dont remember which one.

For instance here's mine:

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		cd8f1784-9cff-484a-84a6-677694ace9a2
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=cd8f1784-9cff-484a-84a6-677694ace9a2 ro **quiet splash **
initrd		/boot/initrd.img-2.6.28-14-generic

---

### Post by CatKiller on 2009-08-05
> **fleamour said:**
> As I thought it refuses to hibernate stating cannot find swap file.  Other than that it boots OK.  Where can I find the fstab file & edit its contents?  Also what new info should replace the current info?

Edit the file with ```
gksudo gedit /etc/fstab
``` Find the line that refers to your swap partition. It'll say something like ```
UUID=bc7ccb70-66c1-4e51-8cc3-f741c0e78e4a       none            swap    sw
``` You'll need to change the UUID number to that of your swap partition, which you can find out with something like ```
sudo vol_id -u /dev/sda2
``` (Obviously you should put where you're swap partition is rather than /dev/sda2. That's just an example. I have no idea how you've got your partitions laid out.)

---

### Post by fleamour on 2009-08-05
OK, well the swap partition is the same partition as before just moved that's all.  I'll try following with correct syntax:  

> sudo vol_id -u /dev/sda2

At work now, & then a blast through the woods on mountain bike, so probs not get a look till Thurs evening but thanks for all your help.  Nice one.

---

### Post by fleamour on 2009-08-05
> **Glyndwr said:**
> Im pretty sure the boot text thing is a setting in menu.lst

/boot/grub/menu.lst

I have found this txt:

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=48a94401-da75-405d-b594-003b523d6c49 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

Nothing entered after quiet option.  What is the correct syntax?

EDIT:  No wait, it already says "ro quiet splash".  Not reading it properly.  Not sure why it boots verbosely?

---

### Post by fleamour on 2009-08-05
> **CatKiller said:**
> Edit the file with ```
gksudo gedit /etc/fstab
```

When I use above code nothing happens.  I tried to manually navigate to fstab but think the directory is different under Xubuntu?

---

### Post by egalvan on 2009-08-05
> **fleamour said:**
> When I use above code nothing happens.  I tried to manually navigate to fstab but think the directory is different under Xubuntu?

Xubuntu 9.04 has the same directory structure.

it shows under /etc/fstab on my xfce install.

gksudo is a Gnome app, not available under xfce,
unless you installed xfce over Gnome...
and kdesu is the KDE equivalent.

I don't know the equivalent for xfce.

but when you say "nothing happens", do you mean absolutely nothing?
Or an error code?

Typing the wrong thing into a bash shell should return an error code at least.

---

### Post by CatKiller on 2009-08-05
> **fleamour said:**
> When I use above code nothing happens.  I tried to manually navigate to fstab but think the directory is different under Xubuntu?

Sorry, didn't register that you were using Xubuntu. I believe the equivalent would be ```
gksudo mousepad /etc/fstab
``` or ```
sudo nano /etc/fstab
``` will work on anything (nano is a command-line text editor).

---

### Post by fleamour on 2009-08-05
> **egalvan said:**
> when you say "nothing happens", do you mean absolutely nothing?
Or an error code?

It just reverts to a command prompt as if nothing has happened.

---

### Post by fleamour on 2009-08-05
Well after carefully following instructions, she will appear to hibernate without error messages, but upon powering up she just reboots afresh?

Can anyone see any errors with my fstab file?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=48a94401-da75-405d-b594-003b523d6c49 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=65d7603b-325f-42a0-b96e-48ed5a42a1e0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by CatKiller on 2009-08-05
It's possible that you need to add/modify a **resume** entry in your menu.lst to tell GRUB where to look for the image to use to wake up, such as ```
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=48a94401-da75-405d-b594-003b523d6c49 ro quiet splash resume=UUID=65d7603b-325f-42a0-b96e-48ed5a42a1e0
``` You can put a similar entry in the **defoptions** line when you know it works if you want this entry to be automatically added to menu.lst when you install a new kernel.

---

### Post by michy99 on 2009-08-05
To make sure you have the right UUID for the swap partition, enter:```
blkid
```

---

### Post by fleamour on 2009-08-06
> **michy99 said:**
> enter:```
blkid
```


OK.  What does that do out of interest?  I have carefully copied/pasted UUID code from command line twice just to make sure and will try adding resume entry to menu.lst when get off work.

---

### Post by michy99 on 2009-08-06
> **fleamour said:**
> OK.  What does that do out of interest?  I have carefully copied/pasted UUID code from command line twice just to make sure and will try adding resume entry to menu.lst when get off work.

blkid just tells you what the ids are for your partitions. Make sure the UUID for the swap partition is the same as the one in the fstab file. If it is different, change the one in the fstab to match. (Without the quotation marks.)

---

### Post by martinbaselier on 2009-08-06
A few tips:

You don't really need UUIDs

You can replace
# /dev/sda2
UUID=65d7603b-325f-42a0-b96e-48ed5a42a1e0 none swap sw 0 0
with 
/dev/sda2 none swap sw 0 0

in /etc/fstab

Use **sudo fdisk -l** to make sure your swap is on /dev/sda2

**sudo swapon /dev/sda2** will also turn the swap on. I think it will make an entry in fstab automatically.

---

### Post by fleamour on 2009-08-06
> **martinbaselier said:**
> **sudo swapon /dev/sda2** will also turn the swap on. I think it will make an entry in fstab automatically.


I get:

/dev/sda2: Device or resource busy

---

### Post by michy99 on 2009-08-06
> **martinbaselier said:**
> A few tips:

You don't really need UUIDs

You can replace
# /dev/sda2
UUID=65d7603b-325f-42a0-b96e-48ed5a42a1e0 none swap sw 0 0
with 
/dev/sda2 none swap sw 0 0

in /etc/fstab

Use **sudo fdisk -l** to make sure your swap is on /dev/sda2

**sudo swapon /dev/sda2** will also turn the swap on. I think it will make an entry in fstab automatically.

That is fine if you never add or remove disks. If you do, the /dev designation can change, while that UUID will not.

---

### Post by fleamour on 2009-08-06
**blkid** just returns a command prompt, nothing happens.

---

### Post by michy99 on 2009-08-06
> **fleamour said:**
> **blkid** just returns a command prompt, nothing happens.

That's odd. What about```
 sudo blkid
```

---

### Post by martinbaselier on 2009-08-06
> /dev/sda2: Device or resource busy 
This normally means your swap is already on. 

To view the status of your swap:

**swapon -s**

---

### Post by fleamour on 2009-08-06
Swap is definitely on & **sudo blkid** works.  Thanks.  Not sure why she won't hibernate?  Ever since moving partition, I may reinstall the whole thing.

---

### Post by fleamour on 2009-08-06
I tried to edit menu.lst to add resume entry but file is locked?  How do I obtain root permission?

---

### Post by CatKiller on 2009-08-06
> **fleamour said:**
> I tried to edit menu.lst to add resume entry but file is locked?  How do I obtain root permission?

The same way you'd get root permissions for anything; with [sudo]("https://wiki.ubuntu.com/RootSudo"). Didn't we do this on page 2?

```
sudo nano /boot/grub/menu.lst
```

or

```
gksudo mousepad /boot/grub/menu.lst
```

---

### Post by michy99 on 2009-08-06
> **fleamour said:**
> I tried to edit menu.lst to add resume entry but file is locked?  How do I obtain root permission?

```
gksudo gedit /boot/grub/menu.lst
```Or for a simple cli editor```
sudo nano /boot/grub/menu.lst
```

Edit: forget gedit, I forgot you were on xubuntu.

---

### Post by fleamour on 2009-08-06
> **CatKiller said:**
> Didn't we do this on page 2?

Your right.  I was blindly copying & pasting, but makes sense just to change the file path.  I'll have to remember that.  Thanks.

---

### Post by fleamour on 2009-08-06
Genius!!!

Thank you everybody for there involvement.  Adding a resume entry to menu.lst was indeed the solution.  

One last thing!  Should Xubuntu show any white writing on black backround when booting?  I don't seem to recall this but cannot remember how it was before moved partition.  That said, I was probably hibernating in which case it would show none.

Thanks.

---

### Post by CatKiller on 2009-08-06
> **fleamour said:**
>  One last thing!  Should Xubuntu show any white writing on black backround when booting?

If it works like standard Ubuntu, then you should only see text by default if there's a warning or something is taking a long time (that's what "quiet" on the kernel line does). You would normally see a splash screen instead (that's what "splash" on the kernel line does).

If you've got both options specified already then I don't know what to suggest, since I don't know that much about boot splash screens. Looking at how people change their splash screens might point you in the right direction to fix yours. I understand that the process to get it to work is quite complicated, but it's been automated to the extent that the user side of it is just a couple of commands.

---

### Post by fleamour on 2009-08-06
Someone seems to have explained it better than me on Experts Exchange forum:

"Now when it is booting up and showing the splash screen, it only shows it until about 30% loaded, then it shows the actual prompt commands while the operating system loads.  Anybody know what caused it to stop showing the splash screen the whole way through the OS load process?"

Pity it's not free content (unless I sign up for free account then cancel membership.)

Def since moved partition but not enough of annoyance to reinstall.  I have not found much with a cursory glance through Google results but will try again later.

---

### Post by fleamour on 2009-08-07
Figured it out.  I actually have two kernel options at start up besides memtest & recovery.  The other is the remnants of another install, I did not format partition when re-installing.

---

