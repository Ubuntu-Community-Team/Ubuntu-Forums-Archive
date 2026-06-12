---
title: "Keyboard typing loses focus"
date: 2011-10-17
forum: General Help
---

### Post by rold50 on 2011-10-17
Hi All,

Ever since I upgraded to 11.10, there are times that I can't type to the active application until I alt-tab out and alt-tab back to the program.

This happens to me in Chrome and Eclipse.


Any ideas what's causing this?

---

### Post by 11jmb on 2011-10-17
The only thing I can think of: 

go to System/Preferences/Windows and tell me if "Select windows when the mouse moves over them" is selected

---

### Post by cajuuh on 2011-10-17
does ubuntu 11.10 have a 'Windows' preferences?

---

### Post by 11jmb on 2011-10-17
> **cajuuh said:**
> does ubuntu 11.10 have a 'Windows' preferences?

Good point! I run 10.04 as my main desktop and glazed right over that detail. This should be the unity-style answer:

[http://askubuntu.com/questions/64605/how-do-i-set-focus-follows-mouse](http://askubuntu.com/questions/64605/how-do-i-set-focus-follows-mouse)

---

### Post by rold50 on 2011-10-17
Hi,

I tried seeting the focus mode to mouse but it still doesn't work.


Any other ideas?


Thanks!

---

### Post by rold50 on 2011-10-24
I actually figured out that SCIM was causing this problem. I set im-switch to none and it fixed it.

---

