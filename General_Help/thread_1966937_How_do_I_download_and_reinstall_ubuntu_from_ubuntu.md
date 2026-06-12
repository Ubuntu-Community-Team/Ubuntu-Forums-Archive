---
title: "How do I download and reinstall ubuntu from ubuntu?"
date: 2012-04-27
forum: General Help
---

### Post by colobix on 2012-04-27
Hey. I'm pretty sure this is possible.
I once saw an icon in the start menu saying "install release" or something like that.
Here's the thing. The source list and stuff is pretty messed up after the upgrade. So is it possible to do a fresh install using the terminal or whatever?
I don't have any blank CDs laying around.

---

### Post by collisionystm on 2012-04-27
> **colobix said:**
> Hey. I'm pretty sure this is possible.
I once saw an icon in the start menu saying "install release" or something like that.
Here's the thing. The source list and stuff is pretty messed up after the upgrade. So is it possible to do a fresh install using the terminal or whatever?
I don't have any blank CDs laying around.

Do you have any usb drives?

---

### Post by dFlyer on 2012-04-27
See this link it explains how to install from a partition. 

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by colobix on 2012-04-27
> **collisionystm said:**
> Do you have any usb drives?
Can't boot from usb. I have one of these older bios'

---

### Post by confused57 on 2012-04-27
You might be able to use Plop boot manager to boot from usb:
[http://www.plop.at/en/bootmanager/plpbt.bin.html](http://www.plop.at/en/bootmanager/plpbt.bin.html)

If your current version uses grub2:
[http://ubuntuforums.org/showpost.php?p=11678754&postcount=10](http://ubuntuforums.org/showpost.php?p=11678754&postcount=10)

---

### Post by josephmills on 2012-04-27
1) open terminal 

2)run 
```
sudo do-release-upgrade -d
```

3) go get your fav drink and start drinking it 

My 
sources.list

12.04 


```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha amd64 (20111222)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha amd64 (20111222)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
# deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse universe

```

---

### Post by mode7 on 2012-04-27
I'm pretty sure the latest images will still fit onto CD-Rs. 
If you happen to have Windows installed as well, you can also try Wubi as a temporary fix if you are unwilling to pursue the more difficult install routes. I'd only recommend that as a temporary setup until you can install Ubuntu on a dedicated partition.

---

### Post by colobix on 2012-04-27
> **josephmills said:**
> 1) open terminal 

2)run 
```
sudo do-release-upgrade -d
```


It says "no new release"
Might be because I already have 12.04.
Any other solutions?

> **rockinfreeworld said:**
> Or you can install VMware in Windows and then install Ubuntu 12.04 virtually in VMware.
Why would I do that?
Also, I don't have windows.

---

### Post by josephmills on 2012-04-27
> **colobix said:**
> It says "no new release"
Part 1 :Might be because I already have 12.04.
Any other solutions?


Part 2 :Why would I do that?
Also, I don't have windows.

**part1**
try this 
change all the precise back to oneiric   in the sources list
```
sudo sed -i 's|precise|oneiric|g' /etc/apt/sources.list && sudo apt-get update && sudo apt-get -f install && sudo do-release-upgrade -d
```

then go grab that beverage. But we will see as dependency's are well just that. but it is worth a shot at this point.

**Part2**
Neither do I :)

---

### Post by colobix on 2012-04-27
> **josephmills said:**
> **part1**
try this 
change all the precise back to oneiric   in the sources list
```
sudo sed -i 's|precise|oneiric|g' /etc/apt/sources.list && sudo apt-get update && sudo apt-get -f install && sudo do-release-upgrade -d
```

then go grab that beverage. But we will see as dependency's are well just that. but it is worth a shot at this point.

**Part2**
Neither do I :)

Thanks. But it still says "no new release found".
It did fetch all the packages successfully though.

So is there no command that will download the installation, install it and wipe out all existing data so it'll all be clean and new?

---

### Post by colobix on 2012-04-27
> **rockinfreeworld said:**
> Maybe some blank dvdrs like they originally mentioned would be the best thing for themselves to do.  Without blanks, they are kinda out of luck.
You guys really like those CDs, huh?:)
I would love not to do that as I normally never burn CDs.
It's just that this would be more officiant, you know.
I do have a USB stick though. But I have an old bios, and I don't know how to upgrade it.
Although, installing fresh release was possible in earlier releases. I have seen an icon once saying Release Installation or something like that.

---

### Post by josephmills on 2012-04-27
> **colobix said:**
> Thanks. But it still says "no new release found".
It did fetch all the packages successfully though.

