---
title: "Intel 5300AGN has no wlan0"
date: 2011-10-14
forum: General Help
---

### Post by TheDesertDragon on 2011-10-14
Hi Ubuntu community.

After upgrading to 11.10, I can no longer access Wireless. My PC does recognize the card because:

lspci | grep Network

returns:
0e:00.0 Network Controller: Intel Corporation Ultimate N WiFi Link 5300

However, wlan0 simply doesn't show up when typing either ifconfig or iwconfig. It's just not there! I can't use the setup command because it says the interface is unknown.

What happened? What can I do?

---

### Post by garvinrick4 on 2011-10-14
If it is a kernel driver like "iwlagn"
```
lspci -nnk | grep -iA2 net
```
Try a different kernel.

---

### Post by TheDesertDragon on 2011-10-14
> **garvinrick4 said:**
> If it is a kernel driver like "iwlagn"
```
lspci -nnk | grep -iA2 net
```
Try a different kernel.

It is, unfortunately.

However, I have no idea how to install alternative kernels.

In the meantime I'm working on it myself, and I found a file in /etc/modprobe.d called settings.conf with a line of code that disables the n band. Removing that, I can now see networks but not connect to them. I'm prompted for the password but literally instantly when the password window pops up it says I'm back offline.

---

### Post by garvinrick4 on 2011-10-14
> In the meantime I'm working on it myself, and I found a file in  /etc/modprobe.d called settings.conf with a line of code that disables  the n band. Removing that, I can now see networks but not connect to  them. I'm prompted for the password but literally instantly when the  password window pops up it says I'm back offline. [COLOR=Red]If you disable
the "N" with a config file then you have to make sure router in 2.4 ghz range is set to
mixed and not just "N". Or will just not connect, just sits there and acts like it is going to.[/COLOR]


