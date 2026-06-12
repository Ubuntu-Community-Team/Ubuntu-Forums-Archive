---
title: "Stream audio through home network"
date: 2010-12-09
forum: General Help
---

### Post by NertSkull on 2010-12-09
Can I stream audio through my home network.  I have an Ubuntu 10.10 pc downstairs as my main computer that I have all my media on.  I play music using Guayadeque (which I love as a replacement for songbird).

Can I get the computer upstairs in my bedroom to pick up the music currently playing on my downstairs computer so I have it playing in multiple rooms at once.

Upstairs is 10.04 and I have SSH all set up and drives connected.  I was hoping there is just a way to maybe get the upstairs to connect into ALSA or something (I have no clue really) to get it to play at the same.

Can anyone point me in the right direction?

(note I'm not just talking about accessing the music.  I have the downstairs drive shared upstairs so I can play music up there solely on that computer.  I want it playing concurrently on both computers so its on two sets of stereo systems)

Thanks

---

### Post by tgalati4 on 2010-12-09
There are a few ways to do it.  You can set up an icecast server and point several computers to it.  Do a search on multicast.

I think pulseaudio can be set up to serve audio to multiple machines.  You would have to get into the details on pulseaudio.

I've played with multicasting on my home network.  It really slams your network, so you might need to upgrade your routers to high quality/business grade units, otherwise they will burn up in no time.

So unlike wikipedia, multicasting is an idea that sounds better on paper than works in real life.

---

### Post by NertSkull on 2010-12-10
Allright, this is where I am.

Multicast led me in the right direction.  But you are right, its no good.  It uses UDP so it drops a ton of packets and I can't get it to stream well enough on my home network.

BUT, it lead me to playing around with pulse audio more.  Its actually a nice little program.

I installed the paprefs and pavucontrol packages (pulse audio preferences and pulse audio volume control).

I followed the guide [here]("http://www.linux.com/learn/tutorials/332418-weekend-project-using-pulseaudio-to-share-sound-across-all-your-computers")

Basically in preferences you enable the network access tab and the network serve tab on BOTH the audio source computer and the audio receiver computer (yes this only works between two computers, for more you need mulcicast.  But I only have two desktops, so it is fine).

Once those are both enabled you open a program (Guayadeque, etc) and play music.

Then you go to the pulse audio volume control, and under playback you'll see your program.  Then you can select where to stream it to, you can select the other computer and it streams to it pretty well.

So success!  ....... almost.

This is where I'm stuck.  It streams great to the other computer.  BUT it takes ALL the audio and sends it there.  You tell the music player to use the other computer as the sole place.  So it NO LONGER plays on the main computer.  So my source computer is playing the music, streaming it to the receive that actually makes sound, but the source computer is silent.

I've been looking around for a while, but everything I find about loopback takes my to multicast--which I don't want.

I'm thinking there must be a way to split the music player to go to both places.  I'm sure someone has an idea.  I'm thinking maybe some sort of virtual card or something??

Anyway, so close yet not quite there.  Any ideas??

---

### Post by NertSkull on 2010-12-11
Solved.  I figured out how to get them together.  I posted how [here]("http://ubuntuforums.org/showthread.php?t=1643167") for anyone else interested

---

