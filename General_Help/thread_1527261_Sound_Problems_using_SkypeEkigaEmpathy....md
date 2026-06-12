---
title: "Sound Problems using Skype/Ekiga/Empathy..."
date: 2010-07-09
forum: General Help
---

### Post by vickoxy on 2010-07-09
Hi,
on my thinkpad r500 i am using Ubuntu 10.04 64bit and have lots of problem with sound using skype. After few seconds i loose in coming sound. Video is going on. So i installed ekiga and empathy and succeeded to activate Video using gmail accounts, but have no luck with incoming voice...
Other side hears my voice just normally.
I played with panel sound settings, but nothing. Any idea, how to make other people to hear me?

Thanks

---

### Post by lidex on 2010-07-09
Have a look here:
[https://help.ubuntu.com/community/SkypeTroubleshooting]("https://help.ubuntu.com/community/SkypeTroubleshooting")

---

### Post by vickoxy on 2010-07-10
> **lidex said:**
> Have a look here:
[https://help.ubuntu.com/community/SkypeTroubleshooting]("https://help.ubuntu.com/community/SkypeTroubleshooting")

Well, under Skype i have no problems with selecting devices,but after some time the other side can not hear me. With ekiga and empathy other side can not hear me from the start.
I don´t know what schould i selected at above pointed link...

---

### Post by lidex on 2010-07-10
> **vickoxy said:**
> Well, under Skype i have no problems with selecting devices,but after some time the other side can not hear me. With ekiga and empathy other side can not hear me from the start.
I don´t know what schould i selected at above pointed link...

You should do this:
> On skype, go to the options menu and look under the sub-menu "sound devices". Switch "Sound out" and "Ringing" to "pulse". In "Sound in", test all the options until you can hear your voice when making a test call. 
Also uncheck the option to let skype change your sound levels. Try the pavucontrol part. I would not suggest removing pulseaudio yet. 

More:
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/]("http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/")

---

### Post by vickoxy on 2010-07-10
> **lidex said:**
> You should do this:

Also uncheck the option to let skype change your sound levels. Try the pavucontrol part. I would not suggest removing pulseaudio yet. 

More:
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/]("http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/")

Well, i have that already and i can not change, even if i unmark auto setup. 
And test call  does job just normally...

---

### Post by lidex on 2010-07-10
You should be able to uncheck that option. They even mention that on the skype wiki. You may need to re-install it.

---

