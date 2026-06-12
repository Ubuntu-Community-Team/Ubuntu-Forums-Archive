---
title: "No Sound =("
date: 2009-07-08
forum: General Help
---

### Post by Chase Young on 2009-07-08
Hey guys, I know this particular problem has been posted before, and I've seen a lot of links to this thread in particular:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

But I tried almost everything on there and I still can't hear sound. My speakers are turned up on full and all of the volumes in the volume control are turned up on full as well. Is there more solutions? From what I read, my sound card is supported by ALSA, so I don't get it :S

Can anybody help?

---

### Post by chriskin on 2009-07-08
wouldn't it be better for those who will answer after me if you said which sound card you have? :)

---

### Post by Chase Young on 2009-07-08
Hmmm...You may be on to something there... =P Yea, I'll get it.

"aplay -l" says my sound card is this:

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

=)

---

### Post by chriskin on 2009-07-08
strangely enough i have the same and sound is pretty much perfect, which release of ubuntu do you have?

---

### Post by Chase Young on 2009-07-08
9.04 =D But I used to have 8.10 (I think) and it didn't work on that either. I am, however, running a laptop, so the speakers aren't plugged in, they're built in. Are you on a laptop also? Becuase that would be very odd indeed.

---

### Post by chriskin on 2009-07-08
yep, a custom built laptop

mine didn't work on 8.04, worked partially on 8.10 and work ok on 9.04
anyway, let's not fill this page as i have nothing else to add
let's wait for someone else to help you , sorry

---

### Post by draperdt on 2009-07-08
I had similar problem. I had to go to the alsamixer from terminal and raise the sliders till I got the volume. 

I dont know if it would help your situation though.

---

### Post by Roasted on 2009-07-08
Make sure "PCM" is not muted and turned up a good deal.

You know how Windows has "volume" and "wave" and they both seem to control the volume level? In Linux, it's "volume" and "PCM."

---

### Post by Chase Young on 2009-07-08
How would I access the Alsamixer from a terminal?

@Chris: No need to apologize.
@Roasted: As said in my thread, all the volume controls are on full.

---

### Post by michy99 on 2009-07-08
```
alsamixer
```

---

### Post by Chase Young on 2009-07-08
Well the PCM in the Terminal alsamixer was turned off, but it's on 100 now, and still, no sound. Any other suggestions? =)

Thanks for everybody who's helped so far, I apprectiate it.

---

### Post by Roasted on 2009-07-08
Just to make sure, what are you using to test your sound? Are you using the test features in system - preferences - sound? 

What device is selected there? ALSA? Or something else?

---

### Post by chriskin on 2009-07-08
might be useless, but i have added the packages said here
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

haven't tested sound before them though to know if i had any problem, it is like a default thing i do after the installation - adding those package i mean

---

### Post by Chase Young on 2009-07-08
@Roasted: Alsa, and yes, thanks.
@Chris: Thanks a lot, I'll install those now and post back results =) I hope it works!

---

### Post by Chase Young on 2009-07-08
Unfortunately, it failed. Thanks for trying though.

---

