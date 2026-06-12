---
title: "can't log into ubuntu after trying to rotate the dock"
date: 2012-04-05
forum: General Help
---

### Post by benj23673 on 2012-04-05
I am still very new to ubuntu, I recently started dual booting ubuntu next to windows. Being a long time windows user I like my dock or dash at the bottom of the screen not the left. I was on step 3 of this [http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html](http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html) article everything went a little crazy I tried the lightdm restart but every time I log onto my main account from start up, I type in my password and a screen pops up then goes away before I can even read a word on it and it asks me to log in again? am I lost forever?

---

### Post by benj23673 on 2012-04-05
I think it has to do with my disk encryption? I can still log in via ctrl+alt+F1

---

### Post by benj23673 on 2012-04-05
Last bump then I fresh restart :'(

---

### Post by kazztan0325 on 2012-04-06
Hi benj23673,

Have you tried to Revert the changes when you logged in via ctrl+alt+F1?

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:paullo612/unityshell-rotated
sudo apt-get remove unityshell-rotated
```

---

### Post by benj23673 on 2012-04-06
Yep tried that, I am allowed to log in on a different account that I made. I don't know how to get into my "main" account from the other account and change the settings back, if that made any sense.

---

### Post by kazztan0325 on 2012-04-10
What about resetting Compiz/Unity?

**"[SOLVED] 11.10 Unity MASSIVE (imo) problem"**
[http://ubuntuforums.org/showthread.php?t=1860400]("http://ubuntuforums.org/showthread.php?t=1860400")

**"Missing Top and Side Panels in Unity: Troubleshooting, Ubuntu Natty / Oneiric"**
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by benj23673 on 2012-04-12
That is alll I needed was to reset the unity launcher thanks my man

---

### Post by kazztan0325 on 2012-04-12
You are welcome, benj23673!

I'm glad to hear you have solved the problem.

See you again somewhere else in this forums.

---

