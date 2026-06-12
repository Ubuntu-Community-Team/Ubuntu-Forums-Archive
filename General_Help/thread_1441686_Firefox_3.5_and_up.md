---
title: "Firefox 3.5 and up"
date: 2010-03-29
forum: General Help
---

### Post by stevecam on 2010-03-29
I know this isn't just me, I have been using this on a few computers now, and the problems come up over and over again

When I quit Firefox and start it again I often get an error advising me that Ubuntu is still running

Now I know how to get past this, I just type "pkill firefox" but when I have been helping other friends of mine install Ubuntu they have been getting very frustrated, (I don't like reinstalling windows on other peoples machines because they couldn't use firefox)

---

### Post by Aizawa on 2010-03-29
It says *Ubuntu* is still running?

---

### Post by stevecam on 2010-03-29
Whoops, I meant firefox is still running

---

### Post by mikewhatever on 2010-03-29
What addons/themes are you running, if any? You could starting Firefox in safe mode, <firefox -safe-mode>, and see if it shuts down properly. If it does, one of the modifications you made is causing the problem. For example, Ghostery was known to cause that same behavior a few months back. I've no idea if it's been fixed since.

---

### Post by lovinglinux on 2010-03-29
> **mikewhatever said:**
> What addons/themes are you running, if any? You could starting Firefox in safe mode, <firefox -safe-mode>, and see if it shuts down properly. If it does, one of the modifications you made is causing the problem. For example, Ghostery was known to cause that same behavior a few months back. I've no idea if it's been fixed since.

I guess it has been fixed, because I use Ghostery and this problem is not affecting my Firefox anymore. I'm not sure if Ghostery was in fact the culprit, because I have about 50 extensions installed. The problem went away and I couldn't determine the source.

> **stevecam said:**
> I know this isn't just me, I have been using this on a few computers now, and the problems come up over and over again

When I quit Firefox and start it again I often get an error advising me that Ubuntu is still running

Now I know how to get past this, I just type "pkill firefox" but when I have been helping other friends of mine install Ubuntu they have been getting very frustrated, (I don't like reinstalling windows on other peoples machines because they couldn't use firefox)

I know is not a solution, but you could create a bash script to kill firefox before starting it, then making it kill again after closing it, just to make sure. Could be something like this:

```
killall firefox
killall firefox-bin
firefox &&
killall firefox
killall firefox-bin
```

---

### Post by CharlieB21 on 2010-03-29
I have been having the same problem for months and then it just stopped all of a sudden. I didn't have to install anything. wish I knew what it was.


------------------

[safari bouncers]("http://inflatablebouncersite.com/inflatable-safari-bouncers/")

---

### Post by lovinglinux on 2010-03-29
> **CharlieB21 said:**
> I have been having the same problem for months and then it just stopped all of a sudden. I didn't have to install anything. wish I knew what it was.

Same here.

---

### Post by stevecam on 2010-03-29
> **mikewhatever said:**
> What addons/themes are you running, if any? You could starting Firefox in safe mode, <firefox -safe-mode>, and see if it shuts down properly. If it does, one of the modifications you made is causing the problem. For example, Ghostery was known to cause that same behavior a few months back. I've no idea if it's been fixed since.

This was happening on a fresh install of Ubuntu and the only plugin that was installed was Adobe Flash Player and the only extension was the Ubuntu Firefox Modifications

And has anyone noticed that firefox is slower in general too?

---

