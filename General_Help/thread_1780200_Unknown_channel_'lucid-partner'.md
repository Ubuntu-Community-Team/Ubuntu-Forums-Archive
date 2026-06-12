---
title: "Unknown channel 'lucid-partner'"
date: 2011-06-11
forum: General Help
---

### Post by Bucky Ball on 2011-06-11
Hi all,

Have just done a minimal install of Ubuntu 10.04 LTS with Xfce desktop environment. Howls along and I'm loving it. Adding things I need as I go but have created a bit of a problem. 

I don't want to install the Medibuntu repositories to get Flash and Java as that's all I want for now. I want to install them manually. I went to the Adobe Flash download  page and selected the option 'apt for 10.04' then clicked download. It asked if I wanted to open the file with 'aptxxx' (I don't remember what was after apt).

Problem is it didn't work but I'd clicked 'Use this program as default for these files'. I should have saved the file (like usual) and done it that way. Who knows, may have ended up with a similar problem.

Anyway, now, when I click download from the Flash page, I get the error message you will find in the screenshot I've attached.

Any ideas more than appreciated ...

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Bucky Ball said:**
> Hi all,

I don't want to install the Medibuntu repositories to get Flash and Java as that's all I want for now..

Why??? :(

Just enable it, use synaptic to grab what you need, and disable medibuntu when you are through.

If you want to do it the hard way just compile them manually instead, and you will have better results.

---

### Post by Bucky Ball on 2011-06-11
> **linuxinstalledfromhdd said:**
> 
If you want to do it the hard way just compile them manually instead, and you will have better results.

It would be pretty easy if I hadn't have made the boob at the beginning. Java was a cinch and Flash is also if I could open the 'APT for 10.04+' which is what I'm trying to figure out and is the point of this thread. 

Currently battling with the Flash tar.gz file instead, which won't cooperate at all, but that is another story. The point of this thread is to fix the problem of the default application giving me an error whenever I attempt to open an 'apt' filetype (which will happen whenever I come across one of those filetypes, not just from the Adobe Flash APT file).

That's the bit I need a solution for. Cheers. ;)

---

### Post by gandaran on 2011-06-11
> **Bucky Ball said:**
> It would be pretty easy if I hadn't have made the boob at the beginning. Java was a cinch and Flash is also if I could open the 'APT for 10.04+' which is what I'm trying to figure out and is the point of this thread. 

Currently battling with the Flash tar.gz file instead, which won't cooperate at all, but that is another story. The point of this thread is to fix the problem of the default application giving me an error whenever I attempt to open an 'apt' filetype (which will happen whenever I come across one of those filetypes, not just from the Adobe Flash APT file).

That's the bit I need a solution for. Cheers. ;)
the apt for ubuntu option installs flash from the ubuntu system repository's, did you disable any repository? and medibuntu doesn't have any flash or java, sun-java and adobe-flashplugin package are from the canonical archive partner repository which you have to enable in software sources.
or why not install the official ubuntu flash package?
```
sudo apt-get install flashplugin-installer
```

---

### Post by oldos2er on 2011-06-11
I don't think either flash or java is in Medibuntu; Sun java is in the partners repo. Anyway, try FlashAid for installing flash, [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by Bucky Ball on 2011-06-12
No repositories removed but not sure if the Minimal Install installs the same repos as the regular Desktop install. The partners are there, though. If anyone has any info on that, fire away.

Oldos2er, Flash Aid worked fine. 

Back to the original issue: How do I stop the wrong app from popping up as default when I hit a APT file like the one encountered on the Adobe Flash download site???

---

### Post by linuxinstalledfromhdd on 2011-06-12
> **Bucky Ball said:**
> No repositories removed but not sure if the Minimal Install installs the same repos as the regular Desktop install. The partners are there, though. If anyone has any info on that, fire away.

Oldos2er, Flash Aid worked fine. 

Back to the original issue: How do I stop the wrong app from popping up as default when I hit a APT file like the one encountered on the Adobe Flash download site???

You need to install partner and independent repos:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

They are almost 1/3 the way down the list.  Install those repositories and you should be all good. :)

---

### Post by WorMzy on 2011-06-12
> **Bucky Ball said:**
> Back to the original issue: How do I stop the wrong app from popping up as default when I hit a APT file like the one encountered on the Adobe Flash download site???

This might be a shot in the wrong direction, but can you post the contents of your ~/.local/share/applications/mimeapps.list?

---

### Post by Bucky Ball on 2011-06-12
> **linuxinstalledfromhdd said:**
> You need to install partner and independent repos:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

They are almost 1/3 the way down the list.  Install those repositories and you should be all good. :)

I'm using 10.04 LTS. And I am using xfce4, not Gnome. Attempting to install the components I need individually rather than by 'adding another repo' as I am attempting to keep this install slim, no fat, and does only what I need it to, nothing more (one filemanager, one text editor, one browser, etc ...).

> **WorMzy said:**
> This might be a shot in the wrong direction, but can you post the contents of your ~/.local/share/applications/mimeapps.list?

