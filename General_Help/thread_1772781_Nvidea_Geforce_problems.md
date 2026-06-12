---
title: "Nvidea Geforce problems"
date: 2011-06-01
forum: General Help
---

### Post by Virgil0211 on 2011-06-01
I've been trying to deal with screen tearing for a while now. It's primarily through the HDMI output to my tv. I'm a recent refugee from Windows 7, and I never experienced this problem when using the HDMI output there. I've already tried whatever solutions I could find online. No change. 

I'm using an MSI laptop with an Nvidia Geforce 8200M G video card, using Ubuntu 11.04.

I've been banging my head against a wall for the past couple of days trying to fix this problem. Any help I can get would be appreciated. 

Thank you.

---

### Post by DinoT1985 on 2011-06-01
Hi

have you tried these settings?

[http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu/](http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu/)

---

### Post by Virgil0211 on 2011-06-01
> **DinoT1985 said:**
> Hi

have you tried these settings?

[http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu/](http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu/)

Yeah. Didn't have any effect.

---

### Post by seawolf167 on 2011-06-01
Have you installed the hardware drivers? System -> Administration -> Hardware Drivers

If those are not working correctly, you can install and use the [proprietary drivers ]("http://www.nvidia.com/object/linux-display-ia32-270.41.19-driver.html")directly from Nvidia.

See if the drivers don't solve you problem, else report back!

---

### Post by Virgil0211 on 2011-06-01
> **seawolf167 said:**
> Have you installed the hardware drivers? System -> Administration -> Hardware Drivers

If those are not working correctly, you can install and use the [proprietary drivers ]("http://www.nvidia.com/object/linux-display-ia32-270.41.19-driver.html")directly from Nvidia.

See if the drivers don't solve you problem, else report back!

I tried downloading the proprietary driver, then followed the instructions from here ( [https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage) ), but it said that "nvidia-installer must be run as root". What do I do from here?

---

### Post by seawolf167 on 2011-06-01
> **Virgil0211 said:**
> I tried downloading the proprietary driver, then followed the instructions from here ( [https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage) ), but it said that "nvidia-installer must be run as root". What do I do from here?


Run it as root :P, add a *sudo* in front of your command

---

### Post by Virgil0211 on 2011-06-01
> **seawolf167 said:**
> Run it as root :P, add a *sudo* in front of your command

Which command is that? I double-clicked on the thing and clicked "run in terminal", as per the instructions I listed. 

I apologize. I'm still quite new at this.

---

### Post by linuxinstalledfromhdd on 2011-06-01
You could install app-runner and then right click on the file you want to run.

Here is a guide to get that installed. It's about half the way down the list.

[FONT=monospace]http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/[/FONT]

---

### Post by seawolf167 on 2011-06-01
No problem, here are step by step instructions, first find the location of the driver and remember it (i.e. is it in your Downloads folder? on your Desktop? etc.)

Enter tty1 by hitting [CTRL][ALT][F1] and login with your username and password

Next, stop gdm with

```
sudo service gdm stop
```

Now you can install your Nvidia driver, so browse to the file location that you remembered from step one

```
cd /path/to/driver
```

i.e. if it was in your Downloads folder, you would browse to

```
cd ~/Downloads
```

make sure the driver is flagged as executable

```
sudo chmod +x name-of-driver-file.run
```

where name-of-driver-file.run is the driver file name :P, you can find this out by typing

```
ls
```

to see the contents of your working directory, next run the driver as root

```
sudo ./name-of-driver-file.run
```

after the installation is finished, you'll restart gdm

```
sudo service gdm start
```

and you should be good to go

---

### Post by smurphy_it on 2011-06-01
If you can't run it with X-windows running you can get around it.

```
Hit ctrl-alt-F1
then kill your window manager.  
(ex.) sudo /etc/init.d/gdm stop
do the install (as a root, or with sudo pre-pended to the line).  Afterwords, run "sudo /etc/init.d/gdm start

```

If gdm doesn't work, just do a ls -l /etc/init.d | grep [gkx]dm
Then stop that one, followed by starting it once your video driver is installed.

NOTE:  instead of 'sudo /etc/init.d/gdm start' it could be a service start instead, so the command would be 'sudo service gdm start'

---

### Post by Virgil0211 on 2011-06-01
> **seawolf167 said:**
> No problem, here are step by step instructions, first find the location of the driver and remember it (i.e. is it in your Downloads folder? on your Desktop? etc.)

Enter tty1 by hitting [CTRL][ALT][F1] and login with your username and password

Next, stop gdm with

```
sudo service gdm stop
```Now you can install your Nvidia driver, so browse to the file location that you remembered from step one

```
cd /path/to/driver
```i.e. if it was in your Downloads folder, you would browse to

```
cd ~/Downloads
```make sure the driver is flagged as executable

```
sudo chmod +x name-of-driver-file.run
```where name-of-driver-file.run is the driver file name :P, you can find this out by typing

```
ls
```to see the contents of your working directory, next run the driver as root

```
sudo ./name-of-driver-file.run
```after the installation is finished, you'll restart gdm

