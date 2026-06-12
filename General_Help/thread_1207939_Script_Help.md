---
title: "Script Help"
date: 2009-07-08
forum: General Help
---

### Post by rbishop on 2009-07-08
Let me begin by saying that I am a noob and this is my first jump into trying to write a script.  I am trying to right a script that will delete files that are older than 20 minutes.  I have a "Netcam" that takes a picture every minute and uploads it to my server.  Once on my server I can then look at the picture from a web page, keeping an eye on the dog.

Every where i have looked I am finding scripts for days+ and no real idea of how to set it up for minutes rather than days, like this.

```
find ./ -type f -mtime +30 -exec rm -- {} \; 
```Any help I could can get would be greatly appreciated.

---

### Post by chriskin on 2009-07-08
check this page

[B][http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/](http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/)

edit[/B] sorry i just saw that you said that you know about days - changing it to 0.x days wouldn't work eh? :$

---

### Post by jonobr on 2009-07-08
Stupid question/comment,

I setup a webcam before using a similar method and just got it to overwrite the upload picture.
That means at any one time I just had one picutre in my upload directory.

Also, to find in minutes you could try

```
find ~ -mmin -30
```

(30 mins)

To find only files and not files and directories

```
find ~ -type f -mmin -30
```

---

### Post by rbishop on 2009-07-08
Another dumb question.....Is there anyway to find only .jpg files?

---

### Post by jonobr on 2009-07-09
find ~ -type f -name *.jpg -mmin -30

---

### Post by whitethorn on 2009-07-09
This isn't what you asked but it might be interesting.  There's a program called motion, which will takes pics from your cam when something moves in the picture every couple minutes. It will also let you stream the video from your webcam to an apache server.

[http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/](http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/)

This is a howto with config files on how to set it up.

---

### Post by rbishop on 2009-07-09
Thanks for all the help guys.

---

