---
title: "Various problems with my new laptop"
date: 2009-07-30
forum: General Help
---

### Post by WindPower on 2009-07-30
Hi there, I've installed Kubuntu 9.04 64-bit on this ASUS laptop that I just bought. So far my experience has been pleasant for the most part, but I still have a large amount of problems. You don't have to read them all (this wall of text probably seems a bit intimidating), I appreciate any answer.
Without further ado, let's go.

[list][*]First, I can't play music while on battery power. The music plays but stutters, it's very noticeable and very annoying. Even with the power plan set to "Performance", and VLC having realtime CPU and I/O priority, the music doesn't play properly. On A/C power, the song stutters in the first few seconds, but then plays fine. The media player used doesn't seem to affect this (I tried VLC, mplayer, Songbird, and Amarok, they all do the same). The filesystem where the song is doesn't matter either, I can't play it from NTFS partition or my home (ext4) partition. Copying it on an external device like a USB key doesn't help either. I can, however, play it on Windows, so it's not a hardware issue.
[*]Second, how to enable tap-to-click and the "right-side-of-the-touchpad-scrolls-the-window" feature? I once installed Kubuntu 9.04 64-bit on another laptop and these two features were available out-of-the-box, but it doesn't seem to be the case here (using the same installation CD), and I can't find any mention about this in the system settings.
[*]Third, how to disable Kbluetooth4 and Klipper, and remove their icons? I don't use them and don't want them cluttering up my system tray.
[*]Fourth, though this might not be the right place to ask: The global Auto-Type hotkey for [KeePassX](http://keepassx.org/) seems to "unregister" after a while and stops working until I reopen KeePassX from the tray, go to its settings, then click OK to save the settings again. The password database isn't locked or anything; the hotkey works sometimes but not others in a weird pattern. It's probably a problem with KeePassX itself (it should use KDE's hotkey API anyway), so I guess it's not the right place to ask this, but if anyone knows the solution...
[*]Fifth, the Network Manager. My only Internet access right now is a 3G USB key. Its box says "works on Windows and Mac OS X", so I assumed it also meant "does not work on Linux" (otherwise they would brag about it on the box too, right?). I plugged it in and a "ttyusb0 device inserted" notification appeared. The "Mobile Broadband" tab, however, was available in the network manager preferences, but when I add a connection (it asks between a GSM and CDMA connection, what are those and what is the difference?), it asks for a bunch of numbers and other information which I don't know/have. I guess they're written into the USB key and the Windows software provided with the key prevents the user from having to type these things. I abandoned the idea and thought I just would go Internet-less for a while. But I happened to have another (Windows) computer at hand, so I installed the software for the 3G key on that other computer and created a "ad-hoc" network with "Internet Connection Sharing" of the 3G connection. Then I booted up my computer on Windows, it worked fine, I could join the wireless ad-hoc network and browse the Internet, but while I do see the wireless network on Linux, I can't seem to connect to it: the network manager just stands there for a minute and then says "Connection on interface wlan0 failed" after a while, even when removing the WEP/WPA key from the ad-hoc network.
[*]Sixth, and this is a minor issue, but when I double-click a video in Dolphin, it opens in VLC (I installed VLC 1.0.0 from the PPA linked from videolan.org) but the video is on the left of the VLC window (there is one big black vertical bar on the right of the video, rather than two equally-wide vertical bars). When I resize or maximize the VLC window, however, it gets centered (there are two equally-wide vertical bars on each side). I'd like it to be centered from the start if possible :)
[*]Seventh, while hovering large video files in Dolphin (excluding .mkv videos, it seems), it freezes up for a long while that seems proportional to the length or size of the video. It's really annoying. I guess it kind of tries to do a "Preview" to get a thumbnail of the video, but even if that was the case, it doesn't seem to be displayed at all: the right sidebar, which does show the thumbnails for images, doesn't seem to do so for videos, so the freezing become both annoying and useless. Is there any way to disable that (while keeping the nice image previews)?
[*]Eighth, and this is a minor issue: I never use Caps Lock, so I thought I'd disable in. I found stuff about it in the System Settings, there's all kinds of options to make it have a different behaviour, which is great. However, none of them seemed to do what I want: Do **nothing**. So I thought I'd try assigning that key to a Hotkey (namely, the Yakuake hotkey. I love Yakuake~). It did work, but since the Caps Lock key wasn't disabled, it turns Caps Lock on when I open Yakuake, and turns it back off when I close it. So I thought I'd give it one of those alternate behavior in the System Settings, but then it stopped working as a Global Hotkey. How can I either: a) Disable it completely / b) Assign it as a global hotkey while turning off its capslocking behavior?
[*]Ninth, a while ago back home I had a SMB share mounted in my filesystem. I noticed that shutdown takes one or two extra minutes whenever that share is mounted, and it says weird messages about CIFS when shutting down. I noticed that holding down the power button at that point was safe, as all the drives were unmounted, but is there a way to disable this delay anyway?
[*]Tenth, I installed Flash using the flashplugin-installer package. It works for the most part, but sometimes it doesn't: the Flash area becomes completely gray, as well as all other Flash embeds in the following web pages. Reloading the page sometimes help, but most of the time I have to restart Firefox, which is annoying.
[*]Eleventh, I can't seem to download Google Gears back when I had Internet access. From what I remember, it had something to do with my platform type not being compatible. I can't really remember right now though :( I thought Google was Linux-friendly?
[*]Twelfth, this seems to be a silly bug and it doesn't bother me at all but I still noticed it. I have a nice OpenGL screensaver, and the unlock dialog is nicely displayed over it. Now, in the system settings -> About Me, there is a "At password prompt" box. The first and default option is "Show one star for each letter", which works fine, and as expected. The last option is "Show nothing", and it works fine as well. The second option is "Show three stars for each letter", and I thought I'd activate it for fun, just to see how long my password would look to someone else as I typed it. However, once enabled, whenever I type into the password field, I can notice a significant FPS drop for the OpenGL screensaver running besides it (goes from ~45 fps to ~8 fps). Stopping to type makes the fps go back to normal. It's weird.
[*]Thirteenth, is there any way (plasmoid?) to show the RAM and/or disk bandwidth usage in the taskbar, like Gnome's System Monitor widget? I only found the CPU usage and temperature. The disk monitor plasmoid only shows disk usage, which isn't really useful.
[*]Fourteenth, my laptop's built-in webcam works in Cheese and Kopete, but doesn't work in Flash or Skype. How can I make it work there? Since Cheese and Kopete can see it, why can't Skype and Flash? (I had to install the gnome-icon-theme package in order to get Cheese to work, otherwise Cheese crashes st startup while trying to load an nonexistent icon. gnome-icon-theme should be added to Cheese's dependencies, I guess. Installing gnome-icon-theme also had the positive side effect to make CompizConfig Settings Manager (ccsm) get pretty icons, so it should be added there too.)[/list]

Please reply even if you don't have the answers to all of the problems mentioned above.
Thanks in advance! :D

---

### Post by Zorael on 2009-07-31
Overwhelming, should've been split up into smaller posts. ;)

[list=1][*]**(sound)** [Try upgrading ALSA](http://ubuntuforums.org/showthread.php?p=6589810) and see if that fixes things. If not, [try passing a model to the driver](http://ubuntuforums.org/showthread.php?p=5017453#post5017453). If that also fails, try OSSv4, or succumb to despair. D:
[*]**(touchpad)** Are you completely sure you have a proper Synaptics touchpad to begin with? I know MSI have started to sell their netbooks with cheapo "Sentelic finger-sensing pads" that don't support drag-to-scroll due to patent infringment (feature patents should go diaf). Try the following two commands in a terminal and see if they output similar...output.
```
$ **xinput list | grep -i pad**
"SynPS/2 Synaptics TouchPad"    id=7    [XExtensionPointer]

$ **grep -i synaptics /var/log/Xorg.0.log**
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
(II) Synaptics touchpad driver version 0.99.3
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(--) SynPS/2 Synaptics TouchPad touchpad found
(--) SynPS/2 Synaptics TouchPad touchpad found
```
Tap-to-click and drag-to-scroll are enabled per default, if indeed you have a Synaptics pad. My netbook came with one of those dreaded Sentelics, so I had to buy a spare pad and replace it. From a competitor laptop brand (ASUS) to boot; MSI didn't get that money because they decided customers shouldn't be allowed to buy spare parts.
[*]**(klipper, kbluetooth)** Right-click them and pick Quit. They should ask you if you want them to start at next login, at which point you pick no. An alternative is to delete or remove **klipper.desktop** and **kblueplugd.desktop** in **/usr/share/autostart/**, which would make it a system-wide change (and as such require superuser permissions).
[*]**(keepassx)** Sounds like a bug, head over to launchpad and see if it's been reported already, else file a bug. Bugs can only be fixed by accident if developers don't know they exist.
[*]**(networkmanager)** The network manager is a bit sketchy, and has been now for some time. If it doesn't work for you, try **wicd** instead - package of the same name. And the manufacturers of your 3G dongle won't ever say "works in Linux" unless they undertake the effort of actually providing *support* for when it doesn't work. ;3
[*]**(vlc)** Sounds like a VLC bug. Again, it can only be fixed by accident unless reported.
[*]**(dolphin)** Yeah, that sounds like it's trying to create a preview thumbnail, though I'm not sure why. In Dolphin's settings, you can set a size limit at which it'll consider files too big to preview them, but by default it should be at 5MB or something similarly small. I can't replicate it in Dolphin 4.2.98 (4.3 rc3), so perhaps it's something that's been fixed since the Dolphin version available from the repositories (4.2.2).
[*]**(capslock)** To fix this, you have t-ooh, shiny.
[*]**(cifs)** Is [this](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/211631) it? If so, it's a papercut and is as such getting considerable attention.
[*]**(flash)** That's Flash crashing. Historically Flash has only been available as a 32-bit binary, and as it isn't open source it was up to Adobe to supply a 64-bit one. To work around this, you either had to run a 32-bit browser (which is possible but doesn't work if you use native, 64-bit input methods, for instance), or despair. Since people didn't want to despair, a 64-bit wrapper was written to encapsulate 32-bit plugins, with the wrapper acting as the medium between the browser and the plugin. A dirty solution, but it mostly worked, until later Flash releases and Firefox 3 when it suddenly started becoming very, very sketchy. There is nowadays a [64-bit Flash alpha](http://labs.adobe.com/downloads/flashplayer10.html) available for Linux (and Linux alone). Installation howto [here](http://ubuntuforums.org/showthread.php?t=1081964). Try that.
[*]**(gears)** Same deal here; the officially available binaries are 32-bit and your browser is 64-bit. However, while you could use a wrapper, this time around the source is open, so people figured out a patch to make it compile for 64-bit use. See [this thread](http://ubuntuforums.org/showthread.php?t=1202997).
[*]**(screensaver fps drop)** To [the launchpadmobile](https://bugs.launchpad.net/ubuntu/+filebug)!
[*]**(monitor applet)** Hmm, I seem to have several System Monitor plasma widgets available (CPU, Hard Disk, Hardware Info, Network, RAM, and Temperature), but then I'm running 4.2.98 (again, 4.3 rc3). I see the package that installed them for me (**plasma-widgets-workspace**) isn't available from the main repositories, only from the 4.2.90 (4.3 rc1) and onwards, from [Kubuntu ppas](https://launchpad.net/~kubuntu-ppa). (Upgrading can be hazardous unless you know how to recover from broken packages from a terminal.)
[*]**(webcam)** It seems to be a case of 32-bit vs 64-bit again, coupled with some unfortunate options used when compiling the webcam drivers. Skype isn't available as a 64-bit binary, and since it isn't open source, there isn't much to do about it. As for the drivers;
[quote=Andy, Skype staff]Attention 64-bit users who can't see their camera in Skype.

We have identified problems with old modules that haven't been compiled with proper compat_ioctl32 support. On Ubuntu, we compiled both uvcvideo and gspca from latest source (no compile options) and then could see the camera fine on our 64-bit test system.

So if you're having problems with your camera not being detected and can't wait for your distribution to update your camera drivers, feel free to grab the latest source for the driver for your camera, decompress, make, make install. And you should be right to go.[/quote]
Source [here](http://forum.skype.com/index.php?showtopic=101297&st=180&p=463468&#entry463468). See [this thread](http://ubuntuforums.org/showthread.php?t=634393) for instructions and pointers.[/list]

---

### Post by WindPower on 2009-08-07
You, sir, are a godsend~
[list][*]Sound - Upgrading ALSA worked. The script crashed thrice (./configure errors, mostly) but I relaunched it and it seemed to complete on its fourth run. For some reason though, it uninstalled kdm, leaving me with no autostarting X session. Thankfully a sudo apt-get install kdm fixed it. I had no sound for the next two boots, but now I do and it works fine, even on battery. The music does stutter a bit but it's a lot less noticeable, except when doing something heavy (launching Firefox/running 3D stuff) while on battery.
[*]Touchpad - I do seem to have a Synaptics touchpad:
```
$ xinput list | grep -i pad
"SynPS/2 Synaptics TouchPad"    id=6    [XExtensionPointer]
$ grep -i synaptics /var/log/Xorg.0.log
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
(II) Synaptics touchpad driver version 1.1.99
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
$
```However, I still don't have those two features. I have them on Windows though, so I'm certain my touchpad can handle it.
[*]klipper/kbluetooth - So simple! That worked for Klipper but not Kbluetooth (it doesn't ask anything when exiting), but the second solution worked. I don't care if it's system-wide, this lappy is mine and mine only (for once).
[*]keepassx - Will do when I have stable internets.
[*]networkmanager - No luck either sadly :( Hopefully I'll be back home soon with a more reliable connection.
[*]vlc - See keepassx. (I noticed it only did it when using the OpenGL output module rather than XVideo, so now I set the setting back to XVideo and it's gone.)
[*]dolphin - Yes, it's set to 5 MB and setting it lower/higher has no effect, it still freezes on large files, no matter if they're above the limit or not. I hope this will get fixed soon.
[*]capslock - Should I take that as an "unfixable" then? Come on, I just want to disable a key! D:
[*]cifs - Yay
[*]flash - Works, fixed!
[*]gears - Works, fixed! (But how about updates? Will I have to go about rebuilding the extension each time or googling for pre-built updated packages?)
[*]screensaver - See keepassx
[*]monitor applet - Too bad then, I'll just wait. I don't miss it that much.
[*]Works, fixed! But doesn't work in Flash. :([/list]

Thanks for everything, and yeah, this thing is pretty overwhelming. I wouldn't want to flood the forums with one threads for each of these, it'd be a mess :( This list is the result of a compilation of problems I've encountered offline for the most part, so I just wrote them down in a little text file which grew over time. With the little bit of internets I have, it's easier to do it all in one big go. Sorry about that D:

---

### Post by kpkeerthi on 2009-08-07
If you have split your queries into multiple posts you would have probably got a lot more responses. Just my 2 cents.

---

### Post by Zorael on 2009-08-09
> **WindPower said:**
> Touchpad - I do seem to have a Synaptics touchpad:
```
$ xinput list | grep -i pad
"SynPS/2 Synaptics TouchPad"    id=6    [XExtensionPointer]
$ grep -i synaptics /var/log/Xorg.0.log
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
(II) Synaptics touchpad driver version 1.1.99
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
$
```However, I still don't have those two features. I have them on Windows though, so I'm certain my touchpad can handle it.
That output looks about right. Does it work in a live CD environment, either one of Jaunty or of (gasp) Karmic?

FWIW, have a look at [http://www.ubuntuforums.org/showthread.php?p=7643273](http://www.ubuntuforums.org/showthread.php?p=7643273). It's concerning the horizontal scroll function, granted, but you'll get an idea of how to tweak the synaptics driver settings. I'm not saying it'll help, though.

> **WindPower said:**
> dolphin - Yes, it's set to 5 MB and setting it lower/higher has no effect, it still freezes on large files, no matter if they're above the limit or not. I hope this will get fixed soon.
Well, "fixed"... chances are it's already fixed *upstream*, but a version in which the fix is included may never hit the Jaunty main repos.
> Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages stays constant for the entire 6 months. For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain at OpenOffice.org 2.0.x for the entire 6-month release cycle, even if a later version gets released during this time. The Ubuntu team may apply important security fixes to 2.0.x, but any new features or non-security bugfixes will not be made available.

This is where Ubuntu Backports comes in. The Backports team believes that the best update policy is a mix of Ubuntu's security-only policy AND providing new versions of some programs. Candidates for version updates are primarily desktop applications, such as your web browser, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system.
Consider upgrading to 4.3. Requires some terminal knowhow and [aptitude-fu](http://ubuntuforums.org/showthread.php?p=7744393#post7744393) though, as chances are something goes wrong in the process, in which case you'll have to know how to put it back on track/beat it into submission.

> **WindPower said:**
> capslock - Should I take that as an "unfixable" then? Come on, I just want to disable a key! D:
You want to set it as something else, no? And not just disable it? If so; first, figure out what the **keycode** for your caps lock key is (should be **66**, I think). Start '**xev**' in a terminal and watch its output when you hit caps lock. Ctrl+C (when the terminal has focus) or close the Event Tester window to exit.
```
KeyPress event, serial 31, synthetic NO, window 0x4000001,
    root 0x1a7, subw 0x0, time 12151922, (-657,728), root:(512,753),
    state 0x0, **keycode [COLOR="Lime"]66[/COLOR]** (keysym 0xffe5, **[COLOR="Lime"]Caps_Lock[/COLOR]**), same_screen YES,
    XLookupString gives 0 bytes:                                      
    XmbLookupString gives 0 bytes:                                    
    XFilterEvent returns: False
```
edit: So I tried this, and it didn't react to the global hotkey. Solution after quote. Keeping it for kicks.
> Now, run '**xmodmap -pke**' and find a suitable, exotic key that you want the caps lock to send instead of *lock*. "**copyright**", perhaps? "**Muhenkan**" (Japanese input related)? Actually Muhenkan, Hiragana and Katakana may be good candidates unless you use Japanese input; then you'd be sure you wouldn't be triggering Yakuake inadvertently when using that key, as would be the case if you set your caps lock key to send "**space**". For obvious reasons, setting it to "**XF86PowerOff**" has its sideeffects, too.
```
$ xmodmap -e "**keycode [COLOR="Lime"]66[/COLOR]** = **[COLOR="RoyalBlue"]muhenkan[/COLOR]**"
```
Test it! Then bind Yakuake's global shortcut to your new caps lock ([COLOR="RoyalBlue"]**muhenkan**[/COLOR]).
**Solution**: just use an F*n* key higher than the max available on your keyboard (usually 12, yeah?).It seems they go all the way up to [COLOR="RoyalBlue"]**F35**[/COLOR], so no shortage of imaginary keys. Extra keys added afterwards decide what key gets sent when the key is pressed with a modifier, like shift and alt. I'm having limited success with getting caps lock to work with another modifier than shift, but it seems to work better on other keys. Regardless, this will make it send [COLOR="RoyalBlue"]**F35**[/COLOR] when pressed normally, and [COLOR="RoyalBlue"]**Caps_Lock**[/COLOR] when pressed with shift.
```
$ xmodmap -e "**keycode [COLOR="Lime"]66[/COLOR]** = **[COLOR="RoyalBlue"]F35 Caps_Lock[/COLOR]**"
```

Supposedly, saving the quoted bits (**keycode [COLOR="Lime"]66[/COLOR]** = **[COLOR="RoyalBlue"]F35 Caps_Lock[/COLOR]**) in **~/.Xmodmap** would make it reapply upon logging, making them persistent for your user.

I found some bug reports about KDE not reading that file automatically, though, *in which case* you would have to complement it with a script in (for instance) **~/.kde/env/**. If in that directory, I think it has to end with a **.sh** extension, but I'm not completely sure.
```
#!/bin/bash
test -r ~/.Xmodmap && xmodmap ~/.Xmodmap
```
So if just having your **.Xmodmap** doesn't make the settings reapply, save that snippet as **~/.kde/env/xmodmap.sh** and try again. Don't forget to set it to executable.

> **WindPower said:**
> gears - Works, fixed! (But how about updates? Will I have to go about rebuilding the extension each time or googling for pre-built updated packages?)
Yep. Perhaps you can [find a ppa](http://ppa-search.appspot.com/) with it already compiled, maintained by someone else. [https://launchpad.net/~stefanlsd/+archive/gears](https://launchpad.net/~stefanlsd/+archive/gears), perhaps? No guarantees.

---

### Post by WindPower on 2009-09-29
I'm going to sound like a broken record but I'm still going to repeat myself: You're a godsend! [-o<

(I know I'm late)

The xmodmap solution didn't seem to work at first but I was actually not pressing the key hard enough :P I mean, this key has really not seen any usage so it's a bit rusty... :)

The touchpad does work in a LiveCD. But don't worry, got that all fixed now (with multitouch to boot! \\:D/)

Couldn't find an up-to-date PPA for Gears (nor an up-to-date build at all), so I'm simply using an old Gears version for now. Firefox bugs me two or three times a week about updating it but I'll have to live with it :)

Marked as solved!

---

