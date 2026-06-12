---
title: "Two sound cards, only one is detected, the wrong one..."
date: 2009-12-28
forum: General Help
---

### Post by Don Scapp on 2009-12-28
I have two sound cards, both PCI, one is for the gameport, and the other I use for the sound, and usually Ubuntu detects both, but after reinstall, for some reason it only detected the gameport card. Is there a way of redetecting my sound card devices so I can use the right one? It is an Audiophile 2496 that I want to use, and I have set up the pulseaudio hack so it works when it is detected.

---

### Post by drdanielfc on 2009-12-28
> **Don Scapp said:**
> I have two sound cards, both PCI, one is for the gameport, and the other I use for the sound, and usually Ubuntu detects both, but after reinstall, for some reason it only detected the gameport card. Is there a way of redetecting my sound card devices so I can use the right one? It is an Audiophile 2496 that I want to use, and I have set up the pulseaudio hack so it works when it is detected.

Try deactivating the bad one through the bios. More of a workaround but this has worked for me in the past.

---

### Post by Don Scapp on 2009-12-28
Thanks, I'll try that, I'm interested in how I might be able to have ubuntu detect both cards as it was doing, so I can change between them in the sound settings? It seems that it's just detecting one of the cards, and moving on without checking for others.

---

### Post by drdanielfc on 2009-12-28
> **Don Scapp said:**
> Thanks, I'll try that, I'm interested in how I might be able to have ubuntu detect both cards as it was doing, so I can change between them in the sound settings? It seems that it's just detecting one of the cards, and moving on without checking for others.

First lets get just one working. Did deactivating it help?

---

### Post by Don Scapp on 2009-12-29
I tried to disable it, but as it is an installed pci card, there is no option in the bios (both my good soundcard and my gameport cards are pci). I beleive it shows when I run 
sudo lshw but it is not showing in Sound.

---

### Post by Don Scapp on 2009-12-30
FIXED! Here is the current working solution to the Audiophile 24/96 problem:
[http://groups.google.com/group/comp.os.linux.advocacy/browse_thread/thread/db03c0affd8def36?fwc=1](http://groups.google.com/group/comp.os.linux.advocacy/browse_thread/thread/db03c0affd8def36?fwc=1)

> [FONT=Courier, Monospaced]If you are getting no sound after a Ubuntu 9.10 install and are using one 
 of the M-Audio cards, like Delta 66/44 and possibly the Audiophile 2496, 
 here is the fix you need. 
 Make sure you edit the section, as SUDO that is for FRONT..... 
 [/FONT][FONT=Courier, Monospaced]Hope this saves someone some time. 
 [/FONT]
[FONT=Courier, Monospaced][https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/]("http://www.google.com/url?sa=D&q=https://bugs.launchpad.net/ubuntu/%2Bsource/pulseaudio/%2Bbug/178442/&usg=AFQjCNE55jsFNGVtBqOKkRCjTu-G8dhgNg") 
 comments/30 
 [/FONT]
[FONT=Courier, Monospaced][http://www.******************/ubuntu-studio-user/270387-delta-44-66-ub...]("http://www.google.com/url?sa=D&q=http://www.******************/ubuntu-studio-user/270387-delta-44-66-ubuntu-&usg=AFQjCNGqBceJU4HoiJAondRx38y-EhkiEg") 
 karmic-rc-no-sound.html 
 [/FONT]
[FONT=Courier, Monospaced]The reason pulseaudio right now doesn't work with this card is that it 
 expects a front device that has only 2 channels. 
 A possible fix for this is changing it's definition to: 
 ICE1712.pcm.front.0 { 
         @args [ CARD ] 
         @args.CARD { 
                 type string 
         } 
         type route 
         ttable.0.0 1 
         ttable.1.1 1 
         slave.pcm { 
                 type hw 
                 card $CARD 
         } 
         slave.format S32_LE 
         slave.channels 10 
 [/FONT]
[FONT=Courier, Monospaced]} 
 
[/FONT]
[FONT=Courier, Monospaced]in /usr/share/alsa/cards/ICE1712.conf 
 This is taken from RedHat's and pulseaudio's bugtracker and the alsa list, 
 I can't find the relevant thread/bugs right now though... [/FONT]

---

