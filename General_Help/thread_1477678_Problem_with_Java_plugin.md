---
title: "Problem with Java plugin"
date: 2010-05-09
forum: General Help
---

### Post by alphacrucis2 on 2010-05-09
Running a clean install of Lucid 64, I have a problem with the Firefox Java plugin with the "Live Timing" feature of the www,formula1.com site. Live Timing is an applet they provide that displays sector and lap time information for races, practice and qualifying sessions. It was working fine under Karmic 32 but no luck so far with Lucid 64.

Initially trying to start Live Timing caused Firefox to become unresponsive, I saw that the Java plugin being used was the IcedTea one, which I have heard can be a bit flakey. (Not sure what I was using under Karmic BTW).

I notice that the Sun proprietary Java stuff is installed - I presume when I installed ubuntu-restricted-extras. So I disabled the IcedTea plugin in Firefox and tried to use the Sun Java Moz plugin by creating a symlink to

```
/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/libnpjp2.so
``` 

in

```
/usr/lib/mozilla/plugins
```

Firefox then lists the Sun proprietary plugin under addons - plugins but it doesn't actually seem to do anything, as I just get an empty Window with the Live Timing Applet. 

Anyone know how to sort this out?

---

### Post by kostkon on 2010-05-09
The only thing you had to do is this:
```
sudo update-java-alternatives -s java-6-sun
```
and then restart Firefox.

---

### Post by alphacrucis2 on 2010-05-09
> **kostkon said:**
> The only thing you had to do is this:
```
sudo update-java-alternatives -s java-6-sun
```
and then restart Firefox.

Many thanks. That did the trick!.

---

