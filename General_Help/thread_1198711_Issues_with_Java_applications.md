---
title: "Issues with Java applications"
date: 2009-06-27
forum: General Help
---

### Post by cumanzor on 2009-06-27
Hi everyone. I'm on a new Ubuntu install and I'm having issues with the fonts in Java. Look at the screenshot, it looks horrible. I've never had issues with previous installs before. Any ideas?

---

### Post by starcraft.man on 2009-06-27
Did you install the java fonts? First thing I thought of.

Applications > Accessories > Terminal.

Then type and enter: 

```
sudo aptitude install sun-java6-fonts
```

You might also want to tweak your font rendering, I've never been quite happy with default.

System > Preferences > Appearances > Fonts tab

Try different rendering and see what happens. If you want even more control, push details and you can really edit the way fonts render.

---

### Post by cumanzor on 2009-06-27
> **starcraft.man said:**
> Did you install the java fonts? First thing I thought of.

Applications > Accessories > Terminal.

Then type and enter: 

```
sudo aptitude install sun-java6-fonts
```

You might also want to tweak your font rendering, I've never been quite happy with default.

System > Preferences > Appearances > Fonts tab

Try different rendering and see what happens. If you want even more control, push details and you can really edit the way fonts render.


Thanks. Ok just tried that. Also played around with the settings. Overall it looks better, but java apps still look the same. :(

---

### Post by credobyte on 2009-06-27
```
sudo apt-get install msttcorefonts
```
Restart your PC ..

---

### Post by cumanzor on 2009-06-27
> **credobyte said:**
> ```
sudo apt-get install msttcorefonts
```
Restart your PC ..

Same issue. I don't know. If you look at the second screenshot I put, you'll notice how Netbeans just overall looks ugly.

Do the fonts that you change in Appearance -> Fonts affect the fonts in java applications?

---

### Post by eddier on 2009-06-27
Which Java JRE are you using 'open'  or 'Sun' ?

I have the same problem in mint with openjava--it is ok with sun java.

eddie

---

### Post by cumanzor on 2009-06-28
> **eddier said:**
> Which Java JRE are you using 'open'  or 'Sun' ?

I have the same problem in mint with openjava--it is ok with sun java.

eddie

Sun Java.


```
manuel@Desktop:~$ java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Client VM (build 11.3-b02, mixed mode, sharing)

manuel@Desktop:~$ java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Client VM (build 11.3-b02, mixed mode, sharing)


```

---

### Post by bjtuna on 2009-11-03
Same issue here, with Sun Java. Haven't found an answer yet, still looking.

---

### Post by pros on 2009-11-08
Same problem here.

Running the application with
```
java -jar -Dawt.useSystemAAFontSettings=on /application
```
the result is a little better...


The following bug is related to the problem.
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/314520](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/314520)

---

### Post by dummiebeginner on 2009-11-13
I hate to read a whole thread and get to an unsolved end after wasting so much time... argh!

I also hate the java fonts

---

