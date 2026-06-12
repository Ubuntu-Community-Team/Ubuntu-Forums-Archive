---
title: "I Can Hear My Microphone But Can't Record?!"
date: 2010-05-30
forum: General Help
---

### Post by derekeverett on 2010-05-30
Hi Everyone,

I have gotten my microphone working, this was an issue for a long time.

Now I can hear myself through my headphones so I know the computer is "hearing" it.

But... I still show "No Input Devices Available" in my Pulse Audio volume control so I'm still not able to record... which of course is my whole point.

Any ideas? Thanks.

---

### Post by fragos on 2010-05-30
Run alsamixer in a terminal window. It shows all possible sound channels and allows you to set/clear Mute and adjust the channels volume. It has always fixed sound related issues for me.

---

### Post by derekeverett on 2010-05-30
> **fragos said:**
> Run alsamixer in a terminal window. It shows all possible sound channels and allows you to set/clear Mute and adjust the channels volume. It has always fixed sound related issues for me.

Thank you for replying, but I've already tried that a few times now.

It was through gnome-alsamixer that I was finally able to fix it so that I could hear the input, but I still can't record as apparently pulse-audio doesn't think I have any input devices.

---

### Post by fragos on 2010-05-30
In sound preferences make sure the input connector is set to a microphone and not line. The sound recorder ap is a good simple ap to test operation with. Note that if you're using Skype it has a different set of configuration parameters.

---

### Post by derekeverett on 2010-05-30
> **fragos said:**
> In sound preferences make sure the input connector is set to a microphone and not line. The sound recorder ap is a good simple ap to test operation with. Note that if you're using Skype it has a different set of configuration parameters.

Again thank you. But done and done. I've tried every option available in sound preferences and test recording with several apps, and nothing.

I've gotten it to work in, Windows and Debian Lenny. And on a mac as well. But I'd really like to get it working in Ubuntu. But I think I'm out of options. I'm almost sure at this point that it's pulseaudio. I just don't know what to do about it.

---

### Post by finlost on 2010-05-30
What software are you trying to record in?

---

### Post by derekeverett on 2010-05-30
> **finlost said:**
> What software are you trying to record in?

I've tried the regular ol' Sound Recorder, gtk-recordmydesktop and audacity.

No luck with any of them.

I've been recording with Audacity and Camtasia on Windows on this same machine without issue.

---

### Post by finlost on 2010-05-30
[Does this YouTube help?]("http://www.youtube.com/watch?v=V0guzwfNKY8")

---

### Post by derekeverett on 2010-05-31
> **finlost said:**
> [Does this YouTube help?]("http://www.youtube.com/watch?v=V0guzwfNKY8")

Thanks again. But I've tried all that too. I think I'm just going to have to buy a new microphone set-up that will work with pulseaudio.

---

