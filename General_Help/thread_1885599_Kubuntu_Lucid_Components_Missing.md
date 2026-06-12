---
title: "Kubuntu Lucid Components Missing?"
date: 2011-11-23
forum: General Help
---

### Post by Valkyr333 on 2011-11-23
Hi,

I've been noticing lately that clicking a lot of the icons I've put on my desktop for installed programs seems to yield an error message saying the program doesn't exist. Looking into Ubuntu Software Center, it seems the programs aren't installed, but when I tell it to install them again, the icons work and all my previous data from these programs is right there with it as if there were never a problem. Then today, while looking for the best way to interface with a Bluetooth connection, I ran into a 404 error:

[http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

The error message reads that this software source couldn't be found and either is no longer available or couldn't be connected to due to a network problem (of course I made sure to check my Internet connection.) I also noticed that after having to re-install System Settings, it seems most of the icons that used to be in there are nowhere to be found. I assume this must have something to do with the missing repository. KDE has also gotten noticably slow lately. Right-click drop-down menues seem to struggle to open, and I'm not sure if that's related to any of the above, but I figured it was worth mentioning.

Has anyone else run into this stuff lately? If so, what would you suggest?

Thanks!

---

### Post by plucky on 2011-11-23
[http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)

does not exist. See [http://ppa.launchpad.net/sevenmachines/](http://ppa.launchpad.net/sevenmachines/)

Remove from your Software Sources and the 404 error will go away.

>  I also noticed that after having to re-install System Settings, it seems most of the icons that used to be in there are nowhere to be found. I assume this must have something to do with the missing repository. KDE has also gotten noticably slow lately. Right-click drop-down menues seem to struggle to open, and I'm not sure if that's related to any of the above, but I figured it was worth mentioning.

This sounds more like a memory or Hard drive problem.Check the logs for errors.


Good Luck

---

### Post by Valkyr333 on 2011-11-23
Thanks for your response.

I'm assuming you're talking about the sub-folders of Root/var/log/. If that's correct, then what sub-folder would have information about memory or hard-drive errors? Looking over these gives me some guesses, but it's still pretty foreign to me.

*Update: I signed off/shut down this morning and left for the day, then came back and turned the computer on only to find that my KDE Desktop is now completely gone. The only options I get at the login screen are "Gnome," "Failsafe Gnome" and one other, I can't remember exactly but I think it's "X-Term" or something like that. This is getting ridiculous. My system has been slowly forgetting all about the installed KDE components and now it seems to have done so almost completely. When I turn on Ubuntu Software Center, though, a lot of the KDE-native programs and packages are still showing as being installed.

*Update II: I went looking around with Google and found [this]("http://news.softpedia.com/news/How-to-Install-KDE-SC-4-5-0-on-Ubuntu-10-04-153097.shtml") page on installing KDE 4.5.0. on Ubuntu Lucid. Updating the "Software Sources" information found me with another error saying yet again that the information couldn't be found, possibly because of a network error (once again, internet connection's running fine) and that if possible, an older version would be used. It may just be that I'm exhausted, but I'm feeling pretty thoroughly without a clue on this one. I haven't the slightest idea why it would be slipping like this.

*Update III: I tried restoring packages with "sudo apt-get update" but that got me another "unable to connect" error with respect to the getdeb site. Could there be something missing in my system that I haven't filled in, or haven't filled in properly that would allow connection to these sites, or is it possible that there's some big change in the sites that makes them unrecognizable or unreachable to the current state of my system? I'm just throwing wild guesses out there. This is really frustrating.

*Update IV: At the moment, right-click is causing open windows to crash so I can't even back up my internal files. I'm afraid to log out and/or shut down because I get the feeling Ubuntu would be even less stable by my next login.

---

