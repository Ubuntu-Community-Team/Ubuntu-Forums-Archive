---
title: "Wanting conky to remain visible after terminal is closed."
date: 2010-03-24
forum: General Help
---

### Post by dluzius on 2010-03-24
[B][SIZE="4"]I finally have my conky source file just the way I want it, at least for now. When I want to display conky, I open terminal and simply type in conky. Then I can see the actual conky display. But when I close terminal, conky disappears. How can I make it remain visible??
    Dave[/SIZE][/B][SIZE="4"][/SIZE]

---

### Post by darolu on 2010-03-24
```
$ conky &
```

---

### Post by dluzius on 2010-03-24
[B]Thank you, it works.
Can I ask where you got this info, I mean a book, online, or what.
    Dave**[B][COLOR="Red"][/COLOR]**[/B][/B]

---

### Post by darolu on 2010-03-24
Uhmmm about the "&"? I don't really remember, it's kinda basic, anyways most of my (as little as it is) linux knowledge comes from reading manuals, anytime I have a problem with a specific tool or application I simply read the manual (most tools and apps have a manual you can read via "man <program>").

As for general Linux knowledge (like using the terminal), I learn a lot from online distros documentation, the one I learned the most from was Gentoo documentation, I still think the [Gentoo handbook]("http://www.gentoo.org/doc/en/handbook/") is the best online documentation out there. This one is also good: [http://tldp.org/guides.html](http://tldp.org/guides.html) And this one is good too (manuals): [http://linuxmanpages.com/](http://linuxmanpages.com/)

I have also learned a lot from books, Mark G. Sobell wrote a Ubuntu specific one: [http://www.informit.com/store/product.aspx?isbn=013236039X](http://www.informit.com/store/product.aspx?isbn=013236039X)

---

### Post by pbrane on 2010-03-24
```

conky -d

```
will daemonize conky. May be better than running in the background.
*man conky* will show you the options.

---

