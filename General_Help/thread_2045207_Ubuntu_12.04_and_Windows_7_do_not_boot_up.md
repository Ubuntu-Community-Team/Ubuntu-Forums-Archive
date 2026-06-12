---
title: "Ubuntu 12.04 and Windows 7 do not boot up"
date: 2012-08-20
forum: General Help
---

### Post by lakesidesoccer on 2012-08-20
Hey,

I was trying to change my splash screen in ubuntu 12.04. I downloaded and used the super-boot-manager.  But when I ran the program with a new splash screen I received a blank screen. So I ran the following script file, fixplymouth-precise script. And when it asked for the resolution I gave 1024x768-24. But my laptop is 1366x768 preferred resolution. In an attempt to change my resolution back to 1266x768 I open and editted the following file:
       /etc/default/grub
and changed the following:
GRUB_GFXMODE=1366x768x32
GRUB_GFXPAYLOAD_LINUX=1366x768x32
GRUB_CMDLINE_LINUX_DEFAULT="...1366x768x32.."

I do not remember the commands before and after the 1366x768x32 on the linux default line. 

When I restarted the computer I no longer see the menus to boot into. After waiting a couple of minutes I then realize that none of the OS where loading, because it usually only takes about 5 seconds to load. So I put my USB with ubuntu 12.04 in and loaded from it. And here I am. After running the boot repair, I am still unable to load either operating systems nor see the menus when the computer is first turned on.

