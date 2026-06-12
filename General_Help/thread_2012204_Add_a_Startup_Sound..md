---
title: "Add a Startup Sound."
date: 2012-06-28
forum: General Help
---

### Post by UAdnan on 2012-06-28
Hello,

So at first it was Ubuntu 12.04 that I had, then after finding out that Xubuntu is lighter than Unity on my low-end computer, and after testing too many desktop environments and keeping on that one, I am having many problem of somehow a "conflict" between the installed desktop environments.
Whatsoever.

Remember the old Ubuntu 4.10 startup sound ? I don't, actually I just discovered it a while ago. ( [http://www.youtube.com/watch?v=3WFCQrCReGU](http://www.youtube.com/watch?v=3WFCQrCReGU) )
So as I was impressed by that, I decided I'd enjoy having it on my Xubuntu, or Ubuntu with the Xubuntu desktop environment.

I have installed the Startup Sound as an .mp3 file, but then found out that it should be an .ogg file.
But the videos showed that I should get to a folder under /usr/share/sounds/ubuntu/stereo and paste the file there and then modify something in Startup applications. But then I figured out that's for Gnome, so I didn't waste any time trying to do that, and actually none of the .ogg files there are being played, so I guess that folder isn't being used by Xubuntu, or something like that.

I also tried just to add the .mp3 file under Startup programs, but that doesn't seem to work.

Thus, my question is, how do I add a Startup sound to Xubuntu ?

Thanks in advance,
UAdnan.

---

### Post by LewisTM on 2012-06-29
First install **sox**
Add a startup application with command:
```
play <full path to your mp3/ogg/wav>
```

That's it!

---

### Post by SparTacux on 2012-06-29
I didn't know you could change the startup sound in Ubuntu  A good old TARZAN call is perfect  Ahhhhhhhaahhhhhhahhhhhhhhha ahhhhh ahhhhhhhhhhhhhhhhhhh !  Me must play around with the idea :-)

---

### Post by UAdnan on 2012-06-30
I'm afraid that didn't work. 
sudo apt-get install sox

Then I went to add a startup application, i wrote the following:
play /home/adnan/startup.mp3 ...

The file is called so and located there... ?

Oh and I figured out after modifying some errors in my computer that the sound called system-ready.ogg is being played when I get my login screen, just as it was with unity actually. However it's not a startup application so I don't know how they get to do it.

EDIT: I got to solve it myself;
But if you use Unity that won't work because if you get any pop-up message or error it will play the startup sound, if you use another desktop distro while you still have unity, and its startup sound being played (It's like some drums when you get to your login screen), AND that you don't get that sound anywhere after, you can do the following:

Go to Terminal. Type sudo -s nautilus. 
Now go to filesystem and browse to this folder  /usr/share/sounds/ubuntu/stereo , enter it.
Now you see some .ogg sound files, so well first you should convert your file if it was an MP3 to OGG, you can use the sound converter in any software center.
now copy your file to that destination (copy/paste  didn't work for me, but drag and drop did the trick).

Delete the dialog-information.ogg file. And then rename your file to that name (If your file was called Startup.ogg for example, rename it to dialog-information.ogg )

Last but not least, delete the system-ready.ogg file, make a link to your newly made dialog-information.ogg, and rename that link to system-ready.ogg .

Hope that helps !

---

### Post by LewisTM on 2012-06-30
You were probably missing the mp3 library
```
sudo apt-get install libsox-fmt-mp3
```

---

### Post by UAdnan on 2012-06-30
Uhm well if I use this method, will the sound get played when I get to the login and that it loads aswell or after I write my logins OR inbetween the boot screen and the login screen ?

---

### Post by LewisTM on 2012-06-30
> **UAdnan said:**
> Uhm well if I use this method, will the sound get played when I get to the login and that it loads aswell or after I write my logins OR inbetween the boot screen and the login screen ?
It will be played after login, along with other startup apps.

---