Here is a link where I explained how to get another kernel. Is not that hard just download 3 packages and click on them and they download thru Ubuntu software center.
No one has reported if it is a kernel thing with "iwlagn" driver or not. It is a kernel driver and works for me with that kernel and others so up to you, no quarantees until reports come back,
but cannot hurt anything, easy to remove if not wanted anymore explained in thread also. Let me know if fixes "iwlagn" driver problem.
[http://ubuntuforums.org/showthread.php?t=1859234](http://ubuntuforums.org/showthread.php?t=1859234)

Anybody reading this if you had the N removed in kernel driver in 11.04 iwlagn you have a config file to be taken out N does work in 11.10 for me now.
                                 [COLOR=#000000][FONT=Times New Roman][SIZE=3]Discovered which workaround works for iwlagn driver intel: [/SIZE][/FONT][/COLOR] [COLOR=Red]For 11.04 and below only.[/COLOR]
 [COLOR=#000000][FONT=Times New Roman][SIZE=3]```
gksudo gedit  /etc/modprobe.d/iwlagn.conf
```[/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Times New Roman][SIZE=3]add this line below and save[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Times New Roman][SIZE=3]Prior to using that workaround my wireless would crash almost immediately when I attempted to do anything more than very low speed web browsing.[/SIZE][/FONT][/COLOR]
 

##Have to had set router to accept "G" and not just only "N" in router in 2.4 ghz range. (11:04 and below)

[COLOR=Red]Check to see if you still have set like this[/COLOR] can just put a # sign in front of options iwlagn 11_ line and save to uncomment that line. (will make it not in play with # in front of line)

##Notice below if you have above config file intact will not have N in this iwconfig command will just say 80211bg
rick@rick:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg[COLOR=Red]n[/COLOR]  ESSID:"Home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:C1:C0:C6:0A:EC   
          Bit Rate=72.2 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:61034  Invalid misc:864   Missed beacon:0

---

### Post by TheDesertDragon on 2011-10-14
> **garvinrick4 said:**
> If you disable
the "N" with a config file then you have to make sure router in 2.4 ghz range is set to
mixed and not just "N". Or will just not connect, just sits there and acts like it is going to.

It is now enabled, it was always in the 2.4GHz range but I just set it again for good measure.

Also, my router is an N router, but it is set to mixed.

It also doesn't sit there and act like it's going to connect. It just plain doesn't connect, period. Click icon -> Instant DC, every time. There are over 40 wireless networks here (dorm) and they all behave the same. Don't even get a chance to type the password before I'm offline, although the dialog appears.

---

### Post by garvinrick4 on 2011-10-14
```
rfkill list
```
is anything blocked?

---

### Post by TheDesertDragon on 2011-10-14
> **garvinrick4 said:**
> ```
rfkill list
```
is anything blocked?

Nope. This returns:

```
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

:(

Thanks for helping btw. It's always easy to forget to say thanks, but I will now. :) I was just outside for a bit - but I'm afraid I can't get to the bottom of this and need more help.

---

### Post by TheDesertDragon on 2011-10-14
BUMP.

I've been trying for the last many hours to install Linux 3.0.6 but the software center is completely and utterly broken.

In general, in fact, this OS seems incredibly broken. Canonical really needs to stop that 6-month release cycle... (You have to update to the newest version to get the latest updates to apps like Eclipse but it's just so much pain every time... Sorry for whining)

EDIT: Got it installed, but now it says I have to reinstall it. Trying to remove it tells me I have to reinstall it before it can proceed but I can't install it properly because the Software Center is so ******* broken it's not even funny. I am just about *this* close to Hackintoshing this machine instead, grr.

EDIT2: Great case in point right here. I open the .deb file again, software center opens. I click the reinstall button, it greys out and nothing happens.

GG

---

### Post by garvinrick4 on 2011-10-14
If any .deb file will not install through Ubuntu software center that you have downloaded.
Lets say you put file on Desktop:
```
cd Desktop
``````
ls
``````
sudo dpkg -i (copy and paste .deb package.)
```If file is in Downloads and want to do it from there just:
cd Downloads
ls
sudo dpkg -i (copy and paste .deb package)

## Just change directorys to the one the .deb file is in to install or drag and drop to location wanted
or download to location wanted. Can set where to download in edit/preferences/general of firefox.


#To reinstall package:
sudo apt-get install --reinstall (name of package)

#Can also reinstall in synaptic
sudo apt-get install synaptic

## I just install same kernel and could not reproduce your problem am using now.
rick@rick-test:~$ grep menuentry /boot/grub/grub.cfg
menuentry "Ubuntu, with Linux 3.0.6-030006-generic" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-12-generic" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-11-generic" --class ubuntu --class gnu-linux --class gnu --class os {

---

### Post by TheDesertDragon on 2011-10-14
> **garvinrick4 said:**
> If any .deb file will not install through Ubuntu software center that you have downloaded.
Lets say you put file on Desktop:
```
cd Desktop
``````
ls
``````
sudo dpkg -i (copy and paste .deb package.)
```If file is in Downloads and want to do it from there just:
cd Downloads
ls
sudo dpkg -i (copy and paste .deb package)

## Just change directorys to the one the .deb file is in to install or drag and drop to location wanted
or download to location wanted. Can set where to download in edit/preferences/general of firefox.


#To reinstall package:
sudo apt-get install --reinstall (name of package)

#Can also reinstall in synaptic
sudo apt-get install synaptic

## I just install same kernel and could not reproduce your problem am using now.
rick@rick-test:~$ grep menuentry /boot/grub/grub.cfg
menuentry "Ubuntu, with Linux 3.0.6-030006-generic" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-12-generic" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-11-generic" --class ubuntu --class gnu-linux --class gnu --class os {

dpkg was not present on my system.

The reinstall command didn't work. (Got the error that no suitable install sources were found)

I've reinstalled the system from scratch.

The wireless problem is still there.

:D

EDIT: Sorry I sound cynical. It's nothing to do with you. I'm just getting frustrated! :(

Btw, Mac OS X booted on top of an EFI emulator like it would on a real Mac. No problems at all... damn it's tempting, but I'll hold out a little longer! :P

---

