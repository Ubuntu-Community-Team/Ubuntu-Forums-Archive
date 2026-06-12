---
title: "Java games running slow"
date: 2011-06-13
forum: General Help
---

### Post by Doctorly on 2011-06-13
[COLOR=#000000][FONT=Sans]Hey guys, I'm having some trouble with Java based games. I am running 11.04 64x and I downloaded and installed the latest sun-jvm. I know my hardware can run these two games very well (Minecraft and Spiral Knights). I'm wondering if maybe sun isn't my default plugin or if there is any advice any of you can give me! thanks[IMG]http://ubuntuforums.org/usr/share/icons/gnome/16x16/emotes/face-smile.png[/IMG]
[/FONT][/COLOR]

---

### Post by r-senior on 2011-06-13
Did you do ...

```

sudo update-java-alternatives -s java-6-sun

```

... to switch to Sun Java?

(This only works if you installed Java from the Ubuntu repositories).

What do you get if you type:

```

java -version

```

into a terminal window?

---

### Post by Doctorly on 2011-06-13
I get: 
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.1) (6b22-1.10.1-0ubuntu1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

I actually had to install in manually because my repository had an invalid line and it took me a while to find it. Could you tell me how?
Thanks a lot!

---

### Post by mmsmc on 2011-06-13
> **Doctorly said:**
> I get: 
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.1) (6b22-1.10.1-0ubuntu1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

I actually had to install in manually because my repository had an invalid line and it took me a while to find it. Could you tell me how?
Thanks a lot!


i get the same results and minecraft is slow for me to, yet i know my hardware can run it

---

### Post by wildmanne39 on 2011-06-13
> **Doctorly said:**
> [COLOR=#000000][FONT=Sans]Hey guys, I'm having some trouble with Java based games. I am running 11.04 64x and I downloaded and installed the latest sun-jvm. I know my hardware can run these two games very well (Minecraft and Spiral Knights). I'm wondering if maybe sun isn't my default plugin or if there is any advice any of you can give me! thanks[IMG]http://ubuntuforums.org/usr/share/icons/gnome/16x16/emotes/face-smile.png[/IMG]
[/FONT][/COLOR]
Hi, I know some people are having trouble because of compiz while playing there games, and they just log into ubuntu classic no effects while they are playing there games and it seems to work a lot better for them.

---

### Post by Doctorly on 2011-06-15
> **wildmanne39 said:**
> Hi, I know some people are having trouble because of compiz while playing there games, and they just log into ubuntu classic no effects while they are playing there games and it seems to work a lot better for them.

Well I tried this, and my results were no different. I did manage to get sun-java running, but Minecraft is still not running as fast as it should be (its at about half speed) and neither is the other game. Man, I was hoping sun would help out more. I appreciate any more help I can get on this, and thanks:)

---

