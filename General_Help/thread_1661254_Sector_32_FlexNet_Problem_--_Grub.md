---
title: "Sector 32 FlexNet Problem -- Grub"
date: 2011-01-06
forum: General Help
---

### Post by Virchanza on 2011-01-06
A few months ago, a friend of mine had an MS-Windows PC that was riddled with viruses, and he asked me to help him out with it.

So I shrunk his main MS-Windows partition and I created a partition for Ubuntu.

When Grub was installing to the MBR, it said something about [COLOR=Blue]Sector 32[/COLOR] being in use by FlexNet, but it didn't say that this was a fatal error.

After I installed Grub, I rebooted the PC, but I wasn't able to get Ubuntu to boot up. I eventually decided to explore the [COLOR=Blue]Sector 32[/COLOR] problem to see if that was the cause.

It seems a lot of people encounter this problem but I haven't seen one solution for it on the web other than to "wipe your hard disk". Total nonsense.

So I'm gonna try put together a solution in this thread. Let's take a look at the problem:

A hard disk is made up of sectors. A sector on a modern hard disk is 512 bytes. The first sector is called [COLOR=Blue]Sector 0[/COLOR], and it stores the Master Boot Record. The MBR consists of:
* 440 bytes for bootable code (such as Grub)
* 4 bytes for the disk signature
* 2 bytes of nulls
*** 64 bytes for the partition table**
* 2 bytes for the MBR signature

The partition table contains the list of partitions, saying what sector they start at and what sector they finish on.

