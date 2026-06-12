---
title: "modprobe: FATAL: Could not load /lib/modules/.../modules.dep et. all"
date: 2010-10-10
forum: General Help
---

### Post by petrasflorin on 2010-10-10
I get this error:

 modprobe: FATAL: Could not load /lib/modules/2.6.35-22/modules.dep
modprobe: FATAL: Could not load /lib/modules/2.6.35-22/modules.dep
(2x)

First: I get this error when I boot-up Ubuntu 10.10 , just before the login screen. Everything works fine however but I was wondering what is it and why am I getting it.

Second: After the install, just when it popped my CD drive open, I got some error repeated 60 or 70 times, something with I/O error on dev/sr0 , sector 533280.

Third: During install, in the partition creation menu, I used one partition mounted on / , one partition mounted on /home and created another one which I wrote in the input box to mount in /data (this is meant to deposit files in case of a reformat of everything I don't format that one).

The question is: In my filesystems, now appears a "data" folder, it's 345 GB large (I don't get it I made it 400 gigs, and this happened to all my partitions, they are considerably smaller, WTH?) is that my partition ? If so, why does it appear under the / partition ? shouldn't it be a partition by itself ? if I now format the / partition will it be formated too ?

Thanks.

---

### Post by warakawa on 2010-10-10
I just installed 10.10, and I have to same message.

---

### Post by petrasflorin on 2010-10-10
Which one lol ? :D

---

### Post by warakawa on 2010-10-10
modprobe FATAL could not load. 

I never got that message in 10.04

---

### Post by petrasflorin on 2010-10-10
anyone?

---

### Post by maedox on 2010-10-11
I'm seeing this too on my upgraded (from 10.04) machine at work. The one at home does not have this issue.

About your drives; First of all, bad idea to mix several issues in one thread. Second: mount|column -t will show you the mounted drives.

---

### Post by petrasflorin on 2010-10-11
,noexec,nosuid,nodev)
/dev/sda7         on  /data                     type  ext4                   (rw,commit=0)
/dev/sda6         on  /home                     type  ext4                   (rw,commit=0)
binfmt_misc       on  /proc/sys/fs/binfmt_misc  type  binfmt_mi


This is a small part of that mount thingy. I see it's mounted, that means it's a separate partition even if it shows up under / , right ?

the folder itself (data) is 365GB large, so that's a partition. I should worry about loosing it if I format / right ?

as for the mixing of questions, I already have about 10 open threads I don't wanna make more as I feel ima get myself shot.

---

### Post by dino99 on 2010-10-11
boot in recovery mode or with an other kernel

check your repo into: synaptic repo tab, you might only have genuine maverick repo activated, then update

you can delete files into /var/lib/dpkg/updates/

