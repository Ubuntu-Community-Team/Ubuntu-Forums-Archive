---
title: "Comupter crash after trying to install Natty Narwhal Beta"
date: 2011-04-25
forum: General Help
---

### Post by lucr on 2011-04-25
I was going to install the Beta for Ubuntu 11.04 using the command update-manager -d. Everything went fine accept the fact that I had maybe two other programs running the same time as the update wich made my computer performance get really high wich ended in overheating and that my computer (using a laptop, of course) shut off. When I started my laptop again it will not go any further than the Ubuntu start screen saying something like "The device / cannot be found or is not ready yet". Now to the questition:

Can I all my files although I haven't done any backup? Any help out there?

---

### Post by sikander3786 on 2011-04-25
Welcome to the forums :-)

Repairing your install from here will be difficult although not impossible so you've taken the correct decision to recover your files and re-install.

Start up your laptop using a Live CD/USB and mount your partition simply by clicking it under the Places menu. Then you can copy your data to a safe location e.g, USB drive.

If your /home directory was encrypted, it may need some more steps. Let us know then.

For Live USB,

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

---

### Post by lucr on 2011-04-25
Thanks for your help.

When I boot the Live-USB I created I choosed "Try Ubuntu" because I thaught it was the best right now. Is this right or should I go another way?

When I am using the "Try Ubuntu" I can see my homefolder and filesystem but has no acsess to them because I have no permission to use or check the file. My guess is that it is encrypted. Any help?

---

### Post by sikander3786 on 2011-04-25
> **lucr said:**
> Thanks for your help.

When I boot the Live-USB I created I choosed "Try Ubuntu" because I thaught it was the best right now. Is this right or should I go another way?

When I am using the "Try Ubuntu" I can see my homefolder and filesystem but has no acsess to them because I have no permission to use or check the file. My guess is that it is encrypted. Any help?
Yes you need to use the "Try Ubuntu" option.

Then go to Applications > Accessories > Terminal and type

```
gksudo nautilus
```

Navigate to your home folder and see if the permission problem is gone.

---

### Post by lucr on 2011-04-26
It worked! But I can not copy them to an external memory. I have to open them av use save as to manage to get them. Any ideas?

---

### Post by sikander3786 on 2011-04-26
> **lucr said:**
> It worked! But I can not copy them to an external memory. I have to open them av use save as to manage to get them. Any ideas?
I couldn't actually understand what is happening there. Can't you simply copy/paste those files to the external one?

---

### Post by lucr on 2011-04-27
Sorry, my bad.

I can't copy/paste to the external one. It only shows the following message:
 > The file "xxxxxxxxx" cannot be handled because you do not have permissions to read it

So I figured out I could open the files in, for exampel, Open Office and then use the option "Save as..." to save the files anywhere else then the home folder I'm trying to get the files from. When the files is on the desktop (after I used "Save as..") I can copy/paste them with no problem.

---

