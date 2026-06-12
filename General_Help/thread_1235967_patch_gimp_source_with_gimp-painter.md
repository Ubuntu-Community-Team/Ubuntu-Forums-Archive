---
title: "patch gimp source with gimp-painter?"
date: 2009-08-09
forum: General Help
---

### Post by Daedal on 2009-08-09
so I've been trying to patch the gimp source with the gimp painter patch found here [HTTP://sourceforge.jp/projects/gimp-painter/releases/](HTTP://sourceforge.jp/projects/gimp-painter/releases/)
i got gimp-painter--20090715.diff as well as the gimp 2.6.6 source from gimp.org 

i uninstalled my previous gimp install, opened a terminal and got the gimp dependencies 

i unpack the gimp source then moved the .diff file into the gimp folder to make things a bit easier

so i go to the gimp source folder in the terminal and type patch -p0 < gimp-painter--20090715.diff

I've never actually patched anything before so I'm not sure but it seems odd that it didn't say anything at all after that it just gave me another prompt just the same as if i had hit enter without even typing anything.

even though i thought that was a bit odd i continued on to the whole ./configure make and make install only to find out once it had all finished that it seems that gimp didn't get patched because the tools the patch should have added weren't there.

I'm wondering if i did anything wrong in that or if i missed something or what. I'm still pretty much a noob at doing most of this stuff even though I've been using ubuntu for over a year now. most of what i do has been made simple with a GUI which is great for starting out but not so great in that it really slows down the rate you learn how to do things like this if you learn them at all.

any help that anyone could give me in teaching me how to get gimp 2.6.6 patched with gimp-painter would be GREATLY appreciated. I'm pretty much a noob at this.  i can navigate folders through the terminal pretty easily but as far as most commands go i might as well have just started. so I'll probably need some detailed instructions.

also, not sure if it really matters but i'm using 9.04

---

### Post by Daedal on 2009-08-09
nevermind... for some reason the patch command just wasn't working before.  it is now and it patched without any problems.
thanks to the people who bothered to look at my problem even if none of you had anything to say. =P

---

### Post by hanson79 on 2011-04-05
> **Daedal said:**
> nevermind... for some reason the patch command just wasn't working before.  it is now and it patched without any problems.
thanks to the people who bothered to look at my problem even if none of you had anything to say. =P

I couldn't make the patch command work like you did, but when I changing to -p1 instead of -p0, it works. In my case I have the patch in the parent directory, but that shouldn't matter. Successfully patched gimp 2.6.11: 
```
patch -p1 < ../gimp-painter--20100627.diff
```

---

