---
title: "Karmic Updates"
date: 2009-12-07
forum: General Help
---

### Post by Tumpster on 2009-12-07
So I've since done a fresh install of Karmic and noticed that I was never getting alerts to updates available for installation. I ran update manager by myself and saw a slew of em available which I selected and installed. Is this normal for the updates to never pop up in the upper toolbar as I'm used to with previous distributions or is it just a glitch I was having?

---

### Post by Strongman332 on 2009-12-07
gconftool -s --type bool /apps/update-notifier/auto_launch false

this will fix your problem

found in

[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

---

### Post by Tumpster on 2009-12-07
> **Strongman332 said:**
> gconftool -s --type bool /apps/update-notifier/auto_launch false

this will fix your problem

found in

[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

So just pop this into terminal and I'm set correct?

---

