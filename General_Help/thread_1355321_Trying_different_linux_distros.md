---
title: "Trying different linux distros?"
date: 2009-12-14
forum: General Help
---

### Post by jmate24 on 2009-12-14
i would like to try at least 4 different linux distros including ubuntu.

and i am wondering how i could set it up on my laptop.

right now i am running ubuntu karmic and it is running pretty well. but i have other linuxes that i would like to try even if it means rewriting my hard drive several times but i would like to either do it on an 8 GB thumb drive or use my laptop hard drive which is 372.61 GB and i have 3GB of ram installed.

how would i go about this? 

the distros i am planing to use are as follows:

Windows XP -- 80GB or not on thumb
Puppy Linux 4.3.1 -- 60GB or 1GB on thumb (thumb installer)
OpenSuse 11.1 -- 60GB or 1GB on thumb (thumb installer)
Ubuntu 9.10 Karmic -- 80GB or 1GB on thumb (thumb installer)
Open Solaris 2009.06  80GB or 1GB on thumb (thumb installer)
linux-swap -- 6GB or 4GB on thumb (thumb installer)

and what would be the best order to install these?

---

### Post by audiomick on 2009-12-14
Hallo.

Have you thought of putting the try-outs in a virtualisation?

If you are installing, windows first. Things I have read here in the forum suggest that SuSe is prone to ignoring other linuxes, but it should see a windows, so that next, then the others.

---

### Post by EndPerform on 2009-12-14
> **audiomick said:**
> Hallo.

Have you thought of putting the try-outs in a virtualisation?

If you are installing, windows first. Things I have read here in the forum suggest that SuSe is prone to ignoring other linuxes, but it should see a windows, so that next, then the others.

Virtualization would definitely be the way to go if you want to experiment.  That's what I'm currently doing right now.  My host OS is Windows 7, and I have Ubuntu 9.10 installed via Virtualbox.  Eventually I may switch back to dual-boot, but being able to start Linux from within Windows is a bit more handy than a reboot.

---

### Post by jeb800e on 2009-12-14
You can try partitioning your drive, but be warned, partitioning may cause file damage to your other operating systems, but the chances of that aren't too too high.

---

### Post by JC Cheloven on 2009-12-14
> **jeb800e said:**
> You can try partitioning your drive, but be warned, partitioning may cause file damage to your other operating systems, but the chances of that aren't too too high.

I also inform people that partitioning is quite a serious thing. But then I say that I have partitioned and repartitioned over 100 times in some 35 different machines without any problem. 

I personally don't like virtualization. You may not get exactly the same behavior as installing. 

I wouldn't install any swap in a pendrive. Probably swap will be never used anyway, but it is intended to work as ram if needed. A pendrive is much more limited in read/write lifetime that ram

I wouldn't install puppy. I'd use it from live, perhaps whith that is called "frugal install". It's what it is intended for. You'll get the best from puppy in that way.

I don't understand the need of trying distros using 60Gb each. With such a huge disk, I'd go for something like this:

xp -->  50 Gb NTFS
YourData  --> 200Gb NTFS  (or more)
then an extended partition containing:
[INDENT]suse --> 12Gb
ubuntu --> 12Gb
solaris --> 12Gb
whatever --> 12Gb
justincase --> 12Gb
(...)
swap  --> (find out how much you really need)[/INDENT]

The idea is to store all your data in the big partition, no matter which OS you are using (perhaps excluding win2, depending of what you do). Hope you find it useful.

EDIT: although you'll probably end up using only ubuntu, I'd suggest you to include Mandriva and Fedora in your tests. They're both worth, better than suse, imo.

---

### Post by jmate24 on 2009-12-19
thanks. that really helps. plus i have an external hdd and i am just going to save all of my data on that and partition my hard drive accordingly.

first i am just going to make my hard drive extended,
then i will install as many Linux OSes as possible while only using one swap partition for all of them.

plus... i believe i have already tried open suse and i think i liked it? but maybe it has changed so much from then that i may end up using it.

i am also wondering if anyone likes open solaris?

the OSes that i am going to use are ubuntu 9.10 amd64 desktop, xubuntu 9.10 amd64 desktop, mandriva 2009.1 gnome i586, open suse 11.1 x86_64, fedora 11 i686, and open solaris 2009.06 x86/64.

i know that they can be finicky, but i am wondering in what order do i install these OSes?

jmate24--:D

---

### Post by JC Cheloven on 2009-12-19
> **jmate24 said:**
>  first i am just going to make my hard drive extended,
[INDENT]A physical drive can have as much as 4 primary partitions. To advoid problems, my advice would be to setup at least one primary partition for windows (the first one). Then you can make an extended partition of the rest of the disk if you want, and put inside this extended partition as many logical partitions as you like (the data one, the small 12gb ones, the swap...)[/INDENT]

