---
title: "Keyboard language problem - Ubuntu 10.10"
date: 2010-12-22
forum: General Help
---

### Post by Costas100 on 2010-12-22
I recently installed the latest version of Ubuntu 10.10 and I am impressed and wish to thank the Ubuntu team, and also report some minor problems here and one in particular that is creating difficulties in my daily use:

I am using a dual language (**English and Greek**) in my computer, installed properly and works in all programs. Only I have three problems:
 
[LIST]
[*] When the second language was installed, a small but very clear language indicator appeared in my top panel. I could switch language from this indicator or with a keyboard command. Now this indicator became too small to read, with the result to create problems, especially when I am asked to enter my password, which of course is in English. I am bypassing it by typing my password in the text editor and then copy/paste. But I am sure there is a solution somewhere. 
[*] Again in the language issue, it appears that language keeps changing at random, without me asking either from the panel applet or the keyboard. I thought that it was only happening when I open a program that had previously used say the Greek language, so I changed the main programs I use, to default English. But it is still happening. I am trying to find a way to make the English language as default in my computer, but no success to this point.
[*] One more thing in the language issue: When I installed the Greek language, a great number of additional (and totally unknown to me) languages were installed. Is it wise to delete these languages from Synaptic? When I tried to delete one of these extra languages I was told that some additional files will be deleted and I am worried that these files may be required by the two languages I am using or other programs.
[/LIST]

**New addition Jan 16, 11**
There is more in this issue with file **kkbswitch** See next page for more details, reply #11.

---

### Post by TeoBigusGeekus on 2010-12-22
Can you post us your xorg.conf?

---

### Post by Costas100 on 2010-12-22
Thank you TeoBigusGeekus

With a command sudo gedit xorg.conf I get an empty text file
On search for xorg.conf in file system I get:
xorg.conf.d	/usr/share/X11
xorg.conf	/usr/share/doc/xserver-xorg-video-nouveau/examples
xorg.conf.5.gz	/usr/share/man/man5

I am confused

---

### Post by TeoBigusGeekus on 2010-12-22
gksu gedit /etc/X11/xorg.conf

---

### Post by Costas100 on 2010-12-22
&#928;&#940;&#955;&#953; &#949;&#947;&#974; &#963;&#965;&#956;&#960;&#945;&#964;&#961;&#953;&#974;&#964;&#951;: 

Under usr/share/X11/xorg.cof.d I have 4 text files:
10-evdev.conf
50-synaptics.conf
50-vmmouse.conf
50-wacom.conf
51-synaptics-quirks.conf	and
60-magictrackpad.conf

I also did a sudo nano /etc/X11/xorg.conf and got within the terminal an apparently empty file

&#922;&#945;&#964;&#940; &#964;&#945; &#940;&#955;&#955;&#945; &#972;&#955;&#945; &#954;&#945;&#955;&#940;, &#963;&#964;&#959; &#954;&#961;&#973;&#959; &#932;&#959;&#961;&#972;&#957;&#964;&#959;. &#917;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974; &#947;&#953;&#945; &#972;&#964;&#953; &#954;&#940;&#957;&#949;&#953;&#962;.
&#922;&#974;&#963;&#964;&#945;&#962;

