---
title: "I have goofed up!"
date: 2011-05-15
forum: General Help
---

### Post by Bigneil on 2011-05-15
Hi all, I was using the compiz settings application to customize my the way my operating system looks and behaves.  I enabled the cube effects and changed a few other bits n bobs. The tool bar at the top of the page crashed as did the Launcher bar from the left hand side (11.04).  So i restarted my computer and now the tool bar and launcher have disappeared and i can not access any programs or applications....nothing. I was able to launch firefox by clicking on a document that was on my desktop and choosing open with other application then choosing firefox.

so i need to find some way of re-instating the default setting for compiz/appearance or whatever makes the toolbar and launcher work.

I'm sorry if my lack of correct jargon makes it difficult for you to understand what i'm trying to explain.

I have been using Ubuntu for years and have usually been able to work through any problems sometimes with a little forum help,  this one has got me stumped...I cant even open a console !


would it help to start my computer up into safe mode?

---

### Post by Sina_RJ on 2011-05-15
i think for fixing you first need to have a full screen and as far as i know that'll be helpful

EDIT: by doing this your window manager will restart and change into metacity which is the ubuntu's default

```
metacity --replace
```
and the shortcut for terminal is alt+ctrl+t
tell us about the result

---

### Post by shadowwyvernx on 2011-05-15
Does <CTRL>+<ALT>+<F1> (or another low-numbered Function key give you a terminal?

---

### Post by Kschikan on 2011-05-15
If you can get access to the terminal (sometimes by changing your display using Ctrl-Alt-F1 or Ctrl-Alt-F2... I believe F7 is the normal graphical display), you can use apt-get to reinstall compiz, which will hopefully install the default configuration.

something like:
```
sudo apt-get remove compiz
sudo apt-get install compiz
```

---

### Post by Bigneil on 2011-05-15
Thanks for your replies, those short cuts are great...why didn't i memorize them   Doh!

so now i can use the terminal, or the ctrl-alt-F1 black screen thing.

I tried using apt-get to uninstall then re-install compiz which switched the cube back off, so it did do something.  I tried the metacity --replace too but recieved an error.

"windows manager error"  then somthing like "unable to access x server" ..I cant remember the exact wording and i have to restart the computer after using the tty1 screen cause when i use ctrl-alt-F7 to come back to normal, it freezes up.


what else can i try?

---

### Post by 5149.5 on 2011-05-15
Try the following:

```
Alt+F2 then enter : Unity --reset
```

---

### Post by Bigneil on 2011-05-15
> **5149.5 said:**
> Try the following:

```
Alt+F2 then enter : Unity --reset
```



That did the trick!  thankyou:)

---

### Post by Bigneil on 2011-05-15
there is some really glitchy stuff going on with the compiz and the unity thing... lots of conflicts and crashes.

---

### Post by 5149.5 on 2011-05-15
> **Bigneil said:**
> there is some really glitchy stuff going on with the compiz and the unity thing... lots of conflicts and crashes.

You are correct. It seemed like every time I did something in Compiz, I would crash Unity. They are like oil and water. What were the devs. thinking?

---

