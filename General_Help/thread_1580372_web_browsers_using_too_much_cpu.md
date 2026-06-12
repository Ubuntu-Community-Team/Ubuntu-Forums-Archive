---
title: "web browsers using too much cpu"
date: 2010-09-23
forum: General Help
---

### Post by konsta82 on 2010-09-23
I have carmic installed in dell laptop with 2.7 ghz celeron processor. CPU usage after startup is between 20-30 %. After I start ANY web browser (firefox,chrome,opera,midori,galeon) CPU is used above 90%. It's the same on any web site,without flash player.
Browsers are using at least 60% CPU. Everything else is ok.
It was the same case with 9.04 installed in past.
Whta to do ? Any ideas ???

---

### Post by konsta82 on 2010-09-23
By the way,ram usage is also normal. After startup it is below 200 mb.

---

### Post by jokes_finder on 2010-09-23
The same here
I have 2.99GHz CPU 2.5 GB RAM
About the RAM it's normal
but the CPU - sometimes - -> >90%
Don't know why
but when I leave it for a while it goes back to its normal state i.e. about 60% or less

---

### Post by Vaphell on 2010-09-23
run top in terminal and see what eats cpu cycles, system monitor is not to be trusted as it adds to the load significantly

flash and javascript heavy sites can tax cpu hard but i don't think 60%+ is normal at all

---

### Post by konsta82 on 2010-09-23
Top says that browser is eating at least 60% on this website,so it's not about flashplayer. While stand's still it's about 70-80%,when reloading up to 99%. Same with all browsers.

---

### Post by ajgreeny on 2010-09-23
Look for **update-apt-xapi** in the *top* command output, which is the update manager working; it always seems to use full cpu on my machine too, but it quickly drops back to a more normal ~5-10% with firefox running.

---

### Post by konsta82 on 2010-09-23
I disabled it with 
```
sudo chmod 644 /etc/cron.weekly/apt-xapian-index
```

This helped for now.
Probably it is all I can do with this.
Thanks for idea !!!

---

### Post by hrickh on 2010-09-23
You can also try to use this little utility: [http://cpulimit.sourceforge.net/](http://cpulimit.sourceforge.net/)

I've not tried it myself, but it looks useful for limiting the cpu usage of specific programs.

R.
==

---

