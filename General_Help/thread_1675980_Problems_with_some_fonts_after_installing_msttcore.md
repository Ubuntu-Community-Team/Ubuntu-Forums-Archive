---
title: "Problems with some fonts after installing msttcorefonts"
date: 2011-01-26
forum: General Help
---

### Post by grant_in_the_box on 2011-01-26
I attempted to install msttcorefonts using the command 'sudo apt-get  install msttcorefonts' something happened during the process. To get to  the point, all my fonts in firefox are messed up (to the point that i  can't read them). In the terminal, i'm getting an error that says 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

I don't really understand any of this yet. Can somebody please help me?:confused:

---

### Post by [Snc] on 2011-01-26
> **grant_in_the_box said:**
> I attempted to install msttcorefonts using the command 'sudo apt-get  install msttcorefonts' something happened during the process. To get to  the point, all my fonts in firefox are messed up (to the point that i  can't read them). In the terminal, i'm getting an error that says 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

I don't really understand any of this yet. Can somebody please help me?:confused:

Well, as the error says, you must go to the terminal and enter

```
sudo dpkg --configure - a
```

then
```
sudo apt-get update
```

then
```
sudo apt-get upgrade
```if you still have problems, post the output of apt-get here.

---

### Post by grant_in_the_box on 2011-01-26
Thanks! It ran the update and everything but it brought me back to where things got messed up before. the package configuration in the terminal. it's a user agreement but there is not way for me to click on the <ok> at the bottom. Last time I closed this window out. I think that s what caused the problem

---

### Post by [Snc] on 2011-01-26
> **grant_in_the_box said:**
> Thanks! It ran the update and everything but it brought me back to where things got messed up before. the package configuration in the terminal. it's a user agreement but there is not way for me to click on the <ok> at the bottom. Last time I closed this window out. I think that s what caused the problem

The terminal is not clickable :) or i am missing something ...

try to hit "o" or Enter or do as the instructions say :) anyway, it would be great if i could see where you end up (screenshot or terminal copy&paste).

ps. it is allways a bad idea to close the terminal, if there are still operations pending, you can do it, but it is bad!

---

### Post by grant_in_the_box on 2011-01-26
This is what shows up in the terminal 
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash1/hs897.ash1/180562_184629678237588_100000716711534_506077_6579125_n.jpg[/IMG]

---

### Post by grant_in_the_box on 2011-01-26
And this is what happened to my browser

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc6/hs272.snc6/180038_184629618237594_100000716711534_506076_971602_n.jpg[/IMG]

---

### Post by grant_in_the_box on 2011-01-26
After I downloaded and attempted to install msttcorefont, my firefox fonts are messed up. here is a screenshot. Can anyone tell me how to fix it?

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc6/hs272.snc6/180038_184629618237594_100000716711534_506076_971602_n.jpg[/IMG]

---

### Post by grant_in_the_box on 2011-01-26
Thank You very much !

I had to hit -tab- to select <ok>

---

### Post by s.fox on 2011-01-26
Please do not create duplicate threads. Thank you.

Threads Merged.

---

