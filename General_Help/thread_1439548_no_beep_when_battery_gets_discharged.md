---
title: "no beep when battery gets discharged"
date: 2010-03-26
forum: General Help
---

### Post by AbuseArt on 2010-03-26
Hello!

When I was using Windows XP, my notebook was beeping very loud when it was running out of power. Since I use Ubuntu it doesnt. I have tried kpowersave but it somehow cannot play ANY SOUNDS. Now I use default power management  and it doesn't beep too.
How can I fix it? Its quite important because I often forget to hook it up.

---

### Post by mikewhatever on 2010-03-26
Try opening alsamixer from Terminal, and make sure the 'beep' channel is not muted. If it is, unmute is with the 'm' key and raise its volume with up/down arrows. There might a gui for this, but I am not familiar with Kubuntu.

---

### Post by 3rdalbum on 2010-03-26
> **AbuseArt said:**
> Hello!

When I was using Windows XP, my notebook was beeping very loud when it was running out of power. Since I use Ubuntu it doesnt. I have tried kpowersave but it somehow cannot play ANY SOUNDS. Now I use default power management  and it doesn't beep too.
How can I fix it?

Strictly speaking, it's not a "problem", so it doesn't require a "fix". Ubuntu doesn't beep when your battery is running low, it displays notifications; that's done by design (less intrusive if you're aware that the battery is low, also uses less power to not beep).

The Udev system could probably be rigged up to do what you're asking about, but I don't actually know how to create udev rules. If you want to research it, go right ahead - just bear in mind that you can get the terminal to play a sound file by installing the "sox" package and using the command:

```
play "filename.wav"
```

So make sure you put that in your Udev rule (assuming this can be done).

---

### Post by AbuseArt on 2010-03-26
Thanks but it seems to be difficult. I'm newbie.

Would it be possible to fix kpowersave to play sounds? They dont work even when i click play button beside filename of a sound.

---

