---
title: "never seen anything like this?"
date: 2009-11-24
forum: General Help
---

### Post by darkreaction on 2009-11-24
virtual box and Vlc player have gone into some crazy language after my update to 9.10 anyone seen this before? I cant seem to change it back to English. A complete un- and re- install of the programs did nothing. screen shot attached.

---

### Post by jacobs444 on 2009-11-24
has to do with locales, am trying to think where they hide this in ubunut

---

### Post by lisati on 2009-11-24
Looks like Greek to me.... Seriously. Beyond that, I have no suggestions.

---

### Post by darkreaction on 2009-11-24
Thats what I thought but even when I find the language settings every language is the same.

---

### Post by jocko on 2009-11-24
> **darkreaction said:**
> virtual box and Vlc player have gone into some crazy language after my update to 9.10 anyone seen this before? I cant seem to change it back to English. A complete un- and re- install of the programs did nothing. screen shot attached.
The crazy language seems to be english, but the fonts are greek.
Only virtualbox and vlc?
In that case the problem seem specific to qt, which stores it's settings in ~/.config/Trolltech.conf. Try deleting that file (it will be regenerated next time you start an app that uses qt):
```
rm ~/.config/Trolltech.conf
```

---

### Post by darkreaction on 2009-11-24
nope didn't work.

---

### Post by jocko on 2009-11-24
Weird. Then I'm out of ideas.

---

### Post by darkreaction on 2009-11-24
bumb

---

### Post by raktarok on 2009-11-25
This should definitely be a qt specific problem.And it certainly is Greek, wish my computer had that font.
Have you tried installing the qt4 config tool and changing fonts from there?
```
sudo apt-get install qt4-qtconfig
```

---

### Post by darkreaction on 2009-11-26
cant do anything in qt4 its all in greek.

---

### Post by NoaHall on 2009-11-26
I've seen something like this a while ago(after last updates) but I can't remember how we fixed it in the end. Give me a minute.

---

### Post by raktarok on 2009-11-26
Here's a screenshot of my config window, if it helps..You could compare the two and try changing the font, but I don't think this is going to work...I'm out if ideas. I'll chek back to see how you solved the problem.

---

### Post by NoaHall on 2009-11-26
It's the font type! See this thread - [http://ubuntuforums.org/showthread.php?t=1250579](http://ubuntuforums.org/showthread.php?t=1250579)


Edit: Damn it, i spent ages finding that thread, only to be beaten xD

---

### Post by StuartN on 2009-11-26
> **NoaHall said:**
> It's the font type!

Yes, selecting Symbol font will produce fake Greek text, substituting similar Greek letters for each Latin while leaving the language the same (file -> &#966;&#953;&#955;&#949; etc). You are looking for any font except &#931;&#965;&#956;&#946;&#959;&#955; (or &#916;&#953;&#957;&#947;&#946;&#945;&#964;&#963;, obviously).

---

### Post by darkreaction on 2009-11-27
thanks guys that worked I feel retarded now.

---

