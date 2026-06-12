---
title: "Adobe Flash Player in Ubuntu 10.04 LTS"
date: 2010-05-05
forum: General Help
---

### Post by rasfl3 on 2010-05-05
Hi. I recently installed a clean copy of Ubuntu 10.04 LTS. I've noticed that flash movies and videos tend to lag, the sound play normally although the video lags. I have tried uninstalling and reinstalling flash but that has been to no avail. Can anyone help me resolve this issue. Thanks!

---

### Post by uRock on 2010-05-05
> **rasfl3 said:**
> Hi. I recently installed a clean copy of Ubuntu 10.04 LTS. I've noticed that flash movies and videos tend to lag, the sound play normally although the video lags. I have tried uninstalling and reinstalling flash but that has been to no avail. Can anyone help me resolve this issue. Thanks!

If you are using 64bit, you may want to check the link in my sig.

---

### Post by spayman on 2010-05-05
[SIZE="4"]I have the 32bits version :)
**SAME PROBLEM !!!**
flash videos > full screen > LAGG =([/SIZE]

---

### Post by uRock on 2010-05-05
> **spayman said:**
> [SIZE=4]I have the 32bits version :)
**SAME PROBLEM !!!**
flash videos > full screen > LAGG =([/SIZE]
How did you install your 32bit flash? You can also use the app in the link in my sig to install 32bit flash.

Please use regular fonts.

---

### Post by spayman on 2010-05-05
[B]dude :)
installed with the terminal 
reinstalled from their main site , nothin changes :KS:KS:KS:KS:KS[/B]

---

### Post by Vaphell on 2010-05-05
run **top** in terminal while playing some flash and see if the cpu is maxed out.

---

### Post by uRock on 2010-05-05
Which way via terminal? The version in ubuntu-restricted-extras is crappy, even on 32bit. Which site, Adobe?

---

### Post by rasfl3 on 2010-05-05
I attempted to install it from the Adobe website and from the Ubuntu Software Center. Nothing changed.

---

### Post by uRock on 2010-05-05
> **rasfl3 said:**
> I attempted to install it from the Adobe website and from the Ubuntu Software Center. Nothing changed.
Are you using 64bit or 32bit? The link in my signature will use a different method that works great for 64bit. I recently installed it via the app in the link and it works great.

---

### Post by QIII on 2010-05-05
rasfl3 --

Are you using Compiz?

---

### Post by rasfl3 on 2010-05-05
Yes, I am. But the issue was occurring before Compiz was installed.

---

### Post by uRock on 2010-05-05
> **spayman said:**
> [B]dude :)
installed with the terminal 
reinstalled from their main site , nothin changes :KS:KS:KS:KS:KS[/B]
I just installed via the app in my link on a 32bit Lucid system. I used the button for Flass Beta which installs a version not shown on Adobe's site. Though it still ate a lot of CPU on the netbook, it ran smooth and never became choppy like the versions on the Adobe site and the two offered in synaptic package manager.

---

### Post by uRock on 2010-05-05
> **rasfl3 said:**
> Yes, I am. But the issue was occurring before Compiz was installed.
Are you using 64bit or 32bit?

---

### Post by rasfl3 on 2010-05-05
32 bit.

---

