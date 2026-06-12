---
title: "Ubuntu 11.04 and ATI Drivers"
date: 2011-05-02
forum: General Help
---

### Post by jodlajodla on 2011-05-02
Hello,

I have problems with ATI Drivers for my graphics HD4850. Opensource drivers work, but oftem lag mouse and other applications. Then I've installed Additional drivers, which are include in Ubuntu. It's good with mouse and other, but sometimes lag applications and moving windows. In CCSM I disabled Vsync and set refresh rate, but it's still lag on applications, moving windows is OK.

What can I do now?

Is ATI Driver version from Additional drivers same as 11.4 from official AMD's webpage?
If I will install drivers version 11.4 from AMD's page, will work good?
OR
How can I solve problems with opensource drivers with mouse and applications lagg?

Thanks for all replies and informations!

Greetings, jodlajodla :)

---

### Post by 3Miro on 2011-05-02
The ATI driver in 11.04 comes straight from AMD (just added an easier installation). It is possible that AMD has a newer version on their web-page, but since 11.04 just came out it is unlikely. Check with the Catalyst ATI settings center for the version installed.

If AMD already has a newer driver, then installing it may help, however, installing a driver manually is somewhat tricky, if done incorrectly it can break the system and you are pretty much guaranteed to have problems with kernel updates (you may have to reinstall the driver every time a new kernel update comes up). The purpose of the "Additional Drivers" tool is that you don't have to do this yourself.

I used Unity on 4250 with the Open Source driver and it worked fine, there was no lag or anything. This issue might be specific to your video card model/hardware/maybe some special setting.

---

### Post by jodlajodla on 2011-05-02
Thanks for reply, first!

I've looked for version in ATI Catalyst, but I haven't found it. 

What can I do with opensource drivers - any trick for solve that problem?

Thanks! :)

---

### Post by lildigiman on 2011-05-02
I've used the proprietary drivers for my 3850 and have not had any issues, and with the open source drivers I did have some (probably many) issues. I have also tried multiple times installing more recent proprietary drivers myself, and like 3Miro says, it's somewhat difficult, and I have in fact broken my system before because of it (but hey, it's all for fun).

You may want to try optimizing your CCSM settings, and also, if you do use the proprietary drivers, it's a good idea to optimize your Catalyst Control Center preferences.

---

### Post by 3Miro on 2011-05-02
> **jodlajodla said:**
> Thanks for reply, first!

I've looked for version in ATI Catalyst, but I haven't found it. 

What can I do with opensource drivers - any trick for solve that problem?

Thanks! :)

Catalyst is for the AMD driver only. The Open Source driver is part of the kernel (2.6.38 in this case).

Did you get this from an upgrade or clean install?

---

### Post by jodlajodla on 2011-05-02
Clean install, and currently I have installed Additional drivers.

[I]I will try to change some settings in CCSM, but also I hope that problem will be solved soon. 
[/I]
Thanks! :)

EDIT: *I've tried to change some settings in CCSM and Catalyst, but nothing better now.*

---

### Post by lildigiman on 2011-05-02
Could you describe more of what the exact issues are, please?

---

### Post by jodlajodla on 2011-05-02
Often when I'm playing game (SuperTux 2) there is lag on Tux - when moving and jumping, when I'm browsing in Firefox and scrolling on page I can see lag, ... with Additional driver.

With opensource driver there is lag on applications like Firefox - also scrolling, often mouse lag (wait for milisecond), ... but those things are very annoying.

Thanks! :)

---

### Post by lildigiman on 2011-05-02
Not entirely sure what to say... it may just be poor drivers for the card... :-(

---

### Post by jodlajodla on 2011-05-02
But when I have installed 10.10 it was good and all work ;)

What now? May I wait to next drivers from AMD's webpage?

Thanks! :)

---

### Post by lildigiman on 2011-05-02
Oh, I see. Knowing that it *did* in fact work before leads me to believe it's an issue other than the driver (so long as there was no update to it). This means something in 11.04 might be causing the issue. It could be a wide range of things such as the new Unity Desktop Environment. 

