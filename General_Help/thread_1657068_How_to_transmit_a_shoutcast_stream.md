---
title: "How to transmit a shoutcast stream"
date: 2010-12-31
forum: General Help
---

### Post by collinstocks on 2010-12-31
So, there is a program on the shoutcast website called sc_trans which can be configured fairly easily to transmit a playlist via shoutcast. However, it seems to require a set playlist, and there is no easy and reliable way to tell it one song after the other what it should play (say, to get it to play whatever I am playing in Rhythmbox if I were to write a program to do that).

So the question I have is this: Is there an alternative (preferably open source) shoutcast transmission library that I can use instead?

---

### Post by Brandon Williams on 2011-01-02
My music server uses mpd to manage the playlist and streams both ogg and mp3 via icecast. Just 'sudo apt-get install mpd mpc icecast2', and then look [here](http://mpd.wikia.com/wiki/Configuration) to start figuring out the necessary configuration details.

---

