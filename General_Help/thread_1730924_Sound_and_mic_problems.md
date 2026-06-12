---
title: "Sound and mic problems"
date: 2011-04-16
forum: General Help
---

### Post by tryceo on 2011-04-16
There are two main problems with my Linux system right now.

1. The microphone doesn't work. There is a microphone port in the front of my computer, and it works when I'm in Windows 7, but does not when I'm on Linux. The microphone doesn't even show up in the Sound Preferences place. I think it might be a driver problem, but have no idea about how to fix it.

2. Sound comes out of both my headphones and my speakers. In Windows, there are two distinct sound options of headphones or speakers, just as there are two different plugs. My speakers are plugged in the back of my system, and my headphones are plugged in the front. However, when I plug my headphones in the front, the sound from the speakers still comes out, unlike in Windows, where the headphones override the sound output of the speakers. I was wondering if there a way to fix this, by having the OS recognize two different sound outputs instead of just one.

Any help is appreciated.

---

### Post by BAZTED on 2011-04-16
I have the same problem on my ASUS K50AD.
+ camera is down-headed

---

### Post by Irony on 2011-04-16
Try running in terminal;

```
gstreamer-properties
```

Press the test button on the sound tab, you should hear an echo of your voice when talking into the microphone - try the plugin button.

---

### Post by tryceo on 2011-04-17
> **Irony said:**
> Try running in terminal;

```
gstreamer-properties
```Press the test button on the sound tab, you should hear an echo of your voice when talking into the microphone - try the plugin button.

Doesn't work... I press test on the Default Input place, but doesn't hear anything good. I tested all the plugin's but none of them echo my voice.

---