sudo rm -f /var/lib/dpkg/updates/*

then update

---

### Post by utvikl on 2010-10-11
I'm seeing the exact same issue. 

Bump to see if there is a solution to this problem.

---

### Post by DogMatix on 2010-10-11
Same issue here

modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or directory

After upgrade to 10.10 from 10.04

dino99 - I don't fully understand the instruction

> boot in recovery mode or with an other kernel

check your repo into: synaptic repo tab, you might only have genuine maverick repo activated, then update

you can delete files into /var/lib/dpkg/updates/

sudo rm -f /var/lib/dpkg/updates/*

then update

Could you elaborate please?

---

### Post by Aydos on 2010-10-11
The same thing has happened to me and many other people.

I started a thread around the same time as the OP with 2 pages of posts as well with no solution or clue on how to fix it.

---

### Post by Aydos on 2010-10-11
There is an official bug report for this as well. Hopefully a resolution is found for the problem. We have 2 threads here about it and that.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421?comments=all)

---

### Post by Meandlinux on 2010-10-11
A reinstall fixed it for me. I downloaded the ISO again and burned it at 8x speed.

---

### Post by mustail on 2010-10-12
I'm having the same issue on a fresh install of 10.10. It only appears at startup, before the ubuntu splash screen. The system feels like working ok to me though.

---

### Post by DogMatix on 2010-10-12
Opted for a fresh install. This has solved the issue along with a few other minor issues that I was experiencing.

---

### Post by petrasflorin on 2010-10-12
I'm in the same situation as mustail, it's a fresh install for me so... why should I reinstall it I don't see how that could fix the problem.

---

### Post by Meandlinux on 2010-10-12
> **petrasflorin said:**
> I'm in the same situation as mustail, it's a fresh install for me so... why should I reinstall it I don't see how that could fix the problem.

Try burning the ISO at the lowest speed.

---

### Post by Xenomorph05 on 2010-10-12
I have this problem on my netbook and I installed via USB.

---

### Post by Netscannur on 2010-10-13
Same issue with Dell Mini 910 with Intel 945 Graphics chipset.  Is this a problem with just the 945 chipset or does it extend across the board?

---

### Post by petrasflorin on 2010-10-13
> **Meandlinux said:**
> Try burning the ISO at the lowest speed.

I'd love to do that but apparently I can't.
Why ?
This is why: [http://ubuntuforums.org/showthread.php?t=1592108](http://ubuntuforums.org/showthread.php?t=1592108)

And nobody seems to know how can I fix it.

---

### Post by viant on 2010-10-14
I had the same problem modprobe fatal in my laptop. However, it does not appear on my another desktop machine.

I have looked at /var/lib/dpkg/updates directory, and it is empty

Has anyone solved the problem yet?

---

### Post by viant on 2010-10-16
Modprobe fatal problem is solved. Look at the other thread at:
[URL="http://ubuntuforums.org/showthread.php?t=1592311&page=2"]
http://ubuntuforums.org/showthread.php?t=1592311&page=2
[/URL]

It works for me

---

### Post by btindie on 2010-10-16
> **viant said:**
> Modprobe fatal problem is solved. Look at the other thread at:


It works for me

At where??!

---

### Post by viant on 2010-10-16
> **btindie said:**
> At where??!

I was still editing it, something wrong with the page, it was loaded very slow. but I have edited and make the url a link, instead of plain text.

This is the url again:
[http://ubuntuforums.org/showthread.php?t=1592311&page=2](http://ubuntuforums.org/showthread.php?t=1592311&page=2)

btw, how can I edit the thread status to be solved? I couldn't find it at thread tools. The thread tools only show:
- Show Printable Version
- Email this Page
- Subscribe to this Thread

---

### Post by btindie on 2010-10-16
Thanks for the link, I've just installed Ubuntu 10.10 Netbook and have the same problem.

As for marking the thread solved, I think it's only the OP that can do that...

---

### Post by btindie on 2010-10-16
I tried making the change to initramfs.conf as suggested and found it got rid of the error message upon startup but am instead left with a totally unresponsive system - when I type it can take a second or two for the text to appear, sometimes missing out characters that I've typed. Not at all useable. Plus I've lost the splash screen at startup. System is a Lenovo T61 Laptop.

---

### Post by draggy on 2010-10-17
Just as an FYI, this can also effect building modules, such as the compat wireless driver. Unfortunately the fix mentioned did not fix my build.

---

### Post by phenriqueff on 2010-11-01
I solve the problem doing this:

sudo gedit /etc/initramfs-tools/initramfs.conf

Then I modify the line 20:

MODULES=most    ->   MODULES=dep

After this reinstall the initramfs-tools:

sudo apt-get install --reinstall initramfs-tools

Finish

---

### Post by btindie on 2010-11-02
Instead of reinstalling initramfs-tools you can just run [FONT=Courier New]update-initramfs[/FONT] which will update the initrd image.
 
I tried doing that a while ago on mine but for some reason it caused other problems, can't quite remember what, so I reverted to the original problem. At least other than the message it still works.

---

### Post by belfastsixpack on 2010-11-05
bump this ****.

---

### Post by azeezp on 2010-11-06
> **mustail said:**
> I'm having the same issue on a fresh install of 10.10. It only appears at startup, before the ubuntu splash screen. The system feels like working ok to me though.

It happened for me after upgrading from 10.04 to 10.1. I did a net upgrade. May be we have to wait till new kernel comes

---

### Post by oregonbob on 2010-11-25
Bump. I gather this still have not been solved. Someone suggested "run update-initramfs", but all that does is show possible command line arguments. I tried the "-u" option so maybe that will fix it.???

---

### Post by comhead on 2010-11-27
> **oregonbob said:**
> Bump. I gather this still have not been solved. Someone suggested "run update-initramfs", but all that does is show possible command line arguments. I tried the "-u" option so maybe that will fix it.???

Try opening /etc/initramfs-tools/initramfs.conf with your text editor. Find the line "Modules=most" (line 20 in my Ubuntu 10.10) and change it to "Modules=dep". Worked for me.

---

### Post by iNsOmNiOuS on 2010-11-27
Funnily enough I get this error when loading up apf (Advanced Policy Firewall) on my server.

---

### Post by vidasov on 2010-12-09
Yes, realy worked for me also:

1. sudo vi /etc/initramfs-tools/initramfs.conf
2. change "MODULES=most" to read "MODULES=dep"
3. sudo  update-initramfs -u

and that's it. No more FATAL error saying that it can't load modules.dep

---

### Post by Bruce H on 2010-12-16
This is affecting me also. I've tried every fix I could find, including the one above, but nothing helps. I'm fully updated on 10.10 i386 on a dell mini 10. Irksome, indeed. Seeing an error message on boot is annoying and destroys the 'experience'.

---

### Post by mamboJambo on 2010-12-25
I also, change "MODULES=most" to read "MODULES=dep" and update-initramfs -u not fix nothing for me, the message it still works.
2.6.35-24-generic-pae

---

### Post by dino99 on 2010-12-25
why are you building headache with such red hiring ? its harmless.

---

### Post by jlgregory on 2010-12-27
I am also getting this on my NC10 at boot, as long as it is harmless then no worries, but as mentioned before it is annoying to see as you boot FAIL :(

---

### Post by DutchieR on 2011-01-19
Tried same ting, didn't work
However, I noticed that when running the "sudo update-initramfs -u" command , the error-message mentioned

 "FATAL: Could not load /lib/modules/2.6.35.25-generic/modules.dep: No such file or directory

This is correct and may be cause of the error since the folder names do not match with the actual folder name which is

 "2.6.35-25-generic" (a dash - between 35 and 25 in stead of a . period)

Is this the cause of the error?

---

### Post by FrankTM on 2011-02-01
> **vidasov said:**
> Yes, realy worked for me also:

1. sudo vi /etc/initramfs-tools/initramfs.conf
2. change "MODULES=most" to read "MODULES=dep"
3. sudo  update-initramfs -u

and that's it. No more FATAL error saying that it can't load modules.dep


works for me :)

---

### Post by begroup on 2011-02-12
hello all,
i am new to ubuntu 10.04.
When i compiled kernel 2.6.36.2 on it, it gave me the same error"
FATAL: could not load /lib/modules/modules.dep" for about few seconds then booted normally.
I tried changing MODULES:most to MODULES:dep in /etc/initramfs-tools/initramfs.conf and then ran"sudo update-initramfs.conf".
I showed "update /boot/initrd-2.6.32.1-generic (which is not the kernel i compiled).
Upon rebooting it displayed the same error message.
I have also read somewhere that it is a documentation bug and is harmless.
So what should do?

Eagerly waiting for reply....

---

### Post by De_Wr0ng on 2011-02-17
From working with RedHat, Fedora & CentOs I have learned that when the boot goes screwy after a kernel upgrade, REBUILD YOUR initrd file (I now do it after every kernel upgrade, regardless)


In Ubuntu's case this your your /boot/initrd.img for your running kernel

simply, the command

sudo update-initramfs -u will recreate the initrd.img 


Reboot and Presto!!!! supposed "FATAL boot error" went away


Just my 2 cents worth

---

### Post by leon.vitanos on 2011-02-18
...

---

