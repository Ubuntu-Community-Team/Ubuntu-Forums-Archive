---
title: "How do i edit my source list using Gedit?"
date: 2011-03-20
forum: General Help
---

### Post by maddbaron on 2011-03-20
I need to switch the "lucid" parts in my ppa's to "maverick" in the format that gedit uses. I believe this will fix some of the software conflicts I am having.

Thanks in advance.

---

### Post by WorMzy on 2011-03-20
I don't understand the question.

You can edit system files with gedit by running
```
gksu gedit /path/to/config-file.conf
```

---

### Post by maddbaron on 2011-03-20
> **WorMzy said:**
> I don't understand the question.

You can edit system files with gedit by running
```
gksu gedit /path/to/config-file.conf
```

I upgraded from lucid to maverick, I am having glitches in terms of appearance that I didn't have in lucid and I am thinking it is because a majority of my ppa's still have lucid as the version.

It would be this:
```
gksu gedit /path/to/source-list.conf
```  ?

---

### Post by runeh76 on 2011-03-20
In maverick its:

```
gksu gedit /etc/apt/sources.list
```

---

### Post by maddbaron on 2011-03-20
> **runeh76 said:**
> In maverick its:

```
gksu gedit /etc/apt/sources.list
```

thanks

---

### Post by maddbaron on 2011-03-20
I was wrong, ppa's aren't sources... I want to be able to edit my ppa's in gedit? How can I do that?

---

### Post by Script Warlock on 2011-03-20
> **maddbaron said:**
> I was wrong, ppa's aren't sources... I want to be able to edit my ppa's in gedit? How can I do that?

gksu /usr/bin/software-properties-gtk

other software

---

### Post by maddbaron on 2011-03-20
thanks

---

