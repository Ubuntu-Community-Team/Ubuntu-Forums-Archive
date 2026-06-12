---
title: "This is how to fix your skype"
date: 2011-05-26
forum: General Help
---

### Post by toshko3 on 2011-05-26
Don't worry it is NOT a virus or something:
[http://supportivo.com/index.php/news/news_details/15](http://supportivo.com/index.php/news/news_details/15)
:popcorn:

---

### Post by micael3000 on 2011-05-26
I am pretty sure that everybody here speaks russian and will for sure understand what you are teaching us to fix! THANKS! [/cool irony]

My skype just crashed today (It was self-closing after 4~5 secs opened and reboot wasn't fixing it). If anyone is experiencing this issue:

run:
```
sudo apt-get purge skype
```and then
```
rm -r ~/.Skype
```and then
```
sudo apt-get install skype
```Be aware that you will lose all of your skype's history. If you want to save it just copy from inside ~/.Skype before removing it and then move back!

note: MAYBE just the "rm -r ~/.Skype" fix it. As I done the whole process I cannot ensure that.

[]'s

---

### Post by f_padia on 2011-05-26
rahter than re-installing skype just go to ~/.Skype and delete shared.xml. re-start skype and everything should be hunkie-dorie again

---

