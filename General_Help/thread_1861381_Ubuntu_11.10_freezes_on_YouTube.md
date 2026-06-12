---
title: "Ubuntu 11.10 freezes on YouTube"
date: 2011-10-15
forum: General Help
---

### Post by bobtheflyingmonkey on 2011-10-15
Hi, I'm using Ubuntu 11.10 and every time I try to watch a YouTube video, it freezes and I have to restart my computer. I've tried it on Unity, Unity 2D, Gnome, and Gnome Classic and it freezes on all of them. I do have flash aid enabled, and I'm using firefox.

---

### Post by bobtheflyingmonkey on 2011-10-15
Seriously? Can anyone help? I've had to force my computer off and restart it 7 times within the last 5 hours because of this.

---

### Post by nomtv80 on 2011-10-15
It does for me too! However it didn't freeze on an embedded youtube video from another site?  It happened before the upgrade too. Not sure if a flash player issue, or what at them moment!?

---

### Post by SeaHawk22 on 2011-10-15
Sorry I dont have better advice than this, but have you tried watching youtube in another browser like Chrome? I am just suggesting to pin point the problem since I believe there is an updated Firefox included in 11.10.

EDIT
I ask this because Firefox freezes on videos for me too on 11.04, but I have yet to have it happen in Chrome.... I have no idea why.

---

### Post by bobtheflyingmonkey on 2011-10-15
Well, for me, it freezes on any browser, even on embedded videos.
The ONLY time I can get it to load a video without freaking out is on XMBC.

---

### Post by studon on 2011-10-18
I am also having Flash cause computer to freeze - happens regardless of browser (Firefox or Chrome). 

Computer is a Lenovo S12 ion. Under 11.04 flash would occasionally cause system to freeze but nothing like 11.10 where it would now be the expected behavior.

I should note certain youtube videos will play without problems however others will cause freeze. Even where videos will play successfully if you are then to begin jumping between them - either by back/forward through browser history, or clicking video link - then Flash problems will occur (sometimes audio will play, but screen will freeze). 

When freeze occurs it is sometimes necessary to force shutdown by holding power button. On other occasions it is possible to restart x with key combo however even when this is possible computer will not play video files again without a restart.

Installing latest Flash beta hasn't made any difference (nor has blocking Cookies from youtube -  I saw this as a suggestion to problems some people were having with video playing pink/red under Flash 10.2 so tried more in hope than expectation...). Clearing Flash cache makes no difference...

Operating system was updated rather than fresh install. 

Additional to problems with Flash I am finding system theme does not always load successfully on login and unity requires a restart after login each time to get hot corners working (or rather this is the quickest way to get them working again. If you change them under ccsm from normal preference setting to an unused screen edge, and then back again; it is not enough to unselect and reselect the corner, then they will start working again until next login).

I'm am in process of updating another S12 so will be interested to see if same problems present themselves on that machine.

---

### Post by studon on 2011-10-19
So rather than updating the second S12 I did a fresh install and Flash seems fine. That being the case and after a bit of thinking I've now deleted /etc/adobe/mms.cfg from the first S12. While I may be premature in reaching a verdict Flash now seems to be working correctly. 

As latest updates have also sorted Unity problems with hot corners 11.10 is now looking much better this evening (now I need to work out why touchpad on S12 number 2 has frozen a couple times...).

---

### Post by barbarian on 2011-10-24
For me too. Some youtube tracks cause entire system freeze, besides cursor. The only way out - cold reboot. Crtrl+Alt+F1 doesnt work either.

GPU - Nvidia 8400m

---

### Post by Angelus-Michael on 2011-10-24
[COLOR=RoyalBlue]***Try Chromium.***[/COLOR]

---

### Post by barbarian on 2011-10-24
[not Fixed] Flash-Aid firefox extension was installed an then STABLE flash renewed from repositories.

Sometimes it happens, by the way, on Chromium hangs also

---

### Post by LADmaticCA on 2011-10-25
Any more suggestions? I still never solved this problem on my maverick install.

