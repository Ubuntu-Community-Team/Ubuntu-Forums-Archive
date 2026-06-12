---
title: "New to Ubuntu, help with various problems please"
date: 2012-06-26
forum: General Help
---

### Post by turtlestone on 2012-06-26
Thanks in advance for any help.

I have been a Windows user for years (used Ubuntu 8.04 for only a few months when it was released), but recently decided to take a good hard try at Ubuntu 12.04LTS. I installed the 64bit version a week ago on my 2007 17" Toshiba X-205 (on 1 of the 2 internal hard drives - the second has all my old windows files like music, games, pictures etc) and all the hardware seems to work perfectly fine as far as I can tell (minus the fingerprint reader), and I'm even mulling over a lot of the "Learn Command Line" links. However, some varied software issues I'm still trying to work out and I'm hoping the awesome community here can help me out. I do not have a dual-boot, Ubuntu is the only OS currently installed on my machine.

**Wine**
I installed Wine from the software/app center and there's a few things I want to try to do that I've been trying to decipher online, but can't come up with a solution.

Issue #1: I have a few GB of iTunes music (AAC format I presume) that I'd like to listen to. Save from taking 1,000 years to burn a city bus load of CDs to import to an Ubuntu media player, I'd like to use Wine instead. I don't plan on using an iPod, so syncing is no worry - just want to be able to buy songs from the store and play them along with my current library. I downloaded the latest version of iTunes to my desktop and "right-click--> Open with Wine". It goes through the motions like it is installing iTunes for me, and says it has been installed successfully. I click OK and the installer, along with Wine, quit.
Is there something else I need to do? How do I ensure it will play my current iTunes library located on the second hard drive (would I have to move it to the drive where Ubuntu is installed)?

Issue #2: I am trying to play Age of Conan through Wine. My AoC files are stored in a folder on the second hard drive (the same on with my iTunes library). When I "right-click--> Open with Wine" on the .exe for the game it also starts to load up like it normally would on Windows (I even hear the background audio of the loading screen), but then it gives me an error of “Internal errors – invalid parameters received”  before I can even see anything actually pop up pertaining to the game - just see the original Wine window through the entire time.

**Firefox**
I installed the most recent version of firefox and then downloaded the add-on NoScript. About a day later whenever I opened FF it would show a big red warning bar on top saying “The bookmarks and history system will not be functional because of FF's files is in use by another application. Some security software can cause this problem.” So yeah, none of my bookmarks were present, FF wouldn't show text as a hyperlink when it was supposed to be and the “Back” button is unusable. I click on the “Learn More” button and follow the steps it gives, but that didn't work. Thinking it was NoScript, I removed the add-on and reinstalled FF. Nope, same issues present. What can cause these issues? I'm using Chromium until I can resolve that.

Thanks again so much!

---

### Post by turtlestone on 2012-06-26
Bump10char

---

### Post by youknowme on 2012-06-26
you have to mount the partition that you want to use! From reading your post, i recommend that you install virtualbox and run windows from inside that - it is far more reliable than wine.

---

### Post by nipunshakya on 2012-06-27
Hello turtlestone...
The error in wine can persist if the game is trying to connect to internet or something.. if you try to install yahoo messenger and run it on wine, you may get the same error...
using itunes for wine? why not use virtualbox and install windows inside it and then use itunes within it?? i think that would be a better idea... i guess you will get the same error as that u got on AoC if you try to connect to the music store on itunes if u use wine.... 

My suggestion, use virtual box and install windows... next, you can do almost everything inside your virtual windows installation

Goodluck. WInuxUser

---

### Post by turtlestone on 2012-06-27
Thanks a ton for the suggestions. I installed VirtualBox, but I'm a little unsure how to go about using it. I click on 'New', then name and choose Windows Vista 64 (the last version of the Win OS I've used). How much RAM should I be allocating for it? What are some suggestions on creating a virtual hard drive? I can select to create a new one, but I'm unsure on which file type to use (Disk Image, Machine Disk, Hard Disk, or Parallels Hard Disk)?

