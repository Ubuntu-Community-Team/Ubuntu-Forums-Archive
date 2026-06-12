---
title: "old versions of source packages"
date: 2012-08-01
forum: General Help
---

### Post by plugwash on 2012-08-01
Does ubuntu have a service like snapshot.debian.org from which old versions of source packages can be downloaded?

---

### Post by mc4man on 2012-08-01
launchpad keeps most source packages, not sure if all?

If you know the source name exactly then something like this will show all current ubuntu releases - ```
https://launchpad.net/ubuntu/+source/[COLOR="Blue"]add-source-here[/COLOR]
```
Ex. nautilus
[https://launchpad.net/ubuntu/+source/nautilus](https://launchpad.net/ubuntu/+source/nautilus)

For a specific release & most? end of life releases like this - 
```
https://launchpad.net/ubuntu/[COLOR="Blue"]add-release-here[/COLOR]/+source/nautilus
```

Ex. - precise/nautilus
[https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)[COLOR="Blue"]precise[/COLOR]/+source/nautilus
Ex., EOL - karmic/nautilus
[https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)[COLOR="Blue"]karmic[/COLOR]/+source/nautilus

Otherwise I get 'in' the neighborhood with a google search like - 
_app-name-here source ubuntu _& then look for launchpad results, ect. 

A lot of pages will have a link "All versions of whatever source in ubuntu" and some pages links to lp:source-name if looking for the upstream where you can parse back commits

---

### Post by plugwash on 2012-08-16
> **mc4man said:**
> 
A lot of pages will have a link "All versions of whatever source in ubuntu" 
I don't see any link with that name.

I've found the answer elsewhere though. On the launchpad page for a package there is a link "view full publishing history". if you follow that it takes you to a page with a list of actions each with an associated version. From there you can follow a link to the page about that version you want and from there you get a download link for it.

---

### Post by mc4man on 2012-08-16
> **plugwash said:**
> I don't see any link with that name.


It's on any particular releases source page, in the end pretty much the same deal.
Example in screen, was on 12.04 source for udisks, link goes to 'all' non 'end of life' releases

---

