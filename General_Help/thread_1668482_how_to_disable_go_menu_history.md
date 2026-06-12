---
title: "how to disable go menu history"
date: 2011-01-16
forum: General Help
---

### Post by jdbausch on 2011-01-16
I never noticed the go menu having history before 10.10 - so I'm not sure when that got introduced.

but since I've noticed it, it is now driving me crazy!

Certainly not a "real" problem, but I want this history turned off, and I can't figure out how to do it. I've been searching the web and forums, no luck there either.


Just to be clear, I'm not talking about "recent documents" - I use that all the time, and know how to disable that if I wanted.


Thanks in advance to anyone who can help!

---

### Post by jdbausch on 2011-01-24
Just thought I'd bump this, just in case.

---

### Post by revilodraw on 2011-04-15
MASSIVE BUMP.

I've been using Ubuntu for 6 years and have never had this problem. 

I would like to bet that the greater majority of Ubuntu users would NOT want the go menu, or any other menu, to list their previously accessed folders.

---

### Post by jdbausch on 2011-05-08
found the answer here:

[http://mikebeach.org/2011/05/disabling-the-gnome-nautilus-navigation-history/]("http://mikebeach.org/2011/05/disabling-the-gnome-nautilus-navigation-history/")


```
sudo gedit /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
```


then remove:

```
<menuitem name="Clear History" action="Clear History"/>
<separator/>
<placeholder name="History Placeholder"/>
```

---

