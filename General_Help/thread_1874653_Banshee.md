---
title: "Banshee"
date: 2011-11-03
forum: General Help
---

### Post by tommy2k10 on 2011-11-03
I don't know if this is in the right place, but here goes:

Despite what I do, check that mute is not on, everything else, I cannot get Banshee Music Player to play any songs!  VLC Player does, so it can't be my speakers!

---

### Post by ericesque on 2011-11-03
Have you installed the proper codecs?  My understanding is that VLC's codecs are built into the client-- whereas Banshee would require installation of the ubuntu-restricted-extras package to support MP3 (and other common audio formats) playback.

---

### Post by tommy2k10 on 2011-11-04
I've installed the Ubuntu restricted extras package

---

### Post by amjjawad on 2011-11-05
> **tommy2k10 said:**
> I don't know if this is in the right place, but here goes:

Despite what I do, check that mute is not on, everything else, I cannot get Banshee Music Player to play any songs!  VLC Player does, so it can't be my speakers!

Hi there,

Your OS please and what release is that?

---

### Post by llelectronics on 2011-11-05
Make sure that 
```
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
```
are installed.

---

### Post by tommy2k10 on 2011-11-07
Thankyou.

And it is Ubuntu 11.10.

---

### Post by tommy2k10 on 2011-11-07
> **llelectronics said:**
> Make sure that 
```
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
```are installed.

I've done that, but it says Command not found, for both!

---

### Post by BillyBoa on 2011-11-07
Maybe is better to install Synaptics from Software Center and afterwards install the two missing:
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

---

### Post by tommy2k10 on 2011-11-07
It still says it!

---

### Post by amjjawad on 2011-11-07
> **tommy2k10 said:**
> It still says it!

```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse -y
```

I'm not sure if that package will help you to run Banshee but in case you want to install any package, you need to put "sudo apt-get install" before the package name.

Also, please make sure to run this first:

```
sudo apt-get update
```

---

### Post by tommy2k10 on 2011-11-07
None of these commands make a difference!

---

### Post by philinux on 2011-11-07
> **tommy2k10 said:**
> None of these commands make a difference!

Type in banshee to run it from a terminal. See if there are any clues there.

---

### Post by amjjawad on 2011-11-07
> **tommy2k10 said:**
> None of these commands make a difference!

Your VLC works perfectly, right? with videos and sounds?

---

### Post by amjjawad on 2011-11-07
> **philinux said:**
> Type in banshee to run it from a terminal. See if there are any clues there.

+1

And please post the output here for us to review but please, make sure to wrap up the text with CODE tags:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---

### Post by tommy2k10 on 2011-11-08
> **philinux said:**
> Type in banshee to run it from a terminal. See if there are any clues there.

This is what banshee says when run from a Terminal:

```

** (Banshee:2643): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:2643): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:2643): DEBUG: Loading the real store page

** (Banshee:2643): WARNING **: Got less number of items in credentials hash table than expected!
[Error 09:00:48.003] GStreamer resource error: NotFound
[Error 09:00:48.562] GStreamer resource error: NotFound
[Error 09:00:48.920] GStreamer resource error: NotFound
[Error 09:00:49.292] GStreamer resource error: NotFound
[Error 09:00:49.657] GStreamer resource error: NotFound
tom@tom-M61PM-S2:~$ 

```

Ubuntu says the GStreamer plugins you asked me to install are there!

---

### Post by tommy2k10 on 2011-11-08
> **amjjawad said:**
> Your VLC works perfectly, right? with videos and sounds?

Yes it does.

---

### Post by tommy2k10 on 2011-11-08
If I execute banshee in the Terminal from root I get:

```

(Banshee:2772): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
[Warn  09:05:51.381] Could no read GConf key library.write_metadata - GLib.GException: No D-BUS daemon running
 (in `gconf-sharp')
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Banshee.GnomeBackend.GConfConfigurationClient.TryGet[Boolean] (System.String namespace, System.String key, System.Boolean& result) [0x00000] in <filename unknown>:0 

```

---

### Post by amjjawad on 2011-11-08
Perhaps you need this?
```
gstreamer-tools
```

I'll give it a try here and let you know. I never use Banshee but will try to help you!

---

### Post by amjjawad on 2011-11-08
It doesn't work here too :/

---

### Post by tommy2k10 on 2011-11-09
Thankyou for trying!
I did 'sudo apt-get install gstreamer0.10 and installed one new package!
However, this still didn't work!

I have downloaded RhythmBox but all my music is in Banshee!  How do I transfer easily?

---

### Post by amjjawad on 2011-11-09
> **tommy2k10 said:**
> Thankyou for trying!
I did 'sudo apt-get install gstreamer0.10 and installed one new package!
However, this still didn't work!

You welcome!
I suggest to use something else that works. I know this is not a solution and I hate to offer this as one but I'm out of ideas. I never used it before.

> I have downloaded RhythmBox but all my music is in Banshee!  How do I transfer easily?
Your Music stored on your HDD, right? you can import them or open them with RhythmBox?

---

