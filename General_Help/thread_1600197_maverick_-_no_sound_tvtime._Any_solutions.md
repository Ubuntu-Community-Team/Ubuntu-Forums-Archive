---
title: "maverick - no sound tvtime. Any solutions?"
date: 2010-10-18
forum: General Help
---

### Post by bowens44 on 2010-10-18
Has anyone been able to get sound out of tvtime time in ubuntu 10.10? If so have you also been able to get the internal volume control to work.


I just amazed that ubuntu devs would just shut off this functionality that affects much more the just tvtime and not offer a viable alternative.

Is there an alternative? I haven't been able to find after a week or so of googling.

---

### Post by guzowskip on 2010-10-22
Running Maverick Meerkat on an AMD64-based system with on-board nVidia chipset and 4gb RAM.

With 10.4, Lucid Lynx, I was happily using mplayer to watch analog tv (channel 3) from my cable box using the following command:

mplayer -vo xv tv:// -tv driver=v4l2:alsa:immediatemode=0:adevice=hw.1,0:norm=ntsc:chanlist=us-cable:channel=3

When I upgraded to Ubuntu 10.10, Maverick Meerkat, the audio and video became so disjointed I had to find something else.  

A work colleague suggested tvtime but I encountered the same sound problem and it is vexing indeed.  There are many opinions about what the problem is but most seem to center on pulseaudio.  Some suggest changing things in alsa mixer but I couldn't get any of thos to work.  Finally, I stumbled upon this suggestion and it works though there is a very, very minor synch problem between audio and video.  It's not elegant but a work around that gets sound for me is to start tvtime from a terminal as follows:

tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

You won't have any control of volume from within tvtime but at least you can watch tv with sound.

---

### Post by franket on 2010-10-23
I just install ubuntu 10.10 today and i found this problem too.

I can't setting line Channel one Sound setting

now I can Solv this problem by install gnome-alsamixer and unmute line This work for me.:guitar:

---

### Post by AllGamer on 2011-04-24
> **franket said:**
> 
now I can Solv this problem by install **gnome-alsamixer** and **unmute line-in** This work for me.:guitar:

This is the easiest solution by far, simple, fast, and clean :KS

---

### Post by lonewohlf42 on 2011-04-25
I had the same problem and discovered that installing a much earlier kernel fixed the problem on 10.04 but didn't work on 10.10. Sound bar displays but never increases from zero.:)

---

### Post by lonewohlf42 on 2011-04-25
Thanks for that Gnome-alsamixer tip works.

---

### Post by AllGamer on 2011-04-25
> **lonewohlf42 said:**
> I had the same problem and discovered that installing a much earlier kernel fixed the problem on 10.04 but didn't work on 10.10. Sound bar displays but never increases from zero.:)

yes, that's exactly the problem TvTime always gets stuck in Zero volume.

So, even after trying out those other commands and making the CD-in available to the alsa driver it was still not getting any sound.

so the last resort was to use the in-line method, using a shorter 3.5mm to 3.5mm cable you can easily hide and tug it into the case ;)

---

### Post by franket on 2011-05-02
Today I install ubuntu 11.04 and found this problem again but can solv by install gnome-alsamixer too :)

---

