---
title: "Missing icons in Evolution"
date: 2009-11-13
forum: General Help
---

### Post by dummiebeginner on 2009-11-13
Hi. The icons of Evolution are missing. I only see red crosses instead.

By googling I have found this guy who solved it, but it doesn't work for me.

He uses Gentoo and maybe the language is different. I am using Karmic and I am a beginner.

[http://markmail.org/message/2eufbrim2sixz56s#query:missing%20icons%20evolution%20gnome+page:1+mid:3k3zgjmozeqlhtsx+state:results](http://markmail.org/message/2eufbrim2sixz56s#query:missing%20icons%20evolution%20gnome+page:1+mid:3k3zgjmozeqlhtsx+state:results)

He says:

[I]"OK folks, I have solved the missing icon question. It may be a Gentoo problem so if the Gentoo Evolution (or Gnome) Package maintainer reads this - here's the solution as discovered in the Gentoo forum at [http://forums.gentoo.org/viewtopic-p-3348839.html#3348839](http://forums.gentoo.org/viewtopic-p-3348839.html#3348839)

The icons in /usr/share/icons were not readable by anyone but root. So, as root I simply executed "chmod -R 0775 /usr/share/icons" and that did the trick.

Thanks all, I hope this helps another Gentoo user."[/I]

Can somebody help?

Thanks.

---

### Post by emigrant on 2009-11-16
what are the icons you are referring to?

---

### Post by dummiebeginner on 2009-11-16
Most of the icons of the program were missing. I solved by reinstalling the Gnome icons that I had accidentally deleted when deleting icons that I was not using from the main icons Ubuntu folder.

Thanks anyway.

---

### Post by emigrant on 2009-11-16
happy you solved it.
by the way, i suggest you to make this thread [SOLVED], by going to **thread tools**.
:)

---

