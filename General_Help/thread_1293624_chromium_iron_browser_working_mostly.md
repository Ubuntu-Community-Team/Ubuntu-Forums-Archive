---
title: "chromium iron browser working mostly"
date: 2009-10-17
forum: General Help
---

### Post by sdowney717 on 2009-10-17
[http://www.srware.net/forum/viewtopic.php?f=18&t=561](http://www.srware.net/forum/viewtopic.php?f=18&t=561)
[http://www.srware.net/en/software_srware_iron_download.php](http://www.srware.net/en/software_srware_iron_download.php)

iron browser is based on chromium and it has pulled out all the chrome tracking data collection that google chrome performs on users.

anyhow i installed it and it works including flash.


extract iron-linux into home folder
cd into folder
change directories to the plugins folder...
cd iron/plugins

system link to libflashplayer.so with the following command...
ln -s /usr/lib/flashplugin-installer/libflashplayer.so

create a Desktop launcher for Iron 
Go to Desktop>right-click in an open space and select Create Launcher. A box pops open. Leave the Type settings alone (it has Application in it)>name it under Name (I called mine obviously Iron)>under the Command setting put...

/home/your-user-name/iron-linux/iron --enable-plugins

link for adware blocking
[http://www.srware.net/forum/viewtopic.php?f=18&t=581&sid=c75a113da9a36ad63d03cb8081b95fb3](http://www.srware.net/forum/viewtopic.php?f=18&t=581&sid=c75a113da9a36ad63d03cb8081b95fb3)

i got adware blocking to work

i made a file called chromiumadware.sh and made it executable. I put this code in there
adsweep.org is now arienh4.net for the files

[QUOTE]
#!/bin/bash
mkdir -p ~/.config/chromium/
mkdir -p ~/.config/chromium/Default/
mkdir -p ~/.config/chromium/Default/User\ Scripts
wget -qO ~/.config/chromium/Default/User\ Scripts/AdSweep.user.js [http://www.adsweep.org/AdSweep.user.js](http://www.adsweep.org/AdSweep.user.js)
wget -qO ~/.config/chromium/Default/User\ Scripts/AdSweep.user.js [http://arienh4.net/AdSweep.user.js](http://arienh4.net/AdSweep.user.js)

# wget -N -P . [http://arienh4.net/AdSweep.user.js](http://arienh4.net/AdSweep.user.js)

# don't forget to execute with the option --enable-user-scripts/QUOTE]

I also downloaded the adsweep.crx and put that in the folders user scripts and default and chromium.
anyhow, it works sometimes and othertimes does not work

[http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html](http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html)
adress bar chrome://extensions shows extensions, how about scripts?

---

### Post by monkeyKata on 2009-10-17
Hey thanks for posting this.  It's good to see someone's got it working.

I made another post that I was tempted to bump, then I saw yours and figured I'd ask for help.  I've basically done everything shy of installing the adware block, so I've extracted the folder into my home, made the system link to libflashplayer.so, created a shortcut using "--enable-plugins" but alas it doesn't launch anything.  Neither does double-clicking the iron executable file in the directory.

Just thought I'd ask if you might have any suggestions of things to try.  Maybe it requires some dependencies I don't or no longer have (I had chromium installed then got rid of it).

You know what, I just searched my /usr/lib/flashplugin-installer/ directory to make certain I made the right system link, and the folder doesn't exist.  I remember installing flash directly from Adobe when I first got Firefox running, I never installed the flashplugin-nonfree package.  So I probably haven't linked Iron to any working flash plugin yet.

Could this be why it is not running?  This doesn't seem right to me, I'd think it would still run without any plugins.

I'd appreciate any help you or someone might be able to offer.  Still very much learning about Linux - I haven't even installed anything else that wasn't a deb or a packaged download.

EDIT:  Just found the location of adobe's flashplugin and system-linked to it from the plugins folder of Iron and that didn't solve it.  Iron won't launch.  When I type 'iron' in the terminal (from w/in the iron-linux directory of course) I'm told "iron: command not found."

---

### Post by sdowney717 on 2009-10-17
hi,
type it as 
./iron --enable-plugins --enable-user-scripts --enable-extensions

you need the ./ in front to tell linux where iron is. in this case the local directory you are in.

i would i suppose install the synaptic package for adobe flash nonfree, then your link should function

---

### Post by monkeyKata on 2009-10-17
Yeah I just remembered having seen that ./ portion of the command in another post.

So I tried that and I get a segmentation fault after some what looks to be gtk theme info:

> ~/iron-linux$ ./iron --enable-plugins --enable-user-scripts --enable-extensions
/usr/share/themes/ClearGlow Pink/gtk-2.0/gtkrc:283: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/ClearGlow Pink/gtk-2.0/gtkrc:295: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/ClearGlow Pink/gtk-2.0/gtkrc:354: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/ClearGlow Pink/gtk-2.0/gtkrc:403: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Segmentation fault

I'm not sure what's up.  Thank you for the help.

---

### Post by sdowney717 on 2009-10-17
i dont know. I am running karmic beta but iron should run on ubuntu as it says that in the forum.
i am not using compiz, just metacity
if you install fusion-icon and run it , then it puts a nice icon on the panel where you can easily switch between them.
what about just ./iron

---

### Post by monkeyKata on 2009-10-17
Yeah still doesn't launch, gives a segmentation fault.  I uninstalled adobe's flash and got the nonfree package and linked Iron to that instead of the former, but this didn't change anything.

Might there be some basic packages I should get to have this functionality, to run programs extracted from tar.gz?  I didn't think this had to or even could be compiled.  In your case did you simply extract it?

---

### Post by monkeyKata on 2009-10-17
> **sdowney717 said:**
> 
i am not using compiz, just metacity



Hmm, I am running Compiz so maybe this has something to do with it.

---

### Post by ycp1 on 2010-08-30
Thank you for the posts. However, I still couldn't make it work in my Lucid.
```
I also downloaded the adsweep.crx and put that in the folders user scripts and default and chromium.
anyhow, 
``` Do you mean you installed adsweep.crx(adsweep chrome extension) or just downloaded it? I couldn't download it. So, I just install the extension by clicking AdSweep.crx in [http://adsweep.org/](http://adsweep.org/). After done that, I got it work.

PS> [http://www.adsweep.org/AdSweep.user.js](http://www.adsweep.org/AdSweep.user.js) is broken.

---

### Post by Dragynn on 2010-09-06
I am running the browser now having installed it a few minutes ago, haven't messed with the ad settings yet, just posting for a quick FYI.

Install was easy, downloaded the linux tar.gz from the Iron site, moved it to my home file, opened command terminal and used this:

```
tar xvfz iron-linux.tar.gz
```

let that run, closed terminal, navigated back to home file which now has the "iron-linux" folder, opened that and clicked on the "iron" icon and it opened right up, immediately it asked if I wanted to import my settings from other browser (Firefox in my case), I imported all bookmarks and set preferences.

Right-clicked after that on desktop and made a launcher, also added the icon that came in the Iron files as the icon used for the desktop shortcut (product_logo_48.png).

Really simple and straightforward, and this browser so far is noticeably faster than Firefox and is using no more resources that I can see.

Hope this helps someone, Happy Labor day y'all!
~D

*edit* I should have mentioned that I am running Lucid 10.04. Also: Just got the adblock feature working, the download I got did NOT have an empty "adblock.ini" file as was posted on Iron's site, so I went to their link and opened Fanboy's list, selected all and copied, opened the terminal and started Nano, pasted the file and tried to save. It wouldn't let me save in /opt so it defaulted to my home file for the save and named it "nano.save", so I renamed the file "adblock.ini" and opened the terminal again, used sudo mv command to move file and re-started Iron. Started working immediately, it's not as smooth as Adblock is in Firefox, shows a tiny icon in places where ads have been blocked, and you can't right-click an image or ad to add to your list, but basic functionality is there and it doesn't seem to slow Iron down any.

Again I have to say that it seems noticeably faster than FF, and I checked Youtube, Hulu etc. for functionality and everything works great, video is nice and crisp and sound is fine. Will update this post again if I find anything pertinent to add to it.

---

