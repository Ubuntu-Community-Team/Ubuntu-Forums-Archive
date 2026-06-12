---
title: "Google Earth for Linux: Weird Stupid Question"
date: 2009-12-15
forum: General Help
---

### Post by supermelon928 on 2009-12-15
I don't know what's wrong with me tonight.

I was led to believe by _[this page]("http://packages.ubuntu.com/jaunty/googleearth-package")_ that there's a Google Earth for ubuntu.

So, I told Terminal to install Googleearth-package, and it replied to me with this:

> [FONT="Courier New"]googleearth-package is already the newest version.[/FONT]

:-k

Okay, so I have no memory of doing it but apparently I've been through this before.

I can't seem to locate Googleearth-package anywhere on my computer. Anybody know how I might handle this situation?

---

### Post by 3rdalbum on 2009-12-15
```
googleearth
```

If that doesn't work, then you'll need to enable Medibuntu and install the googleearth package.

---

### Post by audiomick on 2009-12-15
I have google earth on mine (9.10) and it works well. If it is installed, it should be in applications> internet.

If I remember rightly, it comes from Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I just checked. It is there.

Add the repository to synaptic package manager according to the guide. Don't forget the key.

Search "googleearth" in the synaptic package manager.

Select and install.

---

### Post by supermelon928 on 2009-12-17
> **3rdalbum said:**
> ```
googleearth
```

If that doesn't work, then you'll need to enable Medibuntu and install the googleearth package.

> **audiomick said:**
> 
If I remember rightly, it comes from Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I just checked. It is there.

Add the repository to synaptic package manager according to the guide. Don't forget the key.

Search "googleearth" in the synaptic package manager.

Select and install.

Thanks :) I'll try it when I get home.

---

### Post by dcstar on 2009-12-17
> **supermelon928 said:**
> I don't know what's wrong with me tonight.

I was led to believe by _[this page]("http://packages.ubuntu.com/jaunty/googleearth-package")_ that there's a Google Earth for ubuntu.

So, I told Terminal to install Googleearth-package, and it replied to me with this:



:-k

Okay, so I have no memory of doing it but apparently I've been through this before.

I can't seem to locate Googleearth-package anywhere on my computer. Anybody know how I might handle this situation?

```
man make-googleearth-package
```
Follow the instructions.

---

