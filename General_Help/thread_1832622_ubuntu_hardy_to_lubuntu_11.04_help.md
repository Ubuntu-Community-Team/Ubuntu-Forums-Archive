---
title: "ubuntu hardy to lubuntu 11.04 help"
date: 2011-08-25
forum: General Help
---

### Post by dan0804smith on 2011-08-25
so i have this weird stock version of ubuntu hardy from dell that does not allow for any updates (due to driver and webcam driver support, i assume).  i have literally tried everything to update my hardy, but it is just a fail.  since i pretty much have to boot fresh i thought i would give lubuntu 11.04 a try since my netbook (cd drive-less btw) is only a 1.6ghz (duel) 1gb ram machine.  

so.  i got on my dad's windows computer and used universal USB to create a live USB from the lubuntu 11.04 ISO.  i stuck it into my hardy netbook and selected "boot from usb" in the boot options.  it was the only USB in a slot.  the screen said "no bootable partions"

what do i do?

please help me get rid of this out-dated OS

*note* i do not have a external CD drive to use.  i could buy one for $15, but i am a frugal bastard and i like learning different ways to do things.  if worst comes to worst i will buy one but i feel huge self accomplishment when when i dedicate my time to solving a problem instead of the easy way out (like buying something)

---

### Post by Megaptera on 2011-08-25
I'd say bite the bullet and spend $15. Once you've done that you can have loads of fun for free distro-hopping to try out all the different _buntus, derivatives etc.
As there are loads of _free_ linux live cds out there to try I think it'll be $15 well spent.

Just my opinion of course!!

---

### Post by sidzen on 2011-08-25
Make a bootable USB stick of [SystemRescueCD 2.3.0]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/2.3.0/systemrescuecd-x86-2.3.0.iso/download") on a small flash drive ( have a 512MB stick for this purpose)
in the manner shown [here]("http://www.pane-free.com/pg_2.html").  Boot to it.

Type "startx" when prompted and in the yellow-colored terminal type "gparted" and Enter; then
partition the hard drive.

---

### Post by kerry_s on 2011-08-25
try this:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

point it to your lubuntu iso & it will do the work for you.

if that fails, go head & use it to grab ubuntu, later you can easily make a lubuntu installer with startup disk creator.

---

### Post by dan0804smith on 2011-08-25
hey thanks guys but i am going to need a little bit more of a walk through than that...i am still farly new to linux  the path to the file is /home/daniel/Desktop/lubuntu-11.04.iso

if that helps?

---

### Post by kerry_s on 2011-08-25
> **dan0804smith said:**
> hey thanks guys but i am going to need a little bit more of a walk through than that...i am still farly new to linux  the path to the file is /home/daniel/Desktop/lubuntu-11.04.iso

if that helps?

when you click the button i pointed to in the pic, it will pop up a browser, click computer-> / -> home-> daniel-> Desktop-> lubuntu-11.04.iso

---

### Post by dan0804smith on 2011-08-25
when ever i try to open that file it just says "Couldn't display "/home/daniel/Desktop/unetbootin-linux-549(2)"."  this is the **** i run into because of dell's ubuntu..... i think iw ill have to cut my losses and just get a cd drive

---

### Post by kerry_s on 2011-08-25
> **dan0804smith said:**
> when ever i try to open that file it just says "Couldn't display "/home/daniel/Desktop/unetbootin-linux-549(2)"."  this is the **** i run into because of dell's ubuntu..... i think iw ill have to cut my losses and just get a cd drive

don't get stressed, it's just your lack of knowledge. right click the unetbootin-> properties, look for the box that says executable & check it. once you do that double click it, select execute if it asks.

---

### Post by dan0804smith on 2011-08-25
thank you for teaching this noob a thing or two.  i dont have a flash drive on me right now but i was able to get into it.  thank you for your patience with me

---

### Post by kerry_s on 2011-08-25
> **dan0804smith said:**
> thank you for teaching this noob a thing or two.  i dont have a flash drive on me right now but i was able to get into it.  thank you for your patience with me

your going to need at least 1gb drive to put the iso on, thats what i use.

---

### Post by Megaptera on 2011-08-26
Glad to read you're getting it sorted!!

---

