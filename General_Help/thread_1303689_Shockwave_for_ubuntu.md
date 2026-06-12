---
title: "Shockwave for ubuntu?"
date: 2009-10-28
forum: General Help
---

### Post by x C0MMAND0 x on 2009-10-28
I go to [http://www.calcchat.com/](http://www.calcchat.com/) and then click on "Click Here" for free access.

It says I am missing plugins and won't find what I need.  I need to install Shockwave...I have not heard of this before in Linux and I would like to know,

Is there a way to install shockwave in linux?  I guess I could install IE in wine, then install shockwave that way...but I don't like workarounds and I don't like wine if I can avoid it.

---

### Post by Anonymousable on 2009-10-28
The only ways of doing this involve wine. Adobe/Macromedia haven't, and never will make a linux version of shockwave.

---

### Post by x C0MMAND0 x on 2009-10-28
How come they "never will"?

---

### Post by Anonymousable on 2009-10-28
"Not worth the trouble."

Not my opinion, but pretty much sums up theirs :(

---

### Post by philinux on 2009-10-28
Not sure how old this stuff is.

[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

---

### Post by dj-toonz on 2009-10-28
Or for the people who want there hand holding, here it is it in full

Installation

Unfortunately, the Shockwave player is only available for Windows. On a PC, it may be possible to run Shockwave under Ubuntu using Wine and running the Windows versions of Firefox and the Shockwave player. (Wine does not work on PowerPC and may not work as expected on 64-bit PCs.) You can then use mozplugger, a program that lets you "embed" other programs in your web browser.

First, install the wine and mozplugger packages (for information on how to do this, see InstallingSoftware).

sudo apt-get install wine mozplugger

You then need to install the Windows version of Firefox (yes, you read that right). Download it from Mozilla's web site. Choose to open the installer with Wine and follow the on-screen instructions.

When the installation has finished, you then have to go to a web site that requires Shockwave, and choose to get the missing plugin. Again, follow the on-screen instructions, and when the plugin has installed and is working, you may close Firefox.

Now you need to configure mozplugger to use the Windows version of Firefox for Shockwave files. From a terminal, type:

sudo gedit /etc/mozpluggerrc

Add the following two lines to the end of the file:

application/x-director: dir,dcr,dxr,cst,cct,cxt,w3d,fgd,swa: Macromedia Director file
        swallow(firefox.exe) fill stream: wine "C:\\Program Files\\Mozilla Firefox\\firefox.exe" -chrome "$file"

Finally, you need to make Firefox reload the plugin database. Close all Firefox windows and run this command in a terminal:

rm ~/.mozilla/firefox/*.default/pluginreg.dat

In later versions this file may have been moved:

rm ~/.mozilla/firefox/RANDOM-STRING/pluginreg.dat

Replace "RANDOM-STRING" with the random string your Mozilla has assigned for your computer.

Removal of pluginreg.dat wasn't needed with Ubuntu 9.04 and Firefox 3.0.14.

Congratulations, you should now have a working, if not convuluted, Shockwave setup. You can test it on the Test Macromedia Shockwave & Flash Players page. However, some Shockwave objects may not work. See the issues and workaround solutions section below.

Note: If you want to use Shockwave from multiple user accounts on the same machine, you have to repeat the following steps while logged in as each user: download, install, and launch Windows Firefox; download Shockwave plugin; remove pluginreg.dat if needed.

Issues and workarounds

Objects appear in a small window of their own

Posssible causes:

    *

      Cause 1: Wine or Shockwave is still running in the background.
    *

      Workaround 1: Type this in a terminal to end all wine processes: 

killall wine-preloader -s KILL

    *

      Cause 2: mozplugger does not handle multiple objects. Unfortunately, there is no fix currently known for this. 

Firefox is asking for restoring old sessions before playing objects

    *

      Cause: Session restore is enabled in the Windows version of Firefox
    *

      Workaround 1: Type this in a terminal to end all wine processes: 

killall wine-preloader -s KILL

    * Start the Windows version of Firefox. Type "about:config" in the Location Bar and press Enter. Search for "browser.sessionstore.resume_from_crash" and double click to set it to false. 

Objects claim they're "stolen"

    *

      Cause (when using streaming): The Shockwave object expects the "Referrer" HTTP header to be set, which mozplugger does not do.
    *

      Workaround: None yet. 

Shockwave player shows "Adobe Shockwave Player is now installing" but gets no further

    *

      Cause (not verified): Shockwave Player 11 may not work under Wine
    *

      Workaround: Install Windows Shockwave Player version 9.0.0.434 from [http://kb2.adobe.com/cps/186/tn_18629.html](http://kb2.adobe.com/cps/186/tn_18629.html), Adobe Technote "Stand-alone installers for Shockwave Player: previous versions only" (linked from Shockwave "Support Center" link on [http://www.adobe.com/shockwave/download/alternates/](http://www.adobe.com/shockwave/download/alternates/)).

---

### Post by GhostyGu on 2010-03-22
Hopefully, for some people that are great with the search function, this fixed my issue with Runescape and some facebook apps (petville, zoo world etc). Of course, i don't play such things - but i now have a very very happy wife. Thank-you to the poster, if you only knew the extent of the things i've tried over the last two weeks! Thank-you.

---

### Post by SabreWolfy on 2010-06-12
I thought Shockwave = Flash? So there is a variant of "Flash" that still requires an application that can't be run on Ubuntu? :(

---

