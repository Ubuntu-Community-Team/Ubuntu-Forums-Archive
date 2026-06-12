---
title: "Gimp, Filezilla, Deluge and many more have bug display and important CPU usage!"
date: 2012-01-06
forum: General Help
---

### Post by siick on 2012-01-06
Hello everyone:D
First of all, sorry for my english.:( I try to do my best to explain my problem.
I'm using Ubuntu 11.10 x64 with the gnome-shell environment. I have a lot of weird display problem and CPU usage with some applications.
Gimp, Xchat, Deluge, Filezilla, Gthumb, conduit, grisbi. They all have the same kind of problem.
When i start one of those applications, suddenly my CPU usage go to 80/85% (normally it's 2 to 8%) and i can't use the application in a good way.
When i maximize the window of Filezilla for example, the windows is maximizing but inside no!
[[img]http://img4.hostingpics.net/thumbs/mini_991830Capturedu20111227083753.png[/img]](http://www.hostingpics.net/viewer.php?id=991830Capturedu20111227083753.png)

[[img]http://img4.hostingpics.net/thumbs/mini_366795Capturedu20111227083806.png[/img]](http://www.hostingpics.net/viewer.php?id=366795Capturedu20111227083806.png)
When i use deluge to download, i add the torrent, he's downloading but i can't see nothing. I have to close and re-open the window to refresh inside, and finally see the progression of my download! Weird! And when i close the window (without closing the program just the window) my CPU usage go down to mormal value, when i re-open CPU usage go back to 80/85%!

When i launch Gthumb CPU usage go to 80% and i can't close it without killing the process manually.

For Xchat, i can't see my contact.

Gimp is very weird too! i can't see any changes i do on my picture.... CPU usuge up to 80% too

I thought gnome was guilty, but it's the same with Unity. I beg for help. After 4 years of Ubuntu, it's the first time i'm totally lost with a problem.

A video could help you.
[http://youtu.be/kqDa6Esta2Q](http://youtu.be/kqDa6Esta2Q)

Thanks for the future help.

---

### Post by ajgreeny on 2012-01-06
This looks to me like a graphics driver problem.  You do not say what graphic card you have, nor give any machine specification, which might help solve your problem.

---

### Post by siick on 2012-01-07
That's true, shame on me.
Ubuntu 11.10 x64 Gnome-shell
Nvidia GeForce 8400 GS with Nvidia Driver (current version)[recommended]
[IMG]http://ubuntuone.com/6QNHMe9lgDOtd2Vv1gluB5[/IMG]
I'm not really sure of graphics problem due to driver. I'm using twinview for my 2 screens with this driver and all is ok.
Chromium, firefox, thunderbird, nautilus, terminal, gwibber are working well. Gnome environment is ok too. No glitches.

---

### Post by siick on 2012-01-11
No more idea? Please it's very very annoying for my everyday use...

---

### Post by siick on 2012-01-17
Up! No one else have these problems with only these applications?

---

### Post by siick on 2012-01-23
Please help !!
[IMG]http://g1.globo.com/platb/files/19/2011/06/Please_Help_Me-2dalwc1.jpg[/IMG]

---

### Post by siick on 2012-02-02
T_t

---

### Post by sudodus on 2012-02-02
> **ajgreeny said:**
> This looks to me like a graphics driver problem.  You do not say what graphic card you have, nor give any machine specification, which might help solve your problem.
+1

Your graphics card/chip was released 2007, 5 years ago. I think it is graphics driver problem. You are using the recommended driver, yes, but I suggest that you try also the other alternatives in the menu for proprietary graphics (in the screenshot). One of them might work better.

Also I suggest that you try Ubuntu 10.04 LTS, or the current Xubuntu or Lubuntu with smaller footprints (Lubuntu's desktop LXDE has a very small footprint). Download the iso files and try them live from a USB drive before deciding which version to use!

---

### Post by siick on 2012-02-29
Ok i will try this and report here.
I was using 10.04 LTS, a wonderful one, but i've changed to try Gnome 3. I prefer now waiting for the other LTS version which is coming soon.
Thanks for your answer.

---

### Post by siick on 2012-03-01
So...
I have tried every driver in my list, and nothing change (it was even worst with the 173 one).
Finally, i did what i didn't want to do, a complete reinstallation (from zero i just kept my mozilla and thunderbird files in my home folder) of my 11.10 to see if that can arrange something.
And all is ok now! So it was NOT a driver problem, because i use the same one now (recommended one). 
We will not know what it was T_T but the important thing is that all is working again. Thanks anyway. :)

---

### Post by mastablasta on 2012-03-01
no it seems it was the driver problem afterall. 
 
if you performed an upgrade you would need to first compeltelly purge the old driver and then install new one. 
 
instead it might be that some residual files were left from the old driver which prevented the newer verison to function propperly. upon reinstall all previous settings and any driver files were deleted. and new ones seem to work.

---

