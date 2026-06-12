---
title: "Easy fix for gtk-RecordMyDesktop sound"
date: 2010-09-29
forum: General Help
---

### Post by raafaell on 2010-09-29
[B][SIZE="4"][LIST]
[*]Fixing the Gtk-RecordMyDesktop 'No Sound' issue.
[/LIST][/SIZE][/B]

Since I was breaking my head figuring out how to fix the "Sound Issue" with the gtk-RecordMyDesktop, I should share with you guys this easy workaround. 


[LIST=1]
[*]From here, you will install the 'PulseAudio Volume Control', so open you Terminal and let's get started.


[*]Once your Terminal is opened, do the following...

[*]```
sudo apt-get install pavucontrol
```

[*]Once it's installed.. you may close your Terminal.

[*]Now open your gtk-recordmydesktop, and click Advanced to open the configuration window.

[*]Once it's opened click on the '**Sound**' tab, and where it says **Device** change the value to: pulse, just like the screenshot below.
[/LIST]

Now you're done.. 

Note: If it doesn't work, you may have to turn up the 'Capture' option in your Sound Mixer.

Thanks

---

### Post by 3vi1 on 2010-10-02
Did not work for me in Kubuntu 10.10.  :(

The streams are all enabled, but the only audio that gtk-RecordMyDesktop gets is my microphone at a very faint, near-silent level.  The same mic and settings works fine when I'm playing games like L4D2 under Wine, and the input looks great in the PA volume control.

I get no application sounds in the output video at all, though they are all enabled in the mixer and play fine.

---

### Post by raafaell on 2010-10-02
> **3vi1 said:**
> Did not work for me in Kubuntu 10.10.  :(

The streams are all enabled, but the only audio that gtk-RecordMyDesktop gets is my microphone at a very faint, near-silent level.  The same mic and settings works fine when I'm playing games like L4D2 under Wine, and the input looks great in the PA volume control.

I get no application sounds in the output video at all, though they are all enabled in the mixer and play fine.

Try to change the hardware in the PulseAudio volume Control by going in the Sound & Video.

---

### Post by 3vi1 on 2010-10-03
> **raafaell said:**
> Try to change the hardware in the PulseAudio volume Control by going in the Sound & Video.

I don't follow...  The hardware in the PulseAudio volume Control is already correct; everything looks fine there.  Why would I want to change it and to what would I change it?

---

### Post by 3vi1 on 2010-10-03
Ohhh.... I get what you're saying now....  You mean to change the hardware in the recording stream....  [testing...]

---

### Post by raafaell on 2010-10-03
> **3vi1 said:**
> I don't follow...  The hardware in the PulseAudio volume Control is already correct; everything looks fine there.  Why would I want to change it and to what would I change it?

There's the **Recording** section, and then there's the **Output** and **Input** section, start recording with you gtk-recordmydesktop, and try to change the hardware that show in it. That fixed for me.

---

### Post by 3vi1 on 2010-10-03
I have it working now.  Thank you very much for your assistance!

There are several other problems that 10.10 users might run into that I'd like to add here to your informational post:

#1:  gtk-recordmydesktop is currently broken.  I ran into [bug 591995]("https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/591995"), and cannot get the program to start, even though it started fine in 10.04.

Workaround:  Use RecordItNow instead.  It calls the same recordmydesktop back-end.  Use the Configure|plugins|RecordMyDesktop options to set your sound to pulse as described above.

#2:  The libTheora in Maverick causes major degradation in recording performance.  This is [bug 578397]("https://bugs.launchpad.net/gtk-recordmydesktop/+bug/578397").  The problem is actually with the recordmydesktop package, which sets way too low of a bitrate.  The new libTheora will cut the framerate back to fit the bitrate, no matter how high you set the FPS.

I originally attempted to fix this by compiling a new version of recordmydesktop that used sane defaults (as provided by one of the Fedora devs).  But, even with the new version, I found that it still performed poorly.

Workaround:  Add the karmic repos to your apt sources, force the version of libtheora0 down to the karmic version, then lock it to that version.

Also, you will need to increase the bitrate setting in the RecordItNow options to a sane level, or you'll end up creating videos where VLC won't play them (or will only play a few seconds of audio) and Dragon player will play the video at a horrible FPS and have no audio.

---