```
sudo service gdm start
```and you should be good to go

Thank you for your help, but I still seem to be getting some screen tearing. The install process said something about the packaged pre-config thingy failing, but the install itself was a success. I don't know if that would have something to do with it.

It's ironic. In Windows 7, my computer can't handle streaming video or high-def video, but it connects to my television without difficulty or any tearing. In ubuntu, I can watch streaming and high-def video, but I can't connect it to my Tv without screen tearing.

There's no screen tearing that I'm able to notice on my laptop screen. It's only on my high def TV connected via HDMI.

---

### Post by seawolf167 on 2011-06-01
When you installed the proprietary drivers you'll now have a Control Suite, probably under System -> Administration

If you open that as "Administrator" (i.e. root), take a look in the settings. There should be one that says something like "Wait for vertical sync", or VSync, or VBlank. Enable that, restart your computer and see if that helps at all.

---

### Post by Virgil0211 on 2011-06-01
> **seawolf167 said:**
> When you installed the proprietary drivers you'll now have a Control Suite, probably under System -> Administration

If you open that as "Administrator" (i.e. root), take a look in the settings. There should be one that says something like "Wait for vertical sync", or VSync, or VBlank. Enable that, restart your computer and see if that helps at all.

Tried it, still seeing the tear, though it is a bit less obvious than it was before. It looks like Leonidas' nose is broken instead of the top half of his face being pushed an inch to the left. =P

---

### Post by Virgil0211 on 2011-06-01
*bump*

---

### Post by DinoT1985 on 2011-06-01
what video player are you using?

---

### Post by Virgil0211 on 2011-06-01
> **DinoT1985 said:**
> what video player are you using?

I think the basic one that came with Ubuntu. It's called "Movie Player" in the applications list. Should I use another?

---

### Post by Virgil0211 on 2011-06-01
> **DinoT1985 said:**
> what video player are you using?

It also doesn't seem to just be video files. While selecting a file in Kaffeine, the screen would tear when I scrolled the list from left to right.

---

### Post by Virgil0211 on 2011-06-01
I downloaded nvtv at one point to see if it would help, but whenever I click on it in the applications list, nothing happens. Is that normal?

---

### Post by Virgil0211 on 2011-06-01
Bump

---

### Post by Dustin2128 on 2011-06-01
Check it out in vlc maybe? I never have had tearing issues with any of my GeForce cards, but I use VLC for video.

---

### Post by Virgil0211 on 2011-06-01
> **Dustin2128 said:**
> Check it out in vlc maybe? I never have had tearing issues with any of my GeForce cards, but I use VLC for video.
 
I tried every video player I could find, no difference. I've actually noticed now that its in the general display as well. Like I said, the laptop display is fine. Its just on the TV.

---

### Post by Virgil0211 on 2011-06-01
*Bump*

---

### Post by Dustin2128 on 2011-06-01
> **Virgil0211 said:**
> *Bump*
No need to bump after less than an hour. Are you running the external display cloned, standalone or twinview? And have you tried turning compositing off?

---

### Post by Virgil0211 on 2011-06-02
> **Dustin2128 said:**
> No need to bump after less than an hour. Are you running the external display cloned, standalone or twinview? And have you tried turning compositing off?
 I apologize. Frustration and all that. I feel like I'm consistently running into walls.
 
I've done all three, and seen the screen tearing in all 3 instances. There may be a few individual settings I haven't tried with the TV as standalone or a separate x monitor, though, so I'll try playing with the v sync settings in those display modes to see if there's an improvement. I was hoping that I could either clone my display onto the TV, or have the TV display work in such a way that I wouldn't get that weird extended home bar or that dead space that typically shows up. My laptop monitor is something like 1366x768, while the TV is around 1920x1280 (I think).

---

### Post by Dustin2128 on 2011-06-02
> **Virgil0211 said:**
> I apologize. Frustration and all that. I feel like I'm consistently running into walls.
 
I've done all three, and seen the screen tearing in all 3 instances. There may be a few individual settings I haven't tried with the TV as standalone or a separate x monitor, though, so I'll try playing with the v sync settings in those display modes to see if there's an improvement. I was hoping that I could either clone my display onto the TV, or have the TV display work in such a way that I wouldn't get that weird extended home bar or that dead space that typically shows up. My laptop monitor is something like 1366x768, while the TV is around 1920x1280 (I think).
Did you have compiz/unity on or off though?

---

### Post by Virgil0211 on 2011-06-05
> **Dustin2128 said:**
> Did you have compiz/unity on or off though?

 I think on, but I don't know how to check.   I just reinstalled Ubuntu, anyway. I think I fiddled around in the settings to much, so it started refusing to boot up. Also reverted my C-drive to factory default settings, so I technically reinstalled Windows 7 as well.  Now, I can't even get the screen tearing to stop on my default laptop screen. Things just seem to keep getting worse. I'm going to try the Nvidia tech support as well, see if they can't solve my problems.   On the plus side, though, this has given me an opportunity to memorize certain terminal commands.

---

