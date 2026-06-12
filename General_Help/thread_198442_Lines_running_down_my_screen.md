---
title: "Lines running down my screen"
date: 2006-06-17
forum: General Help
---

### Post by UbuntuniX on 2006-06-17
There are lines running down my screen,
on desktop, login, on applications, everywhere.

When I had the previous version of ubuntu installed I had this too.

My friend tried ubuntu a while back and was also complaining of this problem so I don't think it's just my computer.

I'm guessing it's to do with my graphics card,
so note I'm using a nvidia GeForce MX 440.

I've already tried screen resolution settings but to no avail.

Anyone know how to fix this problem?

-Thanks-

---

### Post by ashrack on 2006-06-17
Try to supply a screen shot. But if I understand U corectly the problem is easily solved by changing in 'xorg.conf'

```
	DefaultDepth     24
```
to
```
	DefaultDepth     16
```

Which sets your display adapter to 16bits

---

### Post by UbuntuniX on 2006-06-17
I've taken screenshots but they don't show up,
it appears completely normal...

Where do I find xorg.conf?

---

### Post by ashrack on 2006-06-17
sudo gedit /etc/X11/xorg.conf

---

### Post by UbuntuniX on 2006-06-17
Ok did that but still see the lines...

---

### Post by UbuntuniX on 2006-06-17
Nevermind I rebooted and it's gone :D

Thanks buddy :)

---

### Post by ashrack on 2006-06-18
forgot to write that U must also restart X server.
Glad to help U

---

### Post by H.E. Pennypacker on 2006-06-18
I have something similar, and I can't remember if the lines are horizontal or vertical.  The lines only appear when starting up.  Hmm..at other times, its perfectly fine.  The lines appear right after this screen:

[img]http://www.blugu.de/uploads/ubuntu_boot.png[/img]

Once that screen is done, the lines show up.  A moment later, the lines go away.  It's not only that there are lines, its that there are these dots somewhere near the top.

I'll see if this fix of yours will work for me too.

---

### Post by Lord Illidan on 2006-06-18
[quote=H.E. Pennypacker]I have something similar, and I can't remember if the lines are horizontal or vertical.  The lines only appear when starting up.  Hmm..at other times, its perfectly fine.  The lines appear right after this screen:

Once that screen is done, the lines show up.  A moment later, the lines go away.  It's not only that there are lines, its that there are these dots somewhere near the top.

I'll see if this fix of yours will work for me too.[/quote]

I had this problem. Probably you hadn't installed the drivers, and were using VESA?

As long as it goes away, it is not that important though.

---

### Post by H.E. Pennypacker on 2006-06-20
[QUOTE=Lord Illidan]I had this problem. Probably you hadn't installed the drivers, and were using VESA?

As long as it goes away, it is not that important though.[/QUOTE]

Install what drivers, and what do you mean I am using VESA?  I simply installed Ubuntu, and that shouldn't require any more installation when it comes to the video card.

Everything shows up perfectly fine when I am in Ubuntu, but the those lines at start up seem to indicate an issue.

---

### Post by WorLord on 2006-06-20
> Install what drivers

The drivers from nVidia for your video card.


> and what do you mean I am using VESA?

He's wondering if your Ubuntu system is using the "Vesa" video card driver instead of the drivers from nVidia.


> I simply installed Ubuntu, and that shouldn't require any more installation when it comes to the video card.

It does, and *will* - this won't change unless/until nVidia decides to release its drivers as open-source.  Otherwise, Ubuntu can't legally ship its distro with these proprietary drivers on the CD.


> Everything shows up perfectly fine when I am in Ubuntu, but the those lines at start up seem to indicate an issue.

They will probably go away when you install nVidia's drivers.

---

### Post by H.E. Pennypacker on 2006-06-21
WorLord, I said I have a similar problem, not the same video card.  I don't know the name of my video card, but its not nVidia.  I guess that's where there's a misunderstanding.

Here's what my problem looks like (I created an image in Gimp to represent what is wrong):

[[IMG]http://img209.imageshack.us/img209/5959/lines0nn.th.jpg[/IMG]](http://img209.imageshack.us/my.php?image=lines0nn.jpg)

Make note that the background color in the image is not the exact color as in the problem, and the lines are a bit too wide. Also, the lines should be vertical, not horizontal (the image's lines are horizontal, because I couldn't figure out how to do vertical lines in Gimp).  Moreover, are these weird dots scattered across the top left.

---

### Post by WorLord on 2006-06-21
H.E. Pennypacker: My bad, I thought you were the OP.  

I had a problem like this using the "nv" drivers, but since you're not using an nVidia card, that probably doesn't matter.  You should figure out what card you *are* using, though, and its probably a good idea to post the contents of your /etc/X11/xorg.conf file here.

---

### Post by H.E. Pennypacker on 2006-06-24
[QUOTE=WorLord]H.E. Pennypacker: My bad, I thought you were the OP.  

I had a problem like this using the "nv" drivers, but since you're not using an nVidia card, that probably doesn't matter.  You should figure out what card you *are* using, though, and its probably a good idea to post the contents of your /etc/X11/xorg.conf file here.[/QUOTE]

Unfortunately, I don't know the name of my video card, and I don't know how to find the answer in Ubuntu.  Sure, I could log into Windows and use PC Wizard or something else to figure out the name, but that would mean I wouldn't learn how to do it in Ubuntu.

I tried finding out using Device Manager, but it doesn't say something obvious like "Video card: Name."  That's the most logical thing to display, but there's nothing like that.

I then considered dmesg, but it shows too many lines, and nothing that says "Video card: Name."  Why isn't there something simple in Ubuntu that could list all of my hardware with a GUI?  It's bothersome to run to the terminal every minute or two.

---

