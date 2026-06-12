---
title: "Audio device in qsstv"
date: 2010-12-01
forum: General Help
---

### Post by vk3xci on 2010-12-01
I upgraded to 10.10 about a month ago from 9.10. I left /home intact. I haven't been able to get the audio device to respond consistently across a number of Ham Radio programs which use the soundcard to receive/transmit.

qsstv simply responds with "Cannot open sounddevice" Which is rather un-helpfull.
fldigi on the other hand works perfectly and has from the start.

Both use /dev/dsp as the sound device. which by the way doesn't appear .n /dev :confused:

I'm a bit lost as to where to start, but I have purged and reinstalled qsstv to no avail.

Norm

---

### Post by vk3xci on 2010-12-01
OK, forget it.

I've spent all night trying to get it to work and it's just not going to. Back to 9.04, IMHO the last stable release!

Norm

---

### Post by kd5mkv on 2010-12-28
I too encounter this bug! I went back to 10.4 where qsstv has worked for me, fldigi has worked also using pulseaudio. Seems getting any audio at all is very difficult until I install pulseaudio. I tried putting /dev/ttyUSB1 about three times and received the same warning. I restarted Ubuntu and tried again and same result. Then began some problems with everything else, so I did clean install of 10.4. I dont use Wubi, as a small partition is fine, I use Ubuntu 24/7 on Xastir. Steve

---

### Post by jcoles on 2011-01-23
I'd love to know how you got fldigi to work in 10.10, vk3xci.

No settings in Configure > Sound Card deliver any audio to the program for me.

---

### Post by jcoles on 2011-01-23
Success! I installed the oss-compat package, then in the fldigi Configure > Sound Card menu, I selected Port Audio and chose my audio card from the Capture list.

I hope this information will help others.

---

### Post by johndoe32102002 on 2011-07-26
I tried installing QSSTV and got this same error with the SoundDevice.  I installed oss-compat and it did not fix QSSTV.  I am running 64-bit Ubuntu 11.04.

---

### Post by on4qz on 2011-12-24
Hi,

Just to let you know: QSSTV 7.1.2 is avalaible at my website
[http://user.telenet.be/on4qz](http://user.telenet.be/on4qz)

Hope this solves a number of issues.

73's
Johan ON4QZ

---

### Post by kd5mkv on 2012-01-02
Tried the link and qsstv_7.1.2 is fantastic! Even the calibration of the clock is simple and ingenious! The addition of more MODES is a real plus.
Great to see the author here on the Ubuntu Forums, I wanted email him about his qsstv-6 alpha version but was content with stable version.
Cheers! Steve kd5mkv:P

---

### Post by lgharriman on 2012-02-18
Thanks Johan.  I finally have QSSTV working in Kubuntu Natty.
When I clicked on your link OpenDNS flagged it for some unknown reason.
I did get this link to work correctly: (I googled it)

[http://users.telenet.be/on4qz/history/index.html](http://users.telenet.be/on4qz/history/index.html)

:popcorn:Larry H  KA4BXY

---

### Post by ab8cl on 2012-07-07
I am running latest version and calibration doesn't work? Running Ubuntu 12.04.  response to 
ntpdc -p  shows me 
=europium.canoni 192.168.1.102    2   64   37 0.11703  0.604649 0.66206
=vps1.bbnx.net   192.168.1.102    2   64   37 0.05428  0.595357 0.66205
*voxl-nyc-15.ser 192.168.1.102    2   64   37 0.03119  0.590272 0.66205
=javanese.kjsl.c 192.168.1.102    2   64   37 0.04021  0.599238 0.66206
=ns1.your-site.c 192.168.1.102    3   64   37 0.04091  0.606640 0.66206
I never get the box that shows it is calibration.  any help please.
Thanks for neat program for sstv.
Keith AB8CL

---

### Post by kd5mkv on 2012-07-30
It worked a few weeks ago, I recently compiled on another machine and have noticed it has stopped working. You may want to email author at his address, as he is active again. He has helped people on this forum before.
Bug report  [email]on4qz@telenet.be[/email] 

I submitted a bug report and received a reply.steve kd5mkv

---

