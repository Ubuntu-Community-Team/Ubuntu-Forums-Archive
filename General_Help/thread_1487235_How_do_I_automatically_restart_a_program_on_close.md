---
title: "How do I automatically restart a program on close?"
date: 2010-05-18
forum: General Help
---

### Post by CTenorman on 2010-05-18
Hi,

I'm trying to get a program to automatically reload if I accidentally close it. This is a remote access program, so it has to be relaunched without me doing anything to help it along if it crashes or I accidentally close it.

I noticed that someone came up with a way to solve this back in 2007 [http://ubuntuforums.org/showthread.php?t=352546]("http://ubuntuforums.org/showthread.php?t=352546") but the files don't appear to exist any more for it to work.

Does anyone have any suggestions how I might get a program to automatically reload on exit? Thanks!

---

### Post by mb_webguy on 2010-05-18
Well, the simplest (but not necessarily best) way to do it would be to write a simple script that runs the program from within a while loop, similar to the following.```
#! /bin/sh

while [ true ]; do
        firefox
done
```If you open Firefox by running the script, Firefox will continue to open every time it's closed until you kill the script.

---

### Post by CTenorman on 2010-05-18
Fantastic! Would the loop take much processing power? An instant reboot isn't required, just every min or two would be fine.

---

### Post by seenthelite on 2010-05-18
System, Preferences, Startup Applications, Options, Remember Currently Running Applications

---

### Post by mb_webguy on 2010-05-23
> **CTenorman said:**
> Fantastic! Would the loop take much processing power? An instant reboot isn't required, just every min or two would be fine.

It won't actually take any processing cycles at all except when you quit the program.  Unless you specifically tell it otherwise, a script will wait for a command to finish before moving along to the next.  So in my example above, the script will launch Firefox and then stop, waiting for Firefox to end.  If you close Firefox, the script will wake up, loop around and open Firefox, then go back to sleep until you close Firefox again.

What you absolutely *don't* want to do is add an ampersand after the command to start your application, since the ampersand tells the script to run the command in the background and don't wait for that command to finish before moving on to others.  So if the line that says "firefox" in my example instead said "firefox &", then you'd lock up your system really quickly as the script opened multiple instances of Firefox in an endless loop.

As long as you don't add the ampersand, though, the script will wait until the command finishes before it continues.  So you get a single instance of the program which is restarted by the script whenever it's closed.

---

### Post by CTenorman on 2010-05-25
Wow, fantastic! Thank you so much for your help and explanation!

---

### Post by WorMzy on 2010-05-25
That's ingenious, I may use that myself, thanks, webguy!

---