Do you have issues when you have Compiz disabled?

---

### Post by Younio on 2011-05-05
Hi 

I'm having the same problem. And I don't think this is because of Unity. I tried to use gnome classic, but am still geting the same problems. So this is probably a **driver issue** or the driver **incompatibility** with Ubuntu 11.04.

I'm regretting the installation of 11.04 :'D

The only solution is to use Unity 2D or gnome without hardware acceleration...

EDIT: After trying to install a driver from ATI website and then uninstalling it again and reverting back to the original one and changing openGL option to disabling sync to blank option. The 3D desktop effects are working much better, but 2D performance is still very lagy. Even the loading logo in chrome or Firefox lags. And when you scroll the websites they lag too.  Can someone fill a bug report, because I have never done that and don't know how to.

---

### Post by Younio on 2011-05-05
> **jodlajodla said:**
> But when I have installed 10.10 it was good and all work ;)

What now? May I wait to next drivers from AMD's webpage?

Thanks! :)

Have you installed the same drivers as in 10.10 ? Because before upgrading in ubuntu 10.10 I had older drivers.

---

### Post by expl0dingz on 2011-05-05
Similar or same issue here, running 11.04 on Sapphire 5750 1GB alongside Phenom II x6 1055T (if that matters) EDIT: 64bit version of Ubuntu...

first time experience with Ubuntu thou...correct me if I'm wrong in any matter.

Lag is an issue here. Scrolling in Firefox/Opera, there is a noticeable slight fps jerking lag. Switching workspaces with Ctrl+Alt+Right/Left/Up/Down makes it quite obvious. I play games @60 fps and this is obviously not 60fps. Even stuff like watching youtube videos and TYPING for that matter, I can already feel the lag. (

This is what I have tried:
1. Downloaded and install the automatically suggested additional drivers when you first install Ubuntu
2. Followed the instructions clearly at [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide")

still experiencing the same laggyness..any insight on this problem? How is it like for you guys, especially Nvidia users? Is the experience silky smooth like on Windows? Or is there a noticeable lag?

---

### Post by Nerotriple6 on 2011-05-05
I'm sorry I can't help but.

I am running Ubuntu 11.04 with a HD4650 and a Pentium 4...
I have transparency settings set to crazy and blur and the lot. No lag at all. Everything works great and fast. Using Proprietary drivers installed with the tool.

Well I have some lag in two things... Software Center and....

Doom 2... :tongue::tongue::tongue: (if I try to run it in 1280x1024)

EDIT: No it's not silky smooth like on Windows.

...It's better... :D

---

### Post by expl0dingz on 2011-05-05
Okay..but when you browse in Firefox/Opera, do you get jerkyness when you scroll? To be specific, scrolling with the side scrollbar. I cannot scroll with my middle mouse wheel due to the fact that my Razer Deathadder's mousewheel scrolling has got some screwed up issues.

Also, I just attempted to copy 17.6GB of a WoW installation from the C: of my windows partition on HDD #1 to my user folder at HDD #2, creating a massive amount of lag and unresponsiveness. Is this normal?

---

### Post by Nerotriple6 on 2011-05-05
I use Chrome and I have not bothered to install Opera yet but..

I opened a Firefox window and there were no performance issue. No lag, no jerkyness ...it's just fast. I tried browsing this thread and youtube.com. Sideways scrolling on Youtube was a _little_ jerky but nothing to make a thread about.

---

### Post by expl0dingz on 2011-05-05
Okay...totally not same as mine I guess. Can really see the choppyness when scrolling in a normal Google search page in Firefox. Just to confirm, by "Proprietary drivers installed with the tool" you mean the one that they prompt you to download and install after you just installed Ubuntu?

And is this on 32 or 64 bit?

---

### Post by Nerotriple6 on 2011-05-05
This is an old Pentium 4 comp running with 1GB RAM a Radeon HD 4650 1GB AGP and Ubuntu 11.04 32bit.
All sorts of fancy effects enabled, I would expect this to be begging for mercy but it's begging for more. Unless I'm playing Doom 2 lol..

Yes, the drivers I was prompted to install after I installed Ubuntu a few days ago.
I forgot to mention that I am using Gnome 2 and not Unity though. I had some minor performance issues in Unity but nothing major like you guys are describing.

---

### Post by nava69 on 2011-05-05
Hi
i installed 11.04 64bit but when im booting to ubuntu (choose 11.04 in boot loader) my screen start to flashing white and purple and i cant see any thing after that,also i tried 32bit but it had same problem
I have ATI HD6870
 
sory for my english

---

### Post by jodlajodla on 2011-05-05
Hello,
After that problems I've installed back 10.10 and lasest 11.4 ATI Driver, but there are lag when moving mouse pointer on buttons in menu. Also there is problem with opensource drivers, because mouse lag and applications.

So what we can do to get better support for our hardware?
Someone must post that problem on Launchpad (if I know right?) and then we must vote for that problem. I think that we should post this first for opensource driver and then on support for Linux ATI Driver.

Greetings, jodlajodla :)

---

### Post by Younio on 2011-05-06
> **jodlajodla said:**
> Hello,
After that problems I've installed back 10.10 and lasest 11.4 ATI Driver, but there are lag when moving mouse pointer on buttons in menu. Also there is problem with opensource drivers, because mouse lag and applications.

So what we can do to get better support for our hardware?
Someone must post that problem on Launchpad (if I know right?) and then we must vote for that problem. I think that we should post this first for opensource driver and then on support for Linux ATI Driver.

Greetings, jodlajodla :)

