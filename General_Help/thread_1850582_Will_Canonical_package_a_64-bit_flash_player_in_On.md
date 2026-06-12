---
title: "Will Canonical package a 64-bit flash player in Oneiric?"
date: 2011-09-26
forum: General Help
---

### Post by CoreyB. on 2011-09-26
Since Adobe is going to release the final version of Flash Player 11 in early October, and Adobe will release a 64-bit Flash player, will Ubuntu finally change the amd64 version of flashplugin-nonfree to a 64-bit native Flash Player in Oneiric, or will it have to wait until Oneiric+1?

---

### Post by cariboo on 2011-09-27
All Canonical does is include a flash installer, flash is downloaded from Adobe when you run the installer.

---

### Post by drawkcab on 2011-09-27
Ya but the question is which one will it install?  The 64 bit beta is a huge improvement as far as I can tell.

---

### Post by garvinrick4 on 2011-09-27
Is this what you are looking for.

---

### Post by ninjaaron on 2011-09-27
> **drawkcab said:**
> Ya but the question is which one will it install?  The 64 bit beta is a huge improvement as far as I can tell.

Whichever is Adobe's current release version.  If Flash 11 is out by then, the installer will get it.

---

### Post by CoreyB. on 2011-10-03
The final Flash 11 is out.  Flash 11 is the first to officially support 64-bit.

So the question is, when Oneiric comes out and I open up Synaptic and install flashplugin-installer, will it download the 64-bit version or the 32-bit version with the plugin wrapper like it does with Natty?

---

### Post by 8_Bit on 2011-10-03
I certainly hope so. When I ran the 32-bit flash player on my 64 bit system, I encountered numerous errors, crashes, and strange graphical glitches. When I switched to the 64 bit alpha, that all went away.

---

### Post by garvinrick4 on 2011-10-03
Download the install_ flash_player_11_linux.x86_64.tar.gz. from adobe and install.
Remove all traces flash first.
```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
```One at a time in terminal
```
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```Download the install_ flash_player_11_linux.x86_64.tar.gz. from adobe.com and install.
Lets say to Desktop:
```
cd Desktop
``````
tar zxvf install_flash_player_11_linux.x86_64.tar.gz
``````
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```Done

Or will be in [COLOR=Red]Flash aid as add-on in Firefox[/COLOR] soon and or Ubuntu Repo's when arrives.
Or a ppa when arrives. Under Adobe flash below.
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
##Lots of ways to install choice of flash. found is better to make sure remove all traces of flash then install new version as above [COLOR=Red]if not in repo's[/COLOR].
Or just use [COLOR=Red]Flash Aid as add-on in Firefox[/COLOR] it runs a script for you and removes old flash and installs your choice.
Of course this is just one users opinion on subject.

---

### Post by cariboo on 2011-10-04
it's much easier to use SevenMachines ppa, locate here:

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

@CoreyB., if you really want to know, you could always ask on the Ubuntu-Devel mailing list, or create a wishlist bug on Launchpad.

---

### Post by garvinrick4 on 2011-10-04
Both the same it seems just different path, both use sevenmachines.
Seems every ppa in ubuntuupdates.org has a corresponding ppa in launchpad.net
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
[https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash")

---

### Post by CoreyB. on 2011-10-05
It looks like we might get it :D

[https://answers.launchpad.net/ubuntu/+source/flashplugin-installer/+question/173230]("https://answers.launchpad.net/ubuntu/+source/flashplugin-installer/+question/173230")

---

### Post by ninjaaron on 2011-10-05
> **cariboo907 said:**
> it's much easier to use SevenMachines ppa, locate here:

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

@CoreyB., if you really want to know, you could always ask on the Ubuntu-Devel mailing list, or create a wishlist bug on Launchpad.

As someone who knows more about this than myself, do the devs also read the stuff on the ayatana website, Ubuntu Brainstorm, or whatever it's called?

---

### Post by CoreyB. on 2011-10-06
Now Natty and Oneirc have 64-bit flash in the Canonical Partner repo under the adobe-flashplugin package.

---

### Post by nPoc on 2011-10-26
Hey thanks a ton, they really need to remove the flashplugin* packages from the repos, and update the package title to say flash plugin version 11 instead of flash plugin version 10.

---

### Post by AbdRahim on 2011-10-29
None of these work in FireFox in Oneiric. Installed sveral times from firefox rebooted even and firefox say plugin missing.

---

### Post by MoeNeigh on 2011-12-10
I installed Google Chrome in kubuntu oneiric and Chrome found Adobe flash player 11 from some third party sources and installed it for me. Works beautifully in Chrome.

However, I still can't get flash player 11 to install in firefox. I've tried installing kubuntu-restricted-extras, but Adobe flash player 11 still won't install in firefox.

Just wondering how Google chrome was able to do this.

---

### Post by gandaran on 2011-12-10
> Just wondering how Google chrome was able to do this
google-chrome 32-bits has built-in flash just like the windows versions and when you install the chrome updates it will come with new flash version too.
for your problems with system installed flash for firefox try the firefox [flash-aid addon]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") to remove conflicting flash plugins and install the right one.

---

