---
title: "How to unistall FireFox Flash Plug-in?"
date: 2009-10-07
forum: General Help
---

### Post by Soujiro Seta on 2009-10-07
Hello people. I have just installed ubuntu, and the automatic firefox plugin for flash movies (for example: youtube videos) does not work like I would like it to do... So I want to remove it completely from my system to install another plug-in. I tryed using the Janitor app and it doesn't find it. I also might be too newb to know how to uninstall from the Synaptic Package Manager tool. Any help is appretiated. Thank you in advanced.

---

### Post by ikisham on 2009-10-07
```
sudo apt-get remove flashplugin-nonfree
```
But I wonder why it's not working for you. It usually works very well.

---

### Post by Soujiro Seta on 2009-10-07
Thank you. It's not that it doesn't work. It just doesn't work very well. The player on youtube it first appears with a big "Play" sign. When I click it, it starts. And the player is a little bit laggy. The "Pause" symbol is not looking good, its like the icon is badly drawn.

Yesterday I was using it before uninstalling and instead of doing automatic installation of software I just downloaded it from macromedias' site. It worked just like it should be working. Today I had to reinstall everything and I just let firefox download the tool automatically and it looked wierd and lagged a bit. 

Anyway, just tryed the command and it says that the package could not be found. I guess I'll just reinstall again. Anyway I didn't had many information in it.

Thanks.

---

### Post by laplace/d on 2009-10-07
open the terminal and type:
 
```
aptitude search swf | grep mozilla
```

what's the output?

---

### Post by gdonwallace on 2009-10-07
Another option is to use Synaptic.

From Menu System -> adminstration -> Synaptic Package Manager.  In the quick search type FIREFOX (lowercase) and it will list all the add-ons and updates for firefox.  You can install swf from there, and make sure that the firefox-nonfree-plugin is installed. (Will have a green box next to it)  If you need to / want to install any of these, right click on the box and choose install.  Then click the apply button.  

I have both installed and youtube works fine for me.

---

### Post by Soujiro Seta on 2009-10-07
Console Output:
i   swfdec-mozilla                  - Mozilla plugin for SWF files (Macromedia F

---

### Post by laplace/d on 2009-10-07
if 
```
aptitude search swf | grep mozilla
```

doesnt give you any output just type

```
aptitude search swf
```

what does it say now?

---

### Post by laplace/d on 2009-10-07
```
**i** swfdec-mozilla - Mozilla plugin for SWF files (Macromedia F
```

what's critical there is the 'i' it means it installed, and that package sucks for watching videos on youtube.

```
sudo aptitude remove swfdec-mozilla
```

then

```
sudo aptitude install flashplugin-nonfree
```

i'm not sure if it's gonna work if u just restart the X so reboot and it should be working fine.

---

### Post by Soujiro Seta on 2009-10-07
Thank you very much! Managed to uninstall it. Installed the correct package. And it works perfectly. Thank you again.

---

### Post by laplace/d on 2009-10-07
no problem, now mark the thread as [SOLVED]

---

### Post by jamily on 2009-10-24
"A man has to know his limits" -- Dirty Harry

I am new to Ubuntu and despite a few problems, I love it.  One of the biggest problems is I can't get flash to work in firefox.  This is a big problem.  I have tried quite a few things.  I even upgraded firefox to version 3.5.3 when I couldn't get flash to work with the original firefix, hoping this will help (strangely the "check for upgrades" is not active in the Help menu in Firefox 3.5.3).

I am running 64bit Ubuntu 9.04.

I have checked Synaptic Package Manager, searching under "flash" and made sure that all flash stuff is uninstalled.  Then I do the following in the bash shell (making sure firefox is closed first):

sudo aptitude purge flashplugin-nonfree
sudo apt-get clean && sudo apt-get autoremove
sudo aptitude install flashplugin-nonfree

Everything looks like it goes fine.  However, when I open firefox and go to [www.youtube.com](www.youtube.com) and try to play a video, I can't even see the video.  Instead I get the message:

"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

A contributor by the name of Zita, wrote on April 6th 2009 that

"flashplugin-nonfree is still 32-bit (as far as I know) so that might be the valid reason for 64-bit users ...
I agree with You in the sense that flashplugin-nonfree is more reliable for less demanding users but You must agree that there is a difference in quality of use for more demanding users on 64-bit installations ...
we have to have a way of circumventing the fact that 64-bit plugins exists and is easily installable but is not yet offered through regular ways ..."

I don't know what to make of this.  I heard that firefox is still 32 bit (but as I mentioned, my system is 64 bit).

Next I uninstalled flashplugin-nonfree again from Synaptic Package and did a 

sudo aptitude purge flashplugin-nonfree
sudo apt-get clean && sudo apt-get autoremove

then I downloaded "libflashplay-10.0.32.18.linux-x86_64.so.tar.gz" from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html).  Uncompressed
and did a 

sudo mv libflashplayer.so /usr/lib/mozilla/plugins

I then rebooted and it still did not work.  

Thinking maybe java was required and not working I installed ubuntu-restricted-extras from Synaptic Package Manager and tried again.  Still does not work.

Any ideas?  Looking on the web this seems to be a major problem (maybe the biggest?) users are having with Ubuntu.  If anyone could help, I would be mucho grateful.

---

### Post by gatordude on 2009-11-24
The fix mentioned on the first page worked for me. I had some flash player installed (I have no idea how, and no it wasnt from porn it was from a Fench Ubuntu themes website) and when I tried to fix it I had such an issue because when I went into the Package manager I could not update firefox or even install the flash player from there because of this :

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F


But after reading for several days I found the fix as poasted by  "[laplace/d]("http://ubuntuforums.org/member.php?u=676533")"


 	Code:
 	**i** swfdec-mozilla - Mozilla plugin for SWF files (Macromedia F 
what's critical there is the 'i' it means it installed, and that package sucks for watching videos on youtube.

 	Code:
 	sudo aptitude remove swfdec-mozilla 
then

 	Code:
 	sudo aptitude install flashplugin-nonfree 
Thank for that bit of info was nice to have a fix for an issue that came up.

---

