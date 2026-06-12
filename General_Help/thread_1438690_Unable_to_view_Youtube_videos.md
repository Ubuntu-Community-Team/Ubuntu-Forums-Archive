---
title: "Unable to view Youtube videos"
date: 2010-03-25
forum: General Help
---

### Post by ubun2010 on 2010-03-25
Viewing random videos on Youtube has never been a problem until now. I have used Ubuntu for a while now, and I have tried everything to fix it but nothing seems to help. I have tried to manually install flash and java programs to see if that help and still nothing.

When I first installed Ubuntu, the videos were working perfectly. And all of the sudden, it just went blank, and nothing appeared on the screen at all. No Java or flash warnings etc... I have everything enabled. Videos do not work in either Google Chrome or Firefox. 

Is there anyway I can fix this, so I do not have to go back and forth between my Windows 7 and Ubuntu?

Thanks!

---

### Post by nechus on 2010-03-25
Do you have a 32 bit or 64 bit processor. In other words, is it an Intel or an AMD processor?

---

### Post by ubun2010 on 2010-03-25
I have Intel

---

### Post by 2hot6ft2 on 2010-03-25
Personally I would just re-install flash and java and clear up any conflicts like this.
Open a terminal
Applications > Accessories > Terminal
and run these
First to make sure the medibuntu repositories are enabled. Or if you know they already are skip this one.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) and flash will be re-installed in the last command (in case there's a version conflict with what you have installed now):
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc adobe-flashplugin
```
 and last to install gecko-mediaplayer, mp3, java, flash, dvd support and divx web player support
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer
```
Close your web browser(s) and reopen one and try it.

---

### Post by Gemnoc on 2010-03-25
> **nechus said:**
> Do you have a 32 bit or 64 bit processor. In other words, is it an Intel or an AMD processor?
More to the point, is his Ubuntu a 32-bit or 64-bit install. There is no point asking if he's got a 64-bit processor if he installed the x86 (32-bit) version of Ubuntu.

On Ubuntu 64-bit, Flash support is still flaky. Adobe has still not released a final 64-bit package. The restricted packages install the 32-bit version of Flash, which causes trouble.

I'm using a prerelease 64-bit version that Adobe provides [here]("http://labs.adobe.com/downloads/flashplayer10_64bit.html"). It works better, even if it's still not perfect. (instructions to install [here]("http://www.sucka.net/2009/07/ubuntu-9-04-flash-10-0-32-18-x86_64/comment-page-1/"))

Obviously, discard this info if you are running the defauly Ubuntu 32-bit.

P.S. I am so praying for the demise of Flash!!! HTML5 FTW. ;)

---

### Post by amite on 2010-03-25
i hv problem with downloading you tube videos.when i try to download video with keepvid or savevid site it give message install java and flash while these are alredy indtalled on my computer.

---

### Post by Gemnoc on 2010-03-25
amite, your problem is unrelated to ubun2010's.

Posting your question here is like hijacking his thread.

You should create a new thread to post your question. It is also possible it has been already discussed. Have you searched the forums?

---

### Post by arnab_das on 2010-03-25
> **ubun2010 said:**
> Viewing random videos on Youtube has never been a problem until now. I have used Ubuntu for a while now, and I have tried everything to fix it but nothing seems to help. I have tried to manually install flash and java programs to see if that help and still nothing.

When I first installed Ubuntu, the videos were working perfectly. And all of the sudden, it just went blank, and nothing appeared on the screen at all. No Java or flash warnings etc... I have everything enabled. Videos do not work in either Google Chrome or Firefox. 

Is there anyway I can fix this, so I do not have to go back and forth between my Windows 7 and Ubuntu?

Thanks!

i think the safest way out right now would be to install ubuntu restricted extras.

sudo apt-get install ubuntu-restricted-extras

if that doesnt resolve the problem, do something.

sudo apt-get clean
sudo apt-get install ubuntu-restricted-extras

(this process will clean up the archived installation files and download the necessary files from the server afresh. this does work)

there is indeed a 64 bit version of flash. its still in beta however and from my experience at least, i can say that its very buggy. install the ubuntu restricted extras again and u shall be fine.

---

### Post by Monotoko on 2010-03-25
Have you tried other flash sites? Do they work or is it actually flash thats causing the problem?

If other sites work, you could try the HTML5 beta on youtube, means you dont need flash to view videos

[www.youtube.com/html5](www.youtube.com/html5)

---

### Post by gychang on 2010-03-27
thanks works for me.  now can watch all those video on youtue on ubuntu...;)

gychang

> **2hot6ft2 said:**
> Personally I would just re-install flash and java and clear up any conflicts like this.
Open a terminal
Applications > Accessories > Terminal
and run these
First to make sure the medibuntu repositories are enabled. Or if you know they already are skip this one.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) and flash will be re-installed in the last command (in case there's a version conflict with what you have installed now):
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc adobe-flashplugin
```
 and last to install gecko-mediaplayer, mp3, java, flash, dvd support and divx web player support
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer
```
Close your web browser(s) and reopen one and try it.

---

