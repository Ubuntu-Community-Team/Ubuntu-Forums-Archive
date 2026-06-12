---
title: "(help a noob, once again!) how do I install this?"
date: 2011-04-10
forum: General Help
---

### Post by chromium48 on 2011-04-10
Hey, I have python installed and py-qt installed via synaptic package manager. Now, how do I install this? 

[http://abhinandh.com/post/2755166494/cloudapp-for-linux-and-windows-py-cloudapp#disqus_thread](http://abhinandh.com/post/2755166494/cloudapp-for-linux-and-windows-py-cloudapp#disqus_thread)

Thanks in advance :D

-westin

---

### Post by Dutch70 on 2011-04-10
Menu to system > admin > synaptic package manager, and search for the programs you want to install. Tick the box on the left, mark it for installation and click "apply"

---

### Post by chromium48 on 2011-04-10
> **Dutch70 said:**
> Menu to system > admin > synaptic package manager, and search for the programs you want to install. Tick the box on the left, mark it for installation and click "apply"

I need to know how to install the app (Cloud) itself, not python and py-qt.

As I stated in the fist post, I already have python and py-qt installed.

---

### Post by orethrius on 2011-04-10
NOTE: Either way, that archive's going to need to be extracted; if you have any trouble with this bit, please say so, and I'll see what I can do to help. :)

It's a self-contained application, for the most part; all you'd have to do is extract the archive to a single location (right-click, "Extract Here" in Kubuntu; IIRC, Gnome has a similar feature) and double-click "CloudApp" to launch.  

You can also copy the whole directory to /usr/bin using **sudo mkdir /usr/bin/app_cloudapp; sudo cp -r abhinandh*/* /usr/bin/app_cloudapp/** and create a blank text file via **sudo nano /usr/bin/cloudapp** where you'd enter the text **python /usr/bin/app_cloudapp/cloudapp** and save, then enter **sudo chmod +x /usr/bin/cloudapp** to have a convenient quick-run alias to CloudApp.

Of course, the first method is quicker and easier. ;)

---

### Post by ~Plue on 2011-04-10
> **chromium48 said:**
> I need to know how to install the app (Cloud) itself, not python and py-qt.

As I stated in the fist post, I already have python and py-qt installed.
just extract the archive and double click [I]cloudapp

[/I]edit: 3 minutes late :[I]| ..
[/I]

---

### Post by orethrius on 2011-04-10
> **~Plue said:**
> just extract the archive and double click [I]cloudapp

[/I]edit: 3 minutes late :[I]| ..
[/I]
Nah, that's fine; I'm only as late as I am because I wanted to be thorough, and even then I had to go back and edit some bits.  This has to be an early version of the CloudApp port, though, since having to xkill the program isn't exactly user-friendly, or process-friendly for that matter. ;)

EDIT: ...and xkill doesn't even do it, I have to use a CLI kill.  Nice. XD

---

### Post by ~Plue on 2011-04-10
^ isn't the there a quit option from the icon in the notification area? i noticed it since it refused to start unless i had a systray running

---

### Post by orethrius on 2011-04-10
> **~Plue said:**
> ^ isn't the there a quit option from the icon in the notification area? i noticed it since it refused to start unless i had a systray running
D'oh.  Here, I'd even come up with a clever kill script to identify it and abort it.  Oh well. :lolflag:

[COLOR="Red"]WARNING[/COLOR]
[COLOR="Black"]Be CAREFUL with this, it'll abort ANYTHING matching the word after **grep**.  I found this out by using **python** rather than **cloudapp** and accidentally killing my printing services.  Whoops.[/COLOR]
```
for i in `ps x | grep cloudapp | awk '{print $1}'`; do kill -9 $i; done
```

---

### Post by Dutch70 on 2011-04-10
> **chromium48 said:**
> I need to know how to install the app (Cloud) itself, not python and py-qt.

As I stated in the fist post, I already have python and py-qt installed.

LOL, sorry...I was looking at your link & didn't refer back to your post.

---

