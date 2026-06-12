---
title: "Need some help with mplayer"
date: 2010-01-02
forum: General Help
---

### Post by cannon_dt on 2010-01-02
Hello,
I just installed the latest 9.10 64 bit version and was setting up my usual list which includes mplayer.
Now when I load a video and hit F, the screen is full size but the video within is still the same size - at the centre, very small
How do I get the video also to occupy the full real estate?

Please help

ananth

---

### Post by cannon_dt on 2010-01-03
Is my question unclear or is there no one who has faced this problem before and found a solution?

---

### Post by andrew.46 on 2010-01-03
Hi ananth,

> **cannon_dt said:**
> I just installed the latest 9.10 64 bit version and was setting up my usual list which includes mplayer.
Now when I load a video and hit F, the screen is full size but the video within is still the same size - at the centre, very small
How do I get the video also to occupy the full real estate?

It could be that your video output device is something like x11, running x11 full screen by default will show the behaviour you describe. Could you have a look at the video out that is set and if it is x11 try setting it to something like xv.

All the best,

Andrew

---

### Post by cannon_dt on 2010-01-04
Error opening/initializing the selected video_out (vo) device.

This is what I get when I set xv :(

---

### Post by andrew.46 on 2010-01-04
Hi cannon_dt,

Could you try your file from the commandline as follows:

```
mplayer -vo x11 -fs -zoom ***[COLOR="Red"]myfile[/COLOR]***
```

where 'myfile' is the name of your media file? This should play full screen and if so it should be a simple matter to add the options to your configuration.

Andrew

---

### Post by cannon_dt on 2010-01-05
Andrew,
From the CL it worked.
I dont want FS and when i ran the CL you gave it worked without the fs.
I was able to change gui.conf anf set x11 but where do I set zoom in the UI.
I tried adding zoom="yes" in gui.conf but that did not help.
Can you please help here, apologies as you expected me to figure out the adding of the options myself - I did try :(

Ananth

---

### Post by andrew.46 on 2010-01-05
Hi Ananth,

> **cannon_dt said:**
> I tried adding zoom="yes" in gui.conf but that did not help. Can you please help here, apologies as you expected me to figure out the adding of the options myself - I did try :(

I will confess that I do not use the MPlayer gui gmplayer, which is why I did not explicitly mention where the zoom setting should go :). I am not sure how $HOME/.mplayer/config and $HOME/.mplayer/gui.conf interact but I have a suspicion that if you place *zoom=yes* in the $HOME/.mplayer/config file you might be ok. Unfortunately I have not tested this.

Hopefully this will work and this may be enough for you, but consider using a better gui such as SMPlayer which is available from the Ubuntu repository:

```
sudo apt-get install smplayer
```

as this is well supported and under active development while GMPlayer has been effectively abandoned by the MPlayer developers.

All the best,

Andrew

---

### Post by cannon_dt on 2010-01-06
Thanks a lot Andrew.
Did install smplayer and it is swell !!

Peace.
Ananth

---

### Post by andrew.46 on 2010-01-06
Hi Ananth,

> **cannon_dt said:**
> Thanks a lot Andrew.
Did install smplayer and it is swell !!

Excellent news :).

Andrew

---

