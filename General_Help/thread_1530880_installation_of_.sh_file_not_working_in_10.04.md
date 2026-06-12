---
title: "installation of .sh file not working in 10.04"
date: 2010-07-14
forum: General Help
---

### Post by jiffyc23 on 2010-07-14
I switched from 8.04 to 10.04 and I now cannot install older .sh files by using the "bash" command it says "This installation does not support glibc-2.1  on x86_64"  

It worked on the same computer with 8.04.

How do I get and use an older glibc or whatever was used on 8.04 onto 10.04?

---

### Post by WorMzy on 2010-07-14
Looks like you switched architectures when you switched Ubuntu versions. I'm guessing you used 32-bit 8.04 and then did a fresh install of 64-bit 10.04. You'll need to find a 64-bit version of the applications you're attempting to run, or install 32-bit 10.04.

---

### Post by xtremesupremacy3 on 2010-07-14
Just out of curiosity, is this a homemade script or one provided by for instance Loki Games?

---

### Post by m4tic on 2010-07-14
Maybe that program has an update, go check if it is available where you downloaded it

---

### Post by jiffyc23 on 2010-07-14
Can an older system support 64 bit 10.04?
I am pretty sure I downloaded the 32 bit version of 10.04.
And yes it is Loki games which I believe is no longer supported with updates.

---

### Post by WorMzy on 2010-07-14
If I got it the wrong way around and you ran a 64-bit OS before, and now run 32-bit Lucid, then you'll be able to run 64-bit Lucid with no problems.

If I'm completely wrong though, and you've never used a 64-bit OS before, then I don't know if you'd be able to run a 64-bit OS. If you open a terminal and run
```
uname -i
```
It'll tell you if you have 32-bit (i386, or i686) or 64-bit (x86_64) currently installed.

---

### Post by jiffyc23 on 2010-07-14
uname -i 
"unknown"
is returned.
I'm pretty sure I've never used 64-bit, the computer is over ten years old.

Can I get and install an older glibc like glibc-2.0 or what 8.04 had?

or is there another way to make the .sh installation file work?

---

### Post by WorMzy on 2010-07-14
I don't like the look of that "unknown", and can't really offer any advice regarding downgrading your glibc package -- a lot of other applications will depend on the current version, so downgrading would potentially break those. If there's no updated version of the .sh files you want to run, then perhaps reinstalling 8.04 would be the best option for you. It's not recommended, but if it works for you, then it works for you, right?

Out of curiosity, what does the non-specific
```
uname
```
return?

---

### Post by jiffyc23 on 2010-07-15
Uname
"Linux"

Thanks for the help and suggestion.

---

### Post by WorMzy on 2010-07-15
Sorry, that should have been ```
uname -a
```

---

