---
title: "going to install debian over ubuntu"
date: 2009-12-31
forum: General Help
---

### Post by mamamia88 on 2009-12-31
does anyone have any advice?  i'm downloading the net install cd now.  i figured since i am accustomed to ubuntu i would give debian a shot.

---

### Post by k64 on 2009-12-31
> **mamamia88 said:**
> does anyone have any advice?  i'm downloading the net install cd now.  i figured since i am accustomed to ubuntu i would give debian a shot.

Debian is the distro Ubuntu is based on, so I don't see why not. My advice: Try setting up a Debian/Ubuntu dual-boot. Put Debian on one partition and Ubuntu on the other. That way, you can boot into both operating systems without having to install one or the other.

-Kenny Strawn

---

### Post by ssam on 2009-12-31
ubuntu installs some nice bits and pieces by default (iirc things like bash-completion and command-not-found), so you might want to install those into debian once you are running. you can see whats in the ubuntu metapackages at [http://packages.ubuntu.com/search?keywords=ubuntu&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=ubuntu&searchon=names&suite=karmic&section=all)
have a look at ubuntu-desktop ubuntu-standard and ubuntu-minimal.

---

### Post by Swagman on 2009-12-31
I hope your good at googling and DONT use an ati card !!

"Your'll be back"!!

---

### Post by m0o on 2009-12-31
If you set a separate partition for /home, it would make doing things like this easier. Your personal files and configurations get transfered over easier.

---

### Post by lykwydchykyn on 2009-12-31
When it comes to installing, use aptitude instead of apt-get in Debian.  It's the official PM front-end in Debian.  Of course, synaptic is also available.

Also, the "desktop" selection during install will install GNOME, so if that's not what you want, don't install that.

---

### Post by mamamia88 on 2009-12-31
nope nvidia card and i already have one computer running ubuntu so i figured whats the point in having 2 and might as well try it. worst case scenario is i format and install something else on

---

### Post by hadi2 on 2009-12-31
if you are going to use debian on a laptop you have to compile a new kernel 
for it . 
my experience on my dell studio xps 1340 :

kernel :         2.6.26          2.6.32

battery
lifetime :        1 hour         3 hours  

on idle .

---

### Post by danastasio on 2009-12-31
eh, i didn't really care for debian actually. Just make sure you read their wiki and the forum and you'll be fine.

---

### Post by mamamia88 on 2009-12-31
so does debian actually give you a list of packages to install or just  a bunch of categories and installs all packages under those categories?  i just selected desktop environment and laptop now its gonna take 2 hours to download 810 files yay should have just got a dvd install disc

---

### Post by AlexDudko on 2009-12-31
> **Swagman said:**
> I hope your good at googling and DONT use an ati card !!

"Your'll be back"!!

I didn't have any problem with any video cards ati in particular with any Debian release starting from "woody". But I can't say the same about Ubuntu. There were several of them that I couldn't boot to install.

---

### Post by lykwydchykyn on 2009-12-31
> **mamamia88 said:**
> so does debian actually give you a list of packages to install or just  a bunch of categories and installs all packages under those categories?  i just selected desktop environment and laptop now its gonna take 2 hours to download 810 files yay should have just got a dvd install disc

The installer runs tasksel, which is also present in Ubuntu (and used in the alternate installer).  Tasksel is basically a tool for installing metapackages.   I've never found much use in Debian's tasksel selections, I just unselect everything but "standard system" and fire up aptitude after the reboot.

---

### Post by Hallvor on 2009-12-31
> **mamamia88 said:**
> does anyone have any advice?  i'm downloading the net install cd now.  i figured since i am accustomed to ubuntu i would give debian a shot.

It is not as hard as its reputation. 

After installation, enable non free and contrib in /etc/apt/sources.list (Log in as root in the terminal and type gedit /etc/apt/sources.list and add contrib and non-free)

For codecs, etc, add the repository on this page and follow the instructions: [http://debian-multimedia.org/](http://debian-multimedia.org/)

Update your system with aptitude update && aptitude safe-upgrade

Then install win32codecs (assuming you use the 32 bit version) and libdvdcss2 to play mp3s, videos and dvds.

If you want to you can install synaptic with aptitude install synaptic

That is pretty much it. :)

---

### Post by Pogeymanz on 2009-12-31
Yeah, it really shouldn't be too difficult. You'll be fine. Ubuntu just installs a lot of stuff for you.

---

### Post by pirog on 2010-01-16
a quick question guys: if i install debian over ubuntu, with a separate /home partition, can i then migrate files from ubuntu to debian /home? i.e. all my photos, music and config files. Does that also mean that if i move all the stuff from /home_ubuntu to /home_debian I won't be able to access them from ubuntu?

thanks :)

---

### Post by nothingspecial on 2010-01-16
> **pirog said:**
> a quick question guys: if i install debian over ubuntu, with a separate /home partition, can i then migrate files from ubuntu to debian /home? i.e. all my photos, music and config files. Does that also mean that if i move all the stuff from /home_ubuntu to /home_debian I won't be able to access them from ubuntu?

thanks :)

You are misunderstanding I think.

