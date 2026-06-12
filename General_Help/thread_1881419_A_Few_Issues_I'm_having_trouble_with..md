---
title: "A Few Issues I'm having trouble with."
date: 2011-11-15
forum: General Help
---

### Post by LandR on 2011-11-15
Hi, 

I upgraded to the latest version of Ubuntu and I'm having a few problems.

1) Banshee crashes on startup if I double click on an audio file. It opens the mp3 and starts playing it but the entire UI of Banshee is then unresponsive. My CPU usage also goes to 100% while it's playing an mp3. I also can't close it and have to kill it from the terminal. I'm having to open mp3s with Movie Player which isn't convenient.

2) I'd like my Home Folder to have maybe a right click menu for quick access to Downloads / Videos / Pictures folders. Is this possible ?  I hate the dash.

3) I went into CompizConfig and enabled the Unity Plugin. I selected "Never" for the option on when to hide the launcher. It still hides the launcher, even after a restart. I hate the launcher. I keep accidentally activating it when going for a File Menu or Back Button on my browser.

4) I use GTKPod to manage an ipod. It isn't putting a menu into the global menu bar. This means I can't close it since it starts maximised. I hate the global menu bar.

5) Emesene won't connect to MSN. I fixed this problem by downloading some files and overwriting other files but I can't remember where I got those files and after running an update today it's broken again. It was fine before ( I was using it) I installed the updates and now it won't connect again. If I manage to remember what I download how do I stop automatic updates from screwing it again ?

6) I can't rearrange the order of anything in the launcher. I try to click the icon and drag it right to snap it out of the launcher but it doesn't let me.

After a little bit of playing I've found Banshee will use 100% and become unresponsive even if I just open it, not even playing an mp3 file.


Please help if you can :) These little niggles are making Unity quite a frustrating experience.

---

### Post by LandR on 2011-11-15
Fixed MSN. Here's what I did.

I downloaded 0.5.6 from here - [http://www.freedesktop.org/software/papyon/releases/](http://www.freedesktop.org/software/papyon/releases/)

I extracted it and copied the papyon folder to /usr/lib/python2.7/dist-packages.


sudo cp -r papyon /usr/lib/python2.7/dist-packages

Emesene now connects to MSN. Although I have no idea what that folder does or why mines doesn't / didn't work.

---

### Post by BHEJU on 2011-11-15
For #3
If you have a program window in a place where it can overlap the launcher bar. It will hide.
Soon as you move the window, the unity bar will be restored and will not hide.. at least until you have another/same program window overlapping the launcher bar.

Cheers

---

### Post by LandR on 2011-11-15
Ah!

That's not what I want. I was hoping to have the launcher on the screen at all times and any maximised window would align along its edge.

is this not possible ?

I really don't like it going away and coming back if I accidentally move the mouse to the left. Sometimes it comes up and doesn't go away without a log-out. This means that I can't access parts of an application it is over.

---

### Post by LandR on 2011-11-15
OK CompizConfig is being ignored because I'm using Unity 2d. Didn't realise it was only Unity 3d.

I installed 2d-Desktop Settings and it has an option to always show the launcher.

Also found how to re-arrange launcher icons. YOu have to click and hold the button down for a couple of seconds, you can then move it up or down the list. I didn't realise they had changed it, I thought you dragged them out and back in.

---

