---
title: "Flash not working in Ubuntu 11.10"
date: 2012-03-29
forum: General Help
---

### Post by flyingfisch on 2012-03-29
Starting this morning after I installed the flash update, my flash is broken.

I don't get any errors about missing plugins, just a blank screen.

I have Adobe flash player 11 installed (not the flash plugin for Firefox). I also have Ubuntu restricted extras (minus firefox flash plugin) installed. I had gnash installed but read that it might cause problems with flash so I uninstalled it, but flash still won't work. I installed Xubuntu restricted extras today (minus firefox flash plugin) since I have XFCE installed to see if that would fix it, but it didn't.

I have tried installing Lightspark, but since it wouldn't work either, I uninstalled it. I used flash-aid to try to fix it too. I have restarted my computer every step of the way.

I don't know what else could be wrong so if you guys would help me out it would be great. :)

---

### Post by dak77 on 2012-03-29
Me too. I'm also on Oneiric and running Firefox 11.

I get a black hole where a YouTube vid should be and the Adobe page helpfully telling me that I haven't got the plugin installed. According to the Firefox add-ons page I've got 'Shockwave Flash 11.2 r202' installed, though.

Have you had any luck fixing your setup?

---

### Post by Jerry N on 2012-03-29
I posted about this a few days ago.  I can't get Firefox flash to work properly in Linux or Windows 7.  I was thinking about deleting Firefox 11 and going back to Firefox 6 in Windows.  However, flash works fine with Chrome in Windows and Chromium and Midori in Linux so I have taken the easy way out and just pop up one of these other browsers when flash isn't working right.  

Jerry

---

### Post by dak77 on 2012-03-29
I just found [this thread]("http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash&page=2") and followed the advice in message #11.

It worked immediately and didn't even require a restart of Firefox :-)

