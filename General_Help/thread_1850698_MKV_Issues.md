---
title: "MKV Issues"
date: 2011-09-27
forum: General Help
---

### Post by forza.stiinta on 2011-09-27
Is it me, or 11.4 causes a lot of trouble? Sometimes it freezes on system load, but now I am writing because of other problems.

I am using VLC on a 2mhz core2dow with 2GB of RAM. However, I cannot play mkvs properly - sound is not syncronised, and sometimes it just freezes. While playing, the CPU load is 'round 40% and the RAM memory 'round 50%. Still, I get these results.

In 10.10 this worked perfectly, and in win 7 the same (still works flawless under win7, on the same computer).

Any fix on this?
Thanks!

---

### Post by seawolf167 on 2011-09-27
I personally haven't had any issues; just curious, have you installed the restricted-extras package?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by forza.stiinta on 2011-09-28
No, I haven't installed the packages. I will and let you know.

---

### Post by papibe on 2011-09-28
Are you using video hardware acceleration for VLC (vaapi or libva1)?

Just to let you know that VAAPI over Nvidia's VDPAU (and maybe over Intel and AMD) is broken in 11.04. The only way I could fix it is using a ppa.

Just some thoughts,
Regards.

---

### Post by forza.stiinta on 2011-09-28
> **papibe said:**
>  The only way I could fix it is using a ppa.


Could you be more specific, please?

---

### Post by papibe on 2011-09-28
> **forza.stiinta said:**
> Could you be more specific, please?
If you have a relatively recent Nvidia card, you can reproduce HD video using hardware acceleration using two API's: VDPAU or VAAPI.

Using VDPAU has been so far the more stable and usable way to play HD in Linux. Among the players that support it: mplayer, SMplayer and XBMC.

VLC decided to support a more official and (a bit) high level APIs: VAAPI. Since they are more recent, they are not that well integrated and stable as VDPAU.

In order to add VAAPI support to VLC you have to install a new library (besides the proprietary driver):
```
$ sudo apt-get install vdpau-va-driver
```
And set VLC -> Tools -> Preferences -> Inputs & Codecs -> Use GPU acceleration.

I've read reports that this works flawlessly in 10.10. However, in 11.04 there were some problems. Here's a [bug]("https://bugs.launchpad.net/ubuntu/+source/libva/+bug/773466") report of the problem on Launchpad.

In that report users suggest a couple of ppa's to avoid the wait for the fix, so you can use either patched or newer version of the libraries.

I decided to used the one that updated 'less' things on my system: ed10vi86's ppa. Here's how (assuming you already installed vdpau-va-driver):

```
$ sudo apt-add-repository ppa:ed10vi86/video
$ sudo apt-get update
$ sudo apt-get upgrade
```
Note that I've tested this for an Nvidia card. I image that support for VAAPI using Intel or AMD cards should be similar.

I hope this helps,
Regards.

---

### Post by forza.stiinta on 2011-09-29
Hello!

I installed "vdpau-va-driver" and VLC did not even start. Then I added the ppa and updated and now it works. It is better than before, but still there is a little sound delay. At least now movies are "watchable". Thanks a lot for the advice.

I will probably revert to 10.10 as since installing 11.4 is causing only but problems.

---

### Post by papibe on 2011-09-29
Although it is working OK for me, I've read about that. Here's [thread]("http://ubuntuforums.org/showthread.php?t=1823062&highlight=vlc+delay") with a solution that's working for most people.

Hope that solve your problem,
Regards.

---

### Post by forza.stiinta on 2011-10-04
This  solved it. Thanks!

---

### Post by papibe on 2011-10-04
:) Good to know! Please mark the thread solved when you have the chance.
Regards.

---

