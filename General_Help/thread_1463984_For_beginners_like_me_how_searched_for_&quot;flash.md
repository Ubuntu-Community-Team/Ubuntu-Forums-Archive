---
title: "For beginners like me how searched for &quot;flashmute&quot; equivalent on ubuntu forum"
date: 2010-04-27
forum: General Help
---

### Post by mzweep on 2010-04-27
Hello, 
I recently switched to ubuntu to replace an old buggy windows installation.
I found everything I need for everyday life, except... Flashmute. (small utility on windows system that mute firefox or any browser, including stupid flash ads or guys who put a flash player on their website). 
So I searched Ubuntu forums for Flashmute, and found only one thread, dated January 5th, 2008 !!!

So I want to post this for every new linux user who wants a flashmute equivalent.

The January 5th, 2008 post leads me to PulseAudio, which is integrated in the Karmic I installed... using firefox, Flashmute could be made with only two command lines :

Command to mute firefox:
```

pacmd "set-sink-input-mute `pacmd list-sink-inputs | egrep "index|application\.name" | grep -B1 firefox | grep index | sed 's/.*index: //'` 1"

```Command to unmute firefox:
```

pacmd "set-sink-input-mute `pacmd list-sink-inputs | egrep  "index|application\.name" | grep -B1 firefox | grep index | sed  's/.*index: //'` 0"

```Create two text files, put the correct command into them, chmod +x this files, and create two launchers with nice icons (for example a speaker and a speaker with a cross on it) on the top bar... and you have a flashmute equivalent.
Of course, you could set up keyboard shortcuts into system/preferences/keyboard
You could do better with one script to really "toggle" mute, but I prefer having two separated icons.

Hope this could help. Using ubuntu since 16 days, I am very happy with it ! I didn't use linux since I run an old debian IRC/web server in my student room, 7 years ago... with no X server.

(hum, this is my first post, maybe I didn't respect some rules ?)

---