(I was anticiptating at least another hour of battling with my machine... I feel like I've been handed back my stolen evening.)

---

### Post by flyingfisch on 2012-03-29
> **dak77 said:**
> I just found [this thread]("http://ubuntuforums.org/showthread.php?t=1948626&highlight=flash&page=2") and followed the advice in message #11.

It worked immediately and didn't even require a restart of Firefox :-)

(I was anticiptating at least another hour of battling with my machine... I feel like I've been handed back my stolen evening.)
Did you have to uninstall anything or just extract it?

EDIT: 
Never mind. Figured it out:

1. If you have Flash player 11 installed, uninstall it. Otherwise go to step 2.
2. Install flashplugin-installer by executing in terminal *sudo apt-get install flashplugin-installer*
3. Download [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml](http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml)
4. Extract libflashplayer.so and move it to /usr/lib/flashplugin-installer/

This should work in pretty much any browser. ;)

---

### Post by apricot on 2012-03-30
Any way to make flash work in 10.04, 'cause after yesterday's update, flash is not working in lucid also, and above solution doesn't apply!

---

### Post by Shadius on 2012-03-30
While trying to fix this problem on Firefox, I uninstalled everything Flash related using Synaptic Package Manager and went to YouTube to test it out and guess what? The videos play! How is this? There is no Flash plugin installed now. So what's the deal here? I'm a beginner with Ubuntu Linx, but this makes no sense to me. Can someone clarify? I've been trying to fix this issue for hours!!!

---

### Post by as2000 on 2012-03-30
I believe Adobe stopped supporting flash for Linux. There is an open source alternative, but my mind fails me on the name.

---

### Post by Karlchen on 2012-03-30
Hello, apricot.

Though your question about Flash and Firefox on Ubuntu 10.04 > **apricot said:**
> Any way to make flash work in 10.04, 'cause after yesterday's update, flash is not working in lucid also, and above solution doesn't apply! seems a bit misplaced in a thread complaining about Flash not working in Ubuntu 11.10, let me try to explain how both (Firefox) and Flash have been setup and updated here ever since Ubuntu 10.04 was installed for the first time. They have never failed during the past two years:


[LIST]
[*]All in all there are 2 different Lucid Lynx Desktop machines here, both 32-bit.
[*]One of them gets the official Firefox versions which Ubuntu offer in their repositories.  (lucid-updates) The current version is 11.0.
[*]The other machine runs the official Mozilla Firefox edition got from the Ubuntuzilla repository (deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main) and is kept up-to-date through the normal Ubuntu updates just as if it were the official Firefox edition offered by Ubuntu. This Firefox has been installed to /opt/firefox. The current version is 11.0.
[*]Both machines and Firefox installations use the same Flash version and get it from the same repository. (deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner)
[*]The installed Flash packages are adobe-flashplugin and adobe-flash-properties-gtk.
[*]Currently both are at version 11.2.202.228-0lucid1
[*]Neither has any of the 2 Firefox editions ever caused any problems after allowing Synaptic to install an available update.
[*]Nor has the Flash player plugin ever caused any problem after allowing Synaptic to install any available update.
[*]Both Firefox editions find the Flash plugin this way:
the flash plugin library file /usr/lib/libflashplayer.so is hardlinked to /usr/lib/adobe-flashplugin/libflashplayer.so
the symlink /usr/lib/mozilla/plugins/flashplugin-alternative.so points to -> /etc/alternatives/mozilla-flashplugin
the symlink /etc/alternatives/mozilla-flashplugin points to => /usr/lib/adobe-flashplugin/libflashplayer.so (and this is where were are back to the flashplugin library file)
[*]No user Firefox profile holds any additional symlink to the flash plugin. The location is defined systemwide.
[/LIST]
All this may read much more complicated and confusing than it really is. The crucial point very likely is that the Firefox packages and the Flash packages are being installed from the (half) official repositories with the help of Synaptic which takes care of the details.
This approach has worked here flawlessly for the past two years.

Kind regards,
Karl

---

### Post by Karlchen on 2012-03-30
Hello, Shadius.
> While trying to fix this problem on Firefox, I uninstalled everything Flash related using Synaptic Package Manager and went to YouTube to test it out and guess what? The videos play! How is this? There is no Flash plugin installed now.  Could it be that you uninstalled the systemwide flash player plugin software with the help of Synaptic, but that your current user has got his own copy of libflashplayer.so inside his Firefox userprofile?
You might locate it by navigating to ~/.mozilla/firefox/*randomcharacters*.default/extensions.
The "~" refers to your home folder.
The sub-folder folder below the folder "firefox" has got some random looking name, but usually ending with ".default".
The pathname here would read "~/.mozilla/firefox/vw9o29p4.default/extensions" e.g.

Kind regards,
Karl

---

### Post by blueshead on 2012-03-30
For Flash in Firefox in Ubuntu 11.10,  I use Flash Aid..

So far all well..

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by ratcheer on 2012-03-30
> **as2000 said:**
> I believe Adobe stopped supporting flash for Linux. There is an open source alternative, but my mind fails me on the name.

They stopped supporting it in future Flash releases, but they say they will support the current latest version on Linux for several years.

Tim

---

### Post by Shadius on 2012-03-30
> **Karlchen said:**
> Hello, Shadius.
 Could it be that you uninstalled the systemwide flash player plugin software with the help of Synaptic, but that your current user has got his own copy of libflashplayer.so inside his Firefox userprofile?
You might locate it by navigating to ~/.mozilla/firefox/*randomcharacters*.default/extensions.
The "~" refers to your home folder.
The sub-folder folder below the folder "firefox" has got some random looking name, but usually ending with ".default".
The pathname here would read "~/.mozilla/firefox/vw9o29p4.default/extensions" e.g.

Kind regards,
Karl

Thank you for replying. I've since fixed the problem with the thread used above. Before I went on to fix it using that method, I kept testing it to see if all of YouTube's videos would play and I encountered that only some played. VEVO didn't play at all. It kept telling me that I needed to install a missing plugin for the videos that didn't play. I don't understand why only some would work even if the libflashplayer.so file was in my userprofile of Firefox, I am the only user, by the way. Also, since I'm a total beginner to Ubuntu, I couldn't find the *.mozilla* file until I had *Show Hidden Files* selected from my Home folder. Found that out with the help of this link, [http://support.mozilla.org/en-US/kb/Profiles#w_how-do-i-find-my-profile]("http://support.mozilla.org/en-US/kb/Profiles#w_how-do-i-find-my-profile"), if that's help to anybody else.

---

### Post by MoYoN on 2012-03-30
Thank you very much for all your help.  Any way, I was be able to fix my problem with these steps.

1. Reinstall the package flash-plugin-installer and flash-plugin-nonfree
2. Download the flash version from adobe in tar.gz
3. Extract all the files
4. I've copied the file libflashplayer.so in folder /usr/lib/adobe-flashplugin
5. There are one folder /usr with several folders inside and files also, I've overwriten those folders and files in the folder /usr.
6. Restart firefox

I use Ubuntu 10.04 and now flash works again.

I Hope this will be helpful.

---

### Post by apricot on 2012-03-31
@Karlchen & MoYon, tnx, but none of that helped.

---

### Post by daedalas1981 on 2012-04-03
**Here is the easiest way to get flash working again (Very Noob Friendly)...**

**1.** Visit Flash-Aid for Firefox.
Flash-Aid Plugin Link: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")
**2.** Install Flash-Aid.
**3.** Restart Firefox.
**4.** Select Tools-> Flash-Aid-> Wizard Mode
**5.** Select "Google, from Chrome" in the drop down for which version to use.
**6.** Click on Next on everything as Defaulted.
**7.** The final screen click execute.
**8.** A shell command window will open, enter your password for sudo.
**9.** Close Shell window.
**10.** Restart Firefox.
**11.** ***You're done.***  :guitar:

---

### Post by apricot on 2012-04-03
There's no option version for chrome, just from ubuntu repository 32 bit version, or from adobe labs beta version, neither one is working. Tnx, for posting.

---

### Post by Chris_Sugden on 2012-04-03
> **flyingfisch said:**
> Did you have to uninstall anything or just extract it?

EDIT: 
Never mind. Figured it out:

1. If you have Flash player 11 installed, uninstall it. Otherwise go to step 2.
2. Install flashplugin-installer by executing in terminal *sudo apt-get install flashplugin-installer*
3. Download [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml](http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml)
4. Extract libflashplayer.so and move it to /usr/lib/flashplugin-installer/

This should work in pretty much any browser. ;)



Thanks! Worked perfectly.

---

### Post by nemesisgus on 2012-04-03
Same thread here: [http://ubuntuforums.org/showthread.php?t=1948626&page=5](http://ubuntuforums.org/showthread.php?t=1948626&page=5)

---

### Post by apricot on 2012-04-04
Thank you for your effort, but that doesn't seem to work. I don't know why. I have even restored backup of disk from month ago and flash worked, but when i upgraded packages something break out.

---

### Post by nexushaxx on 2012-04-04
It's easy, because many sites use html5 and not flash

---

### Post by framil on 2012-04-12
Flash is still working on my Ubuntu 11.10 64-bit pc, but not on my 32-bit pc. I did the following:
Install google chrome browser (not chromium but chrome from google site, not your Ubuntu repositories). Flash player should now work using google chrome. Don't make chrome your default browser if you want to use firefox, and do the following:

Search where the flash file for chrome is located in your directory, it's called "libgcflashplayer.so". On my system it is located in /opt/google/chrome. Copy it to your desktop and change the name to "libflashplayer.so". Search where Mozilla Firefox keeps its "libflashplayer.so"file in your directory.  Mine was located in /usr/lib/mozilla/plugins. Close any nautilus windows. Type gksudo nautilus in a terminal so you can act as root in nautilus. Using nautilus, copy the flash file on your desktop and paste it into the */mozilla/plugins folder so that it replaces the existing file. Close nautilus and the terminal.

Thanks go to:
[http://askubuntu.com/a/120210](http://askubuntu.com/a/120210)

---

### Post by apricot on 2012-04-12
Thank you very much. You're the greatest.

I copied libflashplayer.so to /usr/lib/flashplugin-installer and now flash works both in chromium and firefox!

---

### Post by lovinglinux on 2012-04-12
Everyone downgrading, please read this: 

[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by postscarcity on 2012-04-12
I installed Google Chrome but I still can't get flash to work with Firefox. Plus when I use Chrome to view flash it's out of sync and a little choppy. Is there a good way to tweak it?

Edit: replacing libflashplayer.so got firefox to work, thank you. Is there any way to get Chrome to run flash in fullscreen any more smoothly?

---

### Post by flyingfisch on 2012-11-13
OK, the link I put in my [previous]("http://ubuntuforums.org/showthread.php?p=11803560#post11803560") post doesn't have the right version anymore. So here is what you have to do.

1. If you have Flash player 11 installed, uninstall it. Otherwise go to step 2.
2. Install flashplugin-installer by executing in terminal *sudo apt-get install flashplugin-installer*
3. Download this file: [http://www.toppagedesign.com/linux/libflashplayer.so.tar.xz](http://www.toppagedesign.com/linux/libflashplayer.so.tar.xz) (~5MB)
4. Extract libflashplayer.so and move it to /usr/lib/flashplugin-installer/

This should work in pretty much any browser. ;)

---

### Post by InQontroll on 2012-11-13
Wel i had this to.
open your ubuntu software center and search flash player there. It wil install there and work after.

At least thats what it did for me.
Greetings InQontroll.

---

