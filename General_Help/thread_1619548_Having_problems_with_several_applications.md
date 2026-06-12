---
title: "Having problems with several applications"
date: 2010-11-11
forum: General Help
---

### Post by sbaig on 2010-11-11
Im a newbie to linux, I have ubuntu 10 64bit installed on my laptop. However Im having issues with skype where it keeps stalling, or disconnecting calls then stalling. And i have connect/disconnect with a caller 3 times before they can hear me, something is buggy with the software for the mic cause this worked fine when i had windows. and the quality of video seems to be much poorer. also when i display my own camera to myself the bottom quarter of the video feed window is a copy of the top (its screwed up, thats the best way to describe it).

Also how do I install frostwire, ive downloaded it but it always gives an error on installation that says wrong architecture or something. Sorry if my problems are very noobish but thats what I am when it comes to linux, other than that ubuntu has been fantastic so far.

---

### Post by DeMus on 2010-11-12
> **sbaig said:**
> Im a newbie to linux, I have ubuntu 10 64bit installed on my laptop. However Im having issues with skype where it keeps stalling, or disconnecting calls then stalling. And i have connect/disconnect with a caller 3 times before they can hear me, something is buggy with the software for the mic cause this worked fine when i had windows. and the quality of video seems to be much poorer. also when i display my own camera to myself the bottom quarter of the video feed window is a copy of the top (its screwed up, thats the best way to describe it).

Also how do I install frostwire, ive downloaded it but it always gives an error on installation that says wrong architecture or something. Sorry if my problems are very noobish but thats what I am when it comes to linux, other than that ubuntu has been fantastic so far.

You have obviously the 64 bit version of Ubuntu. Which Ubuntu is unsure since you write version 10. This should be either 10.04 (Lucid) or 10.10 (Maverick)
When you get a message saying wrong architecture it means you downloaded something suitable for the 32 bit version of the Operating System. 
Go to System - Administration - Synaptic. In Synaptic in the little text file don top type frostwire. The list of available software will then filter only frostwire. Click on the little empty box next to the name and select install.
Then in the top menu bar click on install and in a few seconds you have frostwire running.
Always use Synaptic first when you want to install something. It contains a lot of free software which will be automatically updated when an update is available.
Sorry I can't help you with the problems you have with Skype. I'm sure somebody else can do that.
Good luck and try to read as many as possible about Ubuntu, there is so much to learn. When knowing that Ubuntu is not Windows it makes it a lot easier to use.

---

### Post by sbaig on 2010-11-12
> **DeMus said:**
> 
Go to System - Administration - Synaptic. In Synaptic in the little text file don top type frostwire. The list of available software will then filter only frostwire. Click on the little empty box next to the name and select install.
Then in the top menu bar click on install and in a few seconds you have frostwire running.


I'm so sorry I didn't understand what you wanted me to do lol.

And if i type frostwire into synaptic or ubuntu software manager nothing comes up. is there any other p2p app available?

---

### Post by DeMus on 2010-11-13
> **sbaig said:**
> I'm so sorry I didn't understand what you wanted me to do lol.

And if i type frostwire into synaptic or ubuntu software manager nothing comes up. is there any other p2p app available?

Sorry, my mistake. I use Linuxmint Isadora which is based on Lucid 10.04. I just saw that in the Linuxmint repository I find frostwire, so when you use Ubuntu you won't have it.
Which Ubuntu do you use? If it is either Karmic, Lucid or Maverick then go to:
[PPA]("http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=lucid#"), choose the right version and do what it says at the top of the page. Copy-paste the text in the box, line by line, into a terminal. You will add the right repository to your system so you can install frostwire through Synaptic.

---

### Post by sbaig on 2010-11-17
right well I got Frostwire to show up in synaptic. Took a little bit of playing around to get the repository added. But when I click 'apply' after i check frostwire off to be in stalled i get an error > Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-amd64/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-amd64/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.

i thought linux would be a little less complicated to install software, excuse my naiveté.

---

