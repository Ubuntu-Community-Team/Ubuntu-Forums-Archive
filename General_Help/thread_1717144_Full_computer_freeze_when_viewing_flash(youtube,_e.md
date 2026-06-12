---
title: "Full computer freeze when viewing flash(youtube, etc) and downloading torrents"
date: 2011-03-29
forum: General Help
---

### Post by aenemic on 2011-03-29
Hi there!

I have tried to search through the forums here, but the answers I found didn't really help or the threads with somewhat similar issues had not been resolved and was usually quite old. So here I go then.

I have an ASUS 1201N, running Ubuntu 10.10 32bit,  I use the onboard ethernet card, I have deactivated wireless.I also have an external SAMSUNG HDD. 
I have tried both Chromium and Firefox. And at random points when viewing youtube or other flashrelated stuff my entire computer freezes. Meaning I can't move mouse or use keyboard and HDD locks. In other words I have to do a manual reboot. 
This can occur after watching a couple of clips or just into the first clip, it seems a bit random. I have had the system monitor up a couple of times, and it does not seem to be during any CPU peaks.

The same thing happends when I download torrents to my external USB HDD. I have read some similar issues regarding this, but I get no errors when running diagnostics. I have tried to follow the steps in this post: [http://ubuntuforums.org/showthread.php?t=1209389&page=2](http://ubuntuforums.org/showthread.php?t=1209389&page=2) but to no luck sadly. When downloading to my internal HDD I have yet to run into problems. But the same theme runs here aswell. It's all a bit random when it happends. I can easily download a full torrent one day, but the next day it freezes at say 10%.

I might also add that I am not an experienced Ubuntu user, this is my second time using the OS. The previous time was on my stationary a year and a half back. I experienced none of the issues at that time.

Would appreciate any help here!

-Chris

---

### Post by lovinglinux on 2011-03-29
See these:

[http://www.webgapps.org/flash/optimization](http://www.webgapps.org/flash/optimization)
[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)
[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

---

### Post by aenemic on 2011-03-29
Alright, thanks for that, I tried the alternative player, but the CPU went through the roof with it and played it extremely choppy, no matter the setting. I'm trying the tweak utility now to see if that helps.

Anyone have any tips on the downloading issue? I seem to remember my computer freezing when downloading something through chromeium aswell. And that was not to my external HDD.

---

### Post by aenemic on 2011-03-30
After using [http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid) youtube seems to work, not freezing so far atleast. But when I tried to view a viemo video my whole system became extremely choppy! It did not freeze but i still had to reboot because everything was like syrup.

Still no solution to the downloading problem either.

The CPU also spikes when viewing sites with flash content. Banners, etc.

---

### Post by Duncan Williams on 2011-03-30
A lot of problems have been experienced by recent versions of flash.
both linux and windows versions.
[http://my.opera.com/community/forums/search.dml?term=flash&id=](http://my.opera.com/community/forums/search.dml?term=flash&id=)

---

### Post by lovinglinux on 2011-03-30
> **aenemic said:**
> After using [http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid) youtube seems to work, not freezing so far atleast. But when I tried to view a viemo video my whole system became extremely choppy! It did not freeze but i still had to reboot because everything was like syrup.

Still no solution to the downloading problem either.

The CPU also spikes when viewing sites with flash content. Banners, etc.

The problem is that Vimeo is uncapable of using the GPU for flash processing,thus overloading the CPU. For instance, while YouTube uses 30% of both cores in my machine, Vimeo uses 70%.

Me FlashVideoReplacer extension support both sites. I don't why you are experiencing high cpu usage with it, because it replaces the flash player with another vido plugin like totem or gecko-mediaplayer, which uses a lot less CPU. For instance, on my machine gecko-mediaplayer uses 20% of both cores while watching the same YouTube video.

Try to remove totem-mozilla plugin, install gecko-mediaplayer and make sure gstreamer is set to use xv video output.

The first step:

```
sudo apt-get remove totem-mozilla
sudo apt-get install gecko-mediaplayer
```

Then launch gstreamer-properties, go to the video tab and select the option that has xv in the output menu.

---

### Post by aenemic on 2011-03-31
OK, so I tried that. I wouldnt play the videos at all embedded. Not even in standalone. So I changed output to vpdau in the standalone player. And it plays them fine. Is it possible to put the vpdau straight into gstreamer?

And still no suggestion on my downloading issues?

---

### Post by lovinglinux on 2011-03-31
> **aenemic said:**
> OK, so I tried that. I wouldnt play the videos at all embedded. Not even in standalone. So I changed output to vpdau in the standalone player. And it plays them fine. Is it possible to put the vpdau straight into gstreamer?

And still no suggestion on my downloading issues?

Oh, you have vdpau support. That's perfect.

About the download issue, could be a problem with your hard drive. Try to configure your client to do disk writes less often.

---

### Post by aenemic on 2011-03-31
When using transmissions, is there a way to configure this?

---

### Post by lovinglinux on 2011-03-31
> **aenemic said:**
> When using transmissions, is there a way to configure this?

Increase disk cache size.

---

### Post by aenemic on 2011-04-01
I downloaded Deluge torrent last night after Transmissions just kept freezing my system before I could access the settings. Deluge froze aswell before I tried to increase cache size. Now I have increased it, so I'm gonna test it for a while. When/if it freezes though, is there somewhere I can get the system logs to see if there is some sort of errorlog or crashreport?

---

### Post by aenemic on 2011-04-01
Did not work btw. Still freezes, increased disc cache to 4096

---

### Post by lovinglinux on 2011-04-01
> **aenemic said:**
> Did not work btw. Still freezes, increased disc cache to 4096

Try qBittorrent. Is an excellent client and uses less resources than Deluge.

---

### Post by aenemic on 2011-04-02
Doesnt matter which torrent program I use it seems. And my computer still freezes when playing flash. Even when I'm not playing and a youtube page is open it sometimes freezes.

---

### Post by aenemic on 2011-04-05
I'm not really sure whats causes the freezes anymore. I'm thinking it might got to do with download speed. Because now it started freezing while streaming through Sopcast, but only from a stream of over 1000kb/sec, the 800kb/sec stream is not freezing. I'm going to try to download files later on through a torrent client to see if it stops the freezes just by capping the download speed. Might this also be related to the flash issues?

Any ideas as to how to solve this problem? I mean, other than the obvious and capping the download.

---

### Post by lovinglinux on 2011-04-05
> **aenemic said:**
> I'm not really sure whats causes the freezes anymore. I'm thinking it might got to do with download speed. Because now it started freezing while streaming through Sopcast, but only from a stream of over 1000kb/sec, the 800kb/sec stream is not freezing. I'm going to try to download files later on through a torrent client to see if it stops the freezes just by capping the download speed. Might this also be related to the flash issues?

Any ideas as to how to solve this problem? I mean, other than the obvious and capping the download.

The streaming freeze is most likely to be related to flash.

Perhaps you should make some diagnostics on your hardware.

Also, try to replicate the conditions using a LiveCD. This could help determine if the problem is on your system settings.

---

### Post by aenemic on 2011-04-05
How can a stream that goes through VLC be flash related though? Sadly I don't have the LiveCD available now. I'll have to make another image and get a new USB-stick.

---

### Post by aenemic on 2011-04-05
After trying to cap download to 700 it still froze. So it does not seem like that is the issue after all. Would it be worth the try to upgrade to 11.04 Beta? I don't know. I'm just kind of grasping at straws here.

And is there a way to see some sort of crashlog?

---

### Post by lovinglinux on 2011-04-05
> **aenemic said:**
> After trying to cap download to 700 it still froze. So it does not seem like that is the issue after all. Would it be worth the try to upgrade to 11.04 Beta? I don't know. I'm just kind of grasping at straws here.

And is there a way to see some sort of crashlog?

You can start the browser from terminal to see error messages.

You could try to create a new Ubuntu user, just for testing. It could behave differently with clean user settings.

Ubuntu 11.04 is still Beta, so although it could solve your problem, it could create new ones.

---

### Post by aenemic on 2011-05-06
So, I have now tried OpenSUSE and Ubuntu 11.04 final. And the problem persisted in both. Downloading torrents (no matter the speed), youtube and videostreaming over 800kb causes complete computer freezes. I'm seriously considering installing Windows XP now. :(

---