So is there no command that will download the installation, install it and wipe out all existing data so it'll all be clean and new?
[s]
Besides things like bleachbit and things like [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

there is also ftp and rysnc images there is also net images. 
[/s]

              And then I ran Across this \o/ 
:KS:KSThanks gosh for cjwatson and the motu crew:KS:KS
[http://bazaar.launchpad.net/~ubuntu-cdimage/debian-cd/ubuntu/files](http://bazaar.launchpad.net/~ubuntu-cdimage/debian-cd/ubuntu/files)*
also*
[http://people.canonical.com/~cjwatson/bzr/cdimage/mainline/](http://people.canonical.com/~cjwatson/bzr/cdimage/mainline/)
[https://launchpad.net/ubuntu-cdimage](https://launchpad.net/ubuntu-cdimage)

---

### Post by josephmills on 2012-04-27
You Have a usb @_@ that is a whole different story. a big on but a different one why dont you click on the link under all this in my Signature and we can talk live 
joseph

---

### Post by josephmills on 2012-04-27
> **colobix said:**
> DOn't you think I would if I could?
As I've said again and again, I can't boot into USB.
Someone posted a link on how to do it from the grub, but that was too advanced and I don't wanna mess around with things that are too advanced.
I was hoping this could be done easy and fast.

What is your computers motherboard? You can not boot from usb because of bios ? We can work around that. what is the size of the usb ? also if you do not know your motherboard what is the type of computer model also. Thanks 
Joseph

---

### Post by colobix on 2012-04-27
<snip>


> **josephmills said:**
> What is your computers motherboard? You can not boot from usb because of bios ? We can work around that. what is the size of the usb ? also if you do not know your motherboard what is the type of computer model also. Thanks 
Joseph

I have no idea what a motherboard is. The pc is an Acer desktop 64bip.
I Have enough space on the USB sticks. The ones I have are 8gb, 16gb and a 32gb.

---

### Post by confused57 on 2012-04-27
```
wget http://releases.ubuntu.com/precise/ubuntu-12.04-desktop-i386.iso
```

This "should" enable you to download the iso image, then follow the 2nd link I gave you earlier to boot as a live image, then install.

---

### Post by colobix on 2012-04-27
> **confused57 said:**
> ```
wget http://releases.ubuntu.com/precise/ubuntu-12.04-desktop-i386.iso
```

This "should" enable you to download the iso image, then follow the 2nd link I gave you earlier to boot as a live image, then install.

Thanks, but could you guide me step by step.
All this partition and such makes me nerves.
Okay so I download the iso and use unetbootin to put it on a USB.
Now what?

---

### Post by confused57 on 2012-04-28
> **colobix said:**
> Thanks, but could you guide me step by step.
All this partition and such makes me nerves.
Okay so I download the iso and use unetbootin to put it on a USB.
Now what?

Sorry I wasn't able to reply earlier, needed to spend time with the wife.
It's been some time since I've attempted to help on the forum, so if someone
else wants, feel free to chime in.

Am I correct to assume that you've already downloaded the precise iso and installed to usb with unetbootin and you're wanting to try booting with plop
boot manager?

If so, download the plop boot manager zip file from the terminal or console in your broken install:
```
wget http://download.plop.at/files/bootmngr/plpbt-5.0.14.zip
```
then run "ls" to see if the zip file downloaded to your home folder.
If so:
```
unzip plpbt-5.0.14.zip
cd plpbt-5.0.14
```

Copy the bin file to /boot:
```
sudo cp plpbt.bin /boot
```

Then add the entry to grub.cfg to boot the bin file:
```
sudo nano /boot/grub/grub.cfg
```

Add this entry to the very bottom of the file:
```
menuentry "Plop Boot Manager" {
    set root=(hd0,1)
    linux16 /boot/plpbt.bin
}
```
Ctrl+x, then y to save.

The above entry "should" work, if your root partition is sda1.  If you're unsure run "sudo fdisk -l" to see for sure.

If everything worked correctly, there should be an entry at the bottom of your grub menu which will boot the Plop Boot Manager.  None of the above instructions should harm your install, again anyone is welcome to chime in if I'm wrong about this.

Adding plop bm to your grub.cfg will work as long as you don't run update-grub.  It can always be added permanently with:
```
sudo gedit /etc/40_custom
```

---

### Post by mobisallen on 2012-04-28
u really must follow all the instructions guided to u

---

### Post by colobix on 2012-04-28
Okay. I have successfully added it to the grub menu.
Now when I click it, it says "file not found" and then restarts grub.
So I guess it doesn't want to boot the USB.
What now?

---

### Post by confused57 on 2012-04-28
> **colobix said:**
> Okay. I have successfully added it to the grub menu.
Now when I click it, it says "file not found" and then restarts grub.
So I guess it doesn't want to boot the USB.
What now?

From a terminal or console:
```
mount
```
Check which partition is mounted as / (or do you have a separate /boot partition) , is it /dev/sda1?

Then see if the plpbt.bin is in your /boot folder:
```
cd /boot
ls
```

---

### Post by colobix on 2012-04-28
The ext4 partition ( / ) is sda6.
Okay so do I need to change the sda1 to sda6 somewhere?
And yes it's in the /boot directory.

---

### Post by confused57 on 2012-04-28
> **colobix said:**
> The ext4 partition ( / ) is sda6.
Okay so do I need to change the sda1 to sda6 somewhere?
And yes it's in the /boot directory.

Yes, you need to change the root entry:

```
sudo nano /boot/grub/grub.cfg
```

then change the root from (hd0,1) to (hd0,[COLOR="Red"]6[/COLOR]):
```
menuentry "Plop Boot Manager" {
    set root=(hd0,[COLOR="Red"]6[/COLOR])
    linux16 /boot/plpbt.bin
}
```

I have to go out for a little while, but maybe someone else can help you if this doesn't work.

---

### Post by colobix on 2012-04-28
It totally worked. Thanks a lot, man. You rock!
This wasn't so hard actually.
I wish they'd use this boot manager instead of grub, if that's possible. It looks cooler too:)

---

### Post by confused57 on 2012-04-28
Great, glad to have helped and that it actually worked.  I've used
Plop bm before, but I've since sold the computer I needed to use it with...
it does have a nice boot menu interface.

---

