---
title: "Can't see Noontec Media Drive on LAN"
date: 2010-06-29
forum: General Help
---

### Post by Bucky Ball on 2010-06-29
Hi all,

LAN with two desktops and laptop. Using SSH they can all see each other and share files fine. 

Recently bought a Noontec Media player. It can see the three computers okay and grab files from them (or just play them over the network) but the Noontec drive is not visible from any of the three machines on the LAN.

I've bumbled around a lot but not getting anywhere and it's getting late so thought I'd try my luck here. I can ping it!!! Just doesn't appear on the network. Weird.

When I go Places->Connect to Server, I put in the IP and I can get to a password GUI but the manual and nowhere on the net mentions what that password is. What I do know is the media player is supposed to work with Samba and all is set up fine for that, both the computers appear there fine, just not the Noontec. :(

Any ideas welcome; there's not much info around about these things and the website is not very comprehensive.

---

### Post by Bucky Ball on 2010-06-29
I am sitting here tweaking away again and getting nowhere, but just had a whacky idea!

The noontec you can plug into computer via USB. It actually has a small partition which is ... EXT3! So it is actually using a Linux OS by the looks. It has a terrabyte drive which is half FAT32 (only records to that) and other half for data storage NTFS with the small Linux partition in between.

I'm wondering, if I plug the noontec into computer via USB, make a partition and install Ubuntu server ... just a thought. This is obviously going to interfere with the OS already there I guess. Wonder if I could access the OS already there and tweak that to make it visible on the network.

As I say, I can see the samba shares I've set up on the computers on my tele via the noontec, but can't find the noontec on samba on the boxes at all (despite being able to ping, etc.).

Reason I want to do this? So everytime I want to back up to the NTFS partition or access it, I don't need to unplug the noontec, drag it to a computer, and plug in USB. If I could get it visible, all three machines on the network could access it like a server. 

There must be a way to do this without bricking the thing!! ;)

Incidentally, ALL machines have static IPs, including the Noontec.

---

