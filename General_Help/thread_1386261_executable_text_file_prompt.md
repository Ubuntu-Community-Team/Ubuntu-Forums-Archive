---
title: "executable text file prompt"
date: 2010-01-20
forum: General Help
---

### Post by jimmy.eric on 2010-01-20
Hello, I created a bash script to help me mount my network shares.

However when I link the file to the desktop and dbl click on the link it asks me if I want to
```
RUN IN TERMINAL - DISPLAY - CANCEL - RUN
```How can I get it to RUN IN TERMINAL each time I dbl click it?

---

### Post by Cabs21 on 2010-01-20
I think you need to change it from a text based format to a binary format.  i do not know how to do this.  It also might be the wrong direction.  but worth a try.

---

### Post by doas777 on 2010-01-20
add a launcher, pointing to your script. in the launcher config, tell it that it is a "Application in Terminal". taht shoudl do it.

---

### Post by jimmy.eric on 2010-01-20
Thanks! Fast reply and worked perfectly.

---

### Post by wojox on 2010-01-20
If you want to mount them permanently look here

[http://www.makeuseof.com/tag/the-incredible-guide-to-ubuntu-karmic-koala-linux-pdf/](http://www.makeuseof.com/tag/the-incredible-guide-to-ubuntu-karmic-koala-linux-pdf/)

---

### Post by zeroseven0183 on 2010-04-05
I don't know what happened to this machine but I am no longer receiving the prompt to whether Run in Terminal, Display, Cancel or Run every time I double-click an executable file.

Nautilus is set to "Ask each time" under Executable Text Files (Preferences > Behavior) and the file property is also set to "allow executing file as program".

I'm not sure if Ubuntu Tweak, Clamtk or Wine has conflict. Running the file in the Terminal works. ```
bash <filename>
```

What could possibly went wrong?

---

