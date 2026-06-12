---
title: "lm-sensor"
date: 2010-04-18
forum: General Help
---

### Post by robertrose6 on 2010-04-18
I am trying to get lm-sensors up and running. when I run sudo sensors-detect and anser all the questions I get 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
lm85
#----cut here----


But I do not have a /etc/modules. I am looking in the hidden files so I have found /etc but on modules how do I make it or am I missing something?

---

### Post by Mark Phelps on 2010-04-18
From what I recall, it gives you an option of answering Yes and it will do the installation for you.  Use that option and don't go editing the file yourself.

---

### Post by robertrose6 on 2010-04-19
> **Mark Phelps said:**
> From what I recall, it gives you an option of answering Yes and it will do the installation for you.  Use that option and don't go editing the file yourself.

I tried that but it didn't do anything. So I ran it again and was going to edit the file my self but there was no file.

---

### Post by klemes on 2010-04-19
I am assuming that you are running sensors-detect with sudo of course.If otherwise try this first.
As for your /etc/modules file going astray I don't know what to suspect.There simply MUST be on such file.
Anyway if for some reason there is not it's absolutely safe to make one yourself;

```
#sudo touch /etc/modules
#sudo nano /etc/modules
```

cut & paste CTRL-X then  y and finally ENTER to save the file and you are done.

---