You might expect the 1st partition to start at [COLOR=Blue]Sector 1[/COLOR], but actually it tends to start at [COLOR=Blue]Sector 63[/COLOR] on a lot of computers.  (The 1st partition tends to start at [COLOR=Blue]Sector 63[/COLOR] because there's 63  sectors in a cylinder, and MS-DOS wanted every partition to start at a  cylinder boundary). So that means there's 62 unused sectors between the MBR and the 1st partition.

(To find out where your own first partition starts, do [COLOR=Red]fdisk -lu /dev/sda[/COLOR]. On modern PC's this could be all sorts of numbers because of the way recovery partitions are laid out. By the way make sure that fdisk says that the sector size is "512 bytes"... because emm... I don't know what to say if it doesn't!).

It so happens that more than one program likes to make use of those 62 free sectors between the MBR and the 1st partition.

Grub has 440 bytes available to it in the MBR to store its bootable code, but it wants more space than that, so it uses the space between the MBR and the 1st partition. But Grub isn't the only program that wants to use that space, a thing called FlexNet does too. FlexNet is some sort of software license manager, and according to the warning issued by Grub, it likes to store data in [COLOR=Blue]Sector 32[/COLOR].

When you try to install Grub over FlexNet, Grub refuses to overwrite [COLOR=Blue]Sector 32[/COLOR] if it sees FlexNet data in it. It would be great if you could just tell Grub to overwrite [COLOR=Blue]Sector 32[/COLOR], but it provides no such facility. For me, this caused a problem and Ubuntu wouldn't boot up for me.

So what's the solution to get Grub working? You don't need to go wiping your entire hard disk, you just need to wipe the area between the MBR and the 1st partition.

**EXTREME CAUTION ADVISED: Wiping the storage area between your MBR and the 1st partition is an inherently dangerous activity. Doing so may result in serious injury and even  death. Programs which make use of this storage area, such as FlexNet, may cease to function. ****You willingly accept the serious risks involved. You accept as your own  responsiblity any harm that comes about as a result of following this guide, even if the guide contains errors or oversights.**

First, make a backup of the first 63 sectors of your hard disk (i.e. the MBR along with the 62 free sectors):

```

sudo dd if=/dev/sda of=~/first_63_sectors bs=512 count=63

```[B]

Trust me, back this up. No really. Do. Back it up. Seriously. You don't want to lose your partition table.[/B] Plus it's handy to have it backed up just in case you actually need that FlexNet data in future for whatever reason.

Next, erase [COLOR=Blue]Sector 1[/COLOR] through [COLOR=Blue]Sector 62[/COLOR] (i.e the 62 free sectors):

```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=62 seek=1

```That should do it, now [COLOR=Blue]Sector 1 [COLOR=Black]through [COLOR=Blue]Sector 62 [COLOR=Black]should be full of zeroes.[/COLOR][/COLOR][/COLOR][/COLOR] Do "grub-install" again and see what happens.

I'm not sure if FlexNet stores data in sectors other than [COLOR=Blue]Sector 32[COLOR=Black], but that's not a problem since we've just wiped everything between the MBR and the 1st partition.

If you want to target one individual sector to erase, then you can erase [COLOR=Blue]Sector 32[COLOR=Black] as follows:[/COLOR][/COLOR]

```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=[COLOR=Blue]32[/COLOR]

```After I erased the FlexNet data and re-installed Grub, the PC booted up fine.
[B]
If anyone sees any error in this post then please post here ASAP -- I'd hate for someone to lose data because of an error made in this guide.[/B]
[/COLOR][/COLOR]

---

### Post by oldfred on 2011-01-06
It is not just Flexnet which may be part of many different windows programs. Colin Watson from the grub2 team was looking for disk signatures as the windows software kept overwriting grub2. They obviously now have a workaround for flexnet, but may not for all software. Just be aware of other windows programs also.

[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html")
In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)

Some software that may use Flexnet, just so you do not lose it unless you have no need anymore for it.
Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others

---

### Post by EngDrewman on 2011-01-07
I am trying to set up a triple boot Win7 x64, Ubuntu x64, XP x32 setup. 7 and Ubuntu are up and running. While setting up Grub 2 I got the message about FlexNet. XP installer crashes with the 0x0000007B BSOD. I'm wondering if the XP installer thinks FlexNet is a boot sector virus and thus halts.

I really thinking about trying those commands you listed above to see if my theory is correct. The one thing I am not sure on is how to restore the sectors if worse comes for worse. Just to be sure, the command to restore the sectors would be "sudo dd if=~/first_63_sectors of=/dev/sda bs=512 count=63" correct?

---

### Post by EngDrewman on 2011-01-08
Well, tried it anyway. BTW the third command (the one that erases only sector 32) works just fine. Grub reinstalled with no errors.

My hunch was wrong about the XP installer though :( That issue is off topic, however. If someone reading this thinks they know the answer, msg me and I'll start a new thread elsewhere.

---

### Post by oldfred on 2011-01-08
Do you have a primary partition formated NTFS for XP?

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by mutt|ey on 2011-02-19
Thanks for your completed and explained procedure!

---

### Post by uBeer on 2011-02-28
Thanks for this info! I found out that I had to write sector 58 instead of 32 in order to remove FlexNet, but in the end it all worked out well. Thanks to this post and TestDisk!

---

### Post by Alp82 on 2011-07-05
Thanks to this thread i did not have to completely reinstall both my systems. My FlexNet was in sector 10, so i executed:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=[COLOR="Blue"]10[/COLOR]
```

But i have still a problem, after a while i got the same error, where Grub did not start and realized that FlexNet is in the MBR again. I think it was some automatic updater or something like that.

Does anybody know how to wipe FlexNet completely out from my system?

---

### Post by EngDrewman on 2011-07-05
Yeah I had the same problem- after I uninstalled it, I noticed it came right back. Weird. I called Gateway and they would not disclose any information about it unless I started a paid support session. My hunch, after some research, is that a system recovery utility is putting it there.

BTW if you are using Matlab, I know for sure it uses Flexnet. Don't uninstall it or Matlab won't run. Some other super expensive software packages use it too, so be careful. Be sure you back it up (using the instructions in a post above) in case suddenly something doesn't work.

---

### Post by dArksp0re on 2011-08-28
:) The suggestions made here work perfectly.  FlexNet on my dual boot system was on Sector 10 as one of the above posts and is DEFINITELY what was breaking my GRUB (actually in my case, BURG) boot.

Note:  You will have to reinstall/repair GRUB _**every time you ****open**_ whatever program is using FlexNet Licensing Service.  In my case it was Adobe Acrobat.

I'd also like to mention that before I came to this post, I had searched for a good tool to repair GRUB.  The best one I found that requires very little user interaction and is GUI driven and runs from the LIVE CD is [Boot Repair]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html").  It is very easy to use.  Simply add the PPA, download the program, and run.

If the web link to BOOT REPAIR goes inactive, then simply type/paste the following code into a terminal opened on the LIVE CD:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair

```
After the terminal session is finished, you can go to System - Administration - Boot Repair or search for and run Boot Repair.

---

### Post by smile4max on 2011-09-03
OK. it went bad. Now cant boot to anything and when i boot it takes me to GRUB rescue, and cannot boot from my live usb.
how to get back the backup files?

---

### Post by YannBuntu on 2011-12-18
**@all:** the method proposed by Virchanza has been implemented into [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")'s options:

[[img]http://pix.toile-libre.org/upload/img/1324245480.png[/img]](http://pix.toile-libre.org/?img=1324245480.png)

It is easier than command lines, and safe as it asks confirmation before each wipe.

---

### Post by john stiles on 2012-03-04
Thank you Virchanza, an excellent How To that rescued me.
I used your 2nd, command line, method. My /dev/sda first sector begins at 2048. I can confirm that substituting 2048 for 512 in your code works no problem.

---

### Post by Pablo W on 2012-05-08
> **Virchanza said:**
> A few months ago, a friend of mine had an MS-Windows PC that was riddled with viruses, and he asked me to help him out with it.

So I shrunk his main MS-Windows partition and I created a partition for Ubuntu.

When Grub was installing to the MBR, it said something about [COLOR=Blue]Sector 32[/COLOR] being in use by FlexNet, but it didn't say that this was a fatal error.

After I installed Grub, I rebooted the PC, but I wasn't able to get Ubuntu to boot up. I eventually decided to explore the [COLOR=Blue]Sector 32[/COLOR] problem to see if that was the cause.

It seems a lot of people encounter this problem but I haven't seen one solution for it on the web other than to "wipe your hard disk". Total nonsense.

So I'm gonna try put together a solution in this thread. Let's take a look at the problem:

A hard disk is made up of sectors. A sector on a modern hard disk is 512 bytes. The first sector is called [COLOR=Blue]Sector 0[/COLOR], and it stores the Master Boot Record. The MBR consists of:
* 440 bytes for bootable code (such as Grub)
* 4 bytes for the disk signature
* 2 bytes of nulls
*** 64 bytes for the partition table**
* 2 bytes for the MBR signature

The partition table contains the list of partitions, saying what sector they start at and what sector they finish on.

You might expect the 1st partition to start at [COLOR=Blue]Sector 1[/COLOR], but actually it tends to start at [COLOR=Blue]Sector 63[/COLOR] on a lot of computers.  (The 1st partition tends to start at [COLOR=Blue]Sector 63[/COLOR] because there's 63  sectors in a cylinder, and MS-DOS wanted every partition to start at a  cylinder boundary). So that means there's 62 unused sectors between the MBR and the 1st partition.

(To find out where your own first partition starts, do [COLOR=Red]fdisk -lu /dev/sda[/COLOR]. On modern PC's this could be all sorts of numbers because of the way recovery partitions are laid out. By the way make sure that fdisk says that the sector size is "512 bytes"... because emm... I don't know what to say if it doesn't!).

It so happens that more than one program likes to make use of those 62 free sectors between the MBR and the 1st partition.

Grub has 440 bytes available to it in the MBR to store its bootable code, but it wants more space than that, so it uses the space between the MBR and the 1st partition. But Grub isn't the only program that wants to use that space, a thing called FlexNet does too. FlexNet is some sort of software license manager, and according to the warning issued by Grub, it likes to store data in [COLOR=Blue]Sector 32[/COLOR].

When you try to install Grub over FlexNet, Grub refuses to overwrite [COLOR=Blue]Sector 32[/COLOR] if it sees FlexNet data in it. It would be great if you could just tell Grub to overwrite [COLOR=Blue]Sector 32[/COLOR], but it provides no such facility. For me, this caused a problem and Ubuntu wouldn't boot up for me.

So what's the solution to get Grub working? You don't need to go wiping your entire hard disk, you just need to wipe the area between the MBR and the 1st partition.

**EXTREME CAUTION ADVISED: Wiping the storage area between your MBR and the 1st partition is an inherently dangerous activity. Doing so may result in serious injury and even  death. Programs which make use of this storage area, such as FlexNet, may cease to function. ****You willingly accept the serious risks involved. You accept as your own  responsiblity any harm that comes about as a result of following this guide, even if the guide contains errors or oversights.**

First, make a backup of the first 63 sectors of your hard disk (i.e. the MBR along with the 62 free sectors):

```

sudo dd if=/dev/sda of=~/first_63_sectors bs=512 count=63

```[B]

Trust me, back this up. No really. Do. Back it up. Seriously. You don't want to lose your partition table.[/B] Plus it's handy to have it backed up just in case you actually need that FlexNet data in future for whatever reason.

Next, erase [COLOR=Blue]Sector 1[/COLOR] through [COLOR=Blue]Sector 62[/COLOR] (i.e the 62 free sectors):

```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=62 seek=1

```That should do it, now [COLOR=Blue]Sector 1 [COLOR=Black]through [COLOR=Blue]Sector 62 [COLOR=Black]should be full of zeroes.[/COLOR][/COLOR][/COLOR][/COLOR] Do "grub-install" again and see what happens.

I'm not sure if FlexNet stores data in sectors other than [COLOR=Blue]Sector 32[COLOR=Black], but that's not a problem since we've just wiped everything between the MBR and the 1st partition.

If you want to target one individual sector to erase, then you can erase [COLOR=Blue]Sector 32[COLOR=Black] as follows:[/COLOR][/COLOR]

```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=[COLOR=Blue]32[/COLOR]

```After I erased the FlexNet data and re-installed Grub, the PC booted up fine.
[B]
If anyone sees any error in this post then please post here ASAP -- I'd hate for someone to lose data because of an error made in this guide.[/B]
[/COLOR][/COLOR]

Hi,

In my case, the Flexnet-generated problem seems to be in sector 33.
```

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048   152158207    76078080   83  Linux
/dev/sda2       152160254   156301311     2070529    5  Extendida
/dev/sda5       152160256   156301311     2070528   82  Linux swap / Solaris
pablo@pablo-HP-Compaq-dc7700-Small-Form-Factor:~$ sudo grub-install /dev/sda
/usr/sbin/grub-setup: aviso: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

```

I'm trying to follow Virchanza's how-to, but when I do
sudo dd if=/dev/sda of=~/first_63_sectors bs=512 count=63
the outcome is 
```
sudo dd if=/dev/sda of=~/first_63_sectors bs=512 count=63
63+0 registros leídos
63+0 registros escritos
32256 bytes (32 kB) copiados, 0,0120631 s, 2,7 MB/s
```
so I'm not sure what's the highly recommended backup I should perform here. Could please anybody tell me how to go on from here?

---

### Post by YannBuntu on 2012-05-09
Hola Pablo,

don't worry, there is no problem in the command output you indicate (it created a backup of your MBR in your Home folder). Put this backup on a USB key by security. 
Then erase the FlexNet and reinstall GRUB, either by the command lines indicated in Post#1, or graphically via the "FlexNet" option of [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by Pablo W on 2012-05-09
> **YannBuntu said:**
> Hola Pablo,

don't worry, there is no problem in the command output you indicate (it created a backup of your MBR in your Home folder). Put this backup on a USB key by security. 
Then erase the FlexNet and reinstall GRUB, either by the command lines indicated in Post#1, or graphically via the "FlexNet" option of [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair").


Bonjour, Yannbuntu. And hello forum!
Thanks for that. It worked like a charm. I'll be reporting the whole experience in another post (from which I was referred to here), so that other people in the same situation can make use of it. For those interested, that thread is here [http://ubuntuforums.org/showthread.php?t=1976158](http://ubuntuforums.org/showthread.php?t=1976158).

à bientôt ):P

---

### Post by jwdonal on 2012-09-01
Virchanza's solution worked perfectly for me. My GRUB was working fine to begin with but I didn't like the FlexNet remnants being leftover from these reused drives (which used to have windows installed on them).

And, yes, if you're dual-booting windows you might want to leave FlexNet alone because you could break the windows/adobe/rescue/etc software that originally wrote to this sector (worst case). Best case is that when you boot into windows the software will just write its "turds" back into sector 32 (or whatever sector) and you'll have to do this all over again.  So you should really only bother with wiping it out if you're actually having issues with grub working, if not, just leave it alone.

Also, I only wiped the single sector 32 instead of the entire 1 through 62.  Worked fine.

---

