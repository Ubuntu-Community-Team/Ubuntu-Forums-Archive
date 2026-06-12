---
title: "Multi Platform Network Audio"
date: 2009-10-07
forum: General Help
---

### Post by paal on 2009-10-07
I'm looking for a solution for streaming audio to the network from PC of different platforms (Linux and Windows) to a Linux computer. Here's the case:
I've three computers, two running Ubuntu and one running Windows Vista. One of the Ubuntu-computers is an old laptop which I'm going to use as a server for various things. In this case, I'd like to have this computer play audio from one of the two other computers. In other words, I'm looking for a way to send the audio from either Windows or Ubuntu (not necessarily both at the same time) to the Ubuntu laptop acting as a server.
I've had a brief look at shout-/icecast. It might work when receiving from one computer, but I fear it will get quite troublesome when it's going to receive from one of two computers. Currently I'm using Pulseaudio which works quite fine, except for some lagging from time to time and that my upload speed to the server is around 240 kB/s. Feels kind of a waste when the audio is an 128 kbit/s MP3... :) Also, I am not aware of any way to use Pulseaudio in Windows Vista.

Anybody got some suggestions?

---

