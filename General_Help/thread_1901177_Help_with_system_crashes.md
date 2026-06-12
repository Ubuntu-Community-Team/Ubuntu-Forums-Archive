---
title: "Help with system crashes"
date: 2011-12-28
forum: General Help
---

### Post by Mr Nemo on 2011-12-28
My system freezes at random times and I can't seem to find the reason why. It mostly seems to crash while watching some type of video, be it online (flash or whatnot) or with smplayer/mplayer (im seeing if switching to VLC will solve the problem somewhat). At other times my system will freeze even if I'm not playing a video, but it mostly happens when a video is playing. When it crashes I have to restart, alt + f* will not work, although I am still able to open my disk drive. Any ideas would be appreciated. 

Dell XPS 15 - L502x
Nvidia GeForce GT 540M 2gb (OPTIMUS) *iron-hide installed properly
Intel I-7 2630QM Processor
Ubuntu 11.04 64 bit

I have Ubuntu dual booted with windows 7, and I don't have any problems with windows

The only thing i can think of is when I look in the disk utility it says that the partition is misaligned by 512 bytes, but research on Google says that shouldn't affect anything and I'm pretty sure I still had the freezing problem before the misalignment showed up.

---

### Post by 2F4U on 2011-12-28
Did you look into the system log files? What does it show at the time of the freeze?

---

### Post by 3rdalbum on 2011-12-28
It might still be a problem with bad RAM. It may manifest itself when working with big files, for instance, ripping a DVD. Windows leaves a big area of RAM basically unused, and if the bad section of RAM is in that unused area you won't see a problem on Windows (until the bad spot extends outside that area, which invariably happens...)

Unfortunately on a laptop it's sometimes not trivial to open the case and remove some RAM. If it IS easy, then give that a try and see if you can pin down which RAM stick is the bad one. Otherwise, try running the Phoronix Test Suite memory benchmark twice or Memtest for twenty four hours. If either crashes or fails, then you should contact the computer's manufacturer and get them to replace the RAM.

---

### Post by pretty_whistle on 2011-12-28
Could be some program is a CPU hog.  That can cause this.

I was having a similar issue.  I had a thread about my problem, which is here (make a note of post #14):


[http://ubuntuforums.org/showthread.php?t=1900461&page=2](http://ubuntuforums.org/showthread.php?t=1900461&page=2)

This will help you identify a cpu hog.

---

### Post by Mr Nemo on 2011-12-28
Thanks for the responses. I've run memory test for a pass and nothing came up. Ill try again for 24 hours. It seems to mostly happen when watching a video, but sometimes it crashes when the system is sitting idly.

Ill take a look at the log files and post anything that looks suspicious.

---

### Post by Mr Nemo on 2011-12-29
I looked through my log folder and im not sure which ones i would need to look at. Is there a specific file I should post?

---

### Post by Mr Nemo on 2011-12-31
bump

---

### Post by Mr Nemo on 2012-01-03
bump for one last try. Any information I should provide?

---

### Post by Mr Nemo on 2012-01-10
Now I don't really think it has too much to do with the GPU. When the system locks up only a few lights will work. Alt + F1 does not work, the caps lock button won't work, but the cd tray will open.

I've updated my video drivers and anything else i can think of.

---

### Post by varunendra on 2012-01-11
Hi,

So have you tried all the debugging options suggested above? That is - running memtest for 24+ hrs, and running '**top**' command permanently in the background to see if something's hogging CPU/RAM when it freezes.

Among the log files (in /var/log) we are interested in **syslog **file.

Also, install **lmsensors **and run **sensors** command to monitor the temperatures of your CPU cores and motherboard (if available).

---

### Post by Mr Nemo on 2012-01-11
Thanks for the reply,

Ran memtest for 24 hours. No problems. Nothing really seems to be hogging my CPU but I'm gonna keep top open for a bit longer to make sure. Lmsensors is already installed and my temps seem to be pretty stable even when running something intensive.

I was running 11.04 and decided to upgrade to 11.10 to see if that would fix my problem. I just did it, so if my system crashes again ill post my syslog unless you would like to look over it now.

Again thanks for the reply.

---

