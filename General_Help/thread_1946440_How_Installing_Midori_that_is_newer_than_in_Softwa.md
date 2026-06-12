---
title: "How? Installing Midori that is newer than in Software Center?"
date: 2012-03-24
forum: General Help
---

### Post by writebunny on 2012-03-24
Hello all, 

I'm a brand new Linux convert. I've just discovered Xubuntu thanks to some people on the Thinkpad forum. I'm making the transition from my old Macs - and I simply LOVE the look and feel of Xubuntu - even more than other distros I've tried.  The folks at the thinkpad forum got me through some heat issues with my laptop, now I'm ready to get xubuntu set up as I'd like, but I need a little help, please. 

I've learned to use the ubuntu Software Center and think it is fantastic.  The people at the thinkpad forum taught me how to right click on something I downloaded to make it install with the Software Center - and that was nice and easy. 

However, I can't seem to figure out how to install the newest version of Midori browser. There is a much more recent version on the Midori home page than is available to me in the software center. I downloaded it - then right clicked, but it doesn't offer to upload via the Software Center. So I don't know what to do with it. How do I install it? 

Also - does anyone know of other thesaurus and dictionary options for Linux - other than the ones listed in the Software Center? Apple has a perfect one made by Oxford American (or is that American Oxford?) - but I don't think theirs can run on Linux. I was trying to see if Oxford makes a separate one that might run on Linux - or if they make one for Windows that would run through Wine? (I've heard of wine, but have no experience using it.) Any  thoughts? The free ones online are nice, but I've been spoiled by the really detailed on I used on Mac. 

Thanks for any help with this.

---

### Post by idoitprone on 2012-03-24
> **writebunny said:**
> Hello all, 

I'm a brand new Linux convert. I've just discovered Xubuntu thanks to some people on the Thinkpad forum. I'm making the transition from my old Macs - and I simply LOVE the look and feel of Xubuntu - even more than other distros I've tried.  The folks at the thinkpad forum got me through some heat issues with my laptop, now I'm ready to get xubuntu set up as I'd like, but I need a little help, please. 

I've learned to use the ubuntu Software Center and think it is fantastic.  The people at the thinkpad forum taught me how to right click on something I downloaded to make it install with the Software Center - and that was nice and easy. 

However, I can't seem to figure out how to install the newest version of Midori browser. There is a much more recent version on the Midori home page than is available to me in the software center. I downloaded it - then right clicked, but it doesn't offer to upload via the Software Center. So I don't know what to do with it. How do I install it? 

Also - does anyone know of other thesaurus and dictionary options for Linux - other than the ones listed in the Software Center? Apple has a perfect one made by Oxford American (or is that American Oxford?) - but I don't think theirs can run on Linux. I was trying to see if Oxford makes a separate one that might run on Linux - or if they make one for Windows that would run through Wine? (I've heard of wine, but have no experience using it.) Any  thoughts? The free ones online are nice, but I've been spoiled by the really detailed on I used on Mac. 

Thanks for any help with this.

why make your life hard?
use a ppa

this is ubuntu and they use ppa to stay up to date when your distro freezed version feelinging inadaquet

```
sudo apt-add-repository ppa:midori/ppa
sudo apt-get update
sudo apt-get upgrade 
```now when you update apt or synapatic or update manager frontend does it for you

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

---

### Post by Rodney9 on 2012-03-24
A couple of guides for Xubuntu - 

