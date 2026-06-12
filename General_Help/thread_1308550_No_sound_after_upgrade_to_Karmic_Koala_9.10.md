---
title: "No sound after upgrade to Karmic Koala 9.10"
date: 2009-10-31
forum: General Help
---

### Post by petru.marginean on 2009-10-31
Hi,

I used to have sound, but after upgrading to the new Karmic Koala it doesn't work any more.
I googled it, and tried a few commands. The following shows something is wrong:
```
$> sudo aplay -l
aplay: device_list:223: no soundcards found...
```Unfortunately I do not know how to fix it, or how to investigate further.
Any suggestions?

I've also included below some other commands that could help find the issue.

Many thanks,
Petru

```

$> lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
2.6.28-16-generic

``````

$> dmesg | egrep -i "sound|audio|snd"
//nothing

``````

$> cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 22

``````

$> lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

``````

$> lsmod | grep snd
snd_hda_intel         435252  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,
snd_seq_oss,snd_rawmidi,
snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

``````

$> sudo /etc/init.d/alsa-utils restart  
 * Shutting down ALSA...
 * warning: 'alsactl store' failed with error message 'alsactl: save_state:1502: 
No soundcards found...'...
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
//...
 

```

---

### Post by sharky6000 on 2009-10-31
I just wanted to say I'm experiencing the same thing. I also have an Intel HDA card: 

```

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

```

```

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdffc000 irq 16

```

My module info: 

```

snd_hda_intel         559028  2 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  3 snd_pcm_oss
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78920  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  3 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

```


And the output of the rest of the commands are identical to the original post. 

Audacious and mpg123 seem to be "working", eg. they seem to be playing the files without a problem (no error message), but no sound is being produced. This happens when I choose either ALSA or OSS as output plugins within audacious. 

It's as if the sound card is muted; but when I use gnome-alsamixer, no controls are showing up at all (as if ALSA no longer recognizes the sound card) so I get an empty dialogue. I tried other mixers (aumix, xmix) and nothing appears to be muted or at 0 volume level.

---

### Post by thuleni on 2009-11-01
Bump - any ideas folks - I am having the same problem

---

### Post by ccasin on 2009-11-01
I also can't get any sound after upgrade to karmic koala, with a similar card.  My output from aplay is more hopeful, though, and restarting alsa-utils doesn't report any problems.

```

ccasin@EniacOnRails> sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/ccasin not ours.
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I looked through the options in alsamixer, and everything seemed normal.  Also the sound buttons on my lenovo T60 used to work to mute and adjust volume, but they seem to be having no effect now.  Here is my output from the commands everyone else is listing:

```

ccasin@EniacOnRails> cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xee400000 irq 17

``````

ccasin@EniacOnRails> lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

``````

ccasin@EniacOnRails> lsmod | grep snd
snd_hda_codec_analog    59292  1 
snd_hda_intel          26920  5 
snd_hda_codec          75708  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  3 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  18 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  3 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

```

---

### Post by Kyle.Gant on 2009-11-01
*bump*

i too have no sound, and no idea how to fix what's wrong. any and all help would be appreciated...

---

### Post by ccasin on 2009-11-01
OK, I was able to fix it by doing:

```

rm -rf ~/.pulse
killall pulseaudio

```

But I don't have the bad version of the problem where no soundcard shows up.

---

### Post by sharky6000 on 2009-11-01
Firstly, I suggest moving your .pulse to a separate directory rather than removing it, in case that doesn't solve the problem: 

```

mv ~/.pulse ~/.old-pulse

```

And.. it didn't work for me. :( 

thuleni: do you have an Intel HDA card as well?

---

### Post by CuracaoThe on 2009-11-01
Have the same problem.
```
sudo aplay -l
aplay: device_list:223: no soundcards found...
```

```
$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic
2.6.28-11-generic

```

```
$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xddef8000 irq 11

```

```
$ lspci | grep -i audio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

```

```
$ lsmod | grep snd
snd_hda_intel         435636  2
snd_pcm_oss            46336  0
snd_mixer_oss          22656  3 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14336  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  3 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

```

---

### Post by commonplace on 2009-11-01
> **ccasin said:**
> OK, I was able to fix it by doing:

```

rm -rf ~/.pulse
killall pulseaudio

