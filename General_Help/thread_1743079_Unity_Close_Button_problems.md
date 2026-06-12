---
title: "Unity Close Button problems"
date: 2011-04-29
forum: General Help
---

### Post by alphageek89 on 2011-04-29
Some applications minimise to the top panel when clicking the close button-this was in gnome.

Now when I click the close button the application is still running but in the unity bar on the left hand side it is gone ? How do I solve this ?

---

### Post by sikander3786 on 2011-04-29
Which applications are you talking about specifically? I don't think any of the applications minimize to top panel at all.

---

### Post by alphageek89 on 2011-04-29
XChat and Transmission both go to the top when closed . In Unity i just can't open it again .

---

### Post by sikander3786 on 2011-04-29
You need to enable the system tray for that. Please follow the link below and see the section named "Install dconf-editor to tweak some more settings".

[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

---

### Post by alphageek89 on 2011-04-29
> **sikander3786 said:**
> You need to enable the system tray for that. Please follow the link below and see the section named "Install dconf-editor to tweak some more settings".

[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)


This seems to be the solution but when when I press alt+f2 and type 'dconf-editor' nothing happens.

I have installed it .

Also on terminal:
```

varun@varun:~$ dconf-tools
dconf-tools: command not found

```

What am I doing wrong ?

Just realised my mistake. I was tying dconf-tools instead of dconf-editor. Will let you know if it solves my problem

---

### Post by sikander3786 on 2011-04-29
Try

```
dconf-editor
```

I think it is the wrong command posted there. I'll update it :-)

---

### Post by alphageek89 on 2011-04-29
> **sikander3786 said:**
> Try

```
dconf-editor
```

I think it is the wrong command posted there. I'll update it :-)

This works :D

But now it's there on the system tray permanently. Even when the application is open !

---

### Post by sikander3786 on 2011-04-29
> **alphageek89 said:**
> This works :D

But now it's there on the system tray permanently. Even when the application is open !
I think it used to be same in Lucid as well. The icon sits there even if Transmission is open or minimized to tray. But there is not much we can do about this :-)

---