Boot repair made the following link:
[http://paste.ubuntu.com/1158008/](http://paste.ubuntu.com/1158008/)

I am running a Dual Boot laptop with Ubuntu 12.04 64-bit and Windows 7 64-bit. and I can see the file system for the two from running ubuntu 12.04 off my USB. Any ideas on how to fix the issues?

---

### Post by oldfred on 2012-08-21
You have video settings where you should have text.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


Your grub.cfg looks like it still have some extra settings on the linux line.
Can you get grub menu when booting? If not by default hold shift key from BIOS until menu appears. Use e on your entry and edit the linux line to remove the extra video mode settings in the linux line.

```
linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=e982084b-7b0f-477c-8ca1-bfaaf0248869 ro   quiet splash nomodeset [COLOR=Red]video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap $vt_handoff[/COLOR] 
```

---

### Post by lakesidesoccer on 2012-08-21
I really appreciate your help, and I apologize for the late reply. 

After shutting down my computer and removing my USB with Live Ubuntu, then rebooting. I am unable to see any menus appear. I do see "Grub loading" while holding the shift key during BIOS, but it only last for a few seconds. Then I receive a blank lit black screen and it just stays there. Is there any other way to change the extra settings in grub?

---

### Post by oldfred on 2012-08-21
You may be able to edit grub.cfg which you never are supposed to do, but you may be the exception to prove the rule. The other choice is to chroot into your system and do the updates via a chroot or from inside you system but booted with the liveCD.

Edit out the incorrect entries at the end of the first boot stanza on the linux line:

mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

---

### Post by lakesidesoccer on 2012-08-22
When I type mount in the terminal all I see is the following from autocomplete:
/           /dev/sda6        /tmp

When I try to mount /dev/sda6, it informs me that only root can mount /dev/sda6 on swap.

Should I use sudo to mount /dev/sda6?

I can view the files of my ubuntu 12.04 and windows 7 under,
 /media/e982084b-7b0f-477c-8ca1-bfaaf0248869/                     ubuntu 12.04 
/media/9A3291A0329181C5/                                                             windows 7

---

### Post by oldfred on 2012-08-22
Is not sda6 swap, you cannot mount that.

You want sda5. And if mounted with /media/**uuid** then unmount that first.

---

### Post by YannBuntu on 2012-08-22
(@oldfred: I don't know what this "fixplymouth-precise script" is, but maybe it could be a good start point to purge and reinstall GRUB...)

---

### Post by lakesidesoccer on 2012-08-22
I unmounted the /media/**uuid** with the uuid corresponding to my ubuntu file system.
But I still do not see the option to mount /dev/sda5. Im a little confused about why I am not able to see/mount /dev/sda5.

---

### Post by lakesidesoccer on 2012-08-22
In case it is relevant here is the code used within the fixplymouth-precise script.

```
#!/bin/bash
# ----------------------------------
# Author: D0rkye
# Homepage: http://d0rkye.zsenialis.com/
# Most code probably by kyleabaker: http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/
#
# Fix for Ubuntu 11.04, for BURG, and some extra bloat by Paolo Bernardi (http://paolobernardi.wordpress.com/)
# ----------------------------------

# Usage: install_if_not_installed package_name
function install_if_not_installed
{
    PACKAGE="$1"
    INSTALLED=$(dpkg -L "$PACKAGE" > /dev/null 2>&1 && echo OK || echo KO)
    if [ "$INSTALLED" == "KO" ]
    then
        sudo apt-get install "$PACKAGE" -y
    fi
}

# Usage: contains regexp file
function contains
{
    REGEXP="$1"
    FILE="$2"

    grep "$REGEXP" "$FILE" > /dev/null && echo OK || echo KO
}

install_if_not_installed v86d
install_if_not_installed hwinfo

sudo hwinfo --framebuffer
echo "---------------------------------------------------------------"
echo "Please enter the best resolution from the list above"
echo "It usualy looks like this >>Mode 0x0323: 1024x768 (+4096), 24 bits<<"
echo "And you have to enter it like this >>1024x768-24<<"
echo "---------------------------------------------------------------"
read resolution

sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\ nomodeset\ video\=uvesafb\:mode\_option\='$resolution'\,mtrr\=3\,scroll\=ywrap\"/g' /etc/default/grub > ./newgrub
sudo cp -f ./newgrub /etc/default/grub
rm ./newgrub

sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\ nomodeset\ video\=uvesafb\:mode\_option\='$resolution'\,mtrr\=3\,scroll\=ywrap\"/g' /etc/default/burg > ./newburg
sudo cp -f ./newburg /etc/default/burg
rm ./newburg

sed 's/\#GRUB\_GFXMODE\=640x480/GRUB\_GFXMODE\='$resolution'/g' /etc/default/grub > ./newgrub
sudo cp -f ./newgrub /etc/default/grub
rm ./newgrub

if [ "$(contains uvesafb /etc/initramfs-tools/modules)" == 'KO' ]
then
    sudo echo "uvesafb mode_option=$resolution mtrr=3 scroll=ywrap" | sudo tee -a /etc/initramfs-tools/modules
fi

if [ "$(contains FRAMEBUFFER=y /etc/initramfs-tools/conf.d/splash)" == 'KO' ]
then
    echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
fi

#sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"\(.*\)vt\.handoff\=7\(.*\)\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"\1\2\"/g' /etc/grub.d/10_linux > ./new10linux
sed 's/vt\_handoff\=\(.*\)vt\.handoff\=7\(.*\)/vt\_handoff\=\1\2/g' /etc/grub.d/10_linux > ./new10linux
sudo cp -f ./new10linux /etc/grub.d/10_linux
rm ./new10linux
sudo chmod +x /etc/grub.d/10_linux

sudo update-grub2
which update-burg > /dev/null 2>&1 && sudo update-burg
sudo update-initramfs -u
echo "The resolution should be fixed after a reboot"
```

---

### Post by lakesidesoccer on 2012-08-23
I ran the diff command on the following file with that produced my  boot-repair:
/media/**uuid**/boot/grub/grub.cfg

The two files were identical. So i made a backup of the grub.cfg file and made the suggested corrections. But after rebooting I still just get a blank screen with no menus.
If I decide to reinstall ubuntu from my flash drive would that fix everything? Or would I need to reinstall both windows 7 and ubuntu 12.04?

---

### Post by oldfred on 2012-08-23
A total reinstall will reinstall grub so that should fix that issue, but of course their may be others.

You should just be able to uninstall & totally reinstall grub2. Boot-Repair has a helper on the chroot.

The manual procedure:

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by lakesidesoccer on 2012-08-23
I really appreciate your help oldfred.
 
I just have quick question, on the manual procedure to uninstall and reinstall grub2 I am unsure if i have WUBI or a Normal Installation of Ubuntu? I believe it is just a Normal installation but I would like to make sure before I proceed. Also is there any options within the advance tab of boot-repair I can use that will uninstall and reinstall grub2 using chroot?
 
Once I get home I will follow the instructions and proceed.
 
Thanks

---

### Post by oldfred on 2012-08-23
If you have wubi nothing so far would apply as it is just a file inside the NTFS partition and uses the Windows boot loader.

But your BootInfo report showed a full install in sda5 a Linux formated partition.

I believe Boot-Repair has some helper chroot functions under its advanced, but I have not used them. Best to know manual procedure then use Boot-Repair to make it a bit easier.

---

### Post by YannBuntu on 2012-08-23
> **lakesidesoccer said:**
> is there any options within the advance tab of boot-repair I can use that will uninstall and reinstall grub2 using chroot?

Yes, it's very simple: run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the "Purge GRUB before reinstalling it" option, then click the "Apply" button.
Boot-Repair will make adequate checks , ans will simplify the purge procedure so that you will only have to type 2 commands in a terminal (instead of >10 if you do the manual procedure).

[IMG]http://pix.toile-libre.org/upload/img/1335263271.png[/IMG]

If Ubuntu was installed via Wubi, the "GRUB options" tab will be greyed out.

---

### Post by lakesidesoccer on 2012-08-23
> **YannBuntu said:**
>  will simplify the purge procedure so that you will only have to type 2 commands in a terminal (instead of >10 if you do the manual procedure).


What are the two commands I will need to run in the  terminal?

Thanks

---

### Post by lakesidesoccer on 2012-08-23
These two commands? 

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install boot-repair-ubuntu

or just 

sudo apt-get update
boot-repair

---

### Post by YannBuntu on 2012-08-23
The commands will be displayed by Boot-Repair.

They can vary according to your mount points.

---

### Post by lakesidesoccer on 2012-08-23
Thank you oldfred and YannBuntu!

[QUOTE=YannBuntu]run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the "Purge GRUB before reinstalling it" option, then click the "Apply" button.
Boot-Repair will make adequate checks , ans will simplify the purge procedure so that you will only have to type 2 commands in a terminal (instead of >10 if you do the manual procedure).[/QUOTE]

This fixed the problem. I now see the "menus" when I boot up, and I am currently running off ubuntu from my computer. Is there anything else I will need to do to my my computer? Or is everything taken care of now?

If there is nothing else to do then I am ready to mark this thread as SOLVED.

Thanks again,
lakesidesoccer

---

### Post by lakesidesoccer on 2012-08-23
I have an extra windows loader in my grub menu, besides the windows recovery. One is located on /dev/sda1 and the other is on device /dev/sda2. But they both appear the same, I think, when I booted from each option. I'm confused because previously there was just a windows 7 loader and a windows recovery.

---

### Post by YannBuntu on 2012-08-23
This 2nd entry was added by Boot-Repair (that's a security: if one entry fails because of a bootsector problem, you can still use the other).

---