PS: I just found out from [http://askubuntu.com/questions/4662/where-is-x-org-config-file-in-ubuntu-10-10-how-to-configure-x-there]("http://askubuntu.com/questions/4662/where-is-x-org-config-file-in-ubuntu-10-10-how-to-configure-x-there")   that xorg.conf does not exist in 10.10 and it must be created as an empty file which hopefully it will detect information and add it automatically. I think it is getting more confusing as time passes.

---

### Post by TeoBigusGeekus on 2010-12-22
> **Costas100 said:**
> &#922;&#945;&#964;&#940; &#964;&#945; &#940;&#955;&#955;&#945; &#972;&#955;&#945; &#954;&#945;&#955;&#940;, &#963;&#964;&#959; &#954;&#961;&#973;&#959; &#932;&#959;&#961;&#972;&#957;&#964;&#959;. &#917;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974; &#947;&#953;&#945; &#972;&#964;&#953; &#954;&#940;&#957;&#949;&#953;&#962;.
&#922;&#974;&#963;&#964;&#945;&#962;
&#922;&#945;&#953; &#922;&#945;&#963;&#964;&#959;&#961;&#953;&#940; &#964;&#963;&#953;&#956;&#960;&#940;&#949;&#953; &#945;&#961;&#954;&#949;&#964;&#940;...

What I was thinking about was to add this section
```
Section   "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
    Option      "XkbLayout" "us,gr" 
    Option      "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection
```
to your xorg.conf file.
This would cause your pc to have two layouts (us and gr obviously), alternating with alt+shift, but, most importantly, it would make your scroll lock light up whenever you are in the greek layout.
If you are sure that you don't have an xorg.conf file (navigate to /etc/X11 with nautilus, just to make sure), it's worth the effort to try to create one with the above contents and save it.
Reboot then and post us the outcome.

PS: I hope you have a live cd in case something goes wrong and ubuntu doesn't identify your keyboard at all.

---

### Post by Costas100 on 2010-12-22
Hello TeoBigusGeekus, I followed your suggestion and created the file and then did a restart. The file is now there and it has not changed at all from what I entered before reboot (the code from your message).
No major problems yet, I guess I will wait for a few days and observe. If anything new appears, I will post it here.

Thank you very much
&#935;&#943;&#955;&#953;&#945; &#949;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974;

&#922;&#974;&#963;&#964;&#945;&#962;

---

### Post by Costas100 on 2010-12-23
Good morning TeoBigusGeekus and sorry to bother you again. I just noticed that you mentioned to add the xorg.conf file in the /etc/X11 directory. I added mine in the usr/share/X11/ directory. Under the /etc/X11 directory there is a file named xorg.conf.save which is empty. It has a size of 1 byte, but when I open it with gedit it is empty. &#932;&#945; &#956;&#965;&#963;&#964;&#942;&#961;&#953;&#945; &#964;&#969;&#957; Computers.

I can move the xorg.conf file to /etc/X11 if you think this is a better location.

Also when I open Nautilus I get this strange message:

Initializing nautilus-gdu extension

(nautilus:2068): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2068'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I am the only user of this computer, and I am not sure what they are talking. In any case Nautilus opens and is functional. I think this is bug of Nautilus, I was getting it even with previous Ubuntu versions.

Sorry for being a pest, you can contact me at coslaz papaki gmail.com if you wish.
 take care and thank you again.
Costas

---

### Post by TeoBigusGeekus on 2010-12-23
I don't use nautilus so I can't help you with that. Just ignore it.
Edit the xorg.conf which is located in /etc/X11 and add the lines I've posted you, see if it makes any difference.

---

### Post by joham34 on 2011-01-15
Hi , I accidentally removed the whole indication applet ( battery status, keyboard language , internet connection status ) and fortunately , found the solution here : [HTML][/HTML][http://ubuntuforums.org/showthread.php?p=10189878](http://ubuntuforums.org/showthread.php?p=10189878)[HTML][/HTML] 

I've solved my problem by entering in terminal:
```

```gconftool --recursive-unset /apps/panel```

```
and then pressing Alt+F1.
I followed the instruction and had back the initial panel we get after installing ubuntu, to add my own application didnt take long
Hope it helps

---

### Post by Costas100 on 2011-01-16
Thank you joham34, I may try that route with care. My problem is slightly different and I have another post under [http://ubuntuforums.org/showthread.php?t=1665427](http://ubuntuforums.org/showthread.php?t=1665427) with more INFO.

Up until yesterday I had two working indicators in my top panel as shown in the small attached picture. The problem was and still is, that at random they disappear and at random they return.
Yesterday I decided to try locking the unknown applet to panel and today it was non operational. No problem since the kkbswitch applet works fine (today). I am trying to find the command line that I will enter in a custom launcher for the kkbswitch, in order to instantly replace it in the event of a new random loss. 

kkbswitch is an excellent keyboard indicator, only if it stays in the panel all the time.
Both indicators worked in parallel (when they are active and visible) today only the kkbswitch is working and it is fine with me. I also have the feeling that kkbswitch is not really an applet since on right click there is no "remove from panel" or "lock to panel" or "move" In staid it has a very nice menu including configuration and help and "Quit".

This is not such a big deal since my keyboard command works fine, the only problem is when I must enter my password, I must type it first in a text editor to make sure that the language is correct.

Thank you all and despite the fact that I had many small problems with the last two versions of Ubuntu 10.04 and 10.10 I think that Ubuntu is the Greatest computer operation system and one day (I hope soon) will replace all other. The funny thing is that my best Ubuntu installed in a very old Pentium IV machine, with a partially broken hard disk is ArtistX (Ubuntu 9.10 based - fully loaded) and I do not recall one problem with it.

All the best to the Ubuntu team

Costas

---

