---
title: "Unity and Compiz  issues"
date: 2011-06-23
forum: General Help
---

### Post by Anthony A on 2011-06-23
I started to make some changes to the default Compiz settings in CCSM. I noticed that when I enabled some plugins that had been disabled I started to get some issues. The top panel would disappear and some launcher icons would disappear. Disabling the plugin and restarting Ubuntu would fix the problem. After doing some searches it's obvious that there are  issues with Compiz and Unity. Is there a list of what Compiz plugins should not be enabled or what settings are problems? It would save me some hassle of going through all the plugins and settings in Compiz and not knowing which ones will mess up Ubuntu. Thanks

---

### Post by inameiname on 2011-06-23
Personally I found the latest Compiz that is installed on Natty as too problematic and I downgraded it, as per this article:

[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

After it, all the problems with plugins and whatnot went away.

---

### Post by Crempel on 2011-06-23
> **inameiname said:**
> Personally I found the latest Compiz that is installed on Natty as too problematic and I downgraded it, as per this article:

[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

After it, all the problems with plugins and whatnot went away.

That's great, but when I checked the article it warned that Unity would be removed. It is only good for "classic" Gnome. But you are write, compiz is somewhat stuffed in Natty....:(

---

### Post by Crempel on 2011-06-23
Sorry about that - I meant you are right...

---

### Post by Blasphemist on 2011-06-23
There seems to be different levels of how well we can mess things up between compiz and unity. This is from launchpad and covers different levels of reset/replace that may be needed.
> tried unity --reset command in tty but it did not work

And rebooted?

Maybe try this then.
```
unity --replace
```

If nothing helps reset Compiz configuration via tty and reboot. (Close all GUIs and save your work)
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot
```

[http://manpages.ubuntu.com/manpages/natty/en/man1/gconftool-2.1.html](http://manpages.ubuntu.com/manpages/natty/en/man1/gconftool-2.1.html)

Before playing with CCSM again, export the default .profile in order to reset after an occasional misconfiguration or press button 'reset' under 'preferences'.
Test plugins successive, if it works export profile files and give it a meaningful name.
Some plugins conflict with each other, such as wall vs. cube, static switcher vs. ringswitcher.
Workaround by disabling 'automated plugin sorting', after done enabling it again.
Examples.
[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/156305](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/156305)
[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty)

---

### Post by Anthony A on 2011-06-23
it sounds like there is no clear list of what plugins and settings mess up Unity and you're just spinning the wheel hoping one doesn't blow up your install if you change the default Compiz settings.

---

### Post by inameiname on 2011-06-23
Oh I'm sorry about that. I wasn't aware/forgot it remove Unity. I don't use it anyway, so if it did remove it, I wouldn't have known. 

The relationship between the new Unity and Compiz is certainly a budding one. Much like when Plymouth came to be in Ubuntu, or Pulseaudio; anything new will cause issues until people like you and me help those who make the programs fix the bugs. 

Maybe in time there will be a more concrete list of what messes up between the two, and what doesn't.

---

### Post by Anthony A on 2011-06-23
After several hours of playing around with CCSM here is what I have learned. I could change any setting I wanted to on the plugins that are enabled in CCSM by default and they would work with no issues. The problem is that every plugin that I enabled that was not enabled by default in CCSM messed up. I was not able to enable a single plugin that was not enabled by default without the top panel disappearing. Fortunately disabling the plugin and restarting Ubuntu fixed it. So the bottom line is that when using Unity and Compiz leave the plugins that are disabled by default alone.

---

### Post by Blasphemist on 2011-06-23
> **Anthony A said:**
> After several hours of playing around with CCSM here is what I have learned. I could change any setting I wanted to on the plugins that are enabled in CCSM by default and they would work with no issues. The problem is that every plugin that I enabled that was not enabled by default in CCSM messed up. I was not able to enable a single plugin that was not enabled by default without the top panel disappearing. Fortunately disabling the plugin and restarting Ubuntu fixed it. So the bottom line is that when using Unity and Compiz leave the plugins that are disabled by default alone.

This hasn't been my experience. I have changed a number of settings, and have had to reset a couple times. Usually, if the panel goes away when making a change, I just reboot and back it comes, along with what I changed. I can't say that I've figured out what breaks things and what doesn't but I know I'm not at the default and I do pay attention to the prompts I get on dependent settings.

---

### Post by Anthony A on 2011-06-23
> **Blasphemist said:**
> This hasn't been my experience. I have changed a number of settings, and have had to reset a couple times. Usually, if the panel goes away when making a change, I just reboot and back it comes, along with what I changed. I can't say that I've figured out what breaks things and what doesn't but I know I'm not at the default and I do pay attention to the prompts I get on dependent settings.

So are you saying if I change a setting and it makes the panel disappear I can reboot and not change the setting back and after the reboot the top panel is back to normal and the setting keeps?

 Update: After changing a setting that made the top panel disappear I rebooted without undoing the setting change and the top panel was back to normal and the setting kept and worked.  I had been undoing the setting before rebooting. What a PITA though to have to reboot after I change any non default plugin setting.

---

### Post by Blasphemist on 2011-06-23
> **Anthony A said:**
> So are you saying if I change a setting and it makes the panel disappear I can reboot and not change the setting back and after the reboot the top panel is back to normal and the setting keeps? [COLOR="Purple"]Yes, most all of the time this is the case for me.[/COLOR]

 Update: After changing a setting that made the top panel disappear I rebooted without undoing the setting change and the top panel was back to normal and the setting kept and worked.  I had been undoing the setting before rebooting. What a PITA though to have to reboot after I change any non default plugin setting.

I have not had enabling all non-default plugins cause the panel to disappear and require a reboot. Here are screen shots of my plugins, today at least.

---

### Post by wildmanne39 on 2011-06-23
Hi, I use the cube in natty and if you do it right it will work great. To get the cube working in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.

---

### Post by djpurity on 2011-06-25
I was just pissed I gave up logging on, everything locking up, all because of this compiz crap. So I somehow got the help menu to open on a blank desktop, no launcher bar no apps or top bar or anything at all, no way to find ccsm without taking all night to dig through the directories, somehow ended up online by selecting some help topic and after going to the help selection on the enhanced desktop, I got to the Ubuntu Software Center,  so I uninstalled Compiz completely. Of course I got my usual error message upon any install, upgrade, or uninstall, error message 2 returned in some subroutine or something, everytime. I can't use LibreWriter anymore bc of some setting I can't figure out changed in compiz, but now I can't use anything at all. It's a miracle I accidentally ended up on the Internet at all. I am going to just watch Hulu Plus now all night and never log off and just use google docs to write crap and print them out because my entire system is screwed. THANKS for ruining a great O/S!

I used to love ubuntu 10.10 so much I dumped windows 7 entirely for it, bought a new harddrive for my laptop and formatted it for the Ubuntu install. then I upgraded to 11.04 and was upset about OpenOffice.org being replaced, r ight after I manually removed it and installed the upgrade off their website to the latest version, and now i can't run that either, even though it says it is still installed, somewhere, but only as a package, and I hate everything about this system.

I am afraid to log off now because if I log back on, how will I access the internet? I am a computer science BS degree (yeah total BS obviously it feels like) grad and it's been quite a while since I played around and programmed my way thru Unix and Linux red hat. I guess the years passed so long without paying attention since then that I forget all about the way Linux is set up and now I am just screwed because the help menu doesn't tell you what to do when compiz totally screws your entire system into not working or having a launcher or anything at all or what to do when your main office writing program called Libre (WTF?) Writer locks up every single time all of a sudden, right before way major business proposal. Worked fine 2 days ago. What did I do to screw it up? No telling, no idea, can't figure out where to get help.

Currently downloading the Ubuntu 11.04.iso for amd64 (which I have, I know that much derrrrr), and going to try to pull a rabbit out of my *** and build a boot disc with it or something and reinstall the entire thing and lose everything I created in the process and all my memories and photos. AWESOME THANKS UBUNTU!

Man I just am pissed off, hate this computer, hate everything right now because I NEEDD TO BE FINISHING THIS DOCUMENT AND PRINT THESE PHOTOS THAT ARE WEEKS OVERDUE. WHAT CAN I DO? WHAT ? WHAT? I can't find anyone here as stupid as me to ask the right questions that I need answers to.

---

### Post by trizrK on 2011-06-25
> **Anthony A said:**
> I started to make some changes to the default Compiz settings in CCSM. I noticed that when I enabled some plugins that had been disabled I started to get some issues. The top panel would disappear and some launcher icons would disappear. Disabling the plugin and restarting Ubuntu would fix the problem. After doing some searches it's obvious that there are  issues with Compiz and Unity. Is there a list of what Compiz plugins should not be enabled or what settings are problems? It would save me some hassle of going through all the plugins and settings in Compiz and not knowing which ones will mess up Ubuntu. Thanks
Yes there are problems.
Try GNOME

---

### Post by djpurity on 2011-06-25
Okay I reinstalled compiz and here is the crap it says, as usual, "Installetion FAILED" -- (all my attempts to install, uninstall, or upgrade or downgrade all "FAIL" yet they show up in the system as if they didn't fail.... so I don't know if this is a fail or an epic fail....)


installArchives() failed: Selecting previously deselected package python-compizconfig.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 330297 files and directories currently installed.)
Unpacking python-compizconfig (from .../python-compizconfig_0.9.4-0ubuntu1_amd64.deb) ...
Selecting previously deselected package compizconfig-settings-manager.
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.9.4-0ubuntu2_all.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3.1) ...
/var/lib/dpkg/info/bcmwl-kernel-source.postinst: 53: Syntax error: "fi" unexpected (expecting ";;")
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up python-compizconfig (0.9.4-0ubuntu1) ...
Setting up compizconfig-settings-manager (0.9.4-0ubuntu2) ...
Processing triggers for python-central ...
Errors were encountered while processing:
 bcmwl-kernel-source
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3.1) ...
/var/lib/dpkg/info/bcmwl-kernel-source.postinst: 53: Syntax error: "fi" unexpected (expecting ";;")
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2

---

