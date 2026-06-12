---
title: "BBC iplayer flash"
date: 2011-12-19
forum: General Help
---

### Post by agkq62 on 2011-12-19
I am running Ubuntu on two computers, 9.10 and 11.10 and both have the same problem with iplayer needing an upgrade to Flash Version10.1.0.

I have tried the Adobe link which shows two files .tar.gz and .rpm and have downloaded both but I am not clever enought to work out what to do with them.

I have also tried a search and used the Terminal to remove and reinstall flash but that says I have the latest version. Youtube play fine.

Could some kind person talk me throught what to do with the .tar or .rpm  files.

Thanks.

---

### Post by philinux on 2011-12-19
> **agkq62 said:**
> I am running Ubuntu on two computers, 9.10 and 11.10 and both have the same problem with iplayer needing an upgrade to Flash Version10.1.0.

I have tried the Adobe link which shows two files .tar.gz and .rpm and have downloaded both but I am not clever enought to work out what to do with them.

I have also tried a search and used the Terminal to remove and reinstall flash but that says I have the latest version. Youtube play fine.

Could some kind person talk me throught what to do with the .tar or .rpm  files.

Thanks.

First off right click on the flash in BBC Iplayer and let us know what version it thinks you are using. Then in a terminal do

apt-cache policy flashplugin-nonfree

---

### Post by flipper T on 2011-12-19
install & run the flash aid addon in firefox

this solves 99% of known flash problems

---

### Post by philinux on 2011-12-19
> **flipper T said:**
> install & run the flash aid addon in firefox

this solves 99% of known flash problems

+1 [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by agkq62 on 2011-12-20
Thanks for the replies, I'll have try tonight.

---

### Post by agkq62 on 2011-12-20
Sorry still no luck.

Can't find the flash version by right click

Installed Flash Aid but it doesn't seem to have done anything

Terminal says

maxwell@maxwell-laptop:~$ apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: (none)
  Candidate: 10.0.45.2ubuntu0.9.10.1
  Version table:
     10.0.45.2ubuntu0.9.10.1 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
     10.0.32.18ubuntu1 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
maxwell@maxwell-laptop:~$

---

### Post by agkq62 on 2011-12-20
Thought I was getting somewhere. Found the icon for Flash Aid, ran the Wizard and when I click play in iPlayer Firefox shuts down. Hmm.

Tried "install stable Flash" and iPlayer is again asking for Flash Player download.

---

### Post by flipper T on 2011-12-20
just to clarify, are you trying to install the iplayer desktop app or just stream the programmes ?

---

### Post by agkq62 on 2011-12-20
> **flipper T said:**
> just to clarify, are you trying to install the iplayer desktop app or just stream the programmes ?

Just stream the programmes from the iplayer web page [http://www.bbc.co.uk/iplayer/](http://www.bbc.co.uk/iplayer/)

---

### Post by Frogs Hair on 2011-12-20
What Firefox version are you using on the 9.10 computer ? The 9.10 repository would be a problem because the release is no longer supported .

Flash Aid has to be compatible with version of Firefox you are using so an old version may be a problem . This should not affect the 11.10 computer though . 

I could only test BBC radio , which works fine , but TV is unavailable where I live .

---

### Post by Haventfoundme on 2011-12-20
Go to [this adobe site]("http://get.adobe.com/flashplayer/otherversions/") and download the ubuntu version. Adobe recognizes firefox an automatically associates it with Red Hat/raw linux. When you hit the download button it will ask you if you want to open it up in the Ubuntu Software Center(11.10). Go ahead and add it to the software center and you will be able to install it from the Ubuntu Software center. I just did this last night because google chrome didn't come with flash<I assumed it did>. Now I can access youtube and all that other flash junk.
Check out the screenshots and let us know how it worked out.

---

### Post by agkq62 on 2011-12-23
Thanks for all your input. Frogs Hair was correct I am running FF 3.5.3 on the 9.10 laptop. 11.10 machine is now fine after using Flash Aid. I checked on another machine running Ubuntu and that had FF 3.6.3 and was fine. I have downloaded FF3.6.3 as a tar.bz2 file.

Could some kind person talk me through how to install.

Thanks again

---

### Post by valvegrid on 2011-12-23
If you are the only person using the computer then you can just extract Firefox tar.bz2 file to your home folder and run it from there. When its extracted then just look for a file called firefox.bin and double click it and Firefox should open.

You can then make a link to it from Preferences>Menu.

I often do this if I just want to play around with a new version of Firefox if I don't want to install it system wide.

---

### Post by agkq62 on 2011-12-23
Well blow me down, that worked, even the existing FF icon. Thanks everybody.

---