---

### Post by geiroffenberg on 2011-11-02
Any solutions?
This recently began to happen on my ubuntu 11.10 upgraded, and on my wifes 11.04 laptop, the same day. Never happened before, but now 2-3 times during a movie. Only solution is to totally shut system down trough power off, and then start it again. It happens on any flash streaming, not only youtube. Many of the suggestions can be ruled out, it has nothing to do with 11.10 or with firefox, it has to do with streaming flash videos. Since it just now began to happen, it is probably because of some recent update done by system. If someone has a real clue, pls tell us about it, thanks.

*edit1 just noticed that it hasn't happened unless it is playing in full screen, but it doesnt matter what flash player it is.

---

### Post by pqwoerituytrueiwoq on 2011-11-02
sometimes if i hit the back button wile youtube is playing it freezes everything but my mouse (can't even get to a tty may be able to via ssh on another system though)
using 10.04 on my rig (specs in sig)

---

### Post by sarahlizz3 on 2011-11-29
I'm having the same problem.  I've tried Chrome, Chromium, and Firefox.  I will try to play a flash video (like YouTube) and it will hang.  I haven't had to restart the entire computer, just have to kill the browser or tab. 

I've tried re-installing flash and installing the beta version. I also installed a Firefox add-on that is supposed to figure out if you have the right version of flash (Flash-Aid).

Nothing seems to be working.  Any ideas?

I'm on 11.10; I also did an upgrade and not a full reinstall.  I'd really rather not just reinstall it because I have my Virtual Box set up with Win7 and Dreamweaver and a whole bunch of web files downloaded to this computer (e.g. it is a huge pain in the butt to reinstall)

---

### Post by holycow131415 on 2011-11-29
> **sarahlizz3 said:**
> 
I'm on 11.10; I also did an upgrade and not a full reinstall.  I'd really rather not just reinstall it because I have my Virtual Box set up with Win7 and Dreamweaver and a whole bunch of web files downloaded to this computer (e.g. it is a huge pain in the butt to reinstall)

If reinstall is the solution, you can backup your virtual hard drive from your virtual machines so that you dont need to reinstall windows, etc.

---

### Post by sarahlizz3 on 2011-11-29
> **holycow131415 said:**
> If reinstall is the solution, you can backup your virtual hard drive from your virtual machines so that you dont need to reinstall windows, etc.

I've yet to be able to figure that out - I think the one time I looked into it, the instructions were complicated and time consuming.  I'm currently working too many jobs, so the amount of free time I have to mess around with this is minimal.

---

### Post by holycow131415 on 2011-11-29
> **sarahlizz3 said:**
> I've yet to be able to figure that out - I think the one time I looked into it, the instructions were complicated and time consuming.  I'm currently working too many jobs, so the amount of free time I have to mess around with this is minimal.

Just go to the directory that your vm hdd is saved, copy it and paste it somewhere else (like a flash drive). then when you are ready, just copy and paste it back when you are done wiping the system.

You can find the location by going to File > virtual media manager. Click on the .vdi file and below in the window it shows the full path to where it is located.

Or you can export your VM as an appliance, and import it back.

[http://www.virtualbox.org/manual/ch01.html#ovf](http://www.virtualbox.org/manual/ch01.html#ovf)

---

### Post by rahduke on 2011-12-14
I'm having the same issue, updated to 11.10 and flash is totally haywire. causes total system freezes, can't skip forward or rewind any flash video. Flash video randomly causes complete screen lock with no ability to drop into console, restart x or forcekill. Can someone look into this?

---

### Post by jimmydean886-2 on 2011-12-14
This is often an evident problem on older computers.
Either try an upgrade, or switching drivers (BE CAREFUL WITH AMD/ATI DRIVERS! THEY DON'T ALWAYS WORK)

---

### Post by KFwLsKvVAs on 2012-01-06
I'm having the same problem.  It started with 10.10, then persisted through the upgrades to 11.04 and 11.10.  Luckily I ditched Unity and switched to Fluxbox, which doesn't cause the entire system to seize up when this occurs.  Best case scenario is I close the tab with the offending video, the system hangs for a few seconds, then everything runs smoothly.  I'd like to know what's causing this and if there is any solution, since it is fairly obnoxious.  

Also, youtube videos play perfectly fine in Minitube.

---

### Post by ktucker5301 on 2012-01-17
any browser same issue:

A brief hang of a few seconds, followed by a kill option, clicking wait will allow the video to load. annoying. just started today. did not happen yesterday. sheesh. also this morning woke up to a system that was frozen, had to cold boot. never had this problem in 10.10 or 11.04 - this release seems premature
bump

---

### Post by thinkinhurtz on 2012-02-04
bump.
I am also consistently having complete system freezes using Firefox with YouTube on Ubuntu 11.10. I have also tried Chromium to no avail. After 10 minutes of YouTube I am forced to reboot.

No visible solutions here... anyone got any ideas?

---

### Post by oakdog8 on 2012-02-06
I too experience full system freezes after about 10 mins of flash video. I dug through some X logs and saw it was Nvidia drivers hanging, so I wasn't totally sure, but I have not experienced a single freeze since uninstalling Flash about 2 weeks ago. It is a highly frustrating issue since so much of the internet still uses Flash. I have not been able to find a working solution.

---

### Post by jejones3141 on 2012-02-20
I am having this problem as well. I've found one video that appears to be a sure kill: on YouTube, search for "stella splendens" and then play the Qntal video for the song. The URL, as best I can transcribe it, is [http://www.youtube.com/watch?v=KQSqaoj21pU](http://www.youtube.com/watch?v=KQSqaoj21pU) (I provide the search just in case my bad eyes didn't get the v= parameter right in the URL--could that be KQSqaoj2lpU?). One thing I note before the freeze: I can click pause, but the video doesn't stop playing.

This is on Ubuntu 11.10 64-bit, and I was running Google Chrome.

flashplugin-installer version: 11.1.102.62ubuntu0.11.10.2
nvidia-current version: 280.13-0ubuntu6

Has anyone seen this happen with the 290.10 nvidia driver installed?

---

### Post by oren tal on 2012-02-26
Me,

I have the same problem with google chrome and chromium.

Surprisingly it does work for me in opera.

But when it freeze the whole OS freeze and I have to do hard reset.

I really hope that they will do the next version ubuntu 12.04 far more stable and will focus on that.

Both 11.04 and 11.10 are notoriously known for being less stable than windows, at least they were for me less stable than windows.

With all the new feature canonical forgotten that the most important thing for the end user is stability and security.

---

### Post by AlmightyMokona on 2012-03-22
been having same problem...

---

### Post by imachavel on 2012-03-22
if youtube freezes, it's a flash error. But there was a previous thread about this, it strangely has something to do with a library that flash uses that obviously is not the same in windows. There are quite a few plug ins that seem to malfunction lately with ubuntu, I can watch any youtube video with google chrome or firefox. Not sure of malformed lines with the program that uses the java back end that I believe flash streams in on. Well I'm a newb with this and linux, but let's get to work now

open a terminal

ctrl+alt+t

now let's try first for diagnostic purposes the video driver, which won't correctly show the video codec, but none the less let's take a look with this command:

sudo lshw -c display

here is mine:

*-display               
       description: VGA compatible controller
       product: RV730XT [Radeon HD 4670]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:43 memory:c0000000-cfffffff memory:dfdf0000-dfdfffff ioport:dc00(size=256) memory:dfe00000-dfe1ffff

now let's try:

sudo apt-get remove flashplugin-nonfree

now close your browser, and try:

sudo dpkg -i install_flash_player_10_linux.deb

or sudo apt-get install flashplugin-nonfree if the debian flash plug does not seem to work. Now open back up chrome AND firefox browsers and in each browser try watching a youtube video again. Also let's be clear an update won't hurt anything

sudo apt-get install update

if that still doesn't work, the problem is deeper in the back end libraries

---

