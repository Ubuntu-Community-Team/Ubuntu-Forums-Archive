---
title: "Looks Like I'll Have To Go Back To Windows"
date: 2006-04-05
forum: General Help
---

### Post by Mark76 on 2006-04-05
Or I face a future of silence :(

---

### Post by Teroedni on 2006-04-05
right?

Maybe you could specify your problem better;)

If i am not mistaken yourr sound card dosent work?
is that the problem?

---

### Post by ComplexNumber on 2006-04-05
[quote=Mark76]Or I face a future of silence :([/quote]
please explain? i guess you have audio problems.

---

### Post by Mark76 on 2006-04-05
Correct.

It's a Digidesigns Audiomedia 3.

Those swine (DD) can't be arsed to write a driver for Linux :(

---

### Post by Teroedni on 2006-04-05
So are you sure the latest alsa dosen't support this soundcard?

---

### Post by Mark76 on 2006-04-05
Not really.  How would I check?

---

### Post by Teroedni on 2006-04-05
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)



You could also burn a dapper live cd and see if your card works there

Dapper=Latest ubuntu _[COLOR="Red"]Alpha status[/COLOR]_ support for newer hardware:)

[http://cdimage.ubuntu.com/releases/dapper/flight-6/](http://cdimage.ubuntu.com/releases/dapper/flight-6/)

---

### Post by Mark76 on 2006-04-05
I can't burn anything :(

Why are Digidesign not in that drop down menu on the Alsa page?  They really hate Linux, don't they.

---

### Post by Teroedni on 2006-04-05
Dont know never heard of it?

paste this in terminal 
```
cat /proc/asound/cards

```


and paste the answer here, if there are any.


paste this in terminal also
```
sudo lshw -class multimedia

```

and paste the answer here

---

### Post by Mark76 on 2006-04-05
Q1:
A: cat: /proc/asound/cards: No such file or directory
Q2:
A: -multimedia UNCLAIMED
       description: Multimedia audio controller
       product: Avid Technology Inc.
       vendor: Avid Technology Inc.
       physical id: 8
       bus info: pci@02:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: ioport:1080-10bf iomemory:40200000-40200fff iomemory:40000000-401fffff iomemory:40300000-40300fff irq:5

---

### Post by edal on 2006-04-05
Maybe your soundcard can emulate a Soundblaster, try the drivers for them?

As for going back to MS Windows, I wish you luck because I think you will need it. I have four machines at home with three running Ubuntu and #4 running Knopmyth. I haven't had a machine running Windows for three years.

No virus problems
No worm problems
Safer internet browsing
Updates on a regular basis
Updates without having to reboot
No DRM
No product activation
And finally..........
A virtual poke in the eye for Microsoft

Ed Almos

---