I have the directory ~/.local/share/ and there is nothing in it. Minimal install doesn't load a lot of things that are in the regular install. That might be one of them. 'Additional Drivers' is not installed for instance. I have about seven entries in System. 

Thanks for the ideas ... ;)

---

### Post by gandaran on 2011-06-12
> **Bucky Ball said:**
> No repositories removed but not sure if the Minimal Install installs the same repos as the regular Desktop install. The partners are there, though. If anyone has any info on that, fire away.

Oldos2er, Flash Aid worked fine. 

Back to the original issue: How do I stop the wrong app from popping up as default when I hit a APT file like the one encountered on the Adobe Flash download site???
do you have ubuntu software center installed? it's needed to run the apt file on adobe website, how to stop the wrong app popping up sorry that I don't know.

---

### Post by yetiman64 on 2011-06-12
> **Bucky Ball said:**
> ....Back to the original issue: How do I stop the wrong app from popping up as default when I hit a APT file like the one encountered on the Adobe Flash download site???

Not sure this is your problem, but there is a firefox setting that determines what opens an apt link in the browser (I assume you are on firefox). Edit > Preferences > Applications Tab > For content type "apt" set the action as apturl. 

Being a minimal install you may need to install apturl first with ```
sudo apt-get install apturl
``` If apturl is installed and still not working you could set the firefox option I mention above to "Always ask" that should give you back the option to download the file. 
Good Luck.

---

### Post by jocko on 2011-06-12
The apt links in firefox does not actually download and install anything by itself. It opens up a package manager, searches for the package and installs it. If you have not enabled the repo the package is in, you will just get a message that the channel is unknown...
So if you want to install adobe flash using an apt link (which gives exactly the same result as installing it directly from the package manager) you need to enable the repo that the package is in.
There is nothing in that repo that will give you any extra bulk. You will just be able to install a few extra packages IF you yourself choose to. Nothing will be installed without you doing it yourself.

If you want to install flash there are two ways that I recommend:
If you run a 32 bit (x/k/l)ubuntu, just get it from the partner repo.
If you run a 64 bit (x/k/l)ubuntu and want 64 bit flash (better performance and more stable than running the 32 bit plugin in a wrapper), install the firefox extension [Flash-Aid]("https://addons.mozilla.org/sv-se/firefox/addon/flash-aid/").

---

### Post by Bucky Ball on 2011-06-12
> **yetiman64 said:**
> Not sure this is your problem, but there is a firefox setting that determines what opens an apt link in the browser (I assume you are on firefox). Edit > Preferences > Applications Tab > For content type "apt" set the action as apturl. 

I'm thinking you are pretty close to the money there, my friend. apturl is certainly the app in question. What may have happened is when I was asked if I'd like to open the file with apturl, I agreed and set the machine to use it by default for that filetype. Problem? Apturl probably wasn't installed. 

I will log in to the 10.04 minimal install and check. I'm having trouble with network now, though. I updated the wireless driver (all was working fine before) and it has killed all network, wired and wireless! Just about to post about that but get back to you ...

Thanks for the clues ...

---

### Post by Bucky Ball on 2011-06-12
> **yetiman64 said:**
>  If apturl is installed and still not working you could set the firefox option I mention above to "Always ask" that should give you back the option to download the file. 
Good Luck.

Yep, that worked. Gave me back the option to use another app. Cheers, thanks for that tip, Yetiman. ;)

---

### Post by yetiman64 on 2011-06-12
> **Bucky Ball said:**
> Yep, that worked. Gave me back the option to use another app. Cheers, thanks for that tip, Yetiman. ;)

You're welcome.

> I'm having trouble with network now, though. I updated the wireless  driver (all was working fine before) and it has killed all network,  wired and wireless! Funny thing you mention losing your networks on a minimal install, I just did the same here after installing a video driver. Still scratching my head as to how installing a vid driver can take out a wireless and a ethernet adapter in one go :lol:. The fun of minimal installs hey ;)

---

### Post by Bucky Ball on 2011-06-12
I'm loving it so far. I actually installed the latest (apparently) Realtek driver for my card and it killed wired and wireless, don't ask me how. Tracked down the old one, reinstalled, put everything back how it should be and working again. Wireless that is, not wired. Go figure ... 

I have a heap of issues going on here but I've been wanting to do this for ages. When I was first introduced to Linux in 2007 I wanted to do this; now I have the time and if not the nous to do it, the nous to track down some solutions with the generous help of forum users and Tuxers everywhere ... ;)

I'm glad to meet someone that understands the desire for the minimal install because a lot of people don't seem to get it. I have it booting from the grub selection list to the login screen in 12 seconds until I installed the ATI drivers which I've decided I didn't need and it went up to 20 seconds, even though I'm not using them! Sounds petty to some but that is what this install is all about; rock solid racehorse with no fat. 

The ATI drivers are still installed though not in use and I have another thread trying to figure how to remove all trace of them. I won't be satisfied until it's back to 12 seconds!!! lol

Good luck with your minimalism.

---

