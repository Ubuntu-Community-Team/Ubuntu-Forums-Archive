---
title: "Random Artifacting"
date: 2010-09-19
forum: General Help
---

### Post by SquidLord on 2010-09-19
So I notice randomly, my ATI 5870 likes to artifact at random times forcing me to restart. I think I tried to go on the right path and restart X, but it gets stuck checking the battery status of my backup battery.

[THIS](http://dl.dropbox.com/u/1065652/corrupted%20video.png) is what I mean by artifacting. This happened after the mouse looked funky, and then I clicked and dragged [as if highlighting things] and swirled my mouse around the desktop. It makes things highly unreadable and I'm not sure what causes it.

---

### Post by robsoles on 2010-09-20
It looks like your display memory is being mishandled and corrupted. Please have a good poke through the BIOS settings for the computer (access during Power On Self Test by pressing [Delete] or [F1] or [F2] or consult manual :)) and see if you can find options regarding shared memory space or re-mapping.

If you spot options and care to 'have a play' then take note of what you are changing just in case it makes anything worse and try booting with your changes - if not then please notate options available and paste them here.

There is some chance that the memory in use for your display is faulty or perhaps it is badly mapped and the display and something else are fighting over it, just as good a chance I am completely wrong but we can only prove anything by trying something.

---

### Post by SquidLord on 2010-09-21
Took a stroll through my BIOS and found nothing concerning shared memory [XFX 750i]. I feel it important to state that Windows doesn't find any problems with extended use [no BSOD's, no awkward errors, games run fine, Windows graphics work fine]. Could it be a heat issue? It does get pretty hot in the room the computer's in. Though it does stay relatively cool while idle on the desktop [45C while in a room with cooling problems (better than the 70C of my old 9800GX2 haha)].

---

### Post by robsoles on 2010-09-22
Are you using proprietary drivers (from manufacture, referred to usually as 'restricted') or are you using native drivers? (If nothing has prompted you about it then you are using the native driver from Canonical).

---

### Post by SquidLord on 2010-09-22
I manually installed 10.6 at one point.

---

### Post by robsoles on 2010-09-22
> **SquidLord said:**
> I manually installed 10.6 at one point.

Please specify the package you installed which was '10.6'.

Did you successfully remove that?

In "Synaptic Package Manager" does anything ""ATI"" come up if you put 5870 into the search/filter box?

---

