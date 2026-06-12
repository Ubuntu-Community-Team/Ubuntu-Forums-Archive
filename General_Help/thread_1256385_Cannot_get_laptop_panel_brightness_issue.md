---
title: "Cannot get laptop panel brightness issue"
date: 2009-09-02
forum: General Help
---

### Post by vi3t1uv on 2009-09-02
Here's a little background:
I successfully installed Ubuntu 9.04 x64 on my HP DV5t-1000 Laptop. Everything was fine until last night then in noticed the Power Manager Brightness on the top panel display a red icon like this:[IMG]http://img136.imageshack.us/i/screenshotfsg.png/[/IMG]  [IMG]http://img136.imageshack.us/img136/1707/screenshotfsg.png[/IMG]
 and it display the following message "Cannot get laptop panel brightness".  And i wasn't able to adjust any of the brightness level through the Power Managementat all. It was working fine before without any problem, i don't know why that happened. I also tried to look up in Google but no luck, is anyone out there experience this kind of issue, any luck try to get it fixed? Thanks in advance.

---

### Post by michaelzap on 2009-09-02
Same here on a Lenovo Y530 running Jaunty 64-bit. The most recent updates broke brightness control for me. Probably the new kernel, I guess.

I ad brightness issues before these updates. I could control the brightness using the panel app, function keys, or power management control panel, but the screen would frequently flash brighter on mouse movement and playing videos dropped the brightness down to very dark. That's actually the only reason that I added the brightness panel app to my top bar: I had to adjust it all the time.

Now it doesn't flash and playing videos doesn't affect the brightness, so in a way I prefer it this way (but I'd be even happier if it just worked correctly).

---

### Post by vi3t1uv on 2009-09-02
> **michaelzap said:**
> Same here on a Lenovo Y530 running Jaunty 64-bit. The most recent updates broke brightness control for me. Probably the new kernel, I guess.

I ad brightness issues before these updates. I could control the brightness using the panel app, function keys, or power management control panel, but the screen would frequently flash brighter on mouse movement and playing videos dropped the brightness down to very dark. That's actually the only reason that I added the brightness panel app to my top bar: I had to adjust it all the time.

Now it doesn't flash and playing videos doesn't affect the brightness, so in a way I prefer it this way (but I'd be even happier if it just worked correctly).
Yeah that's right. It happened to me right after those new updates. Lucky for me I didn't any of the screen problems other than the ability to adjust the brightness level. So currently there's no fix, or any work around to get it back to normal again? :confused:

---

### Post by michaelzap on 2009-09-02
> **vi3t1uv said:**
> Yeah that's right. It happened to me right after those new updates. Lucky for me I didn't any of the screen problems other than the ability to adjust the brightness level. So currently there's no fix, or any work around to get it back to normal again? :confused:

I imagine you could choose the older kernel when you boot up and that might fix it for you. I figure there will probably be an update that fixes it sometime soon so I'm going to wait it out. Of course I actually prefer the current broken status to the previous one.

---

### Post by vi3t1uv on 2009-09-03
> **michaelzap said:**
> I imagine you could choose the older kernel when you boot up and that might fix it for you. I figure there will probably be an update that fixes it sometime soon so I'm going to wait it out. Of course I actually prefer the current broken status to the previous one.

Then would everything including updates will be reverse (undo) if you boot using the older kernel, wouldn't it? Sorry,i'm new to liux. Yea, i think i'm just gonna wait it out to see what happen.

---

### Post by pteglia on 2009-09-03
I can verify that using the previous kernel (the .14 I think) makes it possible to adjust the brightness again on my Y530.  Didn't seem to mess anything else up either.

---

### Post by michaelzap on 2009-09-03
> **pteglia said:**
> I can verify that using the previous kernel (the .14 I think) makes it possible to adjust the brightness again on my Y530.  Didn't seem to mess anything else up either.

Since you also have a Y530, maybe you can answer a couple questions for me:

I had the annoying brightness issue mentioned above with the earlier kernel; did you experience that also? And if so, did you find a solution for it? I have an Intel (not nVidia) video card in my Y530.

I also have to use Alsa to get my 5.1 sound working, but I have an annoying issue where if Firefox has played any Flash audio I can't play any audio or video files in any other program until I first quit my browser. Does your 5.1 sound work with Pulseaudio, or did you find another solution?

I am running Jaunty 64-bit with all updates and my usual browser is Shiretoko (Firefox 3.5) with Flash 10.

---

