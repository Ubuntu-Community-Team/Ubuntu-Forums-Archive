---
title: "mpd and ncmpc not working"
date: 2010-01-31
forum: General Help
---

### Post by ugujjwal on 2010-01-31
Hello friends,

I am trying to use MPD, for which I have installed a ncmpc client on ubuntu9.10.

I made some changes to mpd.conf:

[LIST=1]
[*]I changed the "music_directory" to "/home", and copied a song to that folder to test if it works.
[*]I commented the ALSA output part, as one of the blog I was reading said it doesn't make any difference, although i am not very sure of this.
[/LIST]
The problem is that whenever i try to restart mpd using this command:

> sudo /etc/init.d/mpd restartI get the following:


> 
* Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                             
output: No "audio_output" defined in config file
output: Attempt to detect audio output device
output: Attempting to detect a alsa audio device
No protocol specified
XOpenDisplay() failed
No protocol specified
XOpenDisplay() failed
output: Successfully detected a alsa audio device
                                                                         [ OK ]
Also I tried to use ncmpc, its also not working.
Thank you for reading this and spending your valuable time.
kindly give your suggestions.

---

### Post by falconindy on 2010-01-31
The output from restarting MPD isn't a fatal error. It's restarting successfully after detecting an alsa audio device, likely because none is explicitly defined in mpd.conf.

What do you mean when you say ncmpc "isn't working"?

---

### Post by ugujjwal on 2010-01-31
I mean to say that i am not able to* use* ncmpc.
I don't know if it is because, my mpd is not configured properly or i am simply ignoring something too obvious.
I am not able to play any songs, searching for them in ncmpc also is useless.

---

### Post by ugujjwal on 2010-01-31
What i have done till now is this:

1) I installed mpd-
> sudo aptitude install mpd

2) Then i installed ncmpc

3) I changed mpc.conf as stated in my first post

4) Then i restarted mpd

5) I started ncmpc-
> sudo ncmpc

 but I can't find any music files listed.
I am new to linux, maybe I am missing something very basic

---

### Post by ugujjwal on 2010-01-31
Got it. Its working now.
Uncommenting the ALSA output part helped, although I don't know why.
Will try to find the answer...
thank you

---

