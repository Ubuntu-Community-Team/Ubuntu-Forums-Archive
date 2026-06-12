---
title: "Audiophile 24/96 hack not working with Pulse..."
date: 2009-12-29
forum: General Help
---

### Post by Don Scapp on 2009-12-29
It seems that the latest Ubuntu update has caused the Audiophile 24/96 profile set trick to cease working, and takes the Sound properties entry for the card out entirely. With the hack, the card appears in Sound, but doesn't play any sound; with the hack, the card disappears from the Sound dialog, and I was wondering if there was any way of gettings this card to work with the latest update?

---

### Post by Don Scapp on 2009-12-30
FIXED! Here is the current working solution to the Audiophile 24/96 problem:
[http://groups.google.com/group/comp.os.linux.advocacy/browse_thread/thread/db03c0affd8def36?fwc=1](http://groups.google.com/group/comp.os.linux.advocacy/browse_thread/thread/db03c0affd8def36?fwc=1)

> [FONT=Courier, Monospaced]If you are getting no sound after a Ubuntu 9.10 install and are using one 
 of the M-Audio cards, like Delta 66/44 and possibly the Audiophile 2496, 
 here is the fix you need. 
 Make sure you edit the section, as SUDO that is for FRONT..... 
 [/FONT] [FONT=Courier, Monospaced]Hope this saves someone some time. 
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

