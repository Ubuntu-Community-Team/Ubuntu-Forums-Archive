---
title: "Why do my videos look horrible when I upload them?"
date: 2010-07-22
forum: General Help
---

### Post by TheNerdAL on 2010-07-22
I use GTK-RecordMyDesktop and when I upload to Youtube it looks horrible. 

[http://www.youtube.com/watch?v=6Ky-WW4-U6w](http://www.youtube.com/watch?v=6Ky-WW4-U6w)

See? 

What's the problem? :(

---

### Post by Hman242 on 2010-07-22
I was expecting just bad quality captures caused by low fps or having the quality bar being set low but wow. That wasn't what I expect at all. Are you using the default settings with it? See what your results are using other software such as Webcamstudio or Istanbul.

---

### Post by TheNerdAL on 2010-07-22
> **Hman242 said:**
> I was expecting just bad quality captures caused by low fps or having the quality bar being set low but wow. That wasn't what I expect at all. Are you using the default settings with it?

Yes.

---

### Post by Hman242 on 2010-07-22
I edited my post to give more information just as you posted. Give it a read if you don't mind...

---

### Post by TheNerdAL on 2010-07-22
> **Hman242 said:**
> I edited my post to give more information just as you posted. Give it a read if you don't mind...

When I play the video on my Ubuntu computer, it works fine but when I upload it, it doesn't. Maybe I should convert it to a .avi file?

---

### Post by Hman242 on 2010-07-22
Are you using any video editing software? What is the video's current format?

---

### Post by TheNerdAL on 2010-07-22
> **Hman242 said:**
> Are you using any video editing software? What is the video's current format?

.ogv and no.

---

### Post by WorMzy on 2010-07-22
Wow, youtube's compression rate is that bad these days, huh?

I think that you've saved the video in a format that Youtube can't handle (or at least can't handle *well*), I'd try saving it in a different format and uploading it again.

---

### Post by TheNerdAL on 2010-07-22
> **WorMzy said:**
> Wow, youtube's compression rate is that bad these days, huh?

I think that you've saved the video in a format that Youtube can't handle (or at least can't handle *well*), I'd try saving it in a different format and uploading it again.

How?

---

### Post by WorMzy on 2010-07-22
I've never used the program, but is there a "Save as" or "Export as" option under the File menu?

This link should help you pick a more suitable format: [http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=55744](http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=55744)

---

### Post by TheNerdAL on 2010-07-22
> **WorMzy said:**
> I've never used the program, but is there a "Save as" or "Export as" option under the File menu?

This link should help you pick a more suitable format: [http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=55744](http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=55744)

No there is not. :(

---

### Post by WorMzy on 2010-07-22
Then you may need to convert it using a different program. I don't do any video editing myself, but here's a list of free and open source applications you could check out: [http://en.wikipedia.org/wiki/List_of_free_and_open_source_software_packages#Video_editing](http://en.wikipedia.org/wiki/List_of_free_and_open_source_software_packages#Video_editing)

It doesn't help you now, but have a look in the options for the recorder you used, it (hopefully) has an option to save the recording in a different format; change it before you next use it so that you don't need to convert it again. If it doesn't have that option, then you'll probably need to convert it every time.

---

### Post by Hman242 on 2010-07-22
If it can't save in a different format, try importing the video as a clip with video editing software and exporting it in a Youtube friendly format.

---

### Post by rubylaser on 2010-07-22
Just try avidemux or  mencoder to convert the ogv to avi.  Youtube apparently doesn't support ogv very well  if at all.

This should work just fine.
[http://visibletrap.blogspot.com/2009/02/ogv-to-avi-with-mencoder.html]("http://visibletrap.blogspot.com/2009/02/ogv-to-avi-with-mencoder.html")

---

### Post by sandyd on 2010-07-22
convert the video to h.264 thru avidemux or winff

---

### Post by lovinglinux on 2010-07-22
That is known issue in Lucid. you need to convert it to another format like avi first. Mencoder will do the job well. Be aware that besides those video glitches, the final recording might have several additional extra minutes of recording after you stop recordmydesktop. So fully check the videos before uploading.

---

### Post by Excedio on 2010-07-22
WinFF is a great program for converting video to different formats.

---

### Post by Nick_Jinn on 2010-07-22
> **TheNerdAL said:**
> How?

I use a program called Devede, or sometimes handbrake.

---

### Post by TheNerdAL on 2010-07-22
> **carlee said:**
> convert the video to h.264 thru avidemux or winff

WinFF doesnt't do anything when I convert and Avidemux gives me an error. :(

---

### Post by lovinglinux on 2010-07-22
> **TheNerdAL said:**
> WinFF doesnt't do anything when I convert and Avidemux gives me an error. :(

Use mencoder. See [http://ubuntuforums.org/showpost.php?p=9406846&postcount=2](http://ubuntuforums.org/showpost.php?p=9406846&postcount=2)

---

### Post by TheNerdAL on 2010-07-22
> **lovinglinux said:**
> Use mencoder. See [http://ubuntuforums.org/showpost.php?p=9406846&postcount=2](http://ubuntuforums.org/showpost.php?p=9406846&postcount=2)

It gives me this: "Audio LAVC, couldn't find encoder for codec libfaac."

---

### Post by lovinglinux on 2010-07-22
> **TheNerdAL said:**
> It gives me this: "Audio LAVC, couldn't find encoder for codec libfaac."

Use this then:

 ```
mencoder source.ogv  -o output.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

---

### Post by no2498 on 2010-07-22
you pulled the video so ill ask was it from a webcam made with cheese if yes try this program wxcam

read and install all the page tells yo to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

hope this helps

---

### Post by TheNerdAL on 2010-07-22
> **lovinglinux said:**
> Use this then:

 ```
mencoder source.ogv  -o output.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

Thanks! :D

---

### Post by RJARRRPCGP on 2010-07-22
> **excedio said:**
> winff is a great program for converting video to different formats.

+1  

I finally figured it out and my videos are smooth. ;) 

I recommend that you set the FPS to 29.997.

---

