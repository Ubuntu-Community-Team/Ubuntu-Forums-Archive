---
title: "Strange font in the terminal?"
date: 2009-11-22
forum: General Help
---

### Post by josephellengar on 2009-11-22
I just upgraded to karmic, and for some reason the font in the terminal is very weird.  Letters have a seemingly random amount of space between them, and some even overlap.  I checked the character set and it is still in UTF8.  Can anybody think of any reason why this would be?

---

### Post by wilee-nilee on 2009-11-22
> **rossholley said:**
> I just upgraded to karmic, and for some reason the font in the terminal is very weird.  Letters have a seemingly random amount of space between them, and some even overlap.  I checked the character set and it is still in UTF8.  Can anybody think of any reason why this would be?

You can change the font type and size, give us a screen-shot.

---

### Post by josephellengar on 2009-11-22
> **wilee-nilee said:**
> You can change the font type and size, give us a screen-shot.

Thanks for getting back to me so fast.  Here's a screenshot

See, it's got really weird spacing and a little overlap (I don't know if you can see the rm near the end- that's an i on the end of that.  I couldn't remember what the character patterns were, but I did get an actual overlap earlier.  Is there a fixed-width font that I can use?  Thank you!

---

### Post by wilee-nilee on 2009-11-22
Here is one of mine using the purisa fonts bold. I found the stock fonts were kind of disconcerting.
[ATTACH]137247[/ATTACH]

---

### Post by josephellengar on 2009-11-22
> **wilee-nilee said:**
> Here is one of mine using the purisa fonts bold. I found the stock fonts were kind of disconcerting.
[ATTACH]137247[/ATTACH]

I don't think mine was a problem with the font.  I just tried typing in again with Sans font, and look at what I got.  See, the mi at the end is overlapped.  Not a great introduction to the koala :(

---

### Post by wilee-nilee on 2009-11-22
I'm not sure, I think you will have to go through the possibilities and see what works for you.

Personally, I just go with the flow, or find what works for me. ;) 

I am not a big CLI user so it works so thats all I need.

---

### Post by josephellengar on 2009-11-22
> **wilee-nilee said:**
> I'm not sure, I think you will have to go through the possibilities and see what works for you.

Personally, I just go with the flow, or find what works for me. ;) 

I am not a big CLI user so it works so thats all I need.

Oh well, thanks anyway.

---

### Post by josephellengar on 2009-11-23
Bump.  Any other suggestions?  The font is still all messed up.  Is there some package that I should un/reinstall

---

### Post by NickJ365 on 2009-12-20
I have just upgraded from 9.04 to 9.10 on a netbook and have noticed the same behaviour in Terminal.

I have the default font with UTF-8 encoding.

As an Ubuntu novice, I'm not particularly well-placed to help - just note the same problem. But if anyone needs further information or has a fix, please let me know! :)

---

### Post by josephellengar on 2009-12-20
> **NickJ365 said:**
> I have just upgraded from 9.04 to 9.10 on a netbook and have noticed the same behaviour in Terminal.

I have the default font with UTF-8 encoding.

As an Ubuntu novice, I'm not particularly well-placed to help - just note the same problem. But if anyone needs further information or has a fix, please let me know! :)

I've had it since I upgraded 9.04 to 9.10, but on my netbook, which had a clean 9.10 install, everything is normal.

---

### Post by nubalci on 2009-12-20
Use a monospaced font, like "DejaVu Sans mono". Terminal cannot display most fonts properly.

---

### Post by josephellengar on 2009-12-20
> **nubalci said:**
> Use a monospaced font, like "DejaVu Sans mono". Terminal cannot display most fonts properly.

Huh, I was using sans before and this seems to work a lot better.  Thanks!

---

### Post by falconindy on 2009-12-20
> **rossholley said:**
> Huh, I was using sans before and this seems to work a lot better.  Thanks!
Sans, and not sans mono. Mono is short for monospaced, which means that each character is the same width. A lower case 'i' takes up the same amount of horizontal space as an uppercase W.

Terminals aren't designed to be used with anything **but** monospaced fonts.

---

### Post by sheepz on 2010-03-03
> **falconindy said:**
> Sans, and not sans mono. Mono is short for monospaced, which means that each character is the same width. A lower case 'i' takes up the same amount of horizontal space as an uppercase W.

Terminals aren't designed to be used with anything **but** monospaced fonts.

Thanks :)

---

