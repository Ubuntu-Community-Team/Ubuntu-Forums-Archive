---
title: "Chromium slow, jaggy fonts after last update"
date: 2010-05-28
forum: General Help
---

### Post by inverseroom on 2010-05-28
I've been running Lucid with great success these past few weeks on my HP dv3 laptop.  Chromium, however, doesn't seem to get along so great with it.  I had problems right off the bat with sluggish behavior, which seemed intermittent for a week or so.  Then I thought I had it licked...Chromium had been working well for two weeks.

Yesterday's updates returned it to the sluggish state, though, and all the fonts now look jaggy.  I have the msttcorefonts installed of course and have turned off all hinting and smoothing.  Everything looked great yesterday and still does in all my other apps including Firefox.

Any ideas where I should look for a fix?

---

### Post by Quake on 2010-05-28
The chromium ppa is really a nightly build, meaning it will brake because developers are adding new untested features.

On thing you can do is to install Chrome: [http://www.google.com/chrome](http://www.google.com/chrome)
This is the final Chromium product.

Or wait until the developers rectify the problem

---

### Post by lovinglinux on 2010-05-28
Although Chromium is the open source version, I also recommend the latest stable Chrome. It works much better than Chromium for me.

---

### Post by inverseroom on 2010-05-28
ah, great, didn't realize there was a linux chrome!  I will try it.

---

### Post by inverseroom on 2010-05-28
Well, I switched over to Chrome, and it does seem speedy again!  But the fonts are still jaggy.  Any ideas?

---

### Post by lovinglinux on 2010-05-28
> **inverseroom said:**
> Well, I switched over to Chrome, and it does seem speedy again!  But the fonts are still jaggy.  Any ideas?

See the last item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html). I'm not sure this will help Chrome, but it does help Firefox with font problems.

---

### Post by Quake on 2010-05-29
Can you give us a screenshot of Chrome?

---

### Post by inverseroom on 2010-05-31
By all means.  Here's what the New York Times looks like.  I should add that no other application looks this way, and that in Chrome, every single typeface looks like this.

[IMG]http://inverseroom.creotia.com/pictures/jaggy.jpg[/IMG]

---

### Post by Quake on 2010-05-31
Perhaps a .fonts.conf will make a difference.
[http://tombuntu.com/index.php/2008/10/15/tweak-your-font-rendering-for-better-appearance/](http://tombuntu.com/index.php/2008/10/15/tweak-your-font-rendering-for-better-appearance/)

---

### Post by sdennie on 2010-05-31
The .fonts.conf is probably the correct solution.  A few revs ago in Chrome, they did something unspeakable to the way fonts behave on linux.  I don't have the same problems you do but, .fonts.conf was the magic that was needed to fix it.

---

### Post by inverseroom on 2010-05-31
Bizarrely, .fonts.conf made things even weirder.  The simple version broke ALL the font rendering in all applications and on the desktop.  The more elaborate version made the fonts WITHIN Chrome look good, BUT all the fonts OUTSIDE Chrome were broken.

I may just throw in the towel and turn on hinting, against my will.  Chrome is just so speedy, I would hate to return to FF...

---

### Post by inverseroom on 2010-06-01
OK, now I have REALLY botched something.  I added a .fonts.conf, as I related above, and when it didn't work for me, I deleted it.  Now, NONE of the hinting and smoothing options in system>preferences>appearance have any effect.  Was there already a .fonts.conf in my home folder that I accidentally overwrote and did not replace?

---

### Post by lovinglinux on 2010-06-01
> **inverseroom said:**
> Was there already a .fonts.conf in my home folder that I accidentally overwrote and did not replace?

I don't think so. But I don't know what could cause this. I have been using .fonts.conf for a while and always worked for me.

---

### Post by Quake on 2010-06-01
If it's any help, I took a screenshot of how chrome looks on my computer and my fonts configuration.

Here's the .fonts.conf I use:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
```

---

### Post by inverseroom on 2010-06-03
Thanks---that is one of the ones I tried...

---

### Post by Quake on 2010-06-03
So, to no avail?

---

### Post by inverseroom on 2010-06-04
Sadly, no.  I can't get back any hinting/smoothing at all via prefs/appearance, either.  I musta broke something...Something tells me I will just deal with it until 10.10 and then upgrade with my fingers crossed.

---

### Post by inverseroom on 2010-06-07
So I finally cracked this problem in the strangest way.  first, I found a .fonts.conf that basically worked, then tweaked it a little...this is it:

```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

But hinting and smoothing still seemed to be completely broken on my desktop.  Only within applications did the .fonts.conf have any effect.

I basically gave up on that half of the problem, then went searching the internet for a particular font I wanted to use for something.  Found it, downloaded it to my desktop, opened it, and hit "install."

Bam!  Suddenly hinting took effect on the desktop.  It was as if installing a font woke up the appearance settings.  Dunno why this should have worked, but lo and behold.  So I am marking this solved.

---

