---
title: "Inconsistent Font Rendering in Firefox"
date: 2010-09-17
forum: General Help
---

### Post by belize1334 on 2010-09-17
First off let me just say that this is my first thread here and I hope that I'm not in the wrong section. I've searched for info on this topic and while there's alot out there about firefox fonts not being "pretty", I wasn't able to find anything on this particular issue.

The problem I'm having is that the contrast ratio of text in firefox seems very inconsistent. 

For example: if I'm reading an article on NYtimes, from one paragraph to the next it looks like some sentences are in bold-face and others are not. If I refresh the page, it'll be different areas that are or aren't bf. Sometimes they even change (getting darker or lighter) as I'm sitting there reading. I tried to take a screenshot but unfortunately the text all becomes uniform as soon as I hit prt-scr so the image doesn't show the effect. 

Another example is viewing my personal favorite forum where threads that I haven't read are in bf as opposed to those I have read which are normal. The problem is that when I do a mouse-over of the bf threads the font rendering becomes more greyed out. It's still bold-face, just not as dark. 

A final example is in text-entry boxes. As I'm typing this right now the line I'm on looks normal but the paragraph above seems to go from regular to bold-face from one line to the next. The paragraph above that looks entirely bold-face...

It did occur to me that this could be a monitor issue or even a vid-card issue. But it's definitely not monitor because I can scroll the whole screen and the variation moves with the text... And it's not vid-card because I installed Chrome as a check and it doesn't have the same problem. None of the above symptoms carry over to that application.

So... any ideas about why Firefox can't make up it's mind about which characters should be rendered bold and which should not?

Thanks in advance...

---

### Post by kerry_s on 2010-09-17
conflicting add on's ?

---

### Post by belize1334 on 2010-09-17
I have no ad-ons. This is a brand new install. The only thing I've done is install msttfonts but that was in an attempt to solve the issue. It didn't help btw.

Edit: I was able to get a screen shot showing the effect. Notice the line in the original post which appears bold...

---

### Post by kerry_s on 2010-09-17
have you checked your monitor refesh rate is right?

---

### Post by soldier1st on 2010-09-17
did you try changing your ubuntu theme? also are you trying to view past 100% view?

---

### Post by belize1334 on 2010-09-17
According to the nVidia XServer settings tool it's set at 59.96 Hz. There's no associated option, just a value... but regardless, since I don't have the same issue using Chrome (or any other applications for that matter) I don't think it's hardware level. It seems like it's a Firefox thing.

---

### Post by kerry_s on 2010-09-17
> **belize1334 said:**
> According to the nVidia XServer settings tool it's set at 59.96 Hz. There's no associated option, just a value... but regardless, since I don't have the same issue using Chrome (or any other applications for that matter) I don't think it's hardware level. It seems like it's a Firefox thing.

what fonts do you have set in firefox?

---

### Post by belize1334 on 2010-09-18
I tried changing to Bilstream but it had no effect. I'm now back to defaults as seen in the first attachment. 

I've included another screen-shot. It's a little hard to see unless you zoom in but you'll notice that the very first clause of the first sentence under "Origin and Publication" is significantly lower contrast than the rest. This is a very understated example since the font becomes much more uniform as soon as I press prt-scr. Before taking the shot the relative difference in contrast is much more extreme and occurs more frequently throughout the text. It also occurs in different places everytime a page is refreshed and even changes when I scroll down and back up so that when sections of text goes off screen and back on the pattern of relative contrasts has shifted within the rerendered text.

---

### Post by kerry_s on 2010-09-18
lets try deleting the firefox settings, so it creates a fresh 1.


close firefox
in applications-> accessories-> terminal
run this-> **rm -rf ~/.mozilla**

---

### Post by belize1334 on 2010-09-20
Tried... no change.

---

### Post by belize1334 on 2010-09-21
Seems to be a nvidia driver problem or else a problem with my gefore 7800gt cards. If I disable SLI via 'nvidia-xconfig --sli=false' then the problem goes away completely. With sli set to auto then i get the problem I described. With sli set to afr or sfr then the colors are terrible AND I get the problem I described. Particularly split-frame seems to have good colors on the top half and bad on the bottom half. Perhaps the primary card is good but the secondary is shot...

Anyway, this is not a firefox issue so we can close the current discussion...

---