```

But I don't have the bad version of the problem where no soundcard shows up.

This worked on my wife's laptop. What's really weird to me is that it was a clean installation, not an upgrade.

Now I just need to resolve the multitude of issues on my own laptop, and the disappearing-mouse-cursor problem on my wife's laptop. :)

Thanks for this!

/Kevin

---

### Post by petru.marginean on 2009-11-01
I want to emphasize I use the kernel version (2.6.28-16-generic) I had BEFORE the upgrade to KK.

This is because with the new kernel (2.6.31-14-generic), even the sound WAS working, I had many applications failing, including 'wicd' and 'sensors':

[IMG]https://mail.google.com/mail/?ui=2&ik=aa119a105d&view=att&th=124ad8a4d5e86b2e&attid=0.1&disp=inline&realattid=f_g1h65rso0&zw[/IMG]

[IMG]https://mail.google.com/mail/?ui=2&ik=aa119a105d&view=att&th=124ad8a4d5e86b2e&attid=0.3&disp=thd&realattid=f_g1h6akjw2&zw[/IMG]

[IMG]https://mail.google.com/mail/?ui=2&ik=aa119a105d&view=att&th=124ad8a4d5e86b2e&attid=0.2&disp=inline&realattid=f_g1h6aghi1&zw[/IMG]


So I need to make the sound working in KK using 2.6.28-16-generic kernel.

Thanks,
Petru

---

### Post by smkelley on 2009-11-01
I had a similar problem -   "aplay: device_list:223: no soundcards found..."

 My solution, seen on another forum somewhere, was to add myself to the "audio" group, as it was actually a policykit-based permissions problem.  

> sudo usermod -a -G audio <username>
Steve

---

### Post by aval57 on 2009-11-01
> **petru.marginean said:**
> So I need to make the sound working in KK using 2.6.28-16-generic kernel.

Kernel must to be **2.6.31-14** according to[ https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816")

Thanks for the post, though.  I had the same problem (aplay: device_list:223: no soundcards found...) but after reading your post I realized that I had elected not to update ***/boot/grub/menu.lst*** during the upgrade so as not to mess with my XP dual-boot setup, and grub was still loading the previous kernel (2.6.28-13).

Alsa now runs fine after fixing menu.lst to load the 2.6.31-14 kernel (just as you said!). For others who may be interested, first confirm whether you have the wrong kernel```
$ uname -r
```then backup your current menu.lst and auto-generate a new one, which should add entries for the new kernel
```
$ sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.orig
$ sudo update-grub

```In my case I had to re-customize it for dual-boot by pasting in my previous XP entry from  */boot/grub/menu.lst.orig.*

-Bahman

---

### Post by michaelzap on 2009-11-01
I what may be the same problem on my Lenovo Y530 (no sound device reported in the Sound Control Panel, no sound input or output, and random crashes). I removed the proprietary driver for my internal modem (which it turns out is a sub-element of my Intel sound card) and suddenly I had sound and the device is visible in the Sound Control Panel (and so far I've had no more crashes). It's too early for me to be sure that the issue is resolved, but I'm happy not to use my modem if my system will be stable and have sound.

---

### Post by goldencako on 2009-11-01
I had this problem twice. First I upgraded it, also keeping menu.lst, and I lost my sound. I proceeded to fresh install 9.04 and then upgraded on a clean slate... same problem. I finally got my hands on a bootable USB with 9.10 and installed it. The sound works just fine now. The weird thing is, on my second try, I installed KDE just for the kicks and sound was working there. 

Anyways, fresh installs are simply not an option to must people (it usually isn't for me, I was lucky to get some storage space this time for backups), but if it is an option I highly recommend it. Both upgrades left my computer sluggish and weird. The fresh install is much better. Oh, and now I keep my home on a separate partition, for future fresh installs.

---

### Post by yjohn on 2009-11-01
i found the sound had been muted on the sound control.

---

### Post by petru.marginean on 2009-11-01
Hmmm...
Executed this command:

```
  $> pkill pulseaudio; sleep 2; pulseaudio -vvv 2>&1 | tee pulse1.log 
```and then:

```
  $> grep controlC0 pulse1.log
  D: module-udev-detect.c: /dev/snd/controlC0 is accessible: no
