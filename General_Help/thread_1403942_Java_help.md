---
title: "Java help"
date: 2010-02-10
forum: General Help
---

### Post by charlton2142 on 2010-02-10
Hi Im trying to play some flash games here on my computer such as pogo.com and it doesnt seem to be working. If I can get some help resolving this issue it would be appreciated.

---

### Post by RedSingularity on 2010-02-10
Are you sure they are flash games?  If so did you install flash yet?

---

### Post by Miljet on 2010-02-10
> Are you sure they are flash games?
No, Pogo games are java.

Open a terminal window, Applications -> Accessories -> Terminal.

Type the following, one line at a time. After the first line it will ask for your password. Use your normal log-in password. It will not show up and look like it is not accepting anything. That is normal, just keep typing in the entire password and press Enter.
```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin 
```

Close the terminal and you should be in business. If that does not work post back and we will explore further.

Almost forgot, at some point during the java install, you will have to accept the EULA. You have to press the TAB key on your keyboard to enable the accept key.

---

### Post by charlton2142 on 2010-02-11
alright I tried that but apparently I already have that installed

---

### Post by Miljet on 2010-02-11
Try opening Firefox and click on Edit -> Preferences. Then the Content tab at the top. Be sure that Enable Javascript and Enable Java are both checked.

If that does not work, you might have a look at this site. 
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

By the way, Pogo.com games work fine on all three of our computers running 9.04 and 9.10, and all I did was install the sun-java packages from the repositories. If you need more help, post back and we can start comparing installed files.

---

### Post by ell02 on 2010-02-14
thanks, word whomp has allways been one of my benchmarks and you made it so simple .

---

### Post by MickS on 2010-02-14
Have you got it blocked with NoScript or something like that? I'm always forgetting to allow stuff.


Mick

---

### Post by Miljet on 2010-02-14
Glad you got it working. Tumble Bees is usually my benchmark.

---

### Post by charlton2142 on 2010-02-23
Thanks, I solved this by installing the icedtea plugin.

---

