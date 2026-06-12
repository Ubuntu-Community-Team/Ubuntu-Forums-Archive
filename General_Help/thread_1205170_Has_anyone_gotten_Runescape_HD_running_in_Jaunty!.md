---
title: "Has anyone gotten Runescape HD running in Jaunty?!"
date: 2009-07-05
forum: General Help
---

### Post by xakh on 2009-07-05
I really want to play RuneScape. I like the game. I really need some help here. Has anyone gotten full screen HD to run, and has anyone gotten it on an intel system using an nVidia video card, running the latest drivers? I'd really really appreciate it if you'd help me.

---

### Post by Drk Guy on 2009-07-05
I'm no runescape fan, i actually hate it, but ill help you, it seems you dont have java installed, so try doing this:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```
Restart Firefox and it should be up and running ;) Good Luck

---

### Post by xakh on 2009-07-05
>.<
I have Java installed. Perhaps I should be more specific. I've asked this question a few times before, I've had another thread dedicated to it as well.
[http://ubuntuforums.org/showthread.php?t=1182986](http://ubuntuforums.org/showthread.php?t=1182986)
At any rate, the game played fine in Intrepid, and I can still play it if I use an unsigned applet, but if I play it that way, I don't have access to full screen, or high detail, which means I essentially don't get textures on anything. So you see why this could present a problem.

---

### Post by Drk Guy on 2009-07-05
Oh! Hmmm... there are two versions of java on repos, java5 and java6, check that you have the latest one :S Else i dont know man

EDIT: Now that i've looked, i was using the open-jdk version of java, which AFAIK, isn't very compatible with most stuff, i just changed to sun's java with:

```
sudo update-alternatives --config java
```

Some paths should show up, notice that there are some numbers in the list? press the number next to "/usr/lib/jvm/java-6-sun/jre/bin/java" and press enter, then you may be able to play RS HD :p But i dont know for sure

---

### Post by xakh on 2009-07-05
No dice. Thanks for your help though.

---