### Post by Virgil0211 on 2011-07-03
Okay. Same person. I've installed xubuntu, and I'm still experiencing the same tearing problems. It would seem now that it's been on my native display this whole time. I simply assumed it was working without testing video before trying to get it to work on an external television. I've tried just about everything, vsync and so forth, that I've been able to come across. The Nvidia forums were barely any help at all. 

If anyone has any idea how to fix this, please let me know. I'd love to be able to switch over to Xubuntu/Ubuntu/Kubuntu completely, but this screen tearing is preventing it. 

I've gotten a few other LiveCD versions of other operating systems, including older versions of Ubuntu, so I'm going to be checking those in the meantime. If one of them seems to get past the screen tearing, I'll let you know.

Please help! T_T

[http://www.youtube.com/watch?v=IRe9ykSfXyQ&feature=related](http://www.youtube.com/watch?v=IRe9ykSfXyQ&feature=related)

I downloaded every version of the above video I could from keepvid.com. In youtube, the test fails at every possible speed. I've only tried a couple of video formats thus far in Parole media player, but they seem to be fine at the slow and rapid speeds. It's primarily at the middle speeds that they begin to tear. However, youtube videos tear all over the place. Will try a video or two on blip.tv and see if there's any difference.

EDIT 2: Blip.tv also tears at any and all horizontal movement, even a head turn. 

Replayed video clips. All clips show tearing at all speeds, so disregard earlier hopeful statement. It seems that all horizontal movement in media player causes tearing. I don't know how to test it outside of a media player (i.e., just programs on the desktop), or if that would even be relevant, so if anyone has suggestions about that, let me know.

---

### Post by Virgil0211 on 2011-09-20
I thought about starting another topic about this, but I figured I might as well use the one I already started.

I tried just about every solution I could find to fix this problem, even installing Xubuntu because I heard it would be easier on computers with lower specs, thus may be friendlier to my laptop. No change. 

Right now, I'm using Xubuntu 11.04 on an msi A6000 laptop equipped with an Nvidia Geforce 9200M G card (I believe I misread the model of card earlier, but that's the result I get when I type 'lspci -v | grep -i vga' into terminal.

```
02:00.0 VGA compatible controller: [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]nVidia [/FONT][/COLOR][COLOR=blue ! important][FONT=inherit ! important]Corporation[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?p=2481950#") C79 [GeForce 9200M G] (rev b1) (prog-if 00 [VGA controller])
```

After ramming my head against a wall, I just gave up and fell back into using Windows 7. Then I started getting interested in programming, and Xubuntu was just so much easier to use for that purpose, so I got into the habit of using Xubuntu to practice programming and do schoolwork, while using Windows 7 for video and other entertainment purposes. So, recently, I decided to try again and see if the results would be any different. So far, no luck. I've tried every version of the V-sync settings, fixed the powermizer so that it was set to max performance by default instead of adaptive, uninstalled noveau, even tried a couple of things that were apparently supposed to work for earlier versions of Ubuntu (remind me not to try that again). I am about to try reinstalling the proprietary drivers again. If that doesn't work, I'll look up how to do a binary install.

Does anybody know anything else I can do to figure out what's causing the screen tearing? It's on my native display and primarily occurs with horizontal movement.

---

### Post by Virgil0211 on 2011-09-21
> **Virgil0211 said:**
> I thought about starting another topic about this, but I figured I might as well use the one I already started.

I tried just about every solution I could find to fix this problem, even installing Xubuntu because I heard it would be easier on computers with lower specs, thus may be friendlier to my laptop. No change. 

Right now, I'm using Xubuntu 11.04 on an msi A6000 laptop equipped with an Nvidia Geforce 9200M G card (I believe I misread the model of card earlier, but that's the result I get when I type 'lspci -v | grep -i vga' into terminal.

```
02:00.0 VGA compatible controller: [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]nVidia [/FONT][/FONT][/COLOR][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]Corporation[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?p=2481950#") C79 [GeForce 9200M G] (rev b1) (prog-if 00 [VGA controller])
```After ramming my head against a wall, I just gave up and fell back into using Windows 7. Then I started getting interested in programming, and Xubuntu was just so much easier to use for that purpose, so I got into the habit of using Xubuntu to practice programming and do schoolwork, while using Windows 7 for video and other entertainment purposes. So, recently, I decided to try again and see if the results would be any different. So far, no luck. I've tried every version of the V-sync settings, fixed the powermizer so that it was set to max performance by default instead of adaptive, uninstalled noveau, even tried a couple of things that were apparently supposed to work for earlier versions of Ubuntu (remind me not to try that again). I am about to try reinstalling the proprietary drivers again. If that doesn't work, I'll look up how to do a binary install.

Does anybody know anything else I can do to figure out what's causing the screen tearing? It's on my native display and primarily occurs with horizontal movement.

Well, I think I fixed the problem somewhat. A downgrade to Ubuntu 10.10 and some fiddling with the xorg.conf file later, and I've either eliminated it or gotten it down to a point where it can be easily ignored.

But now my wireless card won't work. Again, everything I seem to find on the internet doesn't work. What is it with Linux, anyway?

---

