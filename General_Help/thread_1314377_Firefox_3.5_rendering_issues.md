---
title: "Firefox 3.5 rendering issues"
date: 2009-11-04
forum: General Help
---

### Post by Grimnir512 on 2009-11-04
So, I've noticed a problem with Firefox that I didn't get when I was running Jaunty.

Firefox seems to be rendering colours all wrong. For example, when rendering [this site](http://support.proboards.com/index.cgi?) where I first noticed the problem Firefox is rendering the green all wrong. It renders the green tables to the left and middle-right as BAE4AA, where the source defines [and Chromium renders] it as C6DBAF. I have tested these colours using the colour picker in gcolor2.

Screenshots of what I see:

Firefox:
[img]http://img2.pict.com/7e/af/38/1913708/0/fxrender.png[/img]

Chromium:
[img]http://img2.pict.com/cd/bd/d5/1913711/0/chromerender.png[/img]

Have I managed to turn on some sort of accessibility mode or is there some option where I can change this? Firefox definitely rendered colours correctly in Jaunty so I figure this is a change in Karmic?

Thoughts/suggestions?

---

### Post by Grimnir512 on 2009-11-04
Ok, I actually don't know if there's a bumping rule or no, but I can't find one. Correct me if there is one :)

Anywho, this has dropped down like 6 pages so bump :)

Also, I probably should mention that I run Openbox as my window manager, if that helps.

---

### Post by khelben1979 on 2009-11-04
Are you using the latest stable version of [Firefox]("http://en.wikipedia.org/wiki/Mozilla_firefox") (3.5.4)?

---

### Post by Grimnir512 on 2009-11-04
> **khelben1979 said:**
> Are you using the latest stable version of [Firefox]("http://en.wikipedia.org/wiki/Mozilla_firefox") (3.5.4)?

I am. Installed by default directly from the repositories :)

---

### Post by khelben1979 on 2009-11-04
I think it's okay to report this as a bug to the Mozilla developers.

---

### Post by Grimnir512 on 2009-11-04
> **khelben1979 said:**
> I think it's okay to report this as a bug to the Mozilla developers.

Ok, I shall do that :) I didn't think it was an Ubuntu problem, but I wasn't sure.

---

### Post by Grimnir512 on 2009-11-18
I just thought I should share this as I found a solution:

Setting gfx.color_management.mode to 0 fixed my problem. I had it set at 1 somehow [perhaps something to do with merging Firefox3 and Firefox3.5 settings at upgrade to Karmic] and colours were displaying funny.

I hope this helps others who may have this problem :)

Don't know if I'm going to switch back to Firefox, though. I've been using Chromium [daily] and it's incredibly stable now. I'm quite enamoured with the thing :)

---