### Post by uRock on 2010-05-05
Pleas give the app listed in this thread a shot. [http://ubuntuforums.org/showthread.php?p=9244819#post9244819](http://ubuntuforums.org/showthread.php?p=9244819#post9244819)
You will have to run a few commands to give the app permission to run. The way I did it was by downloading the app, placed it in the home folder then ran the following two commands to start the program. Once it is running, click the remove flash button first, let it do its thing, then when it says it is done you can click ton install the beta version which is running great for me on Lucid.
```
chmod +x adobe_flash_installer-ubuntu*
```
```
./adobe_flash_installer-ubuntu*
```

---

### Post by rasfl3 on 2010-05-05
It didn't seem to solve the problem and now my computer runs slow.

---

### Post by physic.dude on 2010-05-05
Re-install Ubuntu,
Are you duel booting?

---

### Post by Dilutu on 2010-05-05
What make of video card are you using? On my system with an ati 2600 , the only way for me to get flash playing decently is to use the fglrx driver.I wish I just could use the regular radeon driver coz apart from flash, it works better....

---

### Post by rasfl3 on 2010-05-05
...

---

### Post by rasfl3 on 2010-05-05
Nvidia GeForce

---

### Post by Dilutu on 2010-05-05
I also have a Nvidia Geforce mx 4000 that I switch with my ati to trouble shoot. Unfortunatly I cannot try it now ...

---

### Post by mick463 on 2010-05-05
> **rasfl3 said:**
> Hi. I recently installed a clean copy of Ubuntu 10.04 LTS. I've noticed that flash movies and videos tend to lag, the sound play normally although the video lags. I have tried uninstalling and reinstalling flash but that has been to no avail. Can anyone help me resolve this issue. Thanks!
I am running 64 bit and the flash works with google chrome really well so it must be a browser issue would like to hear from some one that knows what the issue is but until then i will use google chrome.

---

### Post by QIII on 2010-05-05
rasfl3 --

Can you go to Synaptic and see if you have swfdec or gnash installed?

They conflict with Flash.

---

### Post by mick463 on 2010-05-05
yes i am but that was installed after the adobe problem.and it dose not seem to have the features that it had in previous versions of ubuntu.The fire for one.

---

### Post by Nipas on 2010-05-06
I have the same problem (amd64).. Has anyone reported this as a bug?

---

### Post by uRock on 2010-05-06
> **Nipas said:**
> I have the same problem (amd64).. Has anyone reported this as a bug?
If you install the beta flass that isn't in the repo, your problem should go away.

---

### Post by mjleroux on 2010-05-09
> **spayman said:**
> [SIZE="4"]I have the 32bits version :)
**SAME PROBLEM !!!**
flash videos > full screen > LAGG =([/SIZE]
I have exactly the same problem with my 32 bit Ubuntu 10.04 LTS fresh install.  However, when I upgraded a virtual machine from 9.10 to 10.04, I did not have the problem.  Another virtual 10.04 fresh install does have that problem.  I have also tried un-installing, re-installing flash player but nothing works.  Very disappointing.  I hope someone can come up with a solution.  Thank you

---

### Post by uRock on 2010-05-09
> **mjleroux said:**
> I have exactly the same problem with my 32 bit Ubuntu 10.04 LTS fresh install.  However, when I upgraded a virtual machine from 9.10 to 10.04, I did not have the problem.  Another virtual 10.04 fresh install does have that problem.  I have also tried un-installing, re-installing flash player but nothing works.  Very disappointing.  I hope someone can come up with a solution.  Thank you
Have you tried turning off compiz?

---

### Post by mjleroux on 2010-05-11
> **rasfl3 said:**
> Hi. I recently installed a clean copy of Ubuntu 10.04 LTS. I've noticed that flash movies and videos tend to lag, the sound play normally although the video lags. I have tried uninstalling and reinstalling flash but that has been to no avail. Can anyone help me resolve this issue. Thanks!
I've managed to fix this by right clicking on the player, then clicked on settings and then took the tick out of "enable hardware acceleration", i.e.disable that option.  Woked for me.

---

### Post by ram130 on 2010-05-13
Just curious. For those with flash lag problem, what is your cpu usage like while watching a flash video?

---

### Post by oh4real on 2010-05-29
Thanks so much. Disable hardware acceleration did the trick. For full screen. Although it does run better in small mode with acceleration. 

It'd be nice if Flash had a screen mode conditional option.

---

### Post by Secrop on 2010-08-06
I've fixed this accidentally while trying to put blender3d working correctly with my ATI X1600, and Flash started to work correctly after that:

edit /etc/default/grub and change GRUB_CMDLINE_LINUX= "" to "nomodeset"
sudo upgrade-grub

after reboot everything worked like a charm!

---

### Post by ram130 on 2010-08-06
> **Secrop said:**
> I've fixed this accidentally while trying to put blender3d working correctly with my ATI X1600, and Flash started to work correctly after that:

edit /etc/default/grub and change GRUB_CMDLINE_LINUX= "" to "nomodeset"
sudo upgrade-grub

after reboot everything worked like a charm!

figured it out. Flash still lagging for me tho. Very high cpu.

---

### Post by gannggstaz on 2010-08-06
I play the flash files with vlc. Go to your filesystem to the /tmp directory. If you clicked the play button it will have a file named FLASHXX5IOAkY, or something similar. You can pause the in-browser video. Right click on that file, click open with... and select a media player of your choice. Make sure it's compatible with flash files. It will play as far as the video has downloaded in the browser. 
This may not fix the video-player in-browser, and watching videos this method take a little extra time, but you can also save the files from the /tmp directory. This only works with flash video, and only with media players compatible with flash (.flv)

---

### Post by DaveJ1337 on 2010-10-06
This has been affecting me off-and-on for a year or so, the problem seems to change with every upgrade or distro change.
 
I have an HTPC that pushes a 46" LCD, what I see most often is that after about 5 minutes or so, sometimes up to 20 minutes, Flash video will slow down to about 1 frame every 5 seconds. The sound "usually" keeps playing just fine, and it seems to be a problem with extremely high CPU usage from the Flash player.
 
Although i haven't been able to solve the problem, I HAVE been able to work around it to an extent. Since high CPU usage is at fault, I tried out a couple of LXDE-based distros to give Flash more CPU to work with. For the most part, it works and Flash plays a lot smoother while still hogging all the CPU in the world.
 
On the other hand, I love Gnome. Yesterday I switched back to Ubuntu(64bit) from the Mint-LXDE(32bit) I'd been using for months and after about 20 minutes into the Colbert Report the video started locking up again. Top reports the browser AND Flash eating every bit of CPU in sight, so now I'm back on the lets-fix-this bandwagon.
 
I'll be working on it a little tonight and I'll report back with anything I find. One thing to note is that I took the lazy route and installed ubuntu-restricted-extras to pull in Flash support, so the first thing I'm going to do is try different versions of Flash from different sources.
 
==Dave

---

### Post by davidvandoren on 2010-10-06
I had the same problem with fedora and my fix was to install opera.

For some reason Opera web browser plays the flash videos much better. 
Another thing you can do just ctrl and + to enlarge the flash video to the point where it's still running smooth.

---

### Post by ram130 on 2010-10-06
I guess I'm lucky since flash takes up 50% on mine playing normally but when I go 1080p it eats up 80% and full screen 98%..in windows, it eats up 40% in full screen..I have a core 2 duo with ATI graphics. Anyways Good luck.

---

### Post by DaveJ1337 on 2010-10-07
I did a lot of reading and a lot more experimenting last night, but I've found a couple of reasonable solutions for Flash performance problems.
 
First of all, Flash 10.2 is available via ppa: [http://www.webupd8.org/2010/09/adobe-flash-player-square-102-64bit.html](http://www.webupd8.org/2010/09/adobe-flash-player-square-102-64bit.html)
 
If any one thing I tried last night worked for me, it was this newever version of the 64-bit flash plugin.  It didn't come without it's drawbacks though, my screen stopped locking up randomly while watching fullscreen flash, but the video quality was noticably reduced.  With 10.1, I had silky-smooth video that would freeze my computer every 5 to 10 minutes and then continue being silky-smooth again.  With 10.2, I notice a bit of choppiness with the video but it will no longer freeze and is thus far more tolerable.
 
Something else to note is the ability of Flash to use the GPU for SOME of it's workload.  From what I've read, it's only using the GPU to scale the video from windowed to fullscreen (i.e. from 800x600 to 1280x1024).  It doesn't help the decoding process.  Furthermore, there is a strict set or criteria that OpenGL has to meet before the Flash plugin will even allow the GPU to be used.  Big-ticket items that will disable GPU accelleration are Compiz and open-source drivers like Nuovaeu and the excellent ATI driver.  Flash literally checks to see if open drivers are in use and disables use of the GPU, but luckily there's also a way to override flash's GPU validation that can be read about here: [http://blogs.adobe.com/penguinswf/2008/08/secrets_of_the_mmscfg_file_1.html](http://blogs.adobe.com/penguinswf/2008/08/secrets_of_the_mmscfg_file_1.html)
 
The last thing I will say for now, since I'm pressed for time on my lunch break, is that a large part of my problem was also the result of my CPU overheating while watching Flash video.  Clean up your heatsink and think about installing an exaust fan on the back of your desk if you have your computer tower shoved in a hole (desk, entertainment center, etc.).  
 
I'm sure I've forgotten something, but I'll update this as I remember more.
 
==Dave

---

### Post by desnaike on 2010-10-07
Hey guys I had the same problems 3-4 years ago I now after installing all my plugins flash included I copy the contents of usr/lib/mozilla plugins folder to each of my browser plugins folder in probably usr/lib and sometimes usr/share and even opt and have never had a flash issue since and this is with all the distros I use.

---

### Post by TBABill on 2010-10-07
If you continue to struggle for answers to Flash issues with a browser, search for posts and responses from user LovingLinux. He has helped literally hundreds of people with issues and can probably steer you in the right direction by following the threads where he has walked people from problem to solution. He also has links in his signature for various assistance steps as well.
 
Firefox optimization thread including Flash Optimization:
 
[http://ubuntuforums.org/showthread.php?t=1193567&highlight=flash](http://ubuntuforums.org/showthread.php?t=1193567&highlight=flash)

---

### Post by gesti on 2011-04-20
Hello,

I have struggled with this one for the past week or so. (next to other stuff)
So my system is: **ATI HD4850 on an ASUS P5Q3**
os: **Ubuntu 10.10 The Maverick Meerkat 64-bit** release.
The "glitch" was that I had running **black stripes** in the flash. (a good example for me was in Mafia Wars on facebook). Also sometimes the videos went kinda blank, if I switched to another tab in** Mozilla - Firefox**.

I have tried to disable some tool tips like others advised and also tried to switch hardware acceleration off, but had no such option.

So here comes my **solution**:

[LIST=1]
[*]Remove all the previous flash-players you have (make sure there is no libflashplayer.so in your Firefox plugins folder - /usr/lib/firefox-4.0/plugins/ )
[*]Download the [Adobe Flash Player "Square" Preview]("http://labs.adobe.com/technologies/flashplayer10/square/"). This is the flash player from adobe for 64-bit system users.
[*]After unpacking the tar, there is a **libflashplayer.so** file in it. You will need to **copy** this **in to /usr/lib/firefox-4.0/plugins**.
[*]Now just restart Firefox and then test it!
[/LIST]
I wrote firefox-4.0 as by now i assume that's what most of us are using. If not then of course you will need to go into the folder with the right version number.

Good luck and a happy tux to you all,
s

---

