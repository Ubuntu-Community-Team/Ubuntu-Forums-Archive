---
title: "Setting up brightness shortcuts"
date: 2011-03-14
forum: General Help
---

### Post by MTNoob on 2011-03-14
i know if this has been already written but i noticed a lot of people are complaining about brightness function keys not working . i'm a begginer myself but making this wasn't hard ...
i think it works on all laptops since mine is the most incompatible .
first you must install the xbacklight package : 
sudo apt-get install xbacklight
after that go to system ->prefrences-> keyboard shortcuts and add these two :

name : whatever you like (+)
command xbacklight -set xbacklight -get + 10
key : whatever you want (most likely Mode4(or function key) + F6)

name : whatever you like (-)
command xbacklight -set xbacklight -get - 10
key : whatever you want (most likely Mode4(or function key) + F5)

---

### Post by zinadork on 2011-06-10
Have you tried they in Natty?  Between the disfunction of my function keys and the last of Clickpad support, this laptop is a pain to take on the road.

---

