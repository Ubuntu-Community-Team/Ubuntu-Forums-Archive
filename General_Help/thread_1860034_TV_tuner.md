---
title: "TV tuner"
date: 2011-10-14
forum: General Help
---

### Post by jtheb on 2011-10-14
I am currently using a Hauppauge TV tuner card from my 11 year old Dell Desktop and it works beautifully with TV Time and Ubuntu 10.4.  Our cable company is going to digital signals soon which means i have to use their device to change the digital signal to the old analog.

I don't want to do that.  Is there a device for Ubuntu for digital TV and HD by chance?  Hope so!

---

### Post by fragos on 2011-10-15
I have Comcast and they went digital for basic service as well. They provided a digital to analog convertor so existing analog TV equipment would work, including my old Hauppauge WinTV tuner with TVtime.

---

### Post by jtheb on 2011-10-16
> **fragos said:**
> I have Comcast and they went digital for basic service as well. They provided a digital to analog convertor so existing analog TV equipment would work, including my old Hauppauge WinTV tuner with TVtime.

Thanks and i can get the same from Media Com
Was hoping to find a digital/HD card that would work

---

### Post by fragos on 2011-10-16
> **jtheb said:**
> Thanks and i can get the same from Media Com
Was hoping to find a digital/HD card that would work

Hauppauge WinTV-HVR 1250 works directly connected to the Comcast cable without the the adapter box they provided. In Comcasts case none of the channels included in the basic package are encrypted, only the the likes of HBO are. My channels are all QAM256 and are view-able with the 1250. Note the 1250 comes with an IR remote but it isn't supported by Linux. I'm using the MeTV package with Ubuntu. I'll miss TVtime. Your big issue will be to come up with a list of the frequencies to be scanned for the channels Media Com provides.

The attached file Comcast-QAM256 may be helpful for that.

---

### Post by jtheb on 2011-10-17
> **fragos said:**
> Hauppauge WinTV-HVR 1250 works directly connected to the Comcast cable without the the adapter box they provided. In Comcasts case none of the channels included in the basic package are encrypted, only the the likes of HBO are. My channels are all QAM256 and are view-able with the 1250. Note the 1250 comes with an IR remote but it isn't supported by Linux. I'm using the MeTV package with Ubuntu. I'll miss TVtime. Your big issue will be to come up with a list of the frequencies to be scanned for the channels Media Com provides.

The attached file Comcast-QAM256 may be helpful for that.
-------------------------------------------------------------

I installed the digital tuner and have the picture but no sound.  It is supposed to have a five digit code they give for TV sets so TV time of course is not there.  Not sure how I got the picture w/o the code.  Now I just have to tweak the sound and so far it is a mystery or misery.

---

### Post by fragos on 2011-10-17
It's likely that the sound source is muted. Run alsamixer in a terminal.

---

### Post by jtheb on 2011-10-17
It was muted
All is ok in Ubuntu world
Thanks

---

### Post by Daibhi on 2011-11-01
WIll try also connecting directly. Have jumped through a bunch of hoops at this end to try and get my Hauppauge 1250 card to run in my tower. The upside is that now xFinity which is Comcast, offers the main shows I watch tunable through their website. But that still leaves me cut out of the look for the other 200 odd channels. Other than that I'm spending more time playing in Ubuntu that I am in Windows which is a good thing.

---

### Post by Daibhi on 2011-11-02
FWIW I did do a direct connect and tuned through Kaffiene, this time I was able to pull in some stations, some of which I am interested and then some like Home Shopping Network and all the Jewelry infomercials. Sorry folks, I'm not into infomercial channels.

---

