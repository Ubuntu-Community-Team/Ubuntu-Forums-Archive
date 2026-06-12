---
title: "GRUB menu showing every boot up."
date: 2010-04-28
forum: General Help
---

### Post by nzso on 2010-04-28
I am working with a acer netbook that I originally had WinXP installed on. I downloaded Ubuntu 9.10, transferred the iso contents to a bootable USB drive and installed Ubuntu. I remember during the setup process that I made sure I chose the option to install on one partition. There is only one partition on my netbook with a small second partition as a swap.

After the installation process and reboot I noticed the grub menu would pop up every boot up giving the list of operating systems of which XP was included. I then ran the update manager and updated 9.10 with all updates. After rebooting the grub menu again showed but the option to choose XP was now gone.

Now everytime I boot up the grub menu shows. How can I modify grub so it will automatically just boot to the OS.

Thanks In Advance Guys... :)

---

### Post by Riddl on 2010-04-28
It is normal for GRUB to show up, after a few seconds it should load Ubuntu (automatically).

---

### Post by nzso on 2010-04-28
> **Riddl said:**
> It is normal for GRUB to show up, after a few seconds it should load Ubuntu (automatically).

I had 9.10 installed on this same exact netbook before and all you would see when booting up was "Grub Loading" in the top left hand corner for a split second and boot directly into Ubuntu. Now, on this second installation you see the "Grub Loading" in the top left hand corner then the grub menu pops up listing the different ways to boot with a countdown.

The menu when I had Ubuntu installed before would not even pop up unless I were to not properly shut down the computer.

---

### Post by bcbc on 2010-04-28
This guide should tell you what you need to know: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by towheedm on 2010-04-28
Open a terminal window by clicking **Applications => Accessories => Terminal.**

Open your [COLOR=Blue]/etc/default/grub[/COLOR] file for editing:
```
gksudo gedit /etc/default/grub
```Enter you password when prompted.  At the beginning of the file find this line:
```
#GRUB_HIDDEN_TIMEOUT=0
```Uncomment it by removed the hash (#) symbol.  Save the file and close gedit.  Now update grub with the following command:
```
sudo update-grub
```Reboot.

Hope this helps.

---

### Post by Leppie on 2010-04-28
Open the grub defaults file with a text editor
```
gksudo gedit /etc/default/grub
```and modify the following lines like this:
```
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
```save and exit the file and run update-grub:
```
sudo update-grub
```the menu should not appear anymore.

---

### Post by nzso on 2010-04-29
> **Leppie said:**
> Open the grub defaults file with a text editor
```
gksudo gedit /etc/default/grub
```and modify the following lines like this:
```
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
```save and exit the file and run update-grub:
```
sudo update-grub
```the menu should not appear anymore.

Thanks Leppie, worked like a charm.

---

### Post by Leppie on 2010-04-29
glad it's working as you want it now :)

---

