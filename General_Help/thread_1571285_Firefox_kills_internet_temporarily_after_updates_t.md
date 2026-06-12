---
title: "Firefox kills internet temporarily after updates today."
date: 2010-09-09
forum: General Help
---

### Post by llawwehttam on 2010-09-09
Using ubuntu 9.10 Karmic 64 bit
Firefox version: 3.6.9 Mozilla Firefox for Ubuntu canonical - 1.0
about:config is default
Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.2.9) Gecko/20100825 Ubuntu/9.10 (karmic) Firefox/3.6.9


When I access some websites, especially certain forums or atempt to  post, the tab seems to be loading but doesn't do anything. If I then  exit firefox I cannot ping anything (IP or address) in terminal.

If I then open Epiphany it fixes everything until firefox next does  this. This is happening from 1 - 10 times an hour and is starting to get  to me.


Any ideas anyone?

---

### Post by llawwehttam on 2010-09-09
This is still happening and is getting very annoying. None of the other computers in the house are affected.

---

### Post by llawwehttam on 2010-09-09
Still doing it. This time I had to unplug the ethernet and reconnect it to get back online.

I am strongly considering switching to arch linux. My arch boxes seem to all be fine.

I am going to try downgrading firefox.

---

### Post by llawwehttam on 2010-09-09
Just completely removed firefox and config files and re-installed it.

Also cleared cookies and the cache.

If its going to freeze it will do so when I press "submit post " so here goes,

3,2,1....


 EDIT: and it was fine.
 
 I'll post if it happens again.

For now take it as solved.

---

### Post by llawwehttam on 2010-09-10
I have had several friends with the same thing who couldn't even post on a forum without it freezing. I guess I'm lucky.

Just to let others know there are more people who have this problem after updating firefox.

Mine was solved with a purge, a reboot and a fresh install.

---

### Post by jre6 on 2010-09-10
[LIST]
[*]Uninstall the existing Firefox.
[*]Delete the .mozilla folder in home directory by typing this in a terminal:```
rm ~/.mozilla
```
[*]Download [this version of Firefox]("http://www.mozilla.com/en-US/firefox") and save it in the home directory.
[*]Install by typing:
```

tar -xf firefox-3.*.*.tar.bz2

```
[*]Whenever you need to start Firefox, type:```
~/firefox/firefox
```
[/LIST]

---

### Post by llawwehttam on 2010-09-10
^^^^^^^^^^That is NOT needed.

Thread is marked as solved as I had the solution.

The bump was to inform others.

Solution:

Simply Open firefox, Press Ctrl+Shift+Del and clear cookies and cache for everything.

Then close Firefox and open a terminal and type:

```
sudo apt-get purge firefox
```reboot your computer then open terminal and install firefox again with:

```
sudo apt-get install firefox
```That worked for me.

You should avoid building from source at all costs as it is near impossible to maintain.

---

