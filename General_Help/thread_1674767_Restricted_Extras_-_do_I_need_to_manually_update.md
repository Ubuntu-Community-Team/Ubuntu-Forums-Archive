---
title: "Restricted Extras - do I need to manually update?"
date: 2011-01-24
forum: General Help
---

### Post by nrundy on 2011-01-24
I always had to manually update things like Flash when using M$ Windows.   for Ubuntu, I installed the restricted extras package. I just noticed that Firefox says Flash needs to be updated. Do I need to manually update Flash with Ubuntu or will the "Restricted Extras" package be updated automatically via Ubuntu updates?

---

### Post by endotherm on 2011-01-24
nope. the metapackages itself (ubuntu-restricted-extras) will probably never update, but the constituent packages will appear as updates to them are posted. you may get updates more rapidly if you enable the backports and/or the proposed repos, but you take all the risk of unsupported updates if you do.

---

### Post by uRock on 2011-01-24
Install and run the flash aid add-on for Firefox. It will get the proper flash installed for your system. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) written by [lovinglinux]("http://ubuntuforums.org/member.php?u=649167")

---

### Post by nrundy on 2011-01-24
So things like Flash will be auto updated (ie, an update window will pop open on my panel at some point like other Ubuntu updates occur)?

---

### Post by nrundy on 2011-01-24
> **uRock said:**
> Install and run the flash aid add-on for Firefox. It will get the proper flash installed for your system. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) written by lovinglinux

This provides auto-updates of flash? Don't updates come from Ubuntu updates? What is flash-aid doing that the Ubuntu updates don't?

---

### Post by uRock on 2011-01-24
> **nrundy said:**
> This provides auto-updates of flash? Don't updates come from Ubuntu updates? What is flash-aid doing that the Ubuntu updates don't?
It finds the right version of Flash to match your hardware. I am not sure how [lovinglinux]("http://ubuntuforums.org/member.php?u=649167") wrote the add-on.

Which version of Firefox are you using?

From the add-on's page,> Remove conflicting flash plugins from Ubuntu Linux systems, install the  appropriate version according to system architecture and apply some  tweaks to improve performance and fix common issues.

---

### Post by nrundy on 2011-01-24
Just the version that came with Ubuntu - 3.6.13

---

### Post by uRock on 2011-01-24
> **nrundy said:**
> Just the version that came with Ubuntu - 3.6.13
I am using the same thing. Neither my 10.10 machine nor the 10.04 machines have had the problem with flash being out of date, so I am not sure what is causing it, but I do trust [Lovinglinux]("http://ubuntuforums.org/member.php?u=649167")'s add-on will fix the problem.

---

### Post by nrundy on 2011-01-24
Can you check yours now and see what it says?

open firefox, click Tools > Add-ons > plugins > find updates (lower left corner)

what does your "shockwave flash" show

---

### Post by earthmeLon on 2011-01-24
There are many different 'flash' options for Linux users.  Some work better than others on different system types (x64/i386) and stuff.  The install helper will help you get the correct one installed correctly :D.

Ubuntu has apt package manager.  You may see it pop up and let you know that there are updates available for your system. Whenever you run #'apt-get update', apt checks all the repositories in your '/etc/apt/sources.list' and looks to see if anything you've installed via apt can be upgraded.

This is why it is good to add extra repositories for programs you expect to be updated frequently.  I have [chromium repo]("https://launchpad.net/~chromium-daily/+archive/ppa") that gives me a daily build/update.

If you use another program (such as the earlier-recommended flash installer), you risk the chance of apt not being aware of any new updates.  Also, some would argue that it's insecure/a bad idea to install from anywhere other than trusted Ubuntu repos.  It will help keep your system stable, as Ubuntu has *signed* that these are working/stable versions of whatever it is you're running.

You can use the command $'apt-cache search XXX' (where XXX is the name of the program you want) to search for available packages. An example:

```

[meLon@Yggdrasil] ~$ apt-cache search flash
[COLOR="red"]browser-plugin-gnash[/COLOR] - GNU Shockwave Flash (SWF) player - Plugin for Mozilla and derivatives
gnash - GNU Shockwave Flash (SWF) player
gnash-common - GNU Shockwave Flash (SWF) player - Common files/libraries
gnash-cygnal - GNU Shockwave Flash (SWF) player - Media server
gnash-dbg - GNU Shockwave Flash (SWF) player - Debug symbols
gnash-doc - GNU Shockwave Flash (SWF) player - API documentation
gnash-tools - GNU Shockwave Flash (SWF) player - Command-line Tools
ifpgui - QT based manager for iRiver iFP audio players
jsymphonic - File manager for Sony's MP3 players
klash - GNU Shockwave Flash (SWF) player - Standalone player for KDE
konqueror-plugin-gnash - GNU Shockwave Flash (SWF) player - Plugin for Konqueror
pianobar - console based player for Pandora radio
[COLOR="red"]flashplugin-installer[/COLOR] - Adobe Flash Player plugin installer
[COLOR="red"]flashplugin-nonfree[/COLOR] - Adobe Flash Player plugin installer (transitional package)
[COLOR="Red"]flashplugin64-installer[/COLOR] - Adobe Flash Player plugin 64 bit alpha installer

```

