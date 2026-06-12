---
title: "Windows Alt Codes in Linux?"
date: 2012-06-09
forum: General Help
---

### Post by forrestcupp on 2012-06-09
Does anyone know an easy way to do Windows Alt Codes in Linux? I know all about using Ctrl+Shift+U to enter unicode characters, but the values aren't the same as the Alt Codes all the Facebook kiddies use in Windows.

For instance, in Windows pressing Alt+3 gives you a heart symbol, and pressing Alt+14 gives you double eighth notes. In Linux, Pressing Ctrl+Shift+U and entering 3 doesn't give you a heart symbol, etc.

The only Unicode lists I've found only give you things that are actually useful, like accents and language symbols. I've never seen things like hearts and music notes. Is there any easy way to do this in Linux?

---

### Post by qamelian on 2012-06-09
Those little hearts you see them using in Facebook aren't entered using the windows Alt codes. FB has its own shortcuts for those. For example, if you type <3 in your status, FB interprets it and displays a heart. :)

---

### Post by zombifier25 on 2012-06-09
I was about to mention Ctrl + Shift + U :lolflag:

Yeah, I was looking for the same type of functionality on Linux. But I'm pretty sure it's Windows-specific. Unless someone writes a software for this.
> **qamelian said:**
> Those little hearts you see them using in Facebook aren't entered using the windows Alt codes. FB has its own shortcuts for those. For example, if you type <3 in your status, FB interprets it and displays a heart. :)
Some geeks prefer the Unicode heart :P

---

### Post by philinux on 2012-06-09
> **forrestcupp said:**
> Does anyone know an easy way to do Windows Alt Codes in Linux? I know all about using Ctrl+Shift+U to enter unicode characters, but the values aren't the same as the Alt Codes all the Facebook kiddies use in Windows.

For instance, in Windows pressing Alt+3 gives you a heart symbol, and pressing Alt+14 gives you double eighth notes. In Linux, Pressing Ctrl+Shift+U and entering 3 doesn't give you a heart symbol, etc.

The only Unicode lists I've found only give you things that are actually useful, like accents and language symbols. I've never seen things like hearts and music notes. Is there any easy way to do this in Linux?

Type help in Dash. Tips and tricks. I've not delved any further.

---

### Post by WorMzy on 2012-06-09
You mean like this: &#10084;?

Shift+u+2764.

[https://en.wikipedia.org/wiki/List_of_Unicode_characters](https://en.wikipedia.org/wiki/List_of_Unicode_characters)

---

### Post by Vaphell on 2012-06-09
additionally you should have the charmap application installed on your system in accessories (gucharmap in terminal)

---

### Post by zombifier25 on 2012-06-09
All time favorite: Ctrl+Shift+U+e0ff

---

### Post by forrestcupp on 2012-06-09
> **qamelian said:**
> Those little hearts you see them using in Facebook aren't entered using the windows Alt codes. FB has its own shortcuts for those. For example, if you type <3 in your status, FB interprets it and displays a heart. :)How can you type double eighth music notes without an Alt Code?

> **philinux said:**
> Type help in Dash. Tips and tricks. I've not delved any further.I've seen that, and it looks like it would be the best way in the end. But it looks like it would take a lot of setting up before you got to that point.

> **WorMzy said:**
> You mean like this: &#10084;?

Shift+u+2764.

[https://en.wikipedia.org/wiki/List_of_Unicode_characters](https://en.wikipedia.org/wiki/List_of_Unicode_characters)
Thanks. That's pretty much what I was looking for. It's just that there are so many of them that it's like trying to find a needle in a haystack. Finding 2764 takes a lot longer than finding 3 in a list. That's what I wanted, though. :)

---

### Post by zombifier25 on 2012-06-09
Actually, take a look at the Unicode standard. The symbols are categorized pretty neatly.
[size=10]&#119140;[/size]
1D164, by the way. There are more in the range of 1D157 to 1D172.

---

### Post by Vaphell on 2012-06-09
in charmap bundled with the system you have the unicode blocks listed and the 'musical symbols' block is 1d100-1d1ff

---

### Post by Zvlwab on 2012-06-09
I recommend setting the following values in /etc/default/keyboard
```
XKBVARIANT="altgr-intl"
XKBOPTIONS="compose:ralt"

```

That makes it very easy typing 'unusual' characters. You can create characters by holding the compose key (in my case right alt) press a key and then press another key.
eg:
< + 3 = &#9829;
x + o = ¤
x + x = ×
= + C = €
' + e = é
, + c = ç
t + h = þ
d + h = ð
^ + 6 = &#8310;
etc...

(>×.×<)

---

### Post by forrestcupp on 2012-06-09
> **zombifier25 said:**
> Actually, take a look at the Unicode standard. The symbols are categorized pretty neatly.
[size=10]&#119140;[/size]
1D164, by the way. There are more in the range of 1D157 to 1D172.

> **Vaphell said:**
> in charmap bundled with the system you have the unicode blocks listed and the 'musical symbols' block is 1d100-1d1ff

Yeah, I found the music notes in the unicode list. I was just replying to qamelian, who said that on Facebook, you don't need codes to make a heart because typing <3 gets converted into a heart. I was wondering if there is something you can type that gets converted into music notes, or if you have to have a code for that.

---

### Post by tumutanzi.com on 2012-06-09
I did not know there is such a method to type some special characters.

---

### Post by qamelian on 2012-06-09
> **forrestcupp said:**
> How can you type double eighth music notes without an Alt Code?
Not sure, but I found a list of codes recognized by FB:

[https://www.facebook.com/pages/How-To-Make-Symbol-on-Facebook/101512266573583?v=info](https://www.facebook.com/pages/How-To-Make-Symbol-on-Facebook/101512266573583?v=info)

Based on that, it's probably: Alt + 1 + 8

---

### Post by forrestcupp on 2012-06-09
> **qamelian said:**
> Not sure, but I found a list of codes recognized by FB:

[https://www.facebook.com/pages/How-To-Make-Symbol-on-Facebook/101512266573583?v=info](https://www.facebook.com/pages/How-To-Make-Symbol-on-Facebook/101512266573583?v=info)

Based on that, it's probably: Alt + 1 + 8

Well, that's what I was talking about in the beginning. Those are Alt Codes, and they don't work in Linux. Eighth notes and double eighth notes are actually Alt+13 and Alt+14, respectively. But that doesn't work if you're using Linux.

Anyhow, I got the unicode list that does work with Ctrl+Shift+U in Linux. Thanks, guys.

---

### Post by vasa1 on 2012-06-10
> **Vaphell said:**
> in charmap bundled with the system you have the unicode blocks listed and the 'musical symbols' block is 1d100-1d1ff
I like the gucharmap way. Doubleclick on what I want, then click copy in the lower right and paste wherever &#9787;

---

