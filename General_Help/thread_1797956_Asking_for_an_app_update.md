---
title: "Asking for an app update"
date: 2011-07-05
forum: General Help
---

### Post by dargaud on 2011-07-05
Hello all,
is there a specific place/way to ask for a specific repository application to be updated ?

Case in point, I tried to use the GPS application '[viking]("http://sourceforge.net/projects/viking/")' which is part of the Ubuntu repository, but it's a very old beta version and kept crashing. I downloaded the latest tgz off sourceforge and after installing half a ton of additional libraries, managed to install it. It works fine now, but maybe the version from the repository needs to be updated...?

Is it something I can do _easily_ ?

---

### Post by snowpine on 2011-07-05
You did it the right way. :) Default applications provided by Ubuntu are just the starting point. Because it is "open source" you are then free to customize and update your system in a million different ways!

Applications aren't generally upgraded to newer versions once an Ubuntu has been released. For example 11.04 will always have applications from April 2011; if a newer version of an comes out in May, it goes into the 11.10 release, not retroactive to 11.04. :)

What you are describing falls under the category of "backports" and I think the backports team could always use extra help, if you want to get involved: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by dargaud on 2011-07-06
That makes sense, but still, I wonder if 'they' used the lastest source when building 11.04. In the case of Viking, that version is several years old and severely crash-prone.

---

### Post by grahammechanical on 2011-07-06
This is why the Software Centre was created with its feature of reviewing software. It puts pressure on program developers to reach a higher standard. At some point a program such as this will be dropped from the Software Centre and the developers will only have themselves to blame.

Think of all the work that you had to do to get a crash proof version of this program working. Is it the responsibility of Canonical to do all that work for every program that someone develops? Should not the developers do the work to make their programs easy to install and crash proof?

Regards.

---

### Post by snowpine on 2011-07-06
> **dargaud said:**
> That makes sense, but still, I wonder if 'they' used the lastest source when building 11.04. In the case of Viking, that version is several years old and severely crash-prone.

Ubuntu typically uses whichever version is in Debian, which is not always the latest. :)

---

