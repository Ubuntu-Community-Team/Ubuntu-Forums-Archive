---
title: "Time zone calculation bug???"
date: 2010-03-20
forum: General Help
---

### Post by vi1985 on 2010-03-20
I'm somewhat reluctant to be posting this, as it smells like one of those things that are too simple to have gone wrong - especially in such a large community of users and developers.

In any case, my desktop clock is wrong (it's ahead by 1 hour). We have shifted to daylight savings time a few days ago, and frankly I hadn't noticed the problem until now, so presumably the time was fine beforehand (either the clock broke just now, or else it broke when the time was shifted and I hadn't noticed).

I'm attaching a screenshot with all the relevant info in it... it's pretty self-explanatory.

Any clue as to what the issue may be? Is this a bug, or my own personal fail? :)

Thanks,
Vic.

---

### Post by gmargo on 2010-03-20
I think you're using the wrong tool.  Try setting the time zone through the System -> Administration -> Time and date menu.  Click on the lock symbol to get the password prompt.  Then set the timezone there to America/Toronto. (Alternatively, if you are on an old system, tzdata may not contain the latest DST changes - what release are you using?)

---

### Post by vi1985 on 2010-03-20
> **gmargo said:**
> That is controlled by the **tzdata** package.  So the question is: is your tzdata package up to date?  You don't say what release you're using.

The package version is 2010e-0ubuntu0.9.10 for both tzdata and tzdata-java. They seem to be the latest versions out there.

---

### Post by gmargo on 2010-03-21
Looks like you caught the original version of my post, see the edited one above about the System -> Administration -> Time and date menu.

---

### Post by gmargo on 2010-03-21
I've been confused about the Locations.... 

I added two locations to that time menu, Toronto and San Francisco, and their times show up correctly.  See the screenshot.  My times look right (This is on 9.10 Karmic).  But I sadly have no explanation for yours.

---

### Post by vi1985 on 2010-03-22
> **gmargo said:**
> Looks like you caught the original version of my post, see the edited one above about the System -> Administration -> Time and date menu.

Hey, thanks, this actually helped. Apparently I was on 'manual' mode, and so I switched it to being synchronized with a few time-keeping servers, which seemed to do the trick.

Thanks again for your time and help!

Vi.

---

### Post by lisati on 2010-03-22
<off-topic aside>
This thread prompted me to check the time on my laptop and on my server. After installing ntp modules, the time on my server changed and Dovecot complained:
> Fatal: Time just moved backwards by 6 seconds. This might cause a lot of problems, so I'll just kill myself now. [http://wiki.dovecot.org/TimeMovedBackwards](http://wiki.dovecot.org/TimeMovedBackwards)
:D 
(Come to think of it, I think this has cropped up in the forums before.....)
</off-topic aside>

---

