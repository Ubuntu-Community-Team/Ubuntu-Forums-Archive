---
title: "Laptop won't loggin anymore"
date: 2012-08-27
forum: General Help
---

### Post by jeannot_unbu on 2012-08-27
Old Toshiba laptop. Was working until recently but now when I switch it on it takes me to a screen with different version of Ubuntu (Generic and Generic recovery mode). Form version 2.6.35-22 to 2.6.38-14. No matter what version I use, once I select it nothing happens. Any idea on what I should do thanks. Bear in mind that I am a complete noob, thanks
JC

---

### Post by kimberlite on 2012-08-27
Get an Ubuntu live CD - an older version say 10.04 maybe more appropriate - and try to boot from the CD. If it works you may want to backup your data and reinstall your system.

---

### Post by jeannot_unbu on 2012-08-27
> **kimberlite said:**
> Get an Ubuntu live CD - an older version say 10.04 maybe more appropriate - and try to boot from the CD. If it works you may want to backup your data and reinstall your system.
Thanks for the reply, where can I find a reliable download for the 10.4, if I go to the official website, all i get is 12.04. I have got any data to save on this laptop as I use it only for surfing the net. So once i get the cd, do i just boot from the cd and re-install on the top of the existing version?
Thanks
JC

---

### Post by spiky001 on 2012-08-27
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by jeannot_unbu on 2012-08-27
> **spiky001 said:**
> [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
Thanks
JC

---

### Post by black veils on 2012-08-27
if you don't have any data to save (not even website bookmarks?) then yes choose the install option, and follow the wizard, choose use entire disk to install over whole hard drive

---

### Post by jeannot_unbu on 2012-08-27
> **black veils said:**
> if you don't have any data to save (not even website bookmarks?) then yes choose the install option, and follow the wizard, choose use entire disk to install over whole hard drive
For some reason it is not booting from the CD, I have change the boot sequence in setup, but it keeps taking me to that same screen with all the different Ubuntu versions. Could it be that my laptop is knackered?
JC

---

### Post by black veils on 2012-08-27
if I were you, I would try installing, don't update until having locked the kernel version. and then in software sources, on updates tab, choose only to allow important security updates. 

as for your disc not working, try burning the image at slowest speed.  [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by jeannot_unbu on 2012-08-27
> **black veils said:**
> if I were you, I would try installing, don't update until having locked the kernel version. and then in software sources, on updates tab, choose only to allow important security updates. 

as for your disc not working, try burning the image at slowest speed.  [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
I think that my HD is not behaving the way it should. I have managed to get to a maintenance shell, I have now a line saying: root@myname: ~#

What should I type from there?
Thanks
JC

---

### Post by kimberlite on 2012-08-27
> **jeannot_unbu said:**
> For some reason it is not booting from the CD, I have change the boot sequence in setup, but it keeps taking me to that same screen with all the different Ubuntu versions. Could it be that my laptop is knackered?
JC

Did you get a message "press any key to boot from the CD"? If yes, and miss to hit, than it goes to GRUB screen where you can select boot options. If you have another machine try your CD there to see if it is working (bootable) or not...

---

### Post by jeannot_unbu on 2012-08-27
> **kimberlite said:**
> Did you get a message "press any key to boot from the CD"? If yes, and miss to hit, than it goes to GRUB screen where you can select boot options. If you have another machine try your CD there to see if it is working (bootable) or not...
No I selected one of the option that was coming on the start screen (see above), the laptop ran some script and then came with that line.
JC

---

### Post by spiky001 on 2012-08-27
Hi when you had the options on the cd did you select try ubuntu  As you are now what happens if you enter startx?

---

### Post by jeannot_unbu on 2012-08-27
> **spiky001 said:**
> Hi when you had the options on the cd did you select try ubuntu  As you are now what happens if you enter startx?


OK I have managed to logon on my account but I have not got any visual interface. How do i bring the visual interface now, or maybe it is not possible from where I am right now

JC

---

### Post by spiky001 on 2012-08-27
I pressume you are at  root@myname: ~# Try startx, I dont know why you havn't got a desktop tho?

---

### Post by spiky001 on 2012-08-27
Hi   Just by a chance did you download/install a server edition and not a desktop??

---

### Post by jeannot_unbu on 2012-08-27
> **spiky001 said:**
> I pressume you are at  root@myname: ~# Try startx, I dont know why you havn't got a desktop tho?

When I type startx i get:
user not authorized to run the X server, aborting

So I guess i am not at the root level

JC

EDIT: Managed to get to Root
Some script is running and then after a few seconds i get
xinit: giving up
xinit: unable to connect to X server: Network is unreachable
xinit: server error
xauth: error in locking authority file /root/.Xauthority

and then take me back to root

---

### Post by jeannot_unbu on 2012-08-27
This is from the existing version i had on the laptop not from the cd btw

JC

---

### Post by spiky001 on 2012-08-27
Ok   A recap I take it you want to retrieve some info off of laptop? Or do you want to reinstall?

---

### Post by jeannot_unbu on 2012-08-27
> **spiky001 said:**
> Ok   A recap I take it you want to retrieve some info off of laptop? Or do you want to reinstall?
Thanks for the help spiky btw. No I just want the laptop to run normally as it was before.
Thanks
#JC

---

### Post by spiky001 on 2012-08-27
Ok so why not just reinstall from the cd? If you are going to that why not get the 12.04 version?

---

### Post by jeannot_unbu on 2012-08-27
> **spiky001 said:**
> Ok so why not just reinstall from the cd? If you are going to that why not get the 12.04 version?
Well someone else mentioned to install 10.04 previously that's why. I have managed to find my old cd with ubuntu, it is now reading it from the cd so i guess the other cd i did this morning was faulty. I am going to see if i can do a clean re-install. I will let you know
JC

---

### Post by jeannot_unbu on 2012-08-27
Well I am installing Ubuntu, I keep getting the following error message:

The following file did not match its source copy on the CD/DVD:

This is oftne due to a faulty CD/DVD disk or drive, or a faulty hard disk blah blah blah
To check whether the HD is old and in need of replacemnt, or to move the system to a cooler environment

This laptop is quite old so i guess maybe it is time to get a new one

JC

---

### Post by jeannot_unbu on 2012-09-03
Received my HD this morning, installed it and managed to setup Ubuntu 10.04. Worked perfectly but then got a message telling me to update to 11.04 as 10.04 is not supported anymore. Went through the upgrade and now I am getting stucked at the Ubuntu logo with the 5 dots underneath, nothing happens. I have done a couple of hard reboot but still the same. I am getting annoyed now with Ubuntu, maybe I should use another distro.
Any idea?
Thanks
JC

---

### Post by black veils on 2012-09-03
try **xubuntu 12.04** or **linux mint 13 xfce**. what is your ram?

---

### Post by jeannot_unbu on 2012-09-03
> **black veils said:**
> try **xubuntu 12.04** or **linux mint 13 xfce**. what is your ram?
Can't remember, it is just on old laptop that i use for internet only or watching dvds when i am away
JC

EDIT: 2GB

---

### Post by jeannot_unbu on 2012-09-03
I am now trying to boot from the initial CD I used to install 10.04 (change the bios sequence to boot from cd), i can hear the cd spinning, get that very first screen and then again goes to the ubuntu logo, with the dots highlighting in sequence, cd churning away, and then the 5 dots are red under the logo and nothing else happens. How can I re-install 10.04, and wipe 11.04 out from the HD? Thanks
JC

---

### Post by black veils on 2012-09-03
you just install using the wizard, and when given the option of how to install, choose to erase and use entire disk, provided you dont have any other operating system on the drive that you want to keep.

but you should probably think about installing the latest ubuntu. you could install via the mini.iso, and choose whichever desktop you want from there, as you have the ram. [http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main](http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main)

EDIT:  oh sorry i was dopey and didnt realise you had issues with the live disc. i think it would be a good idea to make a new disc, maybe it got a scratch or something. the mini.iso is very small

---

### Post by jeannot_unbu on 2012-09-03
> **black veils said:**
> you just install using the wizard, and when given the option of how to install, choose to erase and use entire disk, provided you dont have any other operating system on the drive that you want to keep.

but you should probably think about installing the latest ubuntu. you could install via the mini.iso, and choose whichever desktop you want from there, as you have the ram. [http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main](http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main)

EDIT:  oh sorry i was dopey and didnt realise you had issues with the live disc. i think it would be a good idea to make a new disc, maybe it got a scratch or something. the mini.iso is very small
Worked perfectly this morning (well chuffed I was and everything was working, even my wireless connection, which was a problem before HD problems). I am wiping off the HD right now using Darik's boot and Nuke and will try re-installing 10.04 as *I did this morning*, I am not bothered about having the last version, I just want something that works ok
Where do you get the mini-iso anyway, just in case. Thanks
JC

---

### Post by black veils on 2012-09-03
mini [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

if it were me, I would lock the kernel version after install, using synaptic. and only allow important security updates, using update manager settings. 

the reason I said about newest version is because 10.04 end of life (end of security support) is April 2013, and since you are already installing, it made sense.

---

### Post by jeannot_unbu on 2012-09-03
> **black veils said:**
> mini [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

if it were me, I would lock the kernel version after install, using synaptic. and only allow important security updates, using update manager settings. 

the reason I said about newest version is because 10.04 end of life (end of security support) is April 2013, and since you are already installing, it made sense.

OK you lost me there with locking the kernel version after install...
I am not that conversant with Linux, only really use it so I don't have to use Windows. What I may do is buy a magazine with a CD and a working copy of a distro, thanks
JC

---

