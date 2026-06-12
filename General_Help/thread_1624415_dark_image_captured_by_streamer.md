---
title: "dark image captured by streamer"
date: 2010-11-17
forum: General Help
---

### Post by tmetzcc325 on 2010-11-17
I am trying to use streamer to set up a cron job to take a picture with my webcam once/minute.  The image that it is capturing is too dark - does anyone know a way to lighten it?  I am capturing the image as JPEG.

---

### Post by r+9 on 2011-04-02
I'm getting a black image, but I notice my webcam starts out dark when it begins recording.  I'm guessing that I need to find a way to tell stream to let the image warm up a little...

I'm thinking of just doing a 1sec video capture and converting it to a jpeg (somehow..)

---

### Post by r+9 on 2011-04-02
Tag=`date +'%y%m%d_%H%M%S'`
streamer -c /dev/video0 -t 00:00:01 -b32 -o timelapse$Tag_00.jpeg
rm *_0?\.jpeg

I figured a way to "make it work" it's not pretty, but it... works!
Since i'm using the "_00" part I had to make the Tag part to make unique images, but it's just a long timestamp.

So you'll notice I added the -t 00:00:01
that takes about one second of "pictures" all of them are dark until about *07.jpeg and 10 is usually the best (for me)

That last one deletes the bad ones, and I'm left with one good one.

Hope that helps,  I'm going to use something like this to show my 3yo how plants grow with stop-motion etc...

---

### Post by no2498 on 2011-04-02
you can use v4l2ucp to set the cam  with
after its installed it comes up in system preferences as video4linux control panel

---

