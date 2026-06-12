---
title: "how do I make ubuntu run faster"
date: 2006-05-19
forum: General Help
---

### Post by johnathan on 2006-05-19
Ubuntu boots so slowly to the point of freezing up..... 

I think if I shut some programs running in the background, ubuntu may run faster.....

The problem is that I don't know how to do that....

Is there a way to stop running programs from the terminal..

Thanks!

---

### Post by Nano Geek on 2006-05-19
To stop programs from runing using the terminal, type:```
sudo killall program-name
```That should kill the program.

---

### Post by Shay Stephens on 2006-05-19
You could download sysv-rc-conf
```
sudo apt-get install sysv-rc-conf
```

Then run it
```
sudo sysv-rc-conf
```

Now the tricky part is deciding what you don't want running.  I have not come across any clear recomendations on what is safe to turn off and what needs to stay on.  I mainly have used it in the past to turn off powernowd on my laptop.

Once turned off, it stays off until you turn it back on again.  Make notes of anything you change so you can turn it back on again if needed.

---