Just a bit more guidance would be a great help. I figured there would be some tough compatibility with games through Wine, but is VirtualBox typically more successful?

Any suggestions on the FF bug?

---

### Post by dino99 on 2012-06-27
look at "browse apps"  [http://appdb.winehq.org/](http://appdb.winehq.org/)
and install the latest release.

music: [https://one.ubuntu.com/music/](https://one.ubuntu.com/music/)

audio: [http://freshtutorial.com/audio-player-linux-ubuntu/](http://freshtutorial.com/audio-player-linux-ubuntu/)

---

### Post by Vaphell on 2012-06-27
default (disk image .vdi) should be good

hdd space - depends. you need to answer yourself how many win apps (maybe newest MS Office that doesn't work too well with wine?) you want to have inside your VM and adjust accordingly. Creating VMs is trivial so you simply give it a spin and when you figure everything out, do it again, properly.

as for how much memory - probably 1GB at least if you don't want disk thrashing



do you have any windows vista installer? virtual machine creates a fake computer but you still need to perform installation of the OS on it.

---

### Post by nipunshakya on 2012-06-27
> **turtlestone said:**
> Thanks a ton for the suggestions. I installed VirtualBox, but I'm a little unsure how to go about using it. I click on 'New', then name and choose Windows Vista 64 (the last version of the Win OS I've used). How much RAM should I be allocating for it? What are some suggestions on creating a virtual hard drive? I can select to create a new one, but I'm unsure on which file type to use (Disk Image, Machine Disk, Hard Disk, or Parallels Hard Disk)?

Just a bit more guidance would be a great help. I figured there would be some tough compatibility with games through Wine, but is VirtualBox typically more successful?

Any suggestions on the FF bug?
To install ubuntu inside virtual box
[http://www.psychocats.net/ubuntu/virtualbox/](http://www.psychocats.net/ubuntu/virtualbox/)
To install windows 7 in virtualbox:
[http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/](http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/)
[https://seogadget.co.uk/how-to-install-virtualbox/](https://seogadget.co.uk/how-to-install-virtualbox/)
[http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox](http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox)

These links will give u general ideas about what you actually would do normally in a virtualbox

Goodluck

---

### Post by holycow131415 on 2012-06-27
Virtualbox tutorial: [http://www.youtube.com/watch?v=TB-8olhzK6w](http://www.youtube.com/watch?v=TB-8olhzK6w)
Install Windows 7 for free and legal: [http://www.youtube.com/watch?v=fHEqEpEJDAU](http://www.youtube.com/watch?v=fHEqEpEJDAU)

Also, playonlinux is a front end for wine, so you may find it easier to install applications through it: [http://www.youtube.com/watch?v=ZrGDphp6CwY](http://www.youtube.com/watch?v=ZrGDphp6CwY)

---

### Post by youknowme on 2012-06-27
> **WinuxUser said:**
> To install ubuntu inside virtual box
[http://www.psychocats.net/ubuntu/virtualbox/](http://www.psychocats.net/ubuntu/virtualbox/)
To install windows 7 in virtualbox:
[http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/](http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/)
[https://seogadget.co.uk/how-to-install-virtualbox/](https://seogadget.co.uk/how-to-install-virtualbox/)
[http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox](http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox)

These links will give u general ideas about what you actually would do normally in a virtualbox

Goodluck

you would be able to run windows in virtualbox and install and use all your windows programs. when done, you switch off the virtual machine and your back in ubuntu.
virtualbox is very easy to use. just make sure you have your windows installation discs. the value settings are normally recommended for you when you set it up.
i learned recently to make virtualbox even better you should install the guest additions on your virtual machines. the wiki you have been directed to is great and explains things clearly.

---

### Post by nipunshakya on 2012-06-27
> **youknowme said:**
> 
i learned recently to make virtualbox even better you should install the guest additions on your virtual machines. the wiki you have been directed to is great and explains things clearly.

Thats the add-on available at the installation of virtual box on the software center too...

---

