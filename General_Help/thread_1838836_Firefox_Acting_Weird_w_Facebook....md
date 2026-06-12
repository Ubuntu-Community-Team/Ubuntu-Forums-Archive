---
title: "Firefox Acting Weird w/ Facebook..."
date: 2011-09-04
forum: General Help
---

### Post by Valkyr333 on 2011-09-04
Hi, everyone...

My Firefox Browser is behaving strangely with the page structure of Facebook. Since no one else I know is having the problem I'm about to describe, and it started happening after Ubuntu's latest Firefox update, I can only assume that something about the latest Ubuntu version of the browser is somehow incompatible with Facebook's layout.

The problem: A Facebook page finishes loading completely, however, the lines that separate the "ads" bar normally on the right and the various options on the left seem to be pushed much farther towards the center, causing everything that would normally fit between those two bars to be pushed downwards drastically. Also, the options that normally show up on the left are on the right. I've included a screencap (personally identifiable information blurred via Gimp) in case my description is confusing.

I don't know what's going on with this one, but I figure that either someone here could tell me how to fix it, or at least bringing it to the mods' attention could benefit the community.

Any ideas?

Thanks, guys/girls. =)

---

### Post by zero2xiii on 2011-09-04
Hay, 

Thats strange. It has happened to me before aswell. But with an older version. Pressing ctrl + 0 fixed the issue (in other words, resetting the page zoom factor)

Hope it is as simple for you aswell.

Cherz

---

### Post by Valkyr333 on 2011-09-04
Hi,

Resetting the Zoom on the page seems to have no effect, neither does messing with it by zooming in or out. Thanks for writing anyways, though. =)

---

### Post by bodhi.zazen on 2011-09-09
Hard to know, could be an extension or a corruption in your profile.

Start firefox with a new profile and check it out.

```
firefox -P
```

---

### Post by Valkyr333 on 2011-09-09
@bodhi.zazen - That does fix it. Facebook looks normal under the conditions of a new Firefox profile. Where would you recommend to go from here, in terms of further diagnosing the exact source of the problem with my main profile?

*Edit - Thank you, by the way. I very much appreciate your help.

---

### Post by bodhi.zazen on 2011-09-09
> **Valkyr333 said:**
> @bodhi.zazen - That does fix it. Facebook looks normal under the conditions of a new Firefox profile. Where would you recommend to go from here, in terms of further diagnosing the exact source of the problem with my main profile?

*Edit - Thank you, by the way. I very much appreciate your help.

Take a look at your extensions, Noscript  ?

Disable them all, then enable them one at a time until you find the culprit.

If all else fails, back up your passwords / bookmarks and create a new profile.

---

### Post by Valkyr333 on 2011-09-09
Well, I feel silly...

I just went through the whole process of re-building my Firefox only to find out the problem was that I had told it "Minimum font size is 15," which was what made Facebook act that way.

On a brighter note, things are somehow looking sharper and more clear in Firefox, now. o.O

Thanks everyone. Choc this one up to a novice mistake, though. =/

::marks thread as solved::

---

