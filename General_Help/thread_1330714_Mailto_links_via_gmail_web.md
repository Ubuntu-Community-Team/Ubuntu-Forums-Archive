---
title: "Mailto links via gmail web"
date: 2009-11-18
forum: General Help
---

### Post by avacomputers on 2009-11-18
Is it possible to click mail to links and have my gmail web service open up.

---

### Post by Jim_in_Germany on 2009-11-19
In Firefox it is.
In Firefox go to Edit -> Preferences and a menu should open up.
Select the tab 'Applications' and scroll down to the entry 'mailto'.
Click on whatever action is defined and then you can select 'Gmail' from the drop down list.
Press 'close' and that's it.

---

### Post by VCoolio on 2009-11-19
Enter this as command for default email client:
```
gnome-open https://mail.google.com/mail/?extsrc=mailto&url=%s
```

Gnome-open will use your default ubuntu browser; use xdg-open to use your default x-www-browser.

Found [here]("http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/") by the way, along with other options. Read the comments there, they are more interesting than the blog post itself.

---

### Post by artshark on 2009-12-22
> **VCoolio said:**
> Enter this as command for default email client:
```
gnome-open https://mail.google.com/mail/?extsrc=mailto&url=%s
```

Gnome-open will use your default ubuntu browser; use xdg-open to use your default x-www-browser.

Found [here]("http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/") by the way, along with other options. Read the comments there, they are more interesting than the blog post itself.

works well, thanks!

---

