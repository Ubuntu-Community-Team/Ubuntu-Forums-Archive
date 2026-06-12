---
title: "Disabling Compiz through terminal; need help badly"
date: 2009-12-02
forum: General Help
---

### Post by Saronn on 2009-12-02
I was experimenting with the Compiz Effects, and I turned on Reflection. There was an option for "reflection windows(?)" that was unchecked, so I checked it. It froze my computer, so I restarted with high hopes. As soon as I logged in and the wallpaper appeared, it froze.

I need help to disable Compiz through the terminal, since all I can do is the "failsafe terminal".

I'm using my brother's computer, and I really need help.

My computer is running 9.04, btw.

---

### Post by fluffman86 on 2009-12-02
if you can press ctrl+alt+f1 after the desktop freezes, then try:
sudo killall -9 compiz*

Otherwise, remove compiz, purge the configure files, and reinstall:
sudo apt-get remove --purge compiz* && sudo apt-get install compiz

---

### Post by lidex on 2009-12-03
Try this command 
```
metacity --replace
```

---

### Post by steveneddy on 2009-12-03
> **lidex said:**
> Try this command 
```
metacity --replace
```

This is the answer, then 

```
startx
```

I believe, unless you can still view the GUI, then just the **[COLOR="Blue"]metacity --replace[/COLOR]** command should work fine.

---

### Post by Saronn on 2009-12-03
> **fluffman86 said:**
> if you can press ctrl+alt+f1 after the desktop freezes, then try:
sudo killall -9 compiz*

Otherwise, remove compiz, purge the configure files, and reinstall:
sudo apt-get remove --purge compiz* && sudo apt-get install compiz

Wow. I can't believe that worked. Why hasn't the other 30 threads I've looked at not mention that? D:

Anyways, to metacity --replace, I've seen that lots, but it did absolutely nothing for me.

So, solved.

---

### Post by lidex on 2009-12-03
> Wow. I can't believe that worked. Why hasn't the other 30 threads I've looked at not mention that?

Why are your keys always in the last place you look? :rolleyes:

You can mark the thread as solved using "Thread Tools" above your first post

---

### Post by running_rabbit07 on 2009-12-03
> **Saronn said:**
> Wow. I can't believe that worked. Why hasn't the other 30 threads I've looked at not mention that?.

Right place at the right time with the right people replying.:)

---

