---
title: "Buttons"
date: 2010-05-01
forum: General Help
---

### Post by astevens54 on 2010-05-01
What is going on with the buttons on the menu bar, open close, and maximize? They are on the wrong side. Is there a plan to fix this?

---

### Post by luigi_mb on 2010-05-01
> **astevens54 said:**
> What is going on with the buttons on the menu bar, open close, and maximize? They are on the wrong side. Is there a plan to fix this?

They are intended to be there. Search these forums for a 'fix'--if you really want to put them back in the old location. 

/luigi

---

### Post by 73ckn797 on 2010-05-01
It is how it is in Lucid.

Many have posted about  how to switch back to the old, right side, button setup. You could use System/Preferences/Appearance and monkey with theme customization or open terminal and enter ```
gconf-editor
``` Go to apps/metacity/general and change the button layout to ```
menu:minimize,maximize,close
``` You can change the order of the bottons also.

There is another thread ([http://ubuntuforums.org/showthread.php?p=9212824#post9212824](http://ubuntuforums.org/showthread.php?p=9212824#post9212824)) about how this is not the desired way of doing what you are wanting. My first suggestion is that way but I do not have the details and personally feel the second way is easy and works. The comment in that other thread states the "gconf-editor" way is bad. I have not seen any issues with doing that way.

---

### Post by astevens54 on 2010-05-01
Odd, it was announced as a bug on a couple sites I came across...

---

### Post by WorMzy on 2010-05-01
Nope, it's deliberate. Search on google for "Mark Shuttleworth buttons" if you want to know more.

---

### Post by astevens54 on 2010-05-01
Well if it was deliberate, it was easy to fix. I went to "Appearance Preferences" and selected "Themes" "Customize" and reselected the theme I had. That doesn't sound like something deliberate considering the buttons were on the right side of the theme in customize??? But you are right I did the search and at least that's his story. Either way, it's fixed. I fail to see why you would deliberately move the buttons when in MOST OS' they are on the right side. Oh well, I guess you cannot complain about a free OS and I'd really like to see Linux succeed. I have installed Ubuntu on several friends computers that didn't have a legit copy of Windows. They liked it.

---

