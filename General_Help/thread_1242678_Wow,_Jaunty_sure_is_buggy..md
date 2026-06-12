---
title: "Wow, Jaunty sure is buggy."
date: 2009-08-17
forum: General Help
---

### Post by ensleepent on 2009-08-17
First, I have to figure out how to edit xorg.conf to make my machine recognize that my monitor is capable of resolutions higher than 800x600.

And as soon as I do that, my windows' title bars disappear and my terminal window becomes a blank white box.  Thankfully, I was able to fix that one just by going to System>>Preferences>>Appearance and changing Visual Effects to "None."

Then I tried to run a program and ran into this bug:  [https://lists.ubuntu.com/archives/universe-bugs/2009-May/084091.html](https://lists.ubuntu.com/archives/universe-bugs/2009-May/084091.html) (Anyone figure out how to fix this one, btw?  I don't have a clue.)

I gotta tell ya, Jaunty has not been a good first impression for a new Linux user like myself.

I suppose that version 9.04 is still fairly new and is in the process of having its problems ironed out...  my question is:

For the time being, would I be better off downgrading to 8.04.3?

---

### Post by blur xc on 2009-08-17
What hardware do you have?  Jaunty had/has no issues detecting my monitor resolution and automatically changing to what it needs to be.

BM

---

### Post by realzippy on 2009-08-17
Which video driver do you use?

---

### Post by slakkie on 2009-08-17
You cannot downgrade, only clean install 8.04.3. (You can downgrade but it is not for beginners, you will experience pain, and plenty of it).

What you also could do, is install a cli only system and then install a light weight window manager like lxde, which is in favor by a lot of people.

See [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

---

### Post by abhilashm86 on 2009-08-17
> **ensleepent said:**
> 


For the time being, would I be better off downgrading to 8.04.3?

hmm well, people have cleared all bugs in hardy heron, runs great, i've never upgraded since hardy heron will give updates till 2011:guitar:

---

### Post by tripolitan on 2009-08-17
It has been my experience with just about every GNU/Linux distro I have used in the past 9 years (I have used about 7 different ones) to stick with the supported versions (LTS in Cannonical's language). Jaunty, as any new release from any distro is not stable and by the time it becomes stable, the next LTS version will be available.

Ubuntu LTS, Red Hat Enterprise, SuSE enterprise, Debian stable and CentOS are distros that are supported for a number of years. Pick the one that works with your hardware and stick to it.

If you're into the latest and greatest stuff, then you'll have to suffer the consequences.

---

### Post by ensleepent on 2009-08-17
Well, my computer's a few years old, nothing special.  Just a nice, humble little emachines desktop unit with an AMD Sempron.

sudo lspci | grep VGA tells me:

nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

It's an on-board thingy.  I just went to System>>Administration>>Hardware Drivers to get the driver for it.  Installing that actually reduced my available max resolution from 800x600 to 640x480 until I edited xorg.conf.

My monitor's an old acer AL1716 17-inch flat panel LCD.

Downgrade/clean install...  yeah, that's what I meant.  I already have 8.04.3 on CD, no problem.  :)

So, abhilashm86, think it might be a good idea for me to "downgrade?"  Might be the thing to do, 'cause I have no "bug-repellent."

slakkie:  What exactly is a "cli only system" and what are "light weight window managers?"  Sorry if that's a stupid question -- I'm new to Linux and I still don't know as much about computers in general as I'd like to.  I'm a quick and eager learner though.  :)

---

### Post by ensleepent on 2009-08-17
Oh, hi, tripolitan.  You're reply showed up while I was posting mine.

Yeah, that's kind of the impression I was getting.  9.04 is still young.  Might be better to stick with the tried-and-true for reliability purposes.

So how is 8.04.3?  Does it run good?  Can it do a lot?  Versatile and bug-free?  I'd like to hear a few more votes of confidence before I go to the trouble of installing it.  I think I've had enough tedium for one day (more like three days) tweaking with 9.04 to stand any more error messages and reboots.  :)

---

### Post by jerrrys on 2009-08-17
a common saying with 804 "it just works" 
and thats been my experience on two machines...

---

