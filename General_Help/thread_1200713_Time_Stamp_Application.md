---
title: "Time Stamp Application?"
date: 2009-06-30
forum: General Help
---

### Post by BrandonBan6 on 2009-06-30
Hey All,

I was having troubles searching for this, so I thought I would post specifically what I was looking for. I am looking for a program like shortkeys or hotkeys in windows, that allows you to "timestamp" or auto insert via keyboard short cut the current time and date. Any ideas? 

thanks

---

### Post by BrandonBan6 on 2009-06-30
Getting a little closer,

Instead of an application, I thought I could create a keyboard shortcut,

Though I need a way to call /bin/bash/date and paste the results wherever my cursor happens to be, i.e. gedit, email, tomboy notes, etc.

So for example, I'm typing away in an email, and I then execute a keyboard shortcut, which in turn inserts the date function into the email. 

I know little about scripting, any thoughts? 

thank you for your time.

---

### Post by BrandonBan6 on 2009-06-30
Oooohhh getting closer....

```

sudo apt-get install xclip

```
```
date|xclip
```
middle click with the mouse button to paste it into application, it would be nice to join the two steps with a keyboard short though.

where keyboard+shortcut = date|xclip && paste at cursor location.

---

