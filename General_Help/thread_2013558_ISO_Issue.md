---
title: "ISO Issue"
date: 2012-07-01
forum: General Help
---

### Post by fortheloveof on 2012-07-01
I have downloaded Ubuntu 12.04 twice the proper way, and the ISO both times comes back as "unmountable". I would like to upgrade my main desktop.

Is there a torrent of the 32 bit version of Ubuntu12.04?

---

### Post by spikoley on 2012-07-01
It sounds like you might be trying to mount the ISO instead of burning a CD or creating a USB install.  

The first thing you want to do is check the MD5SUM.  Open the terminal and cd to the directory you downloaded the ISO to.  Then run:

```
md5sum ubuntu<hit the tab key to auto complete>
```

It will take a little while to run.  Then compare the result with the [proper MD5SUM for your download]("https://help.ubuntu.com/community/UbuntuHashes/").

If the numbers match, you can burn a CD or create a USB install.  I prefer the USB install because I am a recycling freak.  For the USB install find Startup Disk Creator.  To burn a CD right click on the file.

---

### Post by fortheloveof on 2012-07-01
d791352694374f1c478779f7f4447a3f
d791352694374f1c478779f7f4447a3f

You sir rock! And thank you so much for the very quick response!

Odd how the ISO doesn't mount but thanks all the same! I wanted to mount to see if it was good as I only have 2 blank CDs left and wasting one for a bad ISO or should a burn error happen... well you get the picture. Again thank you so much!

---

### Post by spikoley on 2012-07-01
Get a 2GB USB thumb drive for future installs.

Make sure you mark this thread as solved.  Go to Thread Tools and mark as Solved.

---

