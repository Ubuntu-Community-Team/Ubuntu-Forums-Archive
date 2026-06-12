---
title: "trying to reload"
date: 2009-07-19
forum: General Help
---

### Post by 2roombas on 2009-07-19
I thought I posted this already, but I guess not?!

Anyway, I recently tried installing the 9.10 Alpha according to what it said to do, but after rebooting and happily seeing the Ubuntu logo on the screen, it then only opened to a black blank screen.

My first thought was, "Just have patience, its a new load...." but good grief, 20 minutes of patience later and still only a blank screen??  No, I think something went wrong with that. :(

So then I'm, "OK, no problem, I'll just reload 9.04... I have the Live disk." but when I tried doing that I see this pop up....
----------------------
[INDENT]An error occurred:

Invalid argument

For more information, please see the log file: c:\docume~1\owner\locals~1\temp\wubi-9.04-rev128.log[/INDENT]

------------------------------

What happened? How can I fix this?   I'm using Windows right now..... yuck, icky, phew! I want to get my Ubuntu reloaded! :(

---

### Post by TeoBigusGeekus on 2009-07-19
For starters, why do you use the alpha version and don't download the final, stable version?

---

### Post by 2roombas on 2009-07-19
> **TeoBigusGeekus said:**
> For starters, why do you use the alpha version and don't download the final, stable version?

I didn't know the final/stable was out yet?! It is?

Someone on another forum gave me a link, said he downloaded that and it works great for him, so I foolishly just did the same... sigh!

---

### Post by TeoBigusGeekus on 2009-07-19
It's been here since April (9.04: released April -04- of the year 2009 - 9)
[http://www.ubuntu.com/getubuntu]("http://www.ubuntu.com/getubuntu")

---

### Post by 2roombas on 2009-07-19
I already have the 9.04 Live Disk.  What I tried to load was 9.10 Karmic, that to my understanding won't be final released until October.  Here is the link for the Alpha I used....

[http://www.ubuntu.com/testing/karmic/alpha1](http://www.ubuntu.com/testing/karmic/alpha1)

It didn't work for me, drats!, so I want to reload the stable 9.04 Jaunty now but can't do it.:confused:

---

### Post by TeoBigusGeekus on 2009-07-19
> **2roombas said:**
> I already have the 9.04 Live Disk.  What I tried to load was 9.10 Karmic, that to my understanding won't be final released until October.  Here is the link for the Alpha I used....

[http://www.ubuntu.com/testing/karmic/alpha1](http://www.ubuntu.com/testing/karmic/alpha1)

It didn't work for me, drats!, so I want to reload the stable 9.04 Jaunty now but can't do it.:confused:
Sorry, I totally misread your first post.
Well, I don't have any experience with wubi. Why don't you try to dual boot? It's cleaner and more efficient. Besides, if something happens to your windows installation (crash, virus, etc.) you can say goodbye to Ubuntu as well.

---

### Post by 2roombas on 2009-07-19
> **TeoBigusGeekus said:**
> Sorry, I totally misread your first post.
Well, I don't have any experience with wubi. Why don't you try to dual boot? It's cleaner and more efficient. Besides, if something happens to your windows installation (crash, virus, etc.) you can say goodbye to Ubuntu as well.

Actually a dual-boot is what I had and what I'm trying to re-do. I have 2 other computers that are 100% Linux, but this desktop here I kept as a dual-boot.  I'm using the Windows on iT right now. Blech!  Until that alpha I no problem, but now when it boots I see only:

Windows XP Home (yada, yada...)
Windows (default)

Those are now my two OS choices. I have to pick the XP one because the (default) doesn't work (not sure why that is there?!).  

When I insert the Ubuntu 9.04 to do a dual-boot my thinking is the problem is happening because the computer tries that Windows (default)first and that's the problem.

I tried going to My Computer/Properties and changing the default OS, but the odd thing is there is only "one" choice, the XP Home Edition, in that drop-down of choices?!

---

### Post by 2roombas on 2009-07-20
Could this be  something of the problem I have?

In this windoze when I rt-click my computer/properties/advanced tab then click to "edit the start up files manually", I see ths....
[INDENT]
[boot loader]
timeout=10
default=c:\wubildr.mbr
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect[/INDENT]

Can this be edited to allow a reload of me 9.04? I will just then remain patient until the final karmic comes out. :)

---

### Post by 2roombas on 2009-08-01
Anyone know what the problem is here?  I really want to reload ubuntu.:(

---

