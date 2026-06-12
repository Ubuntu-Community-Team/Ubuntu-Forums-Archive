---
title: "Conky semi-transparent background-color?"
date: 2009-10-22
forum: General Help
---

### Post by hachel on 2009-10-22
Hi there,
first off: transparency is working for me

it's just that my wallpaper changes randomly every 15 minutes. And sometimes there is a wallpaper with a light and bright background, which makes conky unreadable.
So I was wondering if there were an option to make conky have a semi-transparent background. Or more like a shade, basically a black or grey or whatever color background with lower opacity so that you can still see the wallpaper, but the text is given more contrast.

---

### Post by Giblet5 on 2009-10-22
Conky can't do semi-transparent backgrounds without the use of compositing (eg, Compiz).

There are two ways to accomplish "variable transparency, or "opacity"): RGBA (Red, Blue, Green, Alpha) color support, or compositing. Conky doesn't do either one so you have to do that from Compiz, KDE4, Looking Glass, Gnome Shell, or some other compositing window manager.

Here's a [discussion]("http://ubuntuforums.org/showthread.php?t=1154948") about it using Compiz.

---

### Post by proxess on 2009-10-22
Maybe it can be done now with lua scripts?

---

### Post by VCoolio on 2009-10-22
> **proxess said:**
> Maybe it can be done now with lua scripts?

Yes it can: [look here]("http://conky.linux-hardcore.com/?page_id=3002").
This requires conky 1.7.1 or higher with lua support.

---

### Post by proxess on 2009-10-22
> **VCoolio said:**
> Yes it can: [look here]("http://conky.linux-hardcore.com/?page_id=3002").
This requires conky 1.7.1 or higher with lua support.

I knew I'd seen this somewhere.

---

### Post by hachel on 2009-10-22
cool, that works, cheers

---

### Post by bluepicaso on 2010-08-27
> **hachel said:**
> cool, that works, cheers

NOt for me... any help please

---

### Post by narayan.g8 on 2010-11-04
I had the same problem and found the solution here 

[https://bbs.archlinux.org/viewtopic.php?id=105994](https://bbs.archlinux.org/viewtopic.php?id=105994)

Requires conky >=1.7, compiled with lua(Cairo support). 

Finally glad that I got off my todo list..

---

