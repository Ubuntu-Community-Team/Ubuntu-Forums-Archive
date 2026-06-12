---
title: "No sound following Oneiric update on Samsung Chromebook"
date: 2011-12-31
forum: General Help
---

### Post by wormyrocks on 2011-12-31
Hey all,
New to Ubuntu and Linux in general, decided to put Ubuntu on my Chromebook.
I followed the steps listed [here]("http://www.devchronicles.com/2011/10/installing-ubuntu-on-samsung-series-5.html") to put Ubuntu 11.04 on my machine. Sound worked fine at that point. I then took the official update to Oneiric. Following getting myself situated with 11.10, I noticed there was no sound. Plugging in headphones worked fine, but the speakers themselves never emitted a peep.

If anyone could shed some light on what the problem might be and how to fix it I would be eternally grateful. If it helps, [here]('http://groups.google.com/group/chromebook-central/browse_thread/thread/bb655d09fe406696/ba5569b5371af043') are some posts by other people who have made the upgrade and run into the same or other problems. Thanks a million.

---

### Post by LinuxFan999 on 2011-12-31
Did the speakers work in 11.04?

---

### Post by wormyrocks on 2011-12-31
Yes.

---

### Post by lidex on 2011-12-31
Try purging your pulse config files. ```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by wormyrocks on 2012-01-01
No joy with those suggestions, thanks though.

ALSA output here: [http://www.alsa-project.org/db/?f=9ef276fe4b701573c399d89eab9e66fca067222e](http://www.alsa-project.org/db/?f=9ef276fe4b701573c399d89eab9e66fca067222e)

Thanks for your help, and happy new year!

Edit: Tried it again in the morning and those steps worked! Thanks so much!

Edit edit: Turns out when you put the computer to sleep, the sound disappears again. Darn. Well, it's a start, at least.

---

### Post by wormyrocks on 2012-01-01
Here are posts from other Chromebook owners describing their 11.10 issues, btw:

[http://groups.google.com/group/chromebook-central/browse_thread/thread/47d5e44a664fcf48/2a6812ab0e6e0e48](http://groups.google.com/group/chromebook-central/browse_thread/thread/47d5e44a664fcf48/2a6812ab0e6e0e48)
[http://groups.google.com/group/chromebook-central/browse_thread/thread/bb655d09fe406696/ba5569b5371af043?lnk=gst&q=11.10#ba5569b5371af043](http://groups.google.com/group/chromebook-central/browse_thread/thread/bb655d09fe406696/ba5569b5371af043?lnk=gst&q=11.10#ba5569b5371af043)

---

### Post by lidex on 2012-01-01
> **wormyrocks said:**
> No joy with those suggestions, thanks though.

ALSA output here: [http://www.alsa-project.org/db/?f=9ef276fe4b701573c399d89eab9e66fca067222e](http://www.alsa-project.org/db/?f=9ef276fe4b701573c399d89eab9e66fca067222e)

Thanks for your help, and happy new year!

Edit: Tried it again in the morning and those steps worked! Thanks so much!

Edit edit: Turns out when you put the computer to sleep, the sound disappears again. Darn. Well, it's a start, at least.
Sounds like you may need a bios update. When this occurs try reloading alsa:
```
sudo alsa force-reload
```

Your kernel is a little behind, have you tried a later one? My current version on 11.10 is 3.0.0-15

---

### Post by wormyrocks on 2012-01-02
Sorry... you lost me there; bit of a beginner here. Where would I go to update a kernel / BIOS? I have some understanding of what both are but don't know where I would need to go to modify them.
When does alsa need to be reloaded? After a BIOS update or just whenever the sound stops working?

---

### Post by lidex on 2012-01-02
To update your kernel, use a terminal:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
**Reboot**

> When does alsa need to be reloaded?
When it stops working.

Check your vendor's website for bios update - may or may not be available.

---

### Post by wormyrocks on 2012-01-02
Figured out how to fix it: I copied the alsa.conf file from Chrome OS into Ubuntu. Works perfectly so far, even after putting the computer to sleep. Thanks for all your help.

---

### Post by lidex on 2012-01-03
> **wormyrocks said:**
> Figured out how to fix it: I copied the alsa.conf file from Chrome OS into Ubuntu. Works perfectly so far, even after putting the computer to sleep. Thanks for all your help.

Nice work. Would you mind posting that file, I'd be interested to see it? Please mark the thread solved using 'thread tools' near the top.

---

### Post by wormyrocks on 2012-01-03
Here it is (renamed to alsa.txt)

---

### Post by tenletters on 2012-02-07
Hi there, I am encountering a similar issue, and I'm completely new to most / all of this. How do I go about finding the alsa.conf file in Chrome OS, so as to copy it onto Ubuntu? I assume I'd do well to have a USB drive for the task? And where do I then copy it to, exactly, within Ubuntu? Thanks for any help :)

---

### Post by wormyrocks on 2012-02-07
-Download alsa.txt from my previous post to the Ubuntu partition on your Chromebook
-Rename it to alsa.conf
-Copy it to /usr/share/alsa/alsa.conf.

---

### Post by tenletters on 2012-02-08
Is copying the new alsa.conf file to /usr/share/alsa/alsa.conf something that can be done via GUI drag-and-drop, or only via command line?

There is already a read-only file in the /usr/share/alsa location named alsa.conf, and I am not seeing how to replace this. What (undoubtedly very simple step) am I missing?

---

### Post by wormyrocks on 2012-02-08
> **tenletters said:**
> Is copying the new alsa.conf file to /usr/share/alsa/alsa.conf something that can be done via GUI drag-and-drop, or only via command line?

There is already a read-only file in the /usr/share/alsa location named alsa.conf, and I am not seeing how to replace this. What (undoubtedly very simple step) am I missing?

Replace the file that is already there with the one in my post. You can do this either through the command line or with the GUI.

---

### Post by tenletters on 2012-02-09
As the file already in that location was read-only, I eventually (1) opened a terminal window from the dash (2) typed in, without quotes, "sudo gedit /usr/shared/alsa/alsa.conf", then, after an editable version of the file there had opened, pasted in the previously copied contents of your file (after having made and saved elsewhere a back-up copy of the file that had been there.) 

So now I've replaced the file that was there with the (much smaller) one downloaded from here. But there's no change in the sound situation. Did I need to further edit something within that file? I suspect I might after reading the notes within the code that say "You need to customise this section for your specific sound card(s) and then run `update-modules' command." (?)

---

### Post by wormyrocks on 2012-02-09
Not sure, sorry: I just figured this out with the help of one helpful individual and Google. I suggest you try some of the steps that he or she suggested earlier in the thread as I believe that what you did worked for me. Alternately ask someone who knows more about ALSA and Linux in general than me... sorry =/

---

### Post by WhatTheTech on 2013-01-18
I know this thread is a year old, but for what it's worth people are still having issues with this, especially on the new ARM Chromebook.

I have written up a step-by-step guide, specifically directed at those who don't know what their doing in alsameter: [[COLOR="MediumTurquoise"]GUIDE[/COLOR]]("http://www.whatthetech.info/fixing-sound-chromebook-chrubuntu/")

Hope it helps someone!

---

