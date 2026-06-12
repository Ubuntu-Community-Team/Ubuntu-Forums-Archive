---
title: "Video on skype + 11.10 not working"
date: 2011-10-16
forum: General Help
---

### Post by orsula on 2011-10-16
Hi All,
I had skype working with my Logitech Webcam perfectly on 11.04. After upgrade to 11.10, skype (2.2.0.35) starts up fine w/out errors, even seems to detect the webcam but I can't test it (black screen) and it doesn't work when placing calls. Audio calls work fine with I tried using metacity instead of compiz but no go.
details: (snip)
```
user@laptop:~$ lsusb 
Bus 005 Device 002: ID 046d:08dd Logitech, Inc. QuickCam for notebooks

```
and
```
 user@laptop:~$ lsmod | grep videodev
videodev               85626  1 gspca_main

```
couldn't find anything in the forums. Is anybody having similar issues? Can anyone suggest or point to a link?
Tnx very much

---

### Post by a99675 on 2011-10-17
Dear orsula, 

I had the same problem in ubuntu 11.04 and now in ubuntu 11.10, too. Fortunately, the fix I used in 11.04 also works for 11.10. It is described in [http://ubuntuforums.org/showthread.php?t=1759012](http://ubuntuforums.org/showthread.php?t=1759012) However, it seems that the location of the libv4l has changed, I found it in /usr/lib/i386-linux-gnu/. So you have to change the path accordingly. 

It worked for me, hope it works for you, too.

---

### Post by orsula on 2011-10-17
Thank you!
However when I try the new location, I get
```
user@laptop:~$ sudo echo -e "#!/bin/bash \nLD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype.original" > /usr/bin/skype
bash: !/bin/bash: event not found
```

Following your thread I also tried without the ! and with sudo -s:
```
sudo -s echo -e "#/bin/bash \nLD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype.original" > /usr/bin/skype
bash: /usr/bin/skype: Permission denied
```

How did you get around this? I don't get a chance to put my password before the 'denied' message.

---

### Post by a99675 on 2011-10-18
Dear orsula, 

Here is how I did it:

1.) Rename the skype binary, create an empty file for the shell script, and open the empty file with an editor with root permissions:
```

sudo mv /usr/bin/skype /usr/bin/skype-original
sudo touch /usr/bin/skype
gksudo gedit  /usr/bin/skype

```2.) Then copy the following in the empty file:
```

#!/bin/bash 
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype.original

```3.) Make the file executable:
```

sudo chmod +x /usr/bin/skype

```I hope that helps.

---

### Post by orsula on 2011-10-20
a99675 - you are beyond your 'First Cup of Ubuntu'
Thanks! worked like magic.

---

### Post by goreyduke on 2011-10-20
Hello, I have the same problem with my Logitech webcam, having upgraded to Ocelot. But I've never been able to get it work. Yet, strangely, when I first tested the webcam in Ocelot, the camera came on perfectly, but with no sound. When I tried to correct the sound, the vision went. Weird, huh? I've tried the work around here - [http://ubuntuforums.org/showthread.php?t=1862530&highlight=logitech+webcam](http://ubuntuforums.org/showthread.php?t=1862530&highlight=logitech+webcam) - but don't know how a text editor can call up a new app. Do the last commands have to go in  a terminal? Thanks

---

### Post by orsula on 2011-10-21
Actually the solution you have tried has been there for while now

[http://ubuntuforums.org/showpost.php?p=6115686&postcount=30]("http://ubuntuforums.org/showpost.php?p=6115686&postcount=30")

only to have the path change slightly with the 11.10 distribution.
The file you are changing in an editor is executable. That's why a99675 has step (3) with chmod +x. Once all is ready, you simply type 'skype' in the terminal and it should fire up ready to go. It should also work from a generic skype link you might have on the launcher.

---

### Post by jalmado on 2011-11-01
I found this way to make the webcam work in ubuntu 11.10 with skype:

First, follow this tutorial by Frannoe (in Spanish) to be able to create a launcher in the desktop:

[http://ubuntu-cosillas.blogspot.com/2011/10/crear-lanzadores-de-escritorio-en.html](http://ubuntu-cosillas.blogspot.com/2011/10/crear-lanzadores-de-escritorio-en.html)

Second, add this line in the "command" of the launcher:

bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

That's all! Video should work now!

---

### Post by cmfrtblynmb on 2011-11-05
HEllo

IS there a solution for 64bit versions too?

When I try to use 64 bit version of  libv4l, it does not work. In the past we used to install lib32 version of libv4l, but this package does not exist anymore

---

### Post by plucky on 2011-11-05
> **cmfrtblynmb said:**
> HEllo

IS there a solution for 64bit versions too?

When I try to use 64 bit version of  libv4l, it does not work. In the past we used to install lib32 version of libv4l, but this package does not exist anymore

Have you tried looking for the files?

```
~$ locate v4l2convert.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so

~$ locate v4l1compat.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so
```

Good Luck

---

### Post by sdowney717 on 2011-11-05
Since this has been a known problem and known solution for Ubuntu generations, why is this not already dealt with?
Is it a skype packaging issue or what? 
Cause really nun can use skype unless they do this. And who is going to read the esoteric funky message boards for geeky solution, if you want mass adoption, then this stuff has to work from the get go, or people will think it is hopelessly foo-bared and use windows or apple.

---

### Post by pyrforos on 2011-11-06
> **jalmado said:**
> I found this way to make the webcam work in ubuntu 11.10 with skype:

First, follow this tutorial by Frannoe (in Spanish) to be able to create a launcher in the desktop:

[http://ubuntu-cosillas.blogspot.com/2011/10/crear-lanzadores-de-escritorio-en.html](http://ubuntu-cosillas.blogspot.com/2011/10/crear-lanzadores-de-escritorio-en.html)

Second, add this line in the "command" of the launcher:

bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

That's all! Video should work now!

worked like a charm!!!:guitar:

---