```It looks like the controlC0 is not in the /dev/snd but in /dev:

```
  $> find /dev -name controlC0
  /dev/controlC0
```Could this be the issue?!

Regards,
Petru

---

### Post by salingova on 2009-11-01
Is there anything else to try, because I tried everything mentioned here without a success, I even reinstalled grub to grub2 since I was upgrading from Jaunty and it doesn't happen automatically.
Simply the no-sound card problem is still there.

---

### Post by petru.marginean on 2009-11-01
I just did this:

```
$> cd /dev/snd

$> sudo ln -s ../controlC0

$> ls -ltr
total 0
drwxr-xr-x 2 root root 60 2009-10-31 23:51 by-path
lrwxrwxrwx 1 root root 12 2009-11-01 23:17 controlC0 -> ../controlC0
```and then surprise:

```
$> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Still I have no sound, but I believe I'm closer!

Regards,
Petru

---

### Post by CuracaoThe on 2009-11-02
I've solved my problem by upgrading GRUB to version 2. Then I've used the 2.6.31-14 kernel for boot Linux.

```
$ uname -r
2.6.31-14-generic
```However my computer had frozen until I wrote an ACPI parameter to **menu.lst**.
That's why I've used more older version of kernel.
A few minutes ago I did these actions:

```
$ sudo vim /boot/grub/menu.lst

kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=3ba0e00a-7fd3-4adb-9c7b-d43bad09ad44 ro quiet splash _acpi=off_

```After rebooting everything is working well.

---

### Post by salingova on 2009-11-02
> **CuracaoThe said:**
> I solved my problem by upgrading GRUB to 2. Then I used the 2.6.31-14 kernel to boot.

```
$ uname -r
2.6.31-14-generic
```However my computer had been freezing while I not wrote an acpi parameter at **menu.lst**.
That's why I used more older version of kernel.
A few minutes ago I did these actions:

```
$ sudo vim /boot/grub/menu.lst
```...and set at the kernel's string:

```
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=3ba0e00a-7fd3-4adb-9c7b-d43bad09ad44 ro quiet splash _acpi=off_

```After reboot everything's work fine.

I also upgraded to grub2 however I didn't have a problem to boot from the 2.6.31-14 kernel. Anyway, it didn't help me anyhow. Im going desperate guys, computer with no sound is really annoying.

---

### Post by thuleni on 2009-11-02
> **sharky6000 said:**
> Firstly, I suggest moving your .pulse to a separate directory rather than removing it, in case that doesn't solve the problem: 

```

mv ~/.pulse ~/.old-pulse

```

And.. it didn't work for me. :( 

thuleni: do you have an Intel HDA card as well?

Yes also have Intel HDA

---

### Post by mzilhao on 2009-11-02
this may help: 
[https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/449762]("https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/449762")

see if you can get your sound working after
```
sudo alsa force-reload
```

if it works, try removing the package "sl-modem-daemon".
it worked for me...

---

### Post by sharky6000 on 2009-11-02
> **aval57 said:**
> Kernel must to be **2.6.31-14** according to[ https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816")


That fixed my problem as well -- I had conflicts in the merge of menu.lst, so it wasn't updated to the new kernel. I didn't want to lose my custom additions for my dual-boot. 

Thanks!

---

### Post by cslester on 2009-11-03
I too had similar issues; I upgraded from Jaunty to Karmic and my sound card ceased to be recognized.  After attempting several ideas suggested here and elsewhere, I discovered this bit:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816)

In short, I was running a previous kernel (2.6.28-15) instead of the kernel that Karmic is meant to run on, 2.6.31-14.  Issues I had encountered previously with the updating of grub's menu.lst kept me booting into the old kernel.
(see also: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009))

Running
```
sudo update-grub
``` 
and rebooting got my menu.lst up to date and my machine running the most recent kernel... and my sound card recognized and working with no further changes.


I hope this presents a workable solution for at least some of you....

-cslester

---

