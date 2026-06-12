---
title: "Asus Eee Pc Multi-touch"
date: 2010-10-12
forum: General Help
---

### Post by cfree220 on 2010-10-12
Greetings Wizards,

I recently offed my Windows 7 install on my Eee PC (1005HAB) and replaced it with Ubuntu Netbook Remix (10.10).

I quickly decided that the Unity desktop was not my cup of tea, so I've set the default session to Ubuntu Desktop Edition.

Supposedly 10.10 supports multi-touch for my synaptic touchpad, but I haven't been able to get this to work. I can see in Preferences>>Mouse that there is the option for "two-finger" scrolling, but it is grayed out.

I've done some Googling, and determined that the touchpad enhancements for Eee PC can be accomplished using the elantech driver (at least, this was the solution for the previous version).

When I followed the instructions [here]("http://array.org/ubuntu/elantech.html") my computer would not boot.

I determined that it was a problem with xorg.conf. This file was empty before I added the line specified in the elantech instructions. After some more Googling, it was my impression that this should not be the case (ie that it should not be able to boot with an empty xorg.conf).

Even further Googling suggested that newer releases no longer store configuration information in xorg.conf. If this is the case, what files do I need to modify, and in what way, to be able to use the touchpad enhancements on my netbook? Alternatively, is there a way for me to configure the operating system to use a Windows driver?

I'm pretty heavily dependent on my ability to close browser tabs with a two-fingered click.

Your help is much appreciated!!

--cfreeman

---

### Post by terwilligerjones on 2010-10-12
I'm in the same boat. 10.04 multi-touch worked fine on my Asus 1005. Meercat... not so much. Or at all. I'd appreciate any help

---

### Post by terwilligerjones on 2010-10-12
Oh, to be a little more precise, Two-fingered scrolling is greyed out. I haven't tried changing  the driver. Didn't like that part about "my computer wouldn't boot".

stew

---

### Post by lores on 2010-10-13
Same scenario here - I went for 10.10 Desktop Edition with my Asus EeePC 1005P and have the two-finger option greyed out. This is the same behaviour I used to have in 10.04.
Has anyone managed to use multitouch out of the box (i. e. without further modifications)?
I will try to boot the netbook remix and have a glance at its multitouch support, but I don't suppose the edition itself could have any impact - unless there are some packages missing in the desktop edition.

---

### Post by jgans on 2010-10-13
I don't know why it is still greyed out. But running this script will give you the two finger scrolling, I found it somewhere. Have it autostart.

#!/bin/sh
#
# Use xinput --list-props "SynPS/2 Synaptics TouchPad" to extract data
#
sleep 10

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110

---

### Post by lores on 2010-10-13
Thank you. This script can be substituted with synclient, e. g. (the following is my preference)```
synclient TapButton1=1 TapButton2=2 TapButton3=3 VertTwoFingerScroll=1 HorizTwoFingerScroll=1 EmulateTwoFingerMinZ=10 EmulateTwoFingerMinW=6
```Although this is "just an emulation", it works quite well for scrolling and tapping with two fingers. However, the problem is that these settings (regardless whether they had been achieved through xinput or synclient) get overwritten, notably when connecting an external mouse; there probably are other triggers, too. Also, it still would be nice to have an option of graphically enabling it; gpointing-device-settings has a nice GUI with adequate checkboxes, but they don't work.


If I remember well, Ubuntu 10.10 was said to introduce "real" (native?) support for multitouch, which would allow for more advanced features, such as zooming and 3-finger-gestures (e. g. back/forth). Does anyone know how/where/whether this has been implemented? Has anyone had success with enabling two-finger scroll through the built-in GUI?


EDIT:
Further two triggers disabling (some of) the customised synclient settings are standby/resume and changing to another tty. /etc/pm/sleep.d won't work, as there is no connexion to X.

---

### Post by cfree220 on 2010-10-14
Thank you guys for getting back to me on this!

I do have some questions regarding the scripts. I haven't really worked under the hood of a linux machine since I realize that my 15 year old optiplex was not going to suffice as a media server for .mkv, so I'm a little rusty on the terminal end of things.

To run the scripts that you've posted, do I just copy them into a terminal, or do I have to save them as some sort of a file? I feel like I've done something similar before, but I can't remember exactly what I did.

*apologizes for being a script kiddy*

Thanks for the help!

---

### Post by lores on 2010-10-14
First of all, you should test the following command by simply pasting it into a terminal and pressing enter ```
synclient TapButton1=1 TapButton2=2 TapButton3=3 VertTwoFingerScroll=1 HorizTwoFingerScroll=1 EmulateTwoFingerMinZ=10 EmulateTwoFingerMinW=6
``` If the touchpad works as expected, you can have Gnome execute this command at login by adding it into system -> prefs -> autostart. However, the setting will be lost if you suspend/resume (and on some other occasions, too...), so you can consider adding it e.g. to gnome-panel as an icon. I still haven't found an elegant solution for automating reenabling the customised settings and I'm stuck with a loop script, executing the command every n (here: 8 ) seconds...
```
#!/bin/sh
while true ; do
	synclient TapButton1=1 TapButton2=2 TapButton3=3 VertTwoFingerScroll=1 HorizTwoFingerScroll=1 EmulateTwoFingerMinZ=10 EmulateTwoFingerMinW=6
	sleep 8
done

```
So, if it's acceptable for you, you'd better stick with an icon...

If anyone has a better idea (and there surely exists one), please let us know.

---

### Post by superninja on 2010-10-29
I am in the market for an Asus eee pc 1005HAB and I have not found any compatibility charts for it for Ubuntu 10.10 netbook remix, other than the multitouch does everything else work with 10.10?

---

### Post by cfree220 on 2010-10-29
Yup. I haven't tried the card reader, but I would be surprised if that didn't work.

The other thing that you should be aware of is the fact that there are different versions of the 1005HAB. Mine does not have N networking.

---

### Post by Mauby on 2010-10-29
That's good to know.  I joined the forums just to see if anyone installed Ubuntu on their eee pc 1005HAB.

---

### Post by superninja on 2010-10-29
> **cfree220 said:**
> Yup. I haven't tried the card reader, but I would be surprised if that didn't work.

The other thing that you should be aware of is the fact that there are different versions of the 1005HAB. Mine does not have N networking.

What is N networking?

---

### Post by cfree220 on 2010-10-29
Sorry, I could have phrased that better. My netbook does not have a wireless N card, which is about 6 times faster.

---

### Post by superninja on 2010-10-29
Oh ok. Wifi works right?

---

### Post by lores on 2010-10-29
On Eeepc 1005P, everything works flawlessly and battery life (with laptop-mode-tools, v. [http://ubuntuforums.org/showthread.php?p=9962198](http://ubuntuforums.org/showthread.php?p=9962198) ) is better than on other OSes. You can compare the specs and see which hardware is the same as 1005HAB's.

PS
WiFi 802.11n works very well, too.

---

### Post by superninja on 2010-10-30
Awesome thank you very much for the help

---

### Post by superninja on 2010-10-31
The eee pc's (1005HA) BIOS has the ability to boot from USB correct?

---

### Post by cfree220 on 2010-10-31
correct

---

### Post by cfree220 on 2010-10-31
It can also boot from the card reader.

---

### Post by superninja on 2010-11-01
Cool, that makes things easy then :)

---