This shows that you can choose between Gnash and Adobe's flash player.  

I hope this information is helpful in your migration to Ubuntu.

---

### Post by nrundy on 2011-01-24
I didn't have to install an extra repo when I got Reestricted Extras. do I need to install an additional repo to get Flash updates as they become available? Won't the repo that I got the Restricted Extras from also update Flash as it needs it?

---

### Post by uRock on 2011-01-24
> **nrundy said:**
> I didn't have to install an extra repo when I got Reestricted Extras. do I need to install an additional repo to get Flash updates as they become available? Won't the repo that I got the Restricted Extras from also update Flash as it needs it?
You do no need to add a repo to get flash. The repo mentioned above is for Chromium.

Have you installed the add-on yet?

---

### Post by nrundy on 2011-01-24
I haven't installed the add-on cause I'm trying to figure out if Ubuntu will update flash automatically as part of the regular ubuntu updates. I think I'd prefer to do it this way-ubuntu update.

---

### Post by earthmeLon on 2011-01-24
> **nrundy said:**
> I didn't have to install an extra repo when I got Reestricted Extras. do I need to install an additional repo to get Flash updates as they become available? Won't the repo that I got the Restricted Extras from also update Flash as it needs it?

Flash is NON-FREE, so yes, you have to activate that repository.  When you install Ubuntu, it has the restricted repos within the '/etc/apt/sources.list' file, but they are commented.

For example:
[quote=Default]## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner[/quote]

[quote=Modified]## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner[/quote]

So, you want to run 'gksudo gedit /etc/apt/sources.list and make sure any line with starting with **deb** or **deb-src** does *NOT* have # at the beginning.

Now run 'sudo apt-get update' to get everything up to date.  Now you can install whichever flash you want to install.

In the future, you can run 'sudo apt-get update && sudo apt-get upgrade' to check for updates and then install those updates.

---

### Post by nrundy on 2011-01-24
earthmelon, this is some great info, Thanks.

However, after enabling the "partner" repo and loggin out and then back in a check with the update manager does not reveal any updates for Flash. Is it possible the developers just haven't gotten to issuing an update yet? I checked the sources file again and there is no hash preceding the partner repo deb lines like you said. so it looks like I got it correctly. Is your flash up to date?

---

### Post by uRock on 2011-01-24
> **nrundy said:**
> earthmelon, this is some great info, Thanks.

However, after enabling the "partner" repo and loggin out and then back in a check with the update manager does not reveal any updates for Flash. Is it possible the developers just haven't gotten to issuing an update yet? I checked the sources file again and there is no hash preceding the partner repo deb lines like you said. so it looks like I got it correctly. Is your flash up to date?
Which release are you using? Here is a screenshot of flash installed on my system in 10.10. From looking at Synaptic I see that Ubuntu does not maintain flash, so that has to come from Adobe.

---

### Post by nrundy on 2011-01-24
10.04 LTS here. 

When I installed restricted extras a couple weeks ago though it installed the latest edition of Flash. So I assumed it would auto update the stuff.

---

### Post by earthmeLon on 2011-01-24
Administration > Synaptic Package Manager is a GUI program that will help you figure out what you've got installed on the system. 

First, make sure you're packages are up to date.  I am not sure if rebooting the system calls it to be updated.  You can do this with "Reload".  Then, use quick search to look for flash.  I am on x64 and see that I have flashplugin64-installer installed.  It's version 10.3.162.29.  

Because APT is showing that it's installed, whenever flashplugin64-installer is updated, my system should become aware whenever I update my packages.

I'm not sure what version of which player you are using, but don't expect anything to be updates too frequently.  There wont just be flash updates all the time.

---

### Post by JGJones on 2011-01-24
I really don't like to use terminal commands as a guide when there are perfectly good GUI methods of doing the same thing. Let's make it more useful for normal users that don't want to see a terminal :-)

To have Flash as part of "Ubuntu Updates" this is what you'll need to do:

Go to Ubuntu Software Centre.

Click on Edit in the menu and then Software Sources. In the first tab (Ubuntu Software), I believe Flash is found in "Software restricted by copyright or legal issues (multiverse)" so you'll want to tick this box along with restricted.

Then click on Close.

Ubuntu will automatically update the software database. Once this is done, then click on the search box in Ubuntu Software Centre and search for Adobe Flash.

