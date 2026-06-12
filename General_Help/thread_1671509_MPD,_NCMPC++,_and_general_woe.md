---
title: "MPD, NCMPC++, and general woe"
date: 2011-01-20
forum: General Help
---

### Post by Jackzilla on 2011-01-20
Hello, I have been struggling to get a working version of Linux on my laptop for the better part of three days now (even had a friend who has been using it for years come over and help, quote: "I've never seen so many problems happen straight after a fresh install") and I finally have Ubuntu 10.10 working, but still having a couple of issues...

First, mpd. I'm getting the following error:
```
jackzilla@Marvin:~$ mpd
listen: Failed to listen on localhost (line 70): Address already in use
Aborted
jackzilla@Marvin:~$ sudo /etc/init.d/mpd restart 
[sudo] password for jackzilla: 
 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                             listen: bind to 127.0.0.1:6600 failed: Address already in use (continuing anyway, because at least one address is bound)
              
```I have edited the .mpdconf file a lot and am greatly confused by what I've done wrong. I have read lots of threads on this forum about this issue already, but none of those solutions seem to help. I have made sure all the directories referenced in .mpdconf have been created, uncommented the alsa part, recommented it, changed the local directory, user, etc etc... I'm at a complete loss for what else to try.


Next is NCMPC++ - though this will probably (hopefully) be fixed by fixing MPD, right? I can run ncmpc++ fine, but I can't seem to locate any actual files (I have put an album in my ~/Music directory to serve as a test, but the browser is blank, pressing " and ! to go to parent/root directories does nothing)

Finally... Well I have an ATI card, and I guess you all know that can cause trouble. Ubuntu constantly crashes if I install any driver (the community developed one OR the official ATI website one), and the only way I can actually get my laptop to work with Ubuntu is to simply not install any driver. I guess this isn't a "problem", more of a gripe. Just wondering if anyone else has any ideas?

Also, every now and then, the whole computer (mouse included) freezes solid. Sometimes this happens straight after I start up, before my wireless has even connected. I think when this happens Xorg jumps to about 50% CPU, so I'm guessing it's related to the graphics card...?

Whew, long first post. Thanks for taking the time to read it, any help would be GREATLY appreciated, I am so sick of Windows, please don't make me go crawling back!

---

### Post by Jackzilla on 2011-01-21
Someone please help! I was using rhythmbox without issue all day yesterday (at the same time as firefox, evolution and document reader) - now trying to play a song in rhythmbox causes pulseaudio to jump to about 60% cpu usage and rhythmbox itself to about 95%! And the song doesn't play, just makes hellish sounds. 

Please either help me fix rhythmbox or get mpd going... :(

---

### Post by mciverza on 2011-01-21
```

 * Starting Music Player Daemon mpd                                             listen: bind to 127.0.0.1:6600 failed: Address already in use (continuing anyway, because at least one address is bound)
              
```

That "bind to error" means that a program is using that port. Possibly mpd is not actually stopped.

"sudo netstat -tlnp" will show you process IDs and names of the running services.

Finally... Well I have an ATI card, and I guess you all know that can cause trouble. 

I suggest that you make sure that desktop effects are disabled. This can be done via
System --> Preference -->  Appearance.  
In the new window that opens select the "Visual Effects" tab and select "none"
(no logout or restart is required).

---

### Post by Jackzilla on 2011-01-21
```
jackzilla@Marvin:~$ sudo netstat -tinp
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMU
lo        16436 0         4      0      0 0             4      0      0      0 LRU
wlan0      1500 0      1013      0      0 0           917      0      0      0 BMRU
```

I don't understand that, really...

I also do not at all get how rhythmbox can work perfectly with minimal cpu load one day, but be completely f'd the next! :confused:

I have already disabled the visual effects. I think all my graphics based problems have gone away, I was mostly just musing that to fix this problem you have to not install any drivers. Odd.

---

