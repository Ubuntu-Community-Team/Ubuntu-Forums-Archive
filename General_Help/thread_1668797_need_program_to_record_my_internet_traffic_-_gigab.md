---
title: "need program to record my internet traffic - gigabytes per month"
date: 2011-01-16
forum: General Help
---

### Post by Bushcraft Bill on 2011-01-16
Were we are we are now getting dinged by the gigabyte were up till now it was just a monthly cost for unlimited use. I guess they are fishing for more profits anyways I need a program that will record/track my monthly usage is their anything available like this for ubuntu?

---

### Post by Rivers48 on 2011-01-16
gdesklets and screenlets are both widget managers for linux / ubuntu in general. I think i remember screenlets having a traffic monitor on it? If it dosnt then there are 3rd party widgets that people have made that are compatible with screenlets. Have a look at them.

EDIT: I forgot to mention that screenlets its available straight off of the ubuntu software centre

---

### Post by Bushcraft Bill on 2011-01-19
thanks I will check into that...

---

### Post by dcstar on 2011-01-19
> **Bushcraft Bill said:**
> Were we are we are now getting dinged by the gigabyte were up till now it was just a monthly cost for unlimited use. I guess they are fishing for more profits anyways I need a program that will record/track my monthly usage is their anything available like this for ubuntu?

Firefox Net Usage Add-on.

---

### Post by cascade9 on 2011-01-19
Your ISP should have some form of account viewing where you can see your usage.

---

### Post by bouncingwilf on 2011-01-19
Not sure what sort of router you have but with mine, you can log into the router and read the accumulated traffic data off of it.

Bouncingwilf

---

### Post by mr_hangman on 2011-01-19
For each computer you can try vnstat in the repo.

After install, run
```
vnstat -u -i eth0
```
to create a database for eth0. It will start automatically at startup and record your traffic using cronjob.

There is no interface to this but the command line. To see monthly traffic, run
```
vnstat -m
```
or daily
```
vnstat -d
```
Man page will tell you more ;)

---

