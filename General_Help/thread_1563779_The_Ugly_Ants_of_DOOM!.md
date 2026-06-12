---
title: "The Ugly Ants of DOOM!"
date: 2010-08-29
forum: General Help
---

### Post by Joseph Schwenker on 2010-08-29
If you have ever used Photoshop, I'm sure that you are familiar with the marching ants that mark a selection.  Well, I'm sure that you also are familiar with the non-marching ants that mark an ugly interface; they're all over Ubuntu.  They're on the desktop.  They're in our favorite applications.  And they're ugly as hell.  I always find myself clicking on an empty area of the desktop after deleting or unmounting something, just to get rid of the ugly ants of doom.  Is anyone else annoyed by this?  Does anyone have a fix?  So far, I've found that Nautilus, Gwibber, and Miro are affected, though there are probably many more applications, especially ones that load web pages or HTML.

---

### Post by gvernold on 2010-08-29
Not sure which ants you mean.... I once had the lines left behind by moved/deleted icons on 10.04 the first week it was launched but my ATI drivers were all messed up. Not had them since I sorted it out. Can you provide a little more specific description or a link to a screenshot so we can take a look?

---

### Post by Joseph Schwenker on 2010-08-29
> **gvernold said:**
> Not sure which ants you mean.... I once had the lines left behind by moved/deleted icons on 10.04 the first week it was launched but my ATI drivers were all messed up. Not had them since I sorted it out. Can you provide a little more specific description or a link to a screenshot so we can take a look?

They're attached to my original post.

---

### Post by Joseph Schwenker on 2010-08-31
Open up Firefox and drag a link, then let go.  See the ugly border?  Create a new folder on your desktop, then delete it.  See the ugly border around one of your formerly beautiful Faenza icons?

---

### Post by Joseph Schwenker on 2010-09-12
bump

---

### Post by jwbrase on 2010-09-12
Well, I don't know exactly how I got it that way, but the border I get in such situations is solid, rather than "ants". So there is hope, you can, somehow, get rid of the ants. I just don't remember how I did it because I wasn't really trying to.

---

### Post by Joseph Schwenker on 2010-09-12
> **jwbrase said:**
> Well, I don't know exactly how I got it that way, but the border I get in such situations is solid, rather than "ants". So there is hope, you can, somehow, get rid of the ants. I just don't remember how I did it because I wasn't really trying to.

Actually, I was aiming for a way to not have any kind of ants or selection whatsoever.  There should only be an indication of any kind of selection when you select something.  When I eject a drive, I selected nothing, and yet I get the ants on a random object.

---

### Post by WorMzy on 2010-09-12
You can get rid of them on webpages by adding the following CSS code:

```
a:focus {
	outline: 0px;
}
```

If you use Firefox, you can add that code to any webpage with greasemonkey, using ```
GM_addStyle("a:focus { outline: 0px; }");
```

As for getting rid of it on your desktop, I can't help with that.

---

### Post by absolutezero1287 on 2010-09-12
> **Joseph Schwenker said:**
> If you have ever used Photoshop, I'm sure that you are familiar with the marching ants that mark a selection.  Well, I'm sure that you also are familiar with the non-marching ants that mark an ugly interface; they're all over Ubuntu.  They're on the desktop.  They're in our favorite applications.  And they're ugly as hell.  I always find myself clicking on an empty area of the desktop after deleting or unmounting something, just to get rid of the ugly ants of doom.  Is anyone else annoyed by this?  Does anyone have a fix?  So far, I've found that Nautilus, Gwibber, and Miro are affected, though there are probably many more applications, especially ones that load web pages or HTML.

Don't take this the wrong way but don't you think you're being a tad anal? :roll: All the "ants of doom" do is simply remind you that you clicked on something. There might be a way to change it within Ubuntu itself but I don't see how.

---

### Post by Joseph Schwenker on 2010-09-12
> **absolutezero1287 said:**
> Don't take this the wrong way but don't you think you're being a tad anal? :roll: All the "ants of doom" do is simply remind you that you clicked on something. There might be a way to change it within Ubuntu itself but I don't see how.

Actually, it's not, as I stated in my original post.  When I delete a folder or eject a drive, I clicked on nothing, and yet some random folder is always uglified.  If the ants are meant to remind me that I clicked on something, then why are they so ugly?!
Why do I even need to know that I clicked on something, anyway?  This behavior is virtually non-existent in Chrome.

---

### Post by pbrane on 2010-09-12
These artifacts don't happen to me. I use Ubuntu 10.04 and I have an nVidia graphics card. I tried your test, creating a folder on the desktop, deleted it. No selection artifacts. Maybe this has to do with your graphics card or perhaps its your theme?

Actually the selection 'ants' are to indicate an active object too, not just what was selected or clicked.

---

### Post by Joseph Schwenker on 2010-09-12
> **pbrane said:**
> These artifacts don't happen to me. I use Ubuntu 10.04 and I have an nVidia graphics card. I tried your test, creating a folder on the desktop, deleted it. No selection artifacts. Maybe this has to do with your graphics card or perhaps its your theme?

I also have Ubuntu 10.04 and an nVidia graphics card.  I'm using elementary-monochrome.

---

### Post by pbrane on 2010-09-12
I don't have that theme to test. Have you tried other themes?

---

### Post by Joseph Schwenker on 2010-09-12
> **pbrane said:**
> I don't have that theme to test. Have you tried other themes?

o_O

[Elementary]("https://launchpad.net/~elementaryart/+archive/ppa") is the best theme EVAR!

I got the same result with Ubuntu's default theme, Ambiance, I think.

---

### Post by Joseph Schwenker on 2010-10-04
bump

---

