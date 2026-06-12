---
title: "Boot-up problems"
date: 2012-01-10
forum: General Help
---

### Post by dkolars on 2012-01-10
Running 10.10...  this happens occasionally, and a re-start usually fixes it... NOT this time...  When I boot up, the mouse pointer stays a spinning circle.  The Gnome Panel that shows the minimized programs is (sometimes) filled with vertical white bars that show when I pass my mouse over the panel... IF that happens, I know that there are countless instances of "flush-x:y" running...  like I say, usually a re-boot fixes that.  

This time, there is only one (1) instance of flush (8:0) running, but the mouse pointer is a spinning wheel, the HDD is running constantly... looking at the stats, i see that wnck-applet is using 56% of the CPU... looking at CPU usage, BOTH CPU's are running at 97-98%!  There is a program listed with no name, 0% CPU usage, ? for the start time, not using any Virtual Memory... can't kill that one...  

I Stopped the wnck-applet and CPU usage went down to 69-77%, but of course, had to reload its components to have graphic functionality.  So, restarted again... now have the flush-x:y running constantly, HDD spinning non-stop, etc.  

6 reboots and no improvement...  not liking this... Oh, yeah, I rebooted into a repair mode, and it did a LOT of stuff, but didn't improve anything!!

Obviously, I have connectivity, can run all my programs, but as I write this, both CPU's are running at nearly 100%...

When I click on "Re-start", it tells me there is an unknown program running and asks if I want to re-boot anyway.  Sometimes simply opening that window (like just now!) will kill whatever is running... sometimes not.  Right now everything is running "normally" after I clicked to reboot.  And, looking at the re-boot screen, that unknown program is still running, but it has given back all the resources it was using...

Any thoughts, hints, etc.  TIA  dk  :confused:

---

### Post by QIII on 2012-01-10
If you can...

```
sudo apt-get install htop
```

Then

```
htop
``` 
 
and see if you can catch that little unknown bugger running to find out what it is.

Is your ethernet traffic high?

---

### Post by dkolars on 2012-01-10
Thanks... got it installed, showing nothing unusual now...  Nope, ethernet traffic was zero when the system was goofing up...

Not sure what program that reminds me of, but it reminds me of some old DOS program from way back...  hopefully I can ID the culprit...  thanks again!!  Ah'll be back...:p

---

### Post by dkolars on 2012-01-17
OK... got htop installed and running... my, it's sure interesting to see what is eating all the processor time!!  Have just re-booted and encountered the problem again...  see that it's the "gnome panel wnck-applet"...  can kill it with "killall wnck-applet", but that does not solve the problem... the panel still shows countless vertical lines (running processes) and minimizing a program to it shows no icon on the panel, probably because it's at the end of countless others...  so, re-boot is only cure for now...  Still hunting, but at least I can ID the culprit...  Also, see that wnck-applet was a known bug in previous releases... guessing it still is!!

---

