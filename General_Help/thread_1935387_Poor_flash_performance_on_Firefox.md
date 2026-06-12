---
title: "Poor flash performance on Firefox"
date: 2012-03-04
forum: General Help
---

### Post by hatrox on 2012-03-04
I've noticed for some time a quite subpar flash performance in Firefox. When playing a 5 minute 720p youtube video, Firefox drops about ~500 frames, compared to Chrome's ~50 for the same video. Why is that?
I'm running Ubuntu 10.10 on a hp dv5 notebook with Intel T9400, 512MB NVidia 9600M GT and 3 gigs of ram. I have the most recent GPU driver, available from NVidia for Linux (295.20), the latest Adobe flash (11.1.102.62) and the latest Firefox (10.0.2).

---

### Post by synaptix on 2012-03-04
Have you considered trying to use the latest beta version of Flash via Flash-Aid addon? I find the beta versions seem to work better than stable in Firefox.

Also using Flash-Aid will apply the GPU override validation to Firefox (if you don't already have it), which increases performance and full-screen issues.

---

### Post by lovinglinux on 2012-03-04
> **hatrox said:**
> I've noticed for some time a quite subpar flash performance in Firefox. When playing a 5 minute 720p youtube video, Firefox drops about ~500 frames, compared to Chrome's ~50 for the same video. Why is that?
I'm running Ubuntu 10.10 on a hp dv5 notebook with Intel T9400, 512MB NVidia 9600M GT and 3 gigs of ram. I have the most recent GPU driver, available from NVidia for Linux (295.20), the latest Adobe flash (11.1.102.62) and the latest Firefox (10.0.2).

If the performance drops after a while playing the video, then is most likely to be CPU overheating. Flash uses too much CPU even with standard video quality, but can be really intensive with HD content.

I have tested the flash CPU usage on Firefox, Chrome and Opera, using the same flash streaming source and the latest beta version of flash. Here are the results:

**Chrome:**

[IMG]http://i.imgur.com/VEQ2I.png[/IMG]


**Opera:**

[IMG]http://i.imgur.com/G9dvh.png[/IMG]


**Firefox**

[IMG]http://i.imgur.com/vgMrG.png[/IMG]


Although my results show that Firefox has the best CPU usage results, I have noticed it has the worst performance. For instance, if I am watching a video on a separate window and browsing at the same time on another, flash freezes a lot when loading new links. The same problem occurs on Chrome, but less frequently. The best performance on such scenario is from Opera, which practically doesn't freeze. I haven't tested the effects after a prolonged period watching a video and didn't measure frame drop tho. However, I haven't noticed any performance difference after streaming a standard quality video for several hours.

Using Flash-Aid as already mentioned will probably help, but I would also consider checking the cleanliness of your CPU and video card fans.

The difference you are experiencing could be, if you are on a 32bit system, due to the bundled flash version that comes with Chrome. If you use the Advanced mode of Flash-Aid, you can easily copy the plugin from Chrome to use it on Firefox.

---

### Post by hatrox on 2012-03-04
Also I forgot to mention I'm currently using two monitors in TwinView. I'm usually playing a video on one and working on the other. I know this can be very CPU intensive, but doing so on Windows almost doesn't drop any frames.
> **lovinglinux said:**
> If the performance drops after a while playing the video, then is most likely to be CPU overheating. 
I find that unlikely, as I'm using an applet, which allows me to constantly monitor my CPU, GPU and HDD temps, because the cooling system on HP dv5 is absolutely horrendous. Although the temperatures do rise, while playing a flash HD video, they don't get high enough to actually affect the performance of the notebook.
> **lovinglinux said:**
> The difference you are experiencing could be, if you are on a 32bit system, due to the bundled flash version that comes with Chrome. If you use the Advanced mode of Flash-Aid, you can easily copy the plugin from Chrome to use it on Firefox.
I did try copying the plugin from Chrome with Flash-Aid, but to no avail - the performance remains unaffected.

---

### Post by lovinglinux on 2012-03-04
> **hatrox said:**
> Also I forgot to mention I'm currently using two monitors in TwinView. I'm usually playing a video on one and working on the other. I know this can be very CPU intensive, but doing so on Windows almost doesn't drop any frames.

I find that unlikely, as I'm using an applet, which allows me to constantly monitor my CPU, GPU and HDD temps, because the cooling system on HP dv5 is absolutely horrendous. Although the temperatures do rise, while playing a flash HD video, they don't get high enough to actually affect the performance of the notebook.

I did try copying the plugin from Chrome with Flash-Aid, but to no avail - the performance remains unaffected.

How are you measuring frame drop?

---

### Post by hatrox on 2012-03-04
> **lovinglinux said:**
> How are you measuring frame drop?
Right click on a video in YouTube, then "Show video info".

---

### Post by lovinglinux on 2012-03-04
> **hatrox said:**
> Right click on a video in YouTube, then "Show video info".

Do you actually perceive the performance drop or you just considering the benchmark?

Can you post the link of the video you are testing?

---

### Post by hatrox on 2012-03-04
> **lovinglinux said:**
> Do you actually perceive the performance drop or you just considering the benchmark?
A little of both, actually - sometimes the video gets very choppy, which of course reflects in a high number of dropped frames.
> **lovinglinux said:**
> Can you post the link of the video you are testing?
It happens on virtually every HD 720p video. Right now I'm testing [here](http://www.youtube.com/watch?v=rmR3kp1pYt0).

---

### Post by lovinglinux on 2012-03-04
> **hatrox said:**
> A little of both, actually - sometimes the video gets very choppy, which of course reflects in a high number of dropped frames.

It happens on virtually every HD 720p video. Right now I'm testing [here](http://www.youtube.com/watch?v=rmR3kp1pYt0).

I suspect is a network issue, not a performance issue.

Start the video, click pause and let it buffer all the way to the end. Click play and check if drops as many frames as before.

Let me know the results.

---

### Post by hatrox on 2012-03-11
I fixed part of the problem by lowering the niceness of the "plugin-container" Firefox process, as it seemed like the task scheduler wasn't giving enough attention to flash. The video's much smoother than before, but it is still a bit choppy. I'll try reinstalling Firefox and creating a new profile.

[[COLOR=#d40000]**lovinglinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=649167"), it's pretty much the same...

---

### Post by hatrox on 2012-04-06
I've finally figured out the source of my performance issues with flash: it's because I've set it to software video rendering/software video decoding, because of a hardware acceleration bug in Flash, explained [here]("https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091"), affecting Linux builds with binary NVidia drivers. Setting Flash to software video rendering/software video decoding basically degrades the video playing performance in YouTube and several other similar sites, but improves the stability of Flash.

---

