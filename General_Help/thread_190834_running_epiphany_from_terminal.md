---
title: "running epiphany from terminal"
date: 2006-06-06
forum: General Help
---

### Post by syxbit on 2006-06-06
i was looking around for epiphany on dapper.
on breezy it was in applications-internet-epiphany
it's not on dapper.
anyway, i ran
sudo aptitude install epiphany
(from what i understand, aptitude does everything that apt-get does, only it's better if you later want to remove it, am i right ?)
this installed it, rebooted
i thought i could then type "epiphany" in the terminal to run it, but that didn't work
it's not in my applications-internet
where would it be ?

---

### Post by zerwas on 2006-06-06
[QUOTE=syxbit]
anyway, i ran
sudo aptitude install epiphany[/QUOTE]
Epiphany is a game, i think. What you want to do is
**```
sudo aptitude install epiphany-browser
```**

There is also a package called epiphany-extensions. It might be useful :)
To seach for packages on the command line, do:
```
apt-cache search epiphany
```
Or simply use synaptic and its search function, it is a really good program.

Greetings,
zeRwas

---

### Post by syxbit on 2006-06-06
k, thanks, that worked
now, how do i load it from the terminal
i thought you'd just type
```
epiphany-browser
```
but that doesn't work.
is there an easy way to know what to type for any app?
for example, i installed beagle, but running it from the terminal i have to type
```
beagle-search
```
i had to figure this out from the beagle manual
thanks

---

### Post by syxbit on 2006-06-07
bump..

---

### Post by zerwas on 2006-06-08
[QUOTE=syxbit]now, how do i load it from the terminal[/QUOTE]
The command is```
epiphany
```
____________________________________________________________
> is there an easy way to know what to type for any app?
Do you know that you terminal has something called "tab-completion"? It is a **very** good feature and you should use it.
[LIST]
[*]In your terminal, e.g. type the three characters "epi"
[*]press the TAB-Key
[*]see which app you want to start :)
[/LIST]

> for example, i installed beagle, but running it from the terminal i have to type
```
beagle-search
```
i had to figure this out from the beagle manual
The most applications lie in the path /usr/bin, there you find the app :).
If that is not the case, you can start synaptic, **right click** on the app you don't know the name of the executable - **Properties** -** Installed Files**

I hope this helps a bit :)

Greetings,
zerwas

---

