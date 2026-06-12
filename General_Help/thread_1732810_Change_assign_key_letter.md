---
title: "Change assign key letter?"
date: 2011-04-18
forum: General Help
---

### Post by winning on 2011-04-18
Hi,

I know their are several threads pre-taining to keyboard remapping, however I am a newb, though I hate to admitb, to Ubuntu and I own a Toshiba X205 S7483 laptop running Ubuntu 10.10 32 bit with the latest 
updates installed. I like this os overall but here is my question.

My laptop keyboard letter, "b" has broke and Im copying and pasting when I need to use it. Is there a way how I can change either the assigned b letter key to like one of the alt keys or windows menu keys or fn key?

If so for a newb like myself, how would I go about doing this?

It would cost a ridiculous amount of money to get the single key on my laptop fixed.

Thanks.

---

### Post by TeoBigusGeekus on 2011-04-18
Add this line to your startup scripts to use F1 as b
```
xmodmap -e 'keycode 67=b'
```

See [this]("http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/") for more options.

---

### Post by winning on 2011-04-18
Ok, 

Thank you TeoBigusGeekus for the quick response, where would I go and access the start up scripts? Or can I do this through terminal?

Thanks.

---

### Post by TeoBigusGeekus on 2011-04-18
Look in your home folder. Do you have a .xinitrc file?

---

### Post by winning on 2011-04-18
Ahh,

Yes...Figured it out. Thanks so much. Saved me a huge head ache.

---

### Post by TeoBigusGeekus on 2011-04-18
Glad you've made it - don't forget to mark the thread as solved.

---