> plus... i believe i have already tried open suse and i think i liked it? but maybe it has changed so much from then that i may end up using it.
[INDENT]A matter of taste, and of how well it deals with your hardware. I disliked the affairs between M$ and Novell anyway.[/INDENT]

> the OSes that i am going to use are ubuntu 9.10 amd64 desktop, xubuntu 9.10 amd64 desktop, mandriva 2009.1 gnome i586, open suse 11.1 x86_64, fedora 11 i686, and open solaris 2009.06 x86/64.
[INDENT]I can't remember exactly, but I think I've read something about using the same swap space for 64 and 32 bit OSes being problematic. I'd suggest you to do a search[/INDENT]

> i know that they can be finicky, but i am wondering in what order do i install these OSes?
[INDENT]I've never installed solaris, but I'm pretty sure about ubuntu being able to setup grub correctly for the other OSes. So, I'd install ubuntu last.[/INDENT]

---

### Post by jmate24 on 2009-12-20
mandriva 2009.1 gnome i586, fedora 11 i686, and open solaris 2009.06 x86/64, xubuntu 9.10 amd64 desktop, ubuntu 9.10 amd64 desktop. including setting up a swap partition for each individual os. and skip open suse.

well there is a problem with setting up several swap partitions in that my memory on my laptop is 4GB and if i set up each individual one that is 8GB per os. 

5x8=40GB, i wonder if i can get away with only having 2 swap partitions one for x86 compatable and one for x64 compatable?

jmate24--:D

---

### Post by JC Cheloven on 2009-12-25
@jmate: sorry I forgot to follow this post. Hope this is still of any interest for you.

Of course, only 2 swaps would be enough. Even NONE would do, having 4Gb ram !
Plus I wouldn't install any 32bit OS. You'll unable to use about 1 Gb ram from it.
Cheers

---

### Post by jmate24 on 2009-12-31
so what i am wondering is what order should my distros be installed?

---

### Post by dcstar on 2009-12-31
> **jmate24 said:**
> so what i am wondering is what order should my distros be installed?

The piece of string is 4cm long......

---

### Post by rnerwein on 2009-12-31
high - not overclocked
here is my installation order:
vista (32bit), suse 11 (64 bit), ubuntu 9.10 (64 bit) and solaris 10 (64 bit).
i am using the suse grub boot loader - i think this is the information you want
ciao

---

### Post by jmate24 on 2010-01-02
what i meant to ask was what _order_ should my _distros_ be installed?

these are the _distros_ that i am going to use and i have since gotten the x86_64 versions of my x86 versions.

mandriva 2009.1 x86_64, fedora 12 x86_64, and open solaris 2009.06 x86/64, xubuntu 9.10 amd64 desktop, ubuntu 9.10 amd64 desktop.

so which _order_ should i _install_ these?

and yes i am skipping windows and putting it into virtual box... 

and i do acknowledge that now with 4GB of RAM i probably do not need a swap partition.

---

### Post by malspa on 2010-01-02
You could get a lot of different answers to that question, "what order should my distros be installed."  In other words, there is no correct answer.  In my multi-boot set-ups, the first distro is the one I'm most comfortable with and the one I'm usually using as my main system.  After that, it really doesn't matter the order, I just take one at a time, get it installed and set up, go on to the next.

---

### Post by jmate24 on 2010-01-03
ok, i will try that....

thanx,

jmate24--:)

---

### Post by JuseBox on 2010-01-03
I would also suggest trying out archlinux as well.  The comments about vm for testing in my personal trials is that you can't trust the vm compaired to your hardware.  Things work differently in a vm then they would native. I have a testing Pc and have just about everything imaginable partioned out on a 1TB drive.  Good Luck!

---

### Post by Roasted on 2010-01-03
I would heavily stress to use virtualizing as a means of testing other distros. I have a spare computer here that I tried quad booting. I attempted XP, Kubuntu, Suse, and Fedora. After Suse installed I rebooted, and all that was in the options was XP and Suse. I asked in the Suse chat and it turns out Suse 11.2 uses Grub 1 and Kubuntu 9.10 uses Grub 2, aiding in the problem. I also found an open bug with Suse in regard to it having trouble picking up other Linux distros, but always succeeding with picking up Windows and auto-adding it to the Grub menu.

In short - I wouldn't screw with partitioning the crap out of your hard drive. Just virtualize that **** if all you're doing is testing.

---

### Post by malspa on 2010-01-03
As for the "virtualization vs. installation" debate, to each his own.  Not everyone likes virtualization.  Myself, I prefer to install and multi-boot.

---

### Post by Roasted on 2010-01-03
> **malspa said:**
> As for the "virtualization vs. installation" debate, to each his own.  Not everyone likes virtualization.  Myself, I prefer to install and multi-boot.

