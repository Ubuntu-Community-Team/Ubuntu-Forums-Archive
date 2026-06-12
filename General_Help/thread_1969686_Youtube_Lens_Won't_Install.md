---
title: "Youtube Lens Won't Install"
date: 2012-04-30
forum: General Help
---

### Post by Ericj1186 on 2012-04-30
I am having a weird issue with lens. I followed the instructions on [this site]("http://www.omgubuntu.co.uk/2011/12/so-long-productivity-youtube-lens-for-ubuntu-adds-browser-free-searching-of-videos/") to add the repo and the lens/scopes.

Here is what it said to add:

```
sudo add-apt-repository ppa:atareao/lenses

sudo apt-get update && sudo apt-get install lens-video scope-youtube
```

The repo adds okay, but when I try to install lens-video, I cannot find that package. I searched for atareao, and found [this summary of what's in the repo]("https://launchpad.net/~atareao/+archive/lenses"). I see both packages I need to download. I go to Software Sources, and I removed the previous added repos, and added the ones directly from that site I just linked. They look like this:

```

deb http://ppa.launchpad.net/atareao/lenses/ubuntu precise main 
deb-src http://ppa.launchpad.net/atareao/lenses/ubuntu precise main 

```

Sudo apt-get update runs, but again, I cannot find the packages. Any idea where I am messing up?

---

### Post by ShapeShifter499 on 2012-09-09
Hi 

     I know this is a old thread but I thought you should know "lens-video" is the older Ubuntu      Oneiric 11.10 package. To use this youtube lens please do the following:

```
sudo add-apt-repository ppa:atareao/lenses  

sudo apt-get update && sudo apt-get install yavol scope-youtube
``` yavol is "Yet Another VideO Lens"  the updated version of lens-video for 12.04

---

