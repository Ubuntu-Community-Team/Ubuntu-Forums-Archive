---
title: "Sound - Weird 'clack' on my speakers with 9.10"
date: 2010-01-09
forum: General Help
---

### Post by Kredible on 2010-01-09
Hello everyone, I am having this strange 'clack' sound whenever my computer is silent for a couple of seconds and then I do something that would require (or not) a sound to be played.

Let me give you an example: If I am using Skype, and speak to someone, when that person replies, I receive a sound notification, right before that I hear this 'clack', then for the rest of the notifications, nothing similar happens. It will only happen again if the speakers won't produce any sound for a couple of seconds, and then have to play any type of sound.
It seems as if the sound card goes into low consumption mode and turns off, then whenever it needs to work, it just wakes up all surprised! It has only happened after I updated to ubuntu 9.10.

Any help? It's nothing big but it doesn't sound too healthy for my machine.
Oh, right, I am on a Acer Aspire 5920G.

Note: It's like when you click the power button on one of those portable radios, there's always that little 'clack' before the radio starts transmitting sound.

---

### Post by Kredible on 2010-01-10
Well, problem solved! Although there are many posts/topics regarding sound with the 9.10 version, many mentioning no sound, which was not my original problem. Well, I looked up in other websites and managed to fix what was going on! Basically my tip was right, it really felt like Ubuntu was  shutting down the audio when it was idle, for X seconds.

If you check out the **alsa-base.conf** file:

```
**$ sudo gedit /etc/modprobe.d/alsa-base.conf** 
```You will see the last line looks something like this:

*```
options snd-hda-intel power_save=10 power_save_controller=N
```*And I am sure that I am no Ubuntu expert, as I still struggle with the console, but I'm pretty sure that power_save=**10** means that if your sound card is not producing sound for 10 seconds, it will 'go to sleep'.

So I just commented the last line by using the **#** and now my alsa-base.conf file's last line is:

```
***#**options snd-hda-intel power_save=10 power_save_controller=N*
```

I hope this helps someone, so this thread isn't so useless, and I apologize if this issue was posted/solved somewhere else, but I didn't find it!
:D

---

### Post by pbrane on 2010-01-10
here is a thread that has some more info. some of it may be of use.

[http://ubuntuforums.org/showthread.php?t=1043568&page=10]("http://ubuntuforums.org/showthread.php?t=1043568&page=10")

---