### Post by l33tminion on 2009-11-04
> **michaelzap said:**
> I what may be the same problem on my Lenovo Y530 (no sound device reported in the Sound Control Panel, no sound input or output, and random crashes). I removed the proprietary driver for my internal modem (which it turns out is a sub-element of my Intel sound card) and suddenly I had sound and the device is visible in the Sound Control Panel (and so far I've had no more crashes). It's too early for me to be sure that the issue is resolved, but I'm happy not to use my modem if my system will be stable and have sound.

I had the same problem, and this fixed it.  Many thanks!

---

### Post by atimkara on 2009-11-04
I have
```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```I opened alsamixer, raise Master, Headphone,PCM,front, Mono to 100 and unmuted them EVEN IF IT SAYS SO and it worked.

---

### Post by Zoot7 on 2009-11-04
I'm not sure if this'll be any good to anyone, but it might be worth a shot running the script posted here:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
To either upgrade Alsa to the latest version, or to reinstall the default version.

I've no idea whether it'll work or not, but it's what I'd try myself.

---

### Post by crjackson on 2009-11-04
I spent an hour or so looking in to this tonight.  I found that if you install the proprietary modem driver, OFTEN (but not always) the modem grabs audio control before the sound chip.  Removing the driver will solve the issue if this is YOUR problem, however it may take a couple of COLD reboots (power off / on) before things start to work perfectly.

It disappoints me a little that I can't enable the modem, but I've never actually used it anyway and I can always dual boot to windows.

I REALLY hate to say this, BUT...  Windows is MUCH better at handling dial-up modems.  I'll probably get flamed, but it just is.

Any one who's had to STRUGGLE with WVDIAL would probably agree.  WVDIAL works great for some.  Others...  Not so much.

---

### Post by salingova on 2009-11-05
I would like to try the thing with the modem driver, but I am not sure how to do that. Could someone help me here pls. Thx

---

### Post by michaelzap on 2009-11-05
> **salingova said:**
> I would like to try the thing with the modem driver, but I am not sure how to do that. Could someone help me here pls. Thx

Just go to System -> Hardware Drivers and if there's a modem driver listed in there remove it. If this works for you, it will be immediate. You should see your sound card in the volume panel right away.

---

### Post by salingova on 2009-11-05
> **michaelzap said:**
> Just go to System -> Hardware Drivers and if there's a modem driver listed in there remove it. If this works for you, it will be immediate. You should see your sound card in the volume panel right away.

I have no drivers listed there. It says "No proprietary drivers are in use on this system"

---

### Post by michaelzap on 2009-11-05
> **salingova said:**
> I have no drivers listed there. It says "No proprietary drivers are in use on this system"

Then this fix won't work for you. You could also try running "sudo alsa force-reload" in a terminal. That has worked for some other folks (the root issue being that the modem grabs the sound resource before the sound card can, as I understand it).

---

### Post by dootzky on 2009-11-05
hey guys - just to give you my hint, like I've read in this thread:

I had 9.04 installed, and after upgrade to 9.10 the sound was gone.

I tried to do "sudo update-grub", but it still didn't work.

What you need to make sure is that your MENU.LST file **really updated!** mine wasn't getting updated, so I removed my menu.lst file (it's in the /boot/grub/menu.lst), and then ran the command 

```

sudo update-grub

```

and it created a new grub menu for me, and after normal reboot, the new kernel was loaded and the sound worked flawlessly. 

hope this helps somebody, sorry for the double post if I made it.

cheers, keep up the good software going, Ubuntu! :popcorn:

---

### Post by coldsystem on 2009-11-05
try  this [http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)

---

### Post by vicshrike on 2009-11-09
Thanks for all advices, but I realise that I will end up  with a fresh install. The problem(s) is fixable, but due to the configuration on my desktop I`ll do a clean install of the Karmic Koala. On the positive side I must say I do enjoy the UNR Koala on my Eee.:D

---

### Post by salingova on 2009-11-10
> **dootzky said:**
> hey guys - just to give you my hint, like I've read in this thread:

I had 9.04 installed, and after upgrade to 9.10 the sound was gone.

I tried to do "sudo update-grub", but it still didn't work.

What you need to make sure is that your MENU.LST file **really updated!** mine wasn't getting updated, so I removed my menu.lst file (it's in the /boot/grub/menu.lst), and then ran the command 

```

sudo update-grub

