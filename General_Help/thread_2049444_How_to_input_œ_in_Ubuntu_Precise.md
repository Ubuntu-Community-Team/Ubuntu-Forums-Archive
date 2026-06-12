---
title: "How to input œ in Ubuntu Precise?"
date: 2012-08-28
forum: General Help
---

### Post by KenSharp on 2012-08-28
Can someone help me out here?

I am trying to figure out how to input the **œ** (ethel) character using the keyboard.

For example **æ** (ash) is very easy: **Alt Gr + A** but I cannot figure out a shortcut for œ.

At the moment I have to copy and paste from the Character Map, which isn't ideal.

[http://en.wikipedia.org/wiki/%C5%92#Inputting_.C5.92_and_.C5.93](http://en.wikipedia.org/wiki/%C5%92#Inputting_.C5.92_and_.C5.93) was no help.

---

### Post by squenson on 2012-08-28
I am not sure whether it is a standard method, but if I press then release the keys AltGr, a, e, I get the æ letter. Œ is AltGr, O, E.

---

### Post by KenSharp on 2012-08-28
Thanks for the hint! I get a slightly different result:

Alt Gr + A, E = æe
Alt Gr + O, E = øe

Yet

Alt Gr + Shift --> (release) --> a, e = æ
Alt Gr + Shift --> (release) --> o, e = œ

And, of course, if I keep Alt Gr + Shift held down I get Æ and Œ.

An odd combination, but that's that solved. Thanks! :D

---

### Post by Pand5461 on 2012-08-28
It's all about the Compose Key. You can customize it through System Settings -> Keyboard -> Layout Settings -> Options -> Compose key position.

Compose key allows you to enter complex characters by sequential pressing of some letters.
Compose + a + e = æ
Compose + o + e = œ
Compose + A + E = Æ
Compose + a + " = ä
etc.
[Here]("http://www.hermit.org/Linux/ComposeKeys.html") is the full list of Compose key sequences.

---

### Post by KenSharp on 2012-08-28
**VERY** useful, thankyou!

---

### Post by SLIREAND on 2012-08-28
Although it's cumbersome, you can enter any and every character using Unicode.

Using Ubuntu, hold down th SHIFT & CTRL Keys whilst entering "U" plus the hexadecimal code eg o153 for "œ".

An excellent article on inputing unicode can be found on Wikipedia.

Regards, Slireand.

---

### Post by KenSharp on 2012-10-08
Thanks, SLIREAND, that's useful too! :)

Anyone know how to add key combinations?

For example. I would like to add Alt Gr + ? = &#8253;, which isn't currently in use. Trying to remember the Unicode numbers is a headache.

---