Autochanging Wallpaper with Wally. - YouTube
[https://www.youtube.com/watch?v=i4Qd3zW0sk4](https://www.youtube.com/watch?v=i4Qd3zW0sk4)

[http://seandavis-blog.blogspot.com.au/2011/12/xubuntu-1110-setup-guide.html](http://seandavis-blog.blogspot.com.au/2011/12/xubuntu-1110-setup-guide.html)

Rodney

---

### Post by writebunny on 2012-03-24
Thank you for answering. What is PPA?

---

### Post by wildmanne39 on 2012-03-24
Hi, it is a personal package archive for installing a single piece package like the browser you want, just run the commands by idoitprone one line at a time.
Thanks

---

### Post by idoitprone on 2012-03-24
> **writebunny said:**
> Thank you for answering. What is PPA?

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

here is a dictionary in the browser addon for firefox

very useful for quick definition
[https://addons.mozilla.org/en-US/firefox/addon/dictionary-tooltip/](https://addons.mozilla.org/en-US/firefox/addon/dictionary-tooltip/)

---

### Post by writebunny on 2012-03-24
Thank you for helping. I'm sorry, but I don't understand this all very well yet. 

I did each line - one at a time in Terminal (I'm very new at this!)

After I did the first one, it asked me all this:

```
This PPA is signed. You may want to add the corresponding GPG key to your apt keyring:
   sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A69241F1
Starting to Karmic, adding the PPA and its key is as simple as:
   sudo add-apt-repository ppa:midori

***************************
***** IMPORTANT *****
***************************
If you use this repository, you'll also need WebKit-team PPA :
https://launchpad.net/~webkit-team/+archive/ppa
 More info: https://launchpad.net/~midori/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

```

I didn't know what to do, so I just hit enter. Was that right? 

Then I did the other two lines - one at a time - and waited for the end. 

When I went to software center, it still shows the old Midori. I must have done this all wrong. What should I do next? 

(Please remember, I'm very new to this - and I don't understand stuff about terminal at all. I basically cut and paste as directed but I have no idea what this is doing.)

---

### Post by idoitprone on 2012-03-24
> **writebunny said:**
> Thank you for helping. I'm sorry, but I don't understand this all very well yet. 

I did each line - one at a time in Terminal (I'm very new at this!)

After I did the first one, it asked me all this:

```
This PPA is signed. You may want to add the corresponding GPG key to your apt keyring:
   sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A69241F1
Starting to Karmic, adding the PPA and its key is as simple as:
   sudo add-apt-repository ppa:midori

***************************
***** IMPORTANT *****
***************************
If you use this repository, you'll also need WebKit-team PPA :
https://launchpad.net/~webkit-team/+archive/ppa
 More info: https://launchpad.net/~midori/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

```I didn't know what to do, so I just hit enter. Was that right? 

Then I did the other two lines - one at a time - and waited for the end. 

When I went to software center, it still shows the old Midori. I must have done this all wrong. What should I do next? 

(Please remember, I'm very new to this - and I don't understand stuff about terminal at all. I basically cut and paste as directed but I have no idea what this is doing.)

yes you did it properly

accorfing to the ppa you need a webkit ppa```

sudo add-apt-repository ppa:webkit-team/ppa
sudo apt-get update 
sudo apt-get upgrade
```add another ppa
just do all these commands one at a time

add-apt-repository add the ppa to your sources list
apt-get update -update you apt cache so you can see the new midori
apt-get upgrade - upgrade your apps

there is a gui way to do these things through the synaptic or edit the /etc/apt/sources list or watever
the terminal is easier, since it does everthing for you

---

### Post by cortman on 2012-03-24
You're doing great! To install the latest Midori, you should probably run

```
sudo apt-get install midori
```It'll ask for your password- enter it, and it should grab the most up-to-date copy of Midori.
Plus, having the PPA added means that Midori will be updated whenever you update your system software, by running

```
sudo apt-get upgrade
```Good luck!

PS For a dictionary, look up GoldenDict.

---

### Post by writebunny on 2012-03-25
Thank you both. I have the new version of Midori now. This new version seems a whole lot more advanced and more stable than that other one. I like to run a light browser as much as possible.  Thanks for making this easier to understand. 

How does one learn about the commands used in terminal? (Not that I'll learn it all right away - but maybe I can slowly learn over time)

---

### Post by wildmanne39 on 2012-03-25
Hi, you can type man plus the command you want to know about into the terminal and it will tell you all about the one command or here is a link to help.
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)
thanks

---

### Post by cortman on 2012-03-25
> **writebunny said:**
> Thank you both. I have the new version of Midori now. This new version seems a whole lot more advanced and more stable than that other one. I like to run a light browser as much as possible.  Thanks for making this easier to understand. 

How does one learn about the commands used in terminal? (Not that I'll learn it all right away - but maybe I can slowly learn over time)

I would highly recommend becoming familiar with the command line- it's where the real power is in computing, and will give you the knowledge to fix and/or tweak your system should something ever go wrong. Plus, with knowledge comes more confidence in using the system.
Check out the thread Wildmanne39 suggested (it's the same as the link in my signature) and always feel free to post with any questions. Good luck!

---

### Post by Peripheral Visionary on 2012-03-26
> **cortman said:**
> I would highly recommend becoming familiar with the command line- it's where the real power is in computing, and will give you the knowledge to fix and/or tweak your system should something ever go wrong. 

**+1** - and another thing that is helping me learn is to *write down* all the stuff you do, so you know where to look when something goes wrong. Writing down what I do and what the results are helps me avoid repeating mistakes, and helps me learn a lot more.

---

### Post by idoitprone on 2012-03-26
> **Peripheral Visionary said:**
> **+1** - and another thing that is helping me learn is to *write down* all the stuff you do, so you know where to look when something goes wrong. Writing down what I do and what the results are helps me avoid repeating mistakes, and helps me learn a lot more.

sometimes it is not simple. I did not know that midori ppa had the requirement of webkit ppa, since i had another distro. 
I cannot test those commands to be sure. 

Results on one terminal doesnt always translate to another system. For the most part, these commands are self explainatory, but other times the result of hardware specific or distro.

---

### Post by writebunny on 2012-03-27
Thank you all for the help. I'll spend some time studying those links. 


IGNORE THIS PLEASE: > 
While I was dabbling, I got over confident and installed another program via terminal. It is Calligra office suite. I don't like it, however.:confused: How do I remove it? (Ubuntu Software Center doesn't see it - although it shows up in the "history")

EDIT: 
This was the command info I installed with:
[QUOTE]sudo add-apt-repository ppa:kubuntu-ppa/beta \  && sudo apt-get update\  && sudo apt-get install calligra[/QUOTE]

I think I solved my own problem! I found out this works:
sudo apt-get autoremove calligra
I tried sudo apt-get remove calligra - but that did not work. It had to say autoremove. 

Wow! I learned something. Will wonders never cease!!?

---

### Post by tmx84 on 2012-03-27
"sudo apt-get remove calligra" removes the package but leaves the configurations files, "sudo apt-get purge calligra" will remove the package+config files

---

### Post by writebunny on 2012-03-27
Okay - the above definitely got rid of Calligra. But I found a new thing I need to fix. Calligra damaged Kword, which I would have liked to totally remove anyway. (Didn't like it). However, it still appears in my application menu, although both the software center and terminal tell me it is not installed. How do I get Kword to stop appearing in my applications menu?

---

### Post by writebunny on 2012-03-27
> **tmx84 said:**
> "sudo apt-get remove calligra" removes the package but leaves the configurations files, "sudo apt-get purge calligra" will remove the package+config files

Oh - I'm sorry - we cross posted. I'll do that command right now. Thank you. (And have written it down for future reference)

---

### Post by writebunny on 2012-03-27
sudo apt-get purge calligra
did not turn up more files to delete, but that's okay. 

sudo apt-get purge kword 
did turn up files to delete and they're gone. 

However, I still have kword in my application menu list. Odd. 

Is purge better than autoremove?

---

### Post by cortman on 2012-03-27
I prefer purge because it totally removes all files connected to the program.
To get it off your menu, you may just have to reboot.

---

### Post by writebunny on 2012-03-27
Thank you. I'll stick with purge from here forward. 

And - you're right - rebooting removed it. Hurray. My system is back to good again. 

Thanks for your patience!

---

### Post by Peripheral Visionary on 2012-03-27
> **writebunny said:**
>  Hurray. My system is back to good again. 

Thanks for your patience!

Cool! Please remember to mark your thread [SOLVED]. See "Thread Tools" at the top.

---

### Post by maureenc on 2012-04-17
Hi Writebunny,

I wonder which version of Midori you got from the ppa? 


There should be .0.4.4 available but I have tried several times and unable to find it.... I have 0.4.0 which came via the ppa a few weeks ago...


There are some good things in the latest release so was hoping to find it..... Keeps saying nothing to upgrade when I try.

---

