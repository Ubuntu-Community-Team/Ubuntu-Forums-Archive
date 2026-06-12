---
title: "Videos Come Out Distorted"
date: 2011-08-14
forum: General Help
---

### Post by Hosmion on 2011-08-14
Hello everyone!  Today I was in the mood to make some YouTube videos, so I decided to make a very simple one and tell people that use Ubuntu how to install Wine.  

When I went to view the video, it came out distorted and weird.  I put the video up on YouTube so you guys could see what's happening.  The link is at the bottom of this post.

I tried several different recording programs and they all came out with the same result.  I really don't know where to start to try and fix this.

Thanks so much for your help,
Hosmion

link: [http://www.youtube.com/watch?v=w0yRiz4aMzc]("http://www.youtube.com/watch?v=w0yRiz4aMzc")

---

### Post by Enigmapond on 2011-08-14
What are you using as a screencaster?

---

### Post by Hosmion on 2011-08-14
gtkRecordMyDesktop.

---

### Post by Enigmapond on 2011-08-14
I've had good luck with Kazam Screencaster. It will save to a MKV file with better quality or upload to Videobin if you so choose. You need to add the PPA so open terminal and do:

```
sudo add-apt-repository *ppa*:and471/*kazam*-daily-stable
sudo apt-get update && sudo apt-get install kazam
```

---

### Post by Hosmion on 2011-08-14
> **Enigmapond said:**
> I've had good luck with Kazam Screencaster. It will save to a MKV file with better quality or upload to Videobin if you so choose. You need to add the PPA so open terminal and do:

```
sudo add-apt-repository *ppa*:and471/*kazam*-daily-stable
sudo apt-get update && sudo apt-get install kazam
```

I got an error with "sudo apt-get install kazam"

```
lenni@lenni-Aspire-6930:~$ sudo apt-get install kazam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kazam

```

---

### Post by Hosmion on 2011-08-21
Anyone know how to help?

---

### Post by kensclark15 on 2011-08-21
Did you use ```
sudo apt-get update
```?

---

### Post by Hosmion on 2011-08-21
Oh my gosh I feel stupid >///<.

Thanks for the help!

---

