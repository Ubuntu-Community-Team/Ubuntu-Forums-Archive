---
title: "heeeeelpppppp i could lose all my files"
date: 2009-11-10
forum: General Help
---

### Post by kandil on 2009-11-10
hi am new in ubuntu and am using 9.10 and i was gettin to love but suddenly after restarting it crashes and say alot of erors and refuses to boot 
it say "could not update iceauthority file /home/andy/.iceauthority"
then "there is a problem with the configuration server     
           (/usr/lib/libgconf-sanity-check-2 exited with status 256)"
then "nautilus could not create the following required folder:home/andy/desktop ,/home/andy.nautilus.
before running nautilus, please create these folder or set permissions such that nautilus can create them."
and that's it ,it stops there with just the default background without tellin me to enter my password or anything 
what can i do all my files in it and i didn't back it up 
i tried to use ubuntu cd to access my files but it tells me something about permissions 
could anyone helps me to access myy files or help me fix this issue

---

### Post by ZaHACKieL on 2009-11-10
Well, first some questions I would like you to answer:

1) What kind of installation did you used? the inside-windows-installation? a dual boot? a clean use-the-whole-HD installation?

2) How is your HD partitioned?

3) Is it a desktop pc or a laptop?

4) When you get to the default background, what are you able to do?

ZL

---

### Post by blueridgedog on 2009-11-10
I can't help you if this is a wubi install, but if it was a regular install, can you boot off of a live CD and post the output of the following two commands?

```
sudo fdisk -l
```

and 

```
mount
```

The first will show what disks and partitions you have and the second will show how they are mounted.  From there we can determine where your files are and how to back them up.  It sounds as though you may have had a disk or sector failure.

---

### Post by kandil on 2009-11-10
1) a clean use the  whole hd installation

2)only 1 drive (i know its a stupid thing to do :S)

3)laptop

4)the default background is the only thin that is in the screan and the only thing i do i moving the mouse but if i typed alt+ctl+f2 i go to a page like am in a xtreme session

---

### Post by ZaHACKieL on 2009-11-11
Ok, do you have access to the terminal? press Crtl+Alt+F1 ...does it take you to the terminal?

If your answer is yes, do you have access to your files from there?

You may also try booting the linux from the terminal and trying the same thing.

I found this threads:

[http://ubuntuforums.org/showthread.php?t=1081730](http://ubuntuforums.org/showthread.php?t=1081730)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1284161](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1284161)
[https://help.ubuntu.com/community/Troubleshooting#Software%20Issues](https://help.ubuntu.com/community/Troubleshooting#Software%20Issues)

Try those things and let me know what happens =]

ZL

---

### Post by kandil on 2009-11-11
i managed to access my files through the alt ctl f1 thing and i need to copy it through the terminal to an external HD  i will now search for a way to do that

---

### Post by ZaHACKieL on 2009-11-11
> **kandil said:**
> i managed to access my files through the alt ctl f1 thing and i need to copy it through the terminal to an external HD  i will now search for a way to do that

OK OK but did you read the links I posted in my last message? They are about that error msg your got, I believe it may be of help.

Let me know what happens

---

### Post by northern lights on 2009-11-11
Open a terminal and run```
sudo chown username:username ~/.ICEauthority
```. Replace "username" by your username.

---

### Post by kandil on 2009-11-11
i did read those threads and didn't help me
u can really help if u told me how to mount external HD from the terminal and tell  me how to copy my files to it

---

### Post by ZaHACKieL on 2009-11-11
> **kandil said:**
> i did read those threads and didn't help me
u can really help if u told me how to mount external HD from the terminal and tell  me how to copy my files to it

Try this:

[http://linuxservertutorials.blogspot.com/2009/03/how-to-mount-external-hard-drive-in.html](http://linuxservertutorials.blogspot.com/2009/03/how-to-mount-external-hard-drive-in.html)

---

### Post by 824957q on 2009-11-11
maybe its because you have crunch bang linux..

---

### Post by kandil on 2009-11-15
cranch bang linux what???
i have no idea wat r u talkin about

---

### Post by mokamonzy on 2009-11-25
[B][http://ubuntuforums.org/showthread.php?p=8386668#post8386668](http://ubuntuforums.org/showthread.php?p=8386668#post8386668)
[/B]> **[SO**[B]LVED] Auto-login not mounting encrypted home in karmic, unusable system
[/B][B]"Aha!! I worked it out. The GDM settings are stored in /etc/gdm/custom.conf so all I had to do was go into a virtual terminal and edit this file to change AutoLogin to false. Problem solved!..."
[/B]

Try it~!

---

