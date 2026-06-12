---
title: "Blocks appear instead of letters"
date: 2011-01-31
forum: General Help
---

### Post by Sachiko on 2011-01-31
Well, when I started the PC like always, it started normal 
been having issues actually, every time I start up the PC it freezes when I put the password in and its going to the desktop and stuff, then I have to re-start it or it re-starts itself, or just go to where I have to type in the password again, and then it does it again after a while, after 3 or 4 times of that it goes to the desktop normally and works fine, but today it took some time, and after it finally loaded the panel was all odd, everything appeared in block letters, like when Mozilla can't recognize certain language it just shows you blocks, that appears, but I check the system, where images and all that, everything appears normal, it only seems to be the panel.
wondering if its that I need to re-install the panel, or something else, also this odd file appeared too, it says (invalid coding) next to it, when I go to upload an image or something the files there, I wonder if that has something to do, or maybe its just been there who knows
(and the freezing part too), anyways, I'm new here so I don't really know if this place was the right place to post this up 
OTL 
theres a screenshot in an attachemnt thing (if I put it up, it would appear to big)

[IMG]http://img227.imageshack.us/i/screenshotxsq.png/[/IMG]

---

### Post by [Snc] on 2011-01-31
Well, something went wrong with the fonts. Maybe your disk is not healthy and has bad sectors.

---

### Post by Sachiko on 2011-01-31
> **'[Snc] said:**
> Well, something went wrong with the fonts. Maybe your disk is not healthy and has bad sectors.
mmmm, so what can I do for the disk though, get a new one or something like that?

---

### Post by [Snc] on 2011-01-31
> **Sachiko said:**
> mmmm, so what can I do for the disk though, get a new one or something like that?

try to test if the disk is bad first ...

```
badblocks -v /dev/sdx
```

x - the disk

---

### Post by Sachiko on 2011-02-02
> **'[Snc] said:**
> try to test if the disk is bad first ...

```
badblocks -v /dev/sdx
```x - the disk

I tried that, but it says it doesn't recognize the action badblocks 
or should I take that out and just put the rest?

---

### Post by frotzed on 2011-02-02
Just tried this myself and it works fine.  Here's what I typed in terminal:

```
sudo badblocks -v /dev/sda1
```

Oh, but "sda1" is the name of my HDD, yours will probably be different.

---