So to be sure. You installed The latest drivers from ATI website? If so, this means that all we need to do is to install the earlier driver version. It means that all the problems began after installing this new driver from ATI (11.04 was bundled with it) So for now we need to find the older driver version and see if it works with 11.04 :D

EDIT: Found the [link]("http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx") to the older driver versions, [lets try :D]("http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx")
Oh and if someone needs it, the latest version is [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.5.3.1&lang=English")

EDIT2: Failed to install 11.3 driver version. In spite that Xorg should be compatible, because the driver supports 7.6 version But probably that driver doesn't work with new 11.04 kernel. So it should work with Ubuntu 10.10 and fix problems there, but not for 11.04

```
$ sudo sh ati-driver-installer-11-3-x86.x86_64.run
Created directory fglrx-install.2dWUFk
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.831.2.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.38-8-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.2dWUFk

```

---

### Post by lildigiman on 2011-05-06
I have just updated to 11.04 on my main computer (after making an image copy backup of 10.10, of course), and I have found that I am having awful results with Compiz effects with "Classic-Gnome." Everything is slow and it feels/looks like frames are dropped. I have not tried Unity with Compiz, and it's too late to because I'm in the process of copying back my 10.10 copy where Compiz and Gnome worked impeccably.

As I stated in previous posts, and as seen in my signature I'm using an ATI Radeon HD3850 with proprietary drivers (as acquired by "Additional Drivers" in Ubuntu).

This seems to be a somewhat serious issue that multiple people are having, and it needs a bug report (hey, I would on my launchpad account, but I don't think I'm the right person to take on something like this...).

---

### Post by ShadowNate on 2011-05-12
I have an ATI Radeon HD 5770 card. I upgraded to natty from maverick and since I got some display issues and blank screens, I completely removed the previous ati drivers (following the wiki instructions) and installed the latest 11.5. This worked, but now everytime I move the mouse cursor near the right bottom corner of the screen the whole PC lags, and I can hear the (GPU I guess) fans spinning faster. I did not have this issue on Ubuntu 10.10.

This does not happen on my other PC (also upgraded to natty) with catalyst 11.5 and an embedded ATI HD 4250. No lag there.

Is this a known catalyst issue?

---

### Post by cottfcfan on 2011-05-12
I'm experiencing similar problems here, but I think compiz is the culprit.
Install "gtkperf" run it and watch how poor the graphics render & make a note of the time it takes.
Then turn off compiz & use Metacity, (fusion-icon does this easily)
Then run gtkperf again & see the difference.
Of course this can only be done using the "gnome-classic" desktop.
Someone more knowledgable might know better, but thats my thinking.

---

### Post by chronniff on 2011-05-13
I can definately confirm that I am having the same right corner problem with ll.5 where it starts the pointer gets seemingly stuck there for a minute and my cpu goes crazy for a second....I'm also using a 5770, this bug is extremely irritating

---

### Post by s4ms3milia on 2011-05-15
I have the exact same Problem! Bottom right of the screen -> stutter ~1 second. EXTREMELY annoying!

---

### Post by shadysamir on 2011-05-18
When I googled this problem I didnt expect to find any results, but this thread was the first result.

I am also having the bottom right corner problem with latest driver from AMD and 11.04 with Gnome (Classic).

---

### Post by ylsdd on 2011-05-27
I'm having the mouse-lag-at-the-corner problem too!

ATI HD5450. 

After upgrading to ubuntu 11.04, I turned off unit and used gnome classic for a few days. But all video players flicker. 

So I have to use other windows managers, now I'm using LXDE, and videos no long flicker.

And I bought new batteries for my wireless mouse, only to find out this mouse-lag-at-the-corner bug

This bug is universal, in ubuntu 11.04, no matter what windows manager you are using.

---

### Post by shadysamir on 2011-05-29
Installing ATI drivers from repos solved my problem. I removed ATI drivers and used the ones from "Additional Drivers"

---

### Post by linuxinstalledfromhdd on 2011-05-29
Awesome job!!:popcorn:

---

### Post by chuuninkid on 2011-06-03
hello!..
 
im also having similar performance problem here. both unity and classic mode suffer an annoying stutter... previously in maverick, dragging window is very smooth (60fps). but when i upgrading to 11.04 (fresh upgrade) dragging window is lagging like playing crysis in pentium 4 :p (maybe a 5 fps :( ), and causing the pointer to respond poorly to my mouse movement.
 
i notice that natty implement a very nice looking drop shadow effect like macs. is it the one that cause all that stuttering? because my guess is this is a driver performance problem. if so how do i disable that drop shadow?? i read in many article that compiz is a no-go for natty...
 
my desktop specs = athlon2 250 3ghz, 2gb ddr3, ati radeon 5750

---

### Post by abhijitw on 2011-06-13
One more victim here.

I installed drivers recommended by Ubuntu and all my video playbacks are suffering lag. 

I even uninstalled it and but no help.


My specs : AMD Athlon X2 4200+, 3 Gigs of Ram and ATI Radeon HD 5450.

Is there any workaround?

---

### Post by wildmanne39 on 2011-06-13
> **abhijitw said:**
> One more victim here.

I installed drivers recommended by Ubuntu and all my video playbacks are suffering lag. 

I even uninstalled it and but no help.


My specs : AMD Athlon X2 4200+, 3 Gigs of Ram and ATI Radeon HD 5450.

Is there any workaround?
Hi, if it is just video, if you mean in firefox go to tools addons and install flashaid and follow the instructions. If not have you messed with compiz? do you have another video card driver in additional drivers you can try?

---

### Post by hornap on 2011-06-18
Xubu 11.04 64 bit, 5750 same problem.
Source was probably upgrade, because I didn't remove user installed drivers.

Solution:

sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon

removing:
/usr/lib/fglrx/
/usr/lib32/fglrx/

And then installing system/restricted driver manager (I am using Czech localization, not sure witth correct translation.)

Now it works.

Still fgl_glxgears make about 1950 fps and take 100% from one core. Not sure if it is ok, but it is much better.

---

### Post by s4ms3milia on 2011-07-31
Since Catalyst 11.4 every driver has the annoying bottom right corner bug.

Adding SWCursor true to the xorg.conf kind of fixes the problem but introduces new annoying issues.

[http://askubuntu.com/questions/42976/freeze-when-moving-mouse-to-bottom-right-corner-of-screen-since-ati-catalyst-11-5](http://askubuntu.com/questions/42976/freeze-when-moving-mouse-to-bottom-right-corner-of-screen-since-ati-catalyst-11-5)

---

