---
title: "List of sources could not be read"
date: 2011-05-14
forum: General Help
---

### Post by Kruger2147 on 2011-05-14
I just installed natty, I really like it, but every time I try to install an Indicator Applet, I get "E: The list of sources could not be read."

[IMG]http://i.imgur.com/jeNIh.png[/IMG]

Edit: I installed by running the upgrade from Maverick.

---

### Post by wojox on 2011-05-14
What does this return:

```
cat /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
```

---

### Post by Kruger2147 on 2011-05-14
[IMG]http://i.imgur.com/4isSf.png[/IMG]

I just tried installing Dropbox through the Terminal, same thing happened, so it's not just indicator-apps

How do I delete my other post?

---

### Post by wojox on 2011-05-14
Okay run this and copy and paste it up here:

```
gksudo gedit /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
```

You would have to tell a mod to merge or the threads.

---

### Post by Kruger2147 on 2011-05-14
```
deb http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu natty main
deb-src http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu natty main
s-elementary-ppa/ubuntu natty main # disabled on upgrade to natty
```

---

### Post by wojox on 2011-05-14
Okay with that file still open like that remove

```
s-elementary-ppa/ubuntu natty main # disabled on upgrade to natty
```

Save and close and run your updates again.

---

### Post by Kruger2147 on 2011-05-14
Didn't work, I'm still getting "E: The list of sources could not be read." I tried installing a few different things.

---

### Post by wojox on 2011-05-14
> **Kruger2147 said:**
> Didn't work, I'm still getting "E: The list of sources could not be read." I tried installing a few different things.

What are the errors this time?

---

### Post by Kruger2147 on 2011-05-14
[IMG]http://i.imgur.com/4OsMy.png[/IMG]

if you want SS for some of the other apps i tried to install, i can do so

---

### Post by wojox on 2011-05-14
Just repeat the same procedure and remove the last line. :P

---

### Post by Kruger2147 on 2011-05-14
K, I deleted the last line again, tried to reinstall some apps, still not working, same error.

---

### Post by wojox on 2011-05-15
> **Kruger2147 said:**
> K, I deleted the last line again, tried to reinstall some apps, still not working, same error.

Same error from the same or different package? You will need to go through and fix them all.

---

### Post by Kruger2147 on 2011-05-15
new packages. thanks for the help

---

### Post by wojox on 2011-05-15
> **Kruger2147 said:**
> new packages. thanks for the help

You said this happened because of the upgrade or is it the way your installing them?

---

### Post by Kruger2147 on 2011-05-15
I mistyped. sry. Looks like everything is fixed now. Thank you.

---