```

and it created a new grub menu for me, and after normal reboot, the new kernel was loaded and the sound worked flawlessly. 

hope this helps somebody, sorry for the double post if I made it.

cheers, keep up the good software going, Ubuntu! :popcorn:

I would like to try this, but when I go sudo update-grub, the menu.lst doesn't change. I tried removing it from the grub folder and running the update-grub command after, but no new menu.lst was there, so I just put the old one back so that I don't screw up my booting.
Do you know how to get the new menu.lst to generate?

---

### Post by neo_ritz on 2009-11-11
> **mzilhao said:**
> this may help: 
[https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/449762]("https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/449762")

see if you can get your sound working after
```
sudo alsa force-reload
```

if it works, try removing the package "sl-modem-daemon".
it worked for me...

THis worked!
I followed both steps,
```
sudo alsa force-reload
```
 and 
```
sudo apt-get remove sl-modem-daemon
```

Thanx

---

### Post by jarrarist on 2009-11-13
> **neo_ritz said:**
> THis worked!
I followed both steps,
```
sudo alsa force-reload
```
 and 
```
sudo apt-get remove sl-modem-daemon
```

Thanx

worked like a charm for me too, I had to upload grub first.

Thanks alot

---

### Post by That new guy on 2009-11-16
Hiya!!! Just want to say that I had this problem as well. The fix I just used was quite simple. I upgraded to grub 2, and made sure I was booting the upgraded kernel (which it wasn't doing by default) and BAM! its all good people!

Hope this works for you also! Good Luck!!!

Oh BTW I used synaptic to upgrade grub....

---

### Post by goodtimetribe on 2009-12-03
> **aval57 said:**
> Kernel must to be **2.6.31-14** according to[ https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816")

Thanks for the post, though.  I had the same problem (aplay: device_list:223: no soundcards found...) but after reading your post I realized that I had elected not to update ***/boot/grub/menu.lst*** during the upgrade so as not to mess with my XP dual-boot setup, and grub was still loading the previous kernel (2.6.28-13).

Alsa now runs fine after fixing menu.lst to load the 2.6.31-14 kernel (just as you said!). For others who may be interested, first confirm whether you have the wrong kernel```
$ uname -r
```then backup your current menu.lst and auto-generate a new one, which should add entries for the new kernel
```
$ sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.orig
$ sudo update-grub

```In my case I had to re-customize it for dual-boot by pasting in my previous XP entry from  */boot/grub/menu.lst.orig.*

-Bahman

awesome. you saved my KDE life.

thanks :)

---

### Post by garvinrick4 on 2009-12-03
Did 3 installs or upgrades to 9.10 and this worked each time. 9.10 Just have to do
Part A. Just follow instructions. Reboot when done. 

sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio


Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)
All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.
9.10
1. Backup (and then delete) your previous configuration files:
Code:

$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf

Warning: As always, use caution when removing files on your system. Any typos can potentially cause data loss.
Note: Don't worry if some of these files did not exist on your system.


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:
Code:

$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

3. Ensure the evil "libflashsupport" library is not installed:
Code:

$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound

Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks!

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
Note: Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

Note: If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
Code:

$ pulseaudio & pavucontrol

6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):

Code:

$ alsamixer -Dhw

Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.

7. Continue to Part B if you are running Hardy Heron (8.04), or Part C if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect!
__________________
Remember hence where you come and pass it down.
Last edited by garvinrick4; 17 Hours Ago at 11:10 PM.. Reason: This I found and Copied and Pasted it to you all.

---

### Post by beercz on 2009-12-04
> **garvinrick4 said:**
> Did 3 installs or upgrades to 9.10 and this worked each time. 9.10 Just have to do
Part A. Just follow instructions. Reboot when done. 

sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio


Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)
All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.
9.10
1. Backup (and then delete) your previous configuration files:
Code:

$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf

Warning: As always, use caution when removing files on your system. Any typos can potentially cause data loss.
Note: Don't worry if some of these files did not exist on your system.


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:
Code:

$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

3. Ensure the evil "libflashsupport" library is not installed:
Code:

$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound

Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks!

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
Note: Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

Note: If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
Code:

$ pulseaudio & pavucontrol

6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):

Code:

$ alsamixer -Dhw

Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.

7. Continue to Part B if you are running Hardy Heron (8.04), or Part C if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect!
__________________
Remember hence where you come and pass it down.
Last edited by garvinrick4; 17 Hours Ago at 11:10 PM.. Reason: This I found and Copied and Pasted it to you all.

Thanks garvinrick4

This fixed the no sound issue on my daughter's laptop.

Much appreciated!!

---

### Post by Satendra.kohli on 2009-12-04
> **sharky6000 said:**
> Firstly, I suggest moving your .pulse to a separate directory rather than removing it, in case that doesn't solve the problem: 

```

