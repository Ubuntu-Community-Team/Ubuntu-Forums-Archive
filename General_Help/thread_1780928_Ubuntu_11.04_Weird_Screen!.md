---
title: "Ubuntu 11.04 Weird Screen!"
date: 2011-06-12
forum: General Help
---

### Post by cgintan on 2011-06-12
I just reinstalled Ubuntu 11.04 so I can get the USB drives working again which fixed it, but now there are like disappearing windows and white lines on everywhere. When I click something it doesnt show until like I like highlight it and then it goes away again. I can show you a picture if you like.

---

### Post by sikander3786 on 2011-06-12
Yeah a screenshot would be helpful.

And also, press the <Super> key to open up Dash and search for Terminal and open it. Post the output of these commands then.

```
lshw -c video
/usr/lib/nux/unity_support_test -p
```

---

### Post by cgintan on 2011-06-12
Well I'll use the camera since I cant see any windows. I can't see the Terminal but I'll try my best to get it.

---

### Post by cgintan on 2011-06-12
Its impossible to see anything.

---

### Post by sikander3786 on 2011-06-12
You can press Ctrl + Alt + T to see the Terminal or if that doesn't work either, right click you desktop > Create Launcher... > Name=Terminal, Command=gnome-terminal

Double click the newly created Launcher to get to the Terminal.

---

### Post by cgintan on 2011-06-12
Ok. I recored 2 videos. One with the results and one with a screenshots. You can pause them. Where should I upload them?

---

### Post by sikander3786 on 2011-06-12
Why videos? You can just copy&paste the text in your post.

And you can just post a screenshot. That too, in your post here.

---

### Post by cgintan on 2011-06-12
No internet in my Ubuntu since I have wireless adapter. Linksys WUSB600N v2. Once i get the screen working I'll try to install the missing firmware. Plus I used videos since nothing clearly would come up. Fades away and stuff in like seconds.

---

### Post by sikander3786 on 2011-06-12
You can try using YouTube in that case.

---

### Post by cgintan on 2011-06-12
Started uploading onto ImageShack

---

### Post by cgintan on 2011-06-12
[http://imageshack.us/clip/my-videos/31/ns7.mp4/](http://imageshack.us/clip/my-videos/31/ns7.mp4/)
[http://imageshack.us/clip/my-videos/828/u4e.mp4/](http://imageshack.us/clip/my-videos/828/u4e.mp4/)

---

### Post by sikander3786 on 2011-06-12
Ok seen those. Sounds like wrong graphics driver was installed.

On your desktop, press Ctrl + Alt + F1 and login to the tty1 using your credentials. You'll not see any feedback on the screen when you type your password. Just type blindly and hit Enter.

Now, we need to say what this command says. I couldn't find this one in the videos.

```
lshw -c video
```

Or you can post a screenshot of the output as well. It shouldn't be that difficult this time and the screen shouldn't blink/act weird in the tty.

---

### Post by cgintan on 2011-06-12
Whats tty? Do I login and press ALt + F1 and stuff?

---

### Post by cgintan on 2011-06-12
Ok. I got it. Here is what says. I typed it all so there might a typo.
> narendra@narendra-HP-blah blah blah username:~$ lshw -c video
WARNING: you should run this program as super-user.
   *-display
           description: VPS compatible controller
           product: 82865G Intregated Graphics Controller
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:0Z.0
           version: 02
           width: 32 bits
           clock: 33MHz
           capabilites: vga_controller bus_master cap_list rom
           configuration: driver=i915 latency=0
           resources: irg:16 memory:f0000000-f7ffffff memory:fc400000-fc47ffff ioport:24e0(size=8)

---

### Post by sikander3786 on 2011-06-12
If there are long outputs, you can post the screenshots as it would be difficult to type all that stuff.

From the output posted above, looks like there are no driver conflicts. Now just to make sure any culprit packages are not there, need to see the outputs of these as well:

```
dpkg -l | grep nvidia
cat /etc/X11/xorg.conf
```

---

