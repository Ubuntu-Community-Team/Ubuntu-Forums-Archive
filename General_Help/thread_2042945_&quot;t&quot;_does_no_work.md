---
title: "&quot;t&quot; does no work"
date: 2012-08-15
forum: General Help
---

### Post by The musmula on 2012-08-15
I have no idea what is happening, while I am writing his I cant use the "t" character I am helping myself with he character map, anyway I thought it is a problem with my keyboard, but no, I tried to input "t" with onboard but it does not help, the only place where it works is the "Dash Home", what to do? I am a website designer how to design and input text without "t"???

---

### Post by HermanAB on 2012-08-16
I have had the same problem in the past.  It is due to a bug in Xorg.  You can restore the missing character function using xmodmap.

[https://www.google.com/search?hl=en&q=xmodmap+howto](https://www.google.com/search?hl=en&q=xmodmap+howto)

Basically, you need to determine the keycode, then use xmodmap to reset it.

---

### Post by The musmula on 2012-08-16
mmmmm....yeah, what?

I have opened the terminal >xmodmap -pke >found "t", it is keycode 28.

now my question is: what to do now, what to replace?

---