mv ~/.pulse ~/.old-pulse

```And.. it didn't work for me. :( 

thuleni: do you have an Intel HDA card as well?

dfg

---

### Post by garvinrick4 on 2009-12-04
You are welcome beercz. Thanks for posting it was considerate of you.

---

### Post by Druegan on 2009-12-04
As a last ditch for those of you who might still be stuck..

I tried everything that I could find on half a dozen forums to get sound back working after the upgrade to 9.10.. apparently the Koala likes it quiet..  

This is *not* a fix for the Intel HDA problem.. nor is it a particularly "optimal" solution, as I'm a newbie too, and don't know much of what I do..

But basically, after the better part of 14 hours of futzing with my box, I just gave up and uninstalled every "sound" related package in Synaptec that I could without breaking the desktop..   Then I just reinstalled all the ALSA and Gstreamer plugins, and miraculously, I has music now.

So, if yall get stuck to where nothing seems to help... you can always try that.  *shrugs*

---

### Post by cleary on 2009-12-14
for me it was a simple matter of unmuting and turning the volume up on the Mono channel - unfortunately the new sound preferences dialog doesn't give you this capability any longer, so I used alsamixer:

run it with:
```
alsamixer
```

arrow to the right until you get to the Mono channel
* hit M to unmute (this was the bit that is easy to miss, since the volume still goes up, even though it's still muted)
* hit up arrow to turn the volume up

In the sound preferences, under the Hardware tab, my Profile was set to Analog Stereo Output.

Screenshot attached

---

### Post by nextstepusr33 on 2009-12-29
Hello everyone!, I upgrade today, first the mouse cursor did not work, so I hacked to get it to work, my sound is also not working!I do have an Intel HD audio, it seems Ubuntu 9.10 is quite buggy and it indeed needs a group of people to post bugs for the community, it does seem ridiculous that an open-source Operating System is not being constantly updated to rid such bugs.

No sound, and the Intel GPU drivers don't work!, by far this is a buggy release, just like Windows Vista!!!](*,)]

---

### Post by biodagar on 2010-01-01
I searched the forums for a whole day looking for a solution that worked and removing the pulseaudio was the ONLY thing that did!! Thank you so, so much!!

For context I have an SiS 7012 soundcard that was a total fail after upgrading to KK, so I'm enormously grateful for this fix!!! :)

---

### Post by restless on 2010-01-02
hey,

i tried this method to fix my sound but it did not work.
when i first installed KK the sound of the system was ok, but not in media player. i installed banshee and i could play mp3s and videos.
than i installed pulseaudio following the method described above and now even banshee is not working.

any ideas on what i'm doing wrong?
thanx
Lor

p.s. also...it doesn't find any hardware in the sound preferences..which might be the main problem :p
but this is the output of 

:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by wiggie on 2010-01-02
I followed the instructions provided by garvinrick4. The difference for me was that I didn't have libflashsupport installed. 

I believe the important information was the muted PCM channel in alsamixer. I unmuted it and it worked just fine. I also used the
```
$ alsamixer -Dhw
``` command.

Cheers

---

### Post by restless on 2010-01-02
thing is that my alsamixer doesn't show the mono or pcm channel

I attached my alsamixer view, and the channels with the bars are the only one for which i can increase the volume.

after completely remove pulseaudio, now banshee works, but still no sound from movie player...

thank you
Lor

---

### Post by alexela on 2010-01-15
> **mzilhao said:**
> this may help: 
[https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/449762]("https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/449762")

see if you can get your sound working after
```
sudo alsa force-reload
```

if it works, try removing the package "sl-modem-daemon".
it worked for me...

updated grub, to grub 2
reloaded alsa
sudo alsa force-reload
worked for me
(had the same problem after upgrade)

---

### Post by Abdus on 2010-01-22
> **aval57 said:**
> Kernel must to be **2.6.31-14** according to[ https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816") [...]

Thank you, that solved my problem perfectly - I too chose to save old menu.lst during upgrade and forgot to update it later. Excellent, helpful post.

---

### Post by GonzaloFerreyra on 2010-01-29
> **nextstepusr33 said:**
> Hello everyone!, I upgrade today, first the mouse cursor did not work, so I hacked to get it to work, my sound is also not working!I do have an Intel HD audio, it seems Ubuntu 9.10 is quite buggy and it indeed needs a group of people to post bugs for the community, it does seem ridiculous that an open-source Operating System is not being constantly updated to rid such bugs.

No sound, and the Intel GPU drivers don't work!, by far this is a buggy release, just like Windows Vista!!!](*,)]


Hello everyone, I'm still stuck with the same problem with Intel HD Audio...
I did a fresh install of Karmic Koala but I didn't get the GPU drivers to work with GNOME so I decided to try kubuntu 9.10, installing it via aptitude install..... over the fresh installation. Everything was fine except for the 'quiet' thing :) ....

I tried every suggestion that I read on this forum and a few more except upgrading the kernel, but I'm still without sound...

```