If you have a seperate home partition then Debians home and Ubuntu`s home will be the same place. You won`t need to access or migrate files.

---

### Post by pirog on 2010-01-16
> **nothingspecial said:**
> You are misunderstanding I think.

If you have a seperate home partition then Debians home and Ubuntu`s home will be the same place. You won`t need to access or migrate files.

Thanks for reply nothingspecial. i did not realise that would be the case. so, when installing debian and asking to put /home into a separate partition it will create a separate partition using /home from ubuntu. i am surprised that happens just like that - easy! thanks mate!

gonna move tonight :)

---

### Post by nothingspecial on 2010-01-16
No.

Create the home partition first using a terminal, booting from the Ubuntu (or Debian) live cd.

Follow these [[COLOR="Magenta"]instructions[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

Then create another, roughly 6-8 gig partition.

When you install Debian, make sure you know which partition is which.

Install Debian on the new empty partition, tell it to mount your home partition as /home

and dont touch the Ubuntu partition

You will already have a swap space so dont worry about that.

---

### Post by pirog on 2010-01-16
I tried to follow instructions from psychocats some time ago. I tried to move my /home into separate partition. unfortunatelly after doing that I could not log into my account (i think it was to do with access rights). I think the easiest thing would be to backup all files, and then play with your solution. If all fails i'll do a fresh install of debian.
It would be a good thing if developers could automate this process, so that people like me wouldn't have to do fresh installs ;)

thank again dude! i'll keep you posted.

---

### Post by pirog on 2010-01-21
right, time to report my results. i used my laptop to test installation over (k)ubuntu9.10. I installed Mint 8, Ubuntu 9.04 and finally Debian.
Had no trouble installing all of them. I found that my grub.menu (which is installed in its own partition) was not altered when I clicked "Advanced" button at the end of each installation and un-ticked "Install Grub into MBR" (or something like that). Then I could add each OS manually to my old grub menu.
In case of Debian I pointed installation of GRUB into my boot partition. It did not do anything really.

Everything worked until I updated Mint. It decided to update my grub and then upon restarting my system, it was Mint's boot menu (with pictures and colours - GRUB2 ?). After I played with OSes it was time to remove them. So I just wiped every partition, except for Kubuntu9.10.
After i've done that, there was no grub menu, nothing could boot. Used LiveCD to install GRUB into its partition again. Worked fine.

NOTE: I used a separate /home partition and pointed every OS to its location. Make sure to un-tick "Format?" option. The only problem with this is that my kubuntu desktop settings interfered with Mint, and vice-versa. Everything was messed up. NVidia drivers had to be installed for each OS. Debian Gnome configuration was also messed up - could not use anything after logging in.

Moral: use one OS! don't point all the OSes to one /home partition. Backup data and have a LiveCD at hand.

---

### Post by OrangeCrate on 2010-01-21
> **mamamia88 said:**
> **does anyone have any advice? ** i'm downloading the net install cd now.  i figured since i am accustomed to ubuntu i would give debian a shot.

The first time I installed Debian, this tutorial was very informative and helpful. It's worth a bookmark for future reference...

[http://www.howtoforge.com/the-perfect-desktop-debian-lenny](http://www.howtoforge.com/the-perfect-desktop-debian-lenny)

---

### Post by khelben1979 on 2010-01-21
> **Swagman said:**
> I hope your good at googling and DONT use an ati card !!

"Your'll be back"!!

I could use an ATi Radeon 9800 XT successfully with Debian several years ago. I was able to run Unreal Tournament 2003 and Quake 2 in native mode with 3D graphics acceleration, successfully. Seriously, I don't understand why Debian should be worse now.

You have right in some sense though, nVidia is much easier to get working and would be to recommend to newbies.

---

### Post by pirog on 2010-01-22
One more thing. I have been playing around with various OS - installing them side by side of each other and such. I think the best way to avoid using same /home (and hence same config settings, which create a mess) is basically use the whole new separate partition for your data/files, like music, videos, photos, etc.

nice addition to fstab proposed by LinuxRules1 [http://ubuntuforums.org/showpost.php?p=8600911&postcount=5]("http://ubuntuforums.org/showpost.php?p=8600911&postcount=5")

Still, be careful with GRUB installation (although you can always re-install it using LiveCD). Also, I found that Debian won't mount /dev/sda3 (that's my ext3 data-partition) using the above fstab addition.

So, I am going to install 10.04 next to my "rock solid" 9.04 and then I am going to test it for the bugs.

Good luck to those who'd like to install Debian over Ubuntu.
Cheerio.

---

### Post by Hallvor on 2010-01-23
> **OrangeCrate said:**
> The first time I installed Debian, this tutorial was very informative and helpful. It's worth a bookmark for future reference...

[http://www.howtoforge.com/the-perfect-desktop-debian-lenny](http://www.howtoforge.com/the-perfect-desktop-debian-lenny)

That one is very helpful for beginners. Thank you!

---

### Post by OrangeCrate on 2010-01-23
> **Hallvor said:**
> That one is very helpful for beginners. Thank you!

Your welcome. Here's another link you might find useful:

[http://www.debian.org/doc/FAQ/](http://www.debian.org/doc/FAQ/)

---

