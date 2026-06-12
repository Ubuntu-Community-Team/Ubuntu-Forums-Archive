---
title: "DeVeDe problems"
date: 2011-01-22
forum: General Help
---

### Post by donextintor on 2011-01-22
why is it that only my computer and xbox 360 recognize the iso images that i burn to dvd. PS3 nor regular dvd nor blu ray players ever work when using these dics. I've read the guides on how to use dvd i think that i am doing it right but still it isnt working

---

### Post by ajgreeny on 2011-01-22
We need a lot more info about what you've done to be able to answer your question.

Devede has worked brilliantly for me to turn a 2.5 hr mp4 into a DVD disk that plays fine on both my computer and domestic DVD player.  I think, therefore you must be doing something wrong with your settings.

I assume you are burning the ISO as an image and not as a data disk.

---

### Post by davec64 on 2011-01-22
Just to follow up what ajgreeny is saying, when you burn the image to disk are you copying the iso file to a disk or burning the image? The easiest way to burn an image to disk is to right click the iso image (in Nautilus) and select **Write to disc**
:)

---

### Post by donextintor on 2011-01-28
i burn the iso image and put it in my stand alone dvd player it doesnt work....it works in the xbox 360 though

---

### Post by amsterdamharu on 2011-01-28
Did you let devede re encode the video files?

If not, how did you encode them to be DVD compatible video?

To see how the files are encoded you can check the output of
```
ffmpeg myfile.mpg
```

---

### Post by bikodog on 2011-01-28
Make sure that you are setting the correct format (PAL / NTSC) depending on the region of your dvd player.

Make sure that it is correct on both the Unsaved disc structure option (Default Format radio button) and on the File properties setting (Video Format radio button)

---