lspci -v:

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
        Subsystem: Intel Corporation Device 0037
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fe420000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

uname -r
2.6.31-17-generic


```

Did anyone get this solved in any way with hardware like this?????? I don't have more ideas to fix it....

Thanks a lot

Gonzalo

---

### Post by dennisvanderpool on 2010-02-20
Hi,

Thanks for sharing the information! :smile: I had the same issue after upgrading from 9.04 to 9.10. Problem was that i had to use lilo instead of grub because of faulty bios. (Targa Traveller 1576 X2 Laptop with HDA Intel soundcard.  Grub was updated but lilo not so i was using old kernel. After modifying lilo.conf to use kernel vmlinuz-2.6.31-14-generic the problem was solved and i got sound again (after working with laptop without sound since 9.10 release...) I'm still using pulse audio instead of Alsa.

dennis@dennis-laptop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfdfb8000 irq 23

dennis@dennis-laptop:~$ lspci | grep -i audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

Thanks,

Dennis

---

### Post by nanosaw on 2010-02-22
I have same problem. All step already have tried, but still no sound. Until I try plug in earphone/headphone and press Fn+mute function on my laptop keyboard, in my Axioo notebook are Fn+F3, then the sound come back.

SOLVED

---

### Post by NikolaiRach on 2010-03-17
You Just need to reconfigure/Reinstall your alsa-driver, alsa-utils and alsa base.
It is quite simple...
You can just reinstall your current alsa driver or you can install the latest one, the v-1.0.22.1.
I had the same problem, and by doing it I have solved all problem related to this issue.
Here you have how to do it
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

---

### Post by skag on 2010-05-07
> **aval57 said:**
> Kernel must to be **2.6.31-14** according to[ https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456816")

Thanks for the post, though.  I had the same problem (aplay: device_list:223: no soundcards found...) but after reading your post I realized that I had elected not to update ***/boot/grub/menu.lst*** during the upgrade so as not to mess with my XP dual-boot setup, and grub was still loading the previous kernel (2.6.28-13).

Alsa now runs fine after fixing menu.lst to load the 2.6.31-14 kernel (just as you said!). For others who may be interested, first confirm whether you have the wrong kernel```
$ uname -r
```then backup your current menu.lst and auto-generate a new one, which should add entries for the new kernel
```
$ sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.orig
$ sudo update-grub

```In my case I had to re-customize it for dual-boot by pasting in my previous XP entry from  */boot/grub/menu.lst.orig.*

-Bahman

thnx.... my sound was fixed... but another problem came up.... a problem with my nautilus :S i cant see the upper part of the window (so i cant drag it or close it with the x button etc....) :S any answers?

---

### Post by maggiemonic on 2010-10-24
> **mzilhao said:**
> this may help: 
[https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/449762](https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/449762)

see if you can get your sound working after
```
sudo alsa force-reload
```if it works, try removing the package "sl-modem-daemon".
it worked for me...


my sound card was unrecognized after a reboot. this did the trick. thank you!!

---

### Post by petru.marginean on 2012-07-17
closing this issue

---

### Post by oldos2er on 2012-07-17
Closed. Please don't bump old threads.

---

