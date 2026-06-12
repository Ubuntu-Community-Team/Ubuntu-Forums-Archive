---
title: "PDF viewer with grab and drag left click functionality"
date: 2009-10-08
forum: General Help
---

### Post by Nimless on 2009-10-08
As topic says.

Is there a PDF viewer in linux with a grab and drag scrolling with left click,like Adobe on Windows??
I'm using a Dell Latitude tablet and would like to be able to scroll with finger...
Thanks

---

### Post by XCan on 2009-10-08
You could install Adobe Reader on Ubuntu as well. :)

---

### Post by Nimless on 2009-10-08
> **XCan said:**
> You could install Adobe Reader on Ubuntu as well. :)

Oh i didn't know...thanks for pointing that :P
I know it's proprietary but this seems the only solution so far :(

---

### Post by XCan on 2009-10-09
Yah, although I use evince plenty, I always print using Adobe due to some bad luck in Evince. I find the rendering more forgiving in Adobe as well for some vector graphics. But anyway, [http://ubuntuforums.org/showthread.php?t=1148872](http://ubuntuforums.org/showthread.php?t=1148872) if you wonder where to find the package.

---

### Post by naugtur on 2011-02-02
There obviously is (I bet it should state "are" but I settled with first found) a pdf viewer with drag option.

```
sudo apt-cache search pdf | grep view
```

gets you a list of what is avaliable.

I checked two packages and the second one was ```
epdfview
``` which is a simple viewer that looks like evince, but lets you drag the page around.
I might be looking for another one, because it displays one page at a time, which is not what we want... I have a dell L2100 with touchscreen too :)

---

