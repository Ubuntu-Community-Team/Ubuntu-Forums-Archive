---
title: "Wobbly Windows doesn't work! D:"
date: 2011-10-01
forum: General Help
---

### Post by iNeed Help on 2011-10-01
I installed CCSM and I enabled Wobbly Windows, I even restarted, and it still won't work... Help??

I am running Ubuntu 11.04 in Classic (VMware doesn't support Unity)

---

### Post by moorhead98 on 2011-10-01
Make sure that 
1) you are able to run compiz, a.k.a. have a good enough graphics card (to check it, download and run [compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check"))
 2) that you're using compiz as your window manager and not metacity

---

### Post by iNeed Help on 2011-10-01
> **moorhead98 said:**
> Make sure that 
1) you are able to run compiz, a.k.a. have a good enough graphics card (to check it, download and run [compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check"))
 2) that you're using compiz as your window manager and not metacity

My graphics card is quite good. It runs most games pretty good in Windows, so I'm positive it will be good enough.
How do I know if I'm using it as my window manager instead of metacity?


/ubuntu noob

It says GNOME's desktop thing is already running, how do I disable it, and how do I enable it in the future?

---

### Post by realzippy on 2011-10-01
> **iNeed Help said:**
> (VMware doesn't support Unity)
...because you have no 3D acceleration.
That 's why compiz doesn't work also...

---

### Post by iNeed Help on 2011-10-01
> **realzippy said:**
> ...because you have no 3D acceleration.
That 's why compiz doesn't work also...


Awwww. Theres no other way to get Wobbly Windows?

---

### Post by realzippy on 2011-10-01
I do not if it is possible to get 3D in vmware;
in virtualbox it may work (afaik).
Maybe someone else knowing this about virtual machines?

---

### Post by iNeed Help on 2011-10-05
[IMG]http://i.imgur.com/WtzxG.png[/IMG]

Now what!?

---

### Post by moorhead98 on 2011-10-05
> **iNeed Help said:**
> [IMG]http://i.imgur.com/WtzxG.png[/IMG]

Now what!?

I am not an expert on this stuff, but i believe that means "software virtualizer" or something of the likes. Which, if I am correct, means compiz can't run on vmware or virtualbox or whatever it is. Try and go to the vmware or virtualbox websites and see if they have anything on the topic. Also shoot a question over at the compiz forums, they might know what that means

---

### Post by mcduck on 2011-10-06
Have you installed the wmware guest additions? You need those for graphics acceleration (as well as some other stuff), and 3D acceleration is required to run Compiz, which of course is required for any Compiz plugins like wobbly windows or Unity.

[https://help.ubuntu.com/community/VMware/Tools]("https://help.ubuntu.com/community/VMware/Tools")

---

