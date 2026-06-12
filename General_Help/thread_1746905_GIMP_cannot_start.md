---
title: "GIMP cannot start"
date: 2011-05-02
forum: General Help
---

### Post by Tristan_F on 2011-05-02
Hi all,

I made a clean install of Kubuntu 11.04 and cannot get gimp to work. I installed the package using Kpackage and when I try to start GIMP it doesn't. Here it is the output : 

(gimp:13671): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
Segmentation fault

Anyone have the same problem? any fix?

Thanks

---

### Post by cmallam on 2011-05-05
> **Tristan_F said:**
> Hi all,

I made a clean install of Kubuntu 11.04 and cannot get gimp to work. I installed the package using Kpackage and when I try to start GIMP it doesn't. Here it is the output : 

(gimp:13671): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
Segmentation fault

Anyone have the same problem? any fix?

Thanks

i have exactly the same problem!

(gimp:3859): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
Segmentation fault

---

### Post by cmallam on 2011-05-05
In short, this is how I fixed the problem:

[LIST]
[*]set GTK theme to raleigh
[*]start GIMP once
[*]set GTK theme back to oxygen-gtk
[*]GIMP now works with oxygen-gtk, too!
[/LIST]

---

### Post by Njall on 2011-05-06
Alas, I'm running Kubuntu (KDE 4.6.2).  I couldn't run Gimp from the menu after installing it.  So in the terminal I tried it and get the same error  you reported.  

```
$ gimp

(gimp:29547): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
Segmentation fault

```

I installed gtk-chtheme and followed your instructions and it did not correct the problem.  :(

I'm still looking into the issue.

[edit] 
I also changed the Gtk theme using the KDE system config after reading [http://ubuntuforums.org/showthread.php?p=10748575]("http://ubuntuforums.org/showthread.php?p=10748575").  Same thing... still cannot start Gimp; still have GLibe-WARNING message when run from terminal.

---

### Post by jpelorat on 2011-05-06
> **cmallam said:**
> In short, this is how I fixed the problem:

[LIST]
[*]set GTK theme to raleigh
[*]start GIMP once
[*]set GTK theme back to oxygen-gtk
[*]GIMP now works with oxygen-gtk, too!
[/LIST]


This worked for me too :P

---

### Post by TechZilla on 2011-05-08
thanks you jpelorat!

same exact issue.

i really wish these package glitches didn't happen as often as they do.

just some simple regular after build QA, on a normal install would suffice.

---

### Post by zapacit on 2011-05-08
Thx... worked for me also...

You can find Raleight here:

System settings -> Application appearence -> GTK Appearence -> Widget style

Start gimp, restore to oxygen, your good to go.

---

### Post by tamagotono on 2011-05-08
+1
This worked for me too.:p

I am wondering how you figured out what was causing the problem...

---

### Post by brian-w on 2011-05-13
Worked for me too - thanks

---

### Post by Spyderkid on 2011-05-13
All i did is a apt-get --reinstall , fixed it pease of cake

---

### Post by Dakra on 2011-05-15
> **cmallam said:**
> In short, this is how I fixed the problem:

[LIST]
[*]set GTK theme to raleigh
[*]start GIMP once
[*]set GTK theme back to oxygen-gtk
[*]GIMP now works with oxygen-gtk, too!
[/LIST]


It works with Kubuntu 11.04 x86. Thank you.

---

### Post by heitormsilva on 2011-05-19
> **cmallam said:**
> In short, this is how I fixed the problem:

[LIST]
[*]set GTK theme to raleigh
[*]start GIMP once
[*]set GTK theme back to oxygen-gtk
[*]GIMP now works with oxygen-gtk, too!
[/LIST]

Thanks cmallam it's worked to me too :)

I'm just still thinking, why this kind of problems still happening to us and when it will over... :confused:

---

### Post by sage messer on 2011-05-22
> ** said:**
> In short, this is how I fixed the problem:

[LIST]
[*]set GTK theme to raleigh
[*]start GIMP once
[*]set GTK theme back to oxygen-gtk
[*]GIMP now works with oxygen-gtk, too!
[/LIST]


Fixed. Another vote of thanks to cmallam.

---

### Post by denisk on 2011-06-11
> **cmallam said:**
> In short, this is how I fixed the problem:

[LIST]
[*]set GTK theme to raleigh
[*]start GIMP once
[*]set GTK theme back to oxygen-gtk
[*]GIMP now works with oxygen-gtk, too!
[/LIST]

Thank you! Worked like a charm!
> **zapacit said:**
> 
You can find Raleight here:

System settings -> Application appearence -> GTK Appearence -> Widget style

And thanks to zapacit to pointing out to the location of GTK appearance.

---

### Post by ivan314 on 2011-07-07
> **Tristan_F said:**
> Hi all,

I made a clean install of Kubuntu 11.04 and cannot get gimp to work: GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
Segmentation fault


Just for the record and the search engines:
wxglade has the same issue on a fresh kubuntu 11.04 install.

the mentioned fix partially works: Change the gtk theme to Raleigh and LEAVE IT THERE. Changing back to oxygen-gtk reintroduces the segfault.

---

### Post by OlorinIWas on 2011-07-21
jeez...thanks yall 8--)

---

### Post by RudyG on 2011-07-24
Another Thank You. The workaround solved the problem for me as well.

Rudy

---

### Post by j4play on 2011-08-03
yet another vote!
hopefully this workaround will make it to stable release.

---

### Post by mercibe on 2011-09-20
Perfect workaround, thank you!

---

### Post by siabost on 2011-09-24
Thank you, sir!
That worked for me too - Kubuntu 11.04 64bit.

):P

---

### Post by cobaltwarrior19 on 2011-09-30
> **cmallam said:**
> In short, this is how I fixed the problem:

[LIST]
[*]set GTK theme to raleigh
[*]start GIMP once
[*]set GTK theme back to oxygen-gtk
[*]GIMP now works with oxygen-gtk, too!
[/LIST]


This worked for me. Thanks! :)

---

### Post by ADani on 2012-02-07
> **cmallam said:**
> In short, this is how I fixed the problem:

[LIST]
[*]set GTK theme to raleigh
[*]start GIMP once
[*]set GTK theme back to oxygen-gtk
[*]GIMP now works with oxygen-gtk, too!
[/LIST]

Thank you! that worked for me too in a fresh Kubuntu 11.04 32bit, installed in my very non-ubuntu-friendly ASUS X44H.

---

### Post by MrSnowmiss on 2012-02-10
> **cmallam said:**
> In short, this is how I fixed the problem:

[LIST]
[*]set GTK theme to raleigh
[*]start GIMP once
[*]set GTK theme back to oxygen-gtk
[*]GIMP now works with oxygen-gtk, too!
[/LIST]

Well this didn't do the trick for me :(

So I searched a bit more and found this: 
[bugreport](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/742516) where you can find another workaround in 
[comment 19](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/742516/comments/19)

```
The GTK workaround didn't work for me but I found a different workaround:

# mkdir ~/.gimp-2.6
# gimp

voila
```

Which did the trick on my kubuntu 10.10 system :D:P

---

### Post by Scunizi on 2012-10-01
Although this is an old thread I just came across this issue "all of a sudden".  On the first attempt using the GTK Widget change it didn't work.  Then after looking at System Activity I noticed that Gimp was running but just not displayed.  After killing it and attempting the theme widget change again it worked.

---