I do too, but after the headaches I experienced today with Kubuntu magically disappearing due to Suse's existence, and seeing Suse on his list of things to check out, I figured simplicity may favor Virtualizing.

There's something about having the operating system actually boot up on a computer that feels different than it running virtually that I prefer. But it's far too easy to just blam - boot up a virtual image, do your thing, and close it out.

---

### Post by jmate24 on 2010-01-04
then i guess i will go with virtualization, but i understand that it would take up a lot of space on my hdd.

i am wondering if i could fstab an external and use it to hold my virtual hdds?

---

### Post by bodhi.zazen on 2010-01-04
What I suggest :

Use Virtualization, Virtualbox is nice if you are new to Virtualization.

Run the live version of the distro you are interested in (hint you can boot the iso and run live).

If you like what you see, then go through the expense and hassle of burning the iso to disk and installing. I know CD are not *that* expensive, but with Virtualization you can certainly lower your environmental impact.

For those rare versions of Linux that do not run live, make a small (5 Gb) virtual hard drive you can use for testing and recycle it.

Personally I give my root partition 7-10 Gb for Linux and use a large /data partition which is shared across distros.

---

### Post by fesme on 2010-01-04
I Found this on tuxradar.com:

"Installing OpenSolaris

Just like most Linux distributions, OpenSolaris comes with a live CD and a graphical installer that asks you for the standard information, including your location, preferred keyboard map, time/date etc. This will be familiar for Linux users, and if you're installing OpenSolaris as the sole OS on a computer you'll hardly notice the difference, but if you want to create a dual-boot system with OpenSolaris and Linux you might run into problems at the disk-partitioning stage.

The OpenSolaris installer considers all logical partitions on the disk as one extended partition, so it can't be installed on a logical partition. If you choose to install OpenSolaris on this extended partition, all enclosed logical partitions get overwritten. Second, OpenSolaris uses ZFS instead of ext3 as its filesystem. Linux has no ZFS support in the kernel because the Free Software Foundation doesn't consider it free enough to be bundled with GPL software, so if you want to get access to your OpenSolaris documents in Linux you have to mount the ZFS filesystem with Fuse as a filesystem in userland.

A third issue is that the standard Grub version that comes with Linux distributions doesn't understand the ZFS filesystem. So when you install OpenSolaris first and then your favourite Linux distribution, you can't boot into OpenSolaris anymore. The solution is to first install Linux and then OpenSolaris, and add the section for your Linux distro to Grub's menu.lst in OpenSolaris."

Here is the link [http://tuxradar.com/content/opensolaris-vs-linux](http://tuxradar.com/content/opensolaris-vs-linux)
Hope it helps

---

### Post by jmate24 on 2010-01-05
thank you but that does not answer my previous question of:

i wonder if i could just fstab an external hdd so that it loads when i boot and use it to hold my virtualbox hdds?

---

### Post by bodhi.zazen on 2010-01-05
> **jmate24 said:**
> thank you but that does not answer my previous question of:

i wonder if i could just fstab an external hdd so that it loads when i boot and use it to hold my virtualbox hdds?

yes you can do this.

---

### Post by Zoot7 on 2010-01-05
Lets make that another vote for Virtualization. Test out a few distro in Virtualbox before you go installing them to the hard drive, you might decide you don't want them around after that and it's harder to remove them if you do install them to the hard drive.

---

### Post by jmate24 on 2010-01-05
not to mention that i just might loose all of my data in the process if i did not have backups.

plus i just ordered a Western Digital Caviar Green WD10EARS 1TB 5400 RPM 64MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive -Retail 

from newegg.com:

[HTML]http://www.newegg.com/Product/Product.aspx?Item=N82E16822136490[/HTML]

and i am going to use it as an external for my virtual hdds.

now isn't that hdd sweet or what?

---

### Post by egalvan on 2010-01-06
> **JC Cheloven said:**
> 
[INDENT]I can't remember exactly, but I think I've read something about using the same swap space for 64 and 32 bit OSes being problematic. I'd suggest you to do a search[/INDENT]


Swap is a *type* of filesystem.

Absolutely no difference in 32bit & 64bit swap.

Any and all *nix's can use the exact same swap partition...
just make it the largest size needed.
which *should* be twice your RAM.

And i run several Linux with one swap partition.
No worries, mate...

---

### Post by jmate24 on 2010-01-06
yes, but i believe that i am choosing to go with virtualization because i have ordered a 1TB hdd from newegg.com and it has a 64MB cashe so i should not be worried about running 2 or 3 oses at the same time on my laptop.

---

### Post by jmate24 on 2010-01-06
does anyone have any other suggestions or comments they would like to add before i mark this thread as [SOLVED]?

---