### Post by SquidLord on 2010-09-23
Oh, the 10.6, is the [*Catalyst Display Driver v10.6*](http://support.amd.com/us/gpudownload/linux/10-6/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=us&rev=10.4&ostype=Linux%20x86_64) from ATI's site. Also, nothing shows up in Synaptic when 5870, 5800 or 58XX is searched for.

---

### Post by robsoles on 2010-09-24
Would you do us both a favour and try booting this machine from LiveCD to choose 'try ubuntu without changing anything on my computer' (or whatever exact terminology).


Start the browser, start anything else you can see in the LiveCD desktop that you care to play with and have a play for a while - see if you can get it to artifact from the LiveCD, lemme know result(s) please.

---

### Post by SquidLord on 2010-09-24
Thanks to my ingeniousness, I completely dicked the drivers. I tried to update to the latest 10.9 and failed, now I've got a new set of problems with installing the drivers. I can get the 10.9 'run' file to generate the distribution specific packages, but upon install of the generated packages I receive errors claiming that 'fglrx' is not installed. I attempted "sudo apt-get install fglrx" and now I'm getting errors claiming that fglrx is not configured.

---

### Post by robsoles on 2010-09-24
Can you post the entire message relating to the fglrx error? I find the majority of error messages give strong clues as to how to recover from the error.

---

### Post by SquidLord on 2010-09-25
Alright, first I generated the distro specific packages with "sudo sh ati_10.9.run --buildpkg Ubuntu/lucid". Then I attempt to install all of those packages with "sudo dpkg -i fglrx*.deb" and after everything appears to go fine with the install I get:

```
Error! Bad return status for module build on kernel: 2.6.32-24-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
dpkg: error processing fglrx (--install):
subprocess installed post installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
fglrx-amdcccle depends on flgrx; however:
Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
fglrx-dev depends on fglrx; however:
package fglrx is not configured yet.
dpkg error processing fglrx-dev (--install):
dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.771-0ubuntu1) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for pything-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Processing triggers for pything-support ...
Errors were encountered while processing:
fglrx
fglrx-amdcccle
fglrx-dev
```

Upon boot, my monitor fails to recognize any signal from the computer.
On an interesting note, if I run the .run file with "./ATI_10.9.run" and use the graphical installer, I get errors saying it couldn't install the DKMS or something of the such. This method of installing, has no issues with the DKMS.

---

### Post by robsoles on 2010-09-25
> **robsoles said:**
> Would you do us both a favour and try booting this machine from LiveCD to choose 'try ubuntu without changing anything on my computer' (or whatever exact terminology).


Start the browser, start anything else you can see in the LiveCD desktop that you care to play with and have a play for a while - see if you can get it to artifact from the LiveCD, lemme know result(s) please.


Please tell me what it can manage from the LiveCD.

---

### Post by SquidLord on 2010-09-27
Yesterday I ran my system from the LiveCD and could not recreate the artifacting. It's a rather random thing.

---

### Post by SquidLord on 2010-10-01
bump?

---

### Post by robsoles on 2010-10-01
While booted from the LiveCD did you try stuff like changing resolution? Was there anything about the video output that was negative?

> **SquidLord said:**
> Alright, first I generated the distro specific packages with "sudo sh ati_10.9.run --buildpkg Ubuntu/lucid". Then I attempt to install all of those packages with "sudo dpkg -i fglrx*.deb" and after everything appears to go fine with the install I get:

```
Error! Bad return status for module build on kernel: 2.6.32-24-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
dpkg: error processing fglrx (--install):
subprocess installed post installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
fglrx-amdcccle depends on flgrx; however:
Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
fglrx-dev depends on fglrx; however:
package fglrx is not configured yet.
dpkg error processing fglrx-dev (--install):
dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.771-0ubuntu1) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for pything-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Processing triggers for pything-support ...
Errors were encountered while processing:
fglrx
fglrx-amdcccle
fglrx-dev
```Upon boot, my monitor fails to recognize any signal from the computer.
On an interesting note, if I run the .run file with "./ATI_10.9.run" and use the graphical installer, I get errors saying it couldn't install the DKMS or something of the such. This method of installing, has no issues with the DKMS.

If you have a list of everything that the "sudo dpkg -i fglrx*.deb" command installed (or failed to or couldn't configure) and you can successfully uninstall each one (or it isn't there due failure to install) and then use apt-get or aptitude to install the simile stuff from the repository then you might be in a position to tackle the reason you were trying to dpkg this stuff at all in a different way than you have this time.


Do you know how to preserve your /home folder while reinstalling? (It's likely quicker and surer to reinstall at this point)

What was it that drove you to mucking around with these drivers? ([www.google.com/search?q=ATI+5870+ubuntu](www.google.com/search?q=ATI+5870+ubuntu) told me some stories!)

---

### Post by SquidLord on 2010-10-03
I just used it like I would usually use my computer before the artifacting would occur and I got no negative results.

Here are the packages I was attempting to install with dpkg
```
fglrx-amdcccle_8.771-0ubuntu1_amd64.deb
fglrx-dev_8.771-0ubuntu1_amd64.deb
fglrx-installer_8.771-0ubuntu1_amd64.deb
fglrx-modaliases_8.771-0ubuntu1_amd64.deb
fglrx_8.771-0ubuntu1_amd64.deb
```

I have tried uninstalling [by following a few commands to completely remove everything to prep for a new install] but I haven't tried "sudo apt-get install"'ing anything.

The only way I know how to preserve the home folder is by putting it on a different partition entirely [partition for '/' and partition for '/home' and a partition for 'swap']. Unfortunately I don't have it set up that way.

Well, I was hoping upgrading to a newer revision of the drivers would fix the artifacting, so I tried it out. I thought this would be simple since it was so simple to upgrade the previous versions.

---

### Post by robsoles on 2010-10-03
The 10.04 installer will allow you to reinstall 'around' existing items if you persist with mounting old partitions (or LVM) and not formatting them - it will whinge that installing system files without formatting may make an unstable system but if you persist past that it will clear the directories it needs to clear (not /home) and then install nicely enough.

As it runs neatly enough off the LiveCD I think you can very likely achieve usable (even likeable) results using Canonical Open Source driver(s) for your video - before reinstalling (or trying much else) can I encourage you to see if you can get usable drivers out of 'System'->'Administration'->'Synaptic'?

---

### Post by SquidLord on 2010-10-11
After, backing up some files and reinstalling and using the Canonical drivers, on day 2 and no fiddling around with anything, I find it artifacting again. I believe at this point it's just ATI's awful coding reputation [for Linux distros] living up to standards.

---

### Post by robsoles on 2010-10-11
What does 'System'->'Administration'->'Hardware Drivers' offer you? Have you taken any drivers via that method?

---

### Post by SquidLord on 2010-10-12
There is no 'Hardware Drivers', there is "Additional Drivers" though. Examining that shows that those drivers are "active" currently.

---

### Post by robsoles on 2010-10-13
Where about, in which menu, are you finding 'Additional Drivers'?

What drivers are listed in 'Additional Drivers'?

Did the system prompt you about these or did they just install 'behind your  back'?

---