It will show up and you can then click on Adobe Flash and click on the Install button.

Any new Flash updates - you might get a small additional time while you wait for the Flash package to udpate. Ubuntu does not actually update Flash itself. It download the package directly from Adobe themselves including any updates.

Cheers

---

### Post by nrundy on 2011-01-24
So Flash is not automatically updated? I need to manually update it periodically? 

Since when I installed restricted extras I got the latest flash edition, wouldn't reinstalling restricted extras automatically update everything to the latest version?

JGJones, thanks for you walk though. Great info. My config already had restricted extras checked off.

---

### Post by JGJones on 2011-01-24
nrundy - any packages that is updated in restricted/multiverse will be updated on your system automatically.

Thus if Adobe release a new version of Flash - it won't update immediately on your system. There is an additional delay while the Ubuntu package which automatically download Flash from Adobe get updated. Once this happens then it will update Flash. How long does this take I can't say. I have had my Flash updated to the latest version via Ubuntu update manager so I'm happy enough with that.

Hope that answer your question.

---

### Post by nrundy on 2011-01-24
Does this auto-update only occur if you have Restricted Extras installed?  I don't want everything from Restricted extras (like I have no use for QuickTime). If I manually installed just Flash, would enabling the partner repo still update Flash even if I didn't initially install it via the Restricted Extras?  On an aside, do you know how to uninstall the QuickTime and REAL plugins from Firefox? I only see a "Disable" option from within Firefox. And see no uninstall method via Ubuntu.

---

### Post by uRock on 2011-01-24
> **nrundy said:**
> 10.04 LTS here. 

When I installed restricted extras a couple weeks ago though it installed the latest edition of Flash. So I assumed it would auto update the stuff.
Has it always said you need to update flash? If yes, then the installer may have installed the wrong flash for your hardware, which is part of the reason lovinglinux created his add-on for firefox in Ubuntu.

---

### Post by nrundy on 2011-01-25
> **uRock said:**
> Has it always said you need to update flash? If yes, then the installer may have installed the wrong flash for your hardware, which is part of the reason lovinglinux created his add-on for firefox in Ubuntu.

No. It showed flash and quicktime as being up to date until just a couple days ago.

---

### Post by uRock on 2011-01-25
I just ran Flash Aid on a new Ubuntu install and it used Ubuntu's repos to get the latest flash.

---

### Post by nrundy on 2011-01-27
> **uRock said:**
> I just ran Flash Aid on a new Ubuntu install and it used Ubuntu's repos to get the latest flash.

I've literally had an Ubuntu update activate three days in a row now. Yet Flash is still showing as needing to be updated. I guess ubuntu doesn't update it. hmm.

Thanks for letting me know about Flash Aid :)

---

### Post by nrundy on 2011-01-27
I installed Flash Aid and it successfully removed Flash but did not install the new version. I ran it twice.

---

### Post by cottfcfan on 2011-01-27
I don't know why this thread is so long winded.
The answer to your question is, if you have the Adobe Flash repo enabled in your software sources, you will always have the  latest flash that will update automatically.
 And no you do not need the restricted extra package for this to happen.
Hope this helps.

---

### Post by uRock on 2011-01-27
> **cottfcfan said:**
> I don't know why this thread is so long winded.
Because the OP doesn't want to add outside sources, which I understand.

---

### Post by cottfcfan on 2011-01-27
> Because the OP doesn't want to add outside sources, which I understand.

Then i suppose theres not much choice other than to wait & see what comes through the official repos.

---

### Post by nrundy on 2011-01-27
> **cottfcfan said:**
> I don't know why this thread is so long winded.
The answer to your question is, if you have the Adobe Flash repo enabled in your software sources, you will always have the  latest flash that will update automatically.
 And no you do not need the restricted extra package for this to happen.
Hope this helps.

Where can i find the address for the Adobe Flash repo? It's a ppa?

---

### Post by nrundy on 2011-01-27
The Flash version in the synaptic repo is the same as what Adobe is saying the latest version is. Maybe the Firefox update thing is wrong when it says it is out of date?

---

### Post by cottfcfan on 2011-01-27
The latest stable version of flash as far as i'm aware is 10.1.102.65
The ppa I have enabled is the one listed in Ubuntu Tweak.
If you don't have Ubuntu Tweak its a great tool. You can get it from here:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
You can enable whatever ppas you like from the source centre, just by ticking the boxes.

---

### Post by nrundy on 2011-01-28
what's the repo address for Flash, assuming I don't have tweak? I uninstalled tweak cause I didn't use it for anything.

---

### Post by cottfcfan on 2011-01-28
Not sure.
I just use ubuntu-tweak for all my ppas its easier.
Just Google it.

edit.. Actually ive just checked the adobe site and if your using the version mentioned in post 33 then that is the latest version.

---

