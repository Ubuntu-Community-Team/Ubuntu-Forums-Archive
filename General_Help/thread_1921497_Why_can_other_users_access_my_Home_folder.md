---
title: "Why can other users access my Home folder?"
date: 2012-02-06
forum: General Help
---

### Post by ki4jgt on 2012-02-06
I have setup a user for my friends to use on my computer. Mainly because I didn't want them to have access to my files. Ubuntu had this problem back in the day, but then it was fixed. Now it's back again. How do I deny other users the right to be in my files?

I've navigated to /home/jesse from my "friends" account. I am able to see and open EVERY one of my documents.

---

### Post by Vaphell on 2012-02-06
try
```
chmod o-rx $HOME
```
your $HOME will have read and execute permissions for 'other' users removed

---

### Post by sportfreak2020 on 2012-02-06
or you could also use
> sudo chown username:username /home/userhomefolder -R

That should fix things up for you ..

---

### Post by Vaphell on 2012-02-06
change of ownership won't do anything, because he owns his own home already and if that's not the case permissions will stay the same either way (rx for others)

---

### Post by ecopccare on 2012-02-07
by default they have read permissions but not write.  
```
chmod o-rx $HOME
``` will do it, and you can also do it from nautilus, open your home folder, right click a black space, click on permissions, and you get a few options there to play with

---

### Post by HiImTye on 2012-02-07
don't premissions reset for the files the next time they are written?
the best option to hide your home folder is to use an encrypted home folder

---

