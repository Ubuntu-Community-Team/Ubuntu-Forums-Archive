---
title: "Good Program For Streaming Webcam"
date: 2011-12-08
forum: General Help
---

### Post by onaridge on 2011-12-08
I am looking for a good program to stream my laptop webcam. I am using Broadcam on my Windows7 side of my double boot but I HATE windows and would like to use it on Maverick Meerkat. What's a recommended one that is simple and easy to use.

---

### Post by wolfen69 on 2011-12-08
What do you mean by stream? What are you going to be using your cam for?

---

### Post by lechien73 on 2011-12-08
I've just used VLC for webcam streaming. There are plenty of tutorials online, but I just go to Media -> Streaming. Then select the Capture Device tab, and type the device name of my webcam.

I usually set the output video profile to WMV format so that Windows Media Player can open it.

---

### Post by onaridge on 2011-12-08
My camera doesn't have a name, it's the webcam in my laptop. I am using it for keeping an eye on my fish tank. I have several thousand dollars sunk into it so when I am away I like to see that everything is ok. Eventually I will buy an IP webcam and then I think this will all be easy. But until then, my device doesn't have a name and I am curious why it doesn't work when I access it via a browser....or maybe that's just a cell phone thing. I put the IP of my laptop in, maybe that's the problem? Not sure what the address of the webcam is.

---

### Post by Derek Karpinski on 2011-12-08
Your camera does have a name. If your cam is working, and plugged in, it is assigned a /dev/video. So, in termnial, type:
 
```
cd /dev
ls video*
```
 
```
cat /dev/video0 > ~/Desktop/test.mpg
```
(you may need to 'sudo' the above command)
 
replacing '0' with any of the numbers you found in in the ls video*
 
Let it 'record' for a few seconds, then 'ctrl-c' to stop. Check the file test.mpg on your desktop. If it didn't record anything, try another number (/dev/video1).

---

