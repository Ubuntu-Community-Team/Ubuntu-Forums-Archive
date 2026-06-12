---
title: "Caps Lock Key, disable it, or change it"
date: 2010-09-29
forum: General Help
---

### Post by old farmer on 2010-09-29
Is there a way of changing the Caps lock key to a shift key?
The caps LOCK key , to me, is the most useless key on the keyboard.
Here is a program for Windoze that I use, [http://www.ihatethecapslockkey.com/](http://www.ihatethecapslockkey.com/)
Thanks

---

### Post by luigi_mb on 2010-09-29
> **old farmer said:**
> Is there a way of changing the Caps lock key to a shift key?
The caps LOCK key , to me, is the most useless key on the keyboard.
Here is a program for Windoze that I use, [http://www.ihatethecapslockkey.com/](http://www.ihatethecapslockkey.com/)
Thanks

Here is how I _disabled_ capslock:

```

$ gedit ~/.Xmodmap 

```

If the file is blank, just add the line (minus the quotation marks):

"clear Lock"

Log out/in . A window will asks whether to load Xmodmap; highlite the name and click on Load. 

Capslock is now disabled.


/luigi

---

### Post by mike555 on 2010-09-29
You could install "Xkeycaps" , start from terminal ..it will let you change most any key to any key ...

---

### Post by old farmer on 2010-09-29
> **mike555 said:**
> You could install "Xkeycaps" , start from terminal ..it will let you change most any key to any key ...

THanks, I like that
hmmmmm.... change any key..........

hehe

:-k

---

### Post by silbar on 2011-03-11
> **luigi_mb said:**
> Here is how I _disabled_ capslock:

```

$ gedit ~/.Xmodmap 

```

If the file is blank, just add the line (minus the quotation marks):

"clear Lock"

Log out/in . A window will asks whether to load Xmodmap; highlite the name and click on Load. 

Capslock is now disabled.


/luigi

Well, I did all that and got the window, but it didn't disable the key.
Hmm, maybe I didn't highlight the name?  But on re-logging in, now I don't get a window.

  r. r. SILBAR (see?)

---

### Post by silbar on 2011-05-15
Greetings, again,

This issue is solved, for me at least.  I don't know where I found this, but it was probably somewhere on this forum:

System > Keyboard > Layouts > USA > Options > Capslock key behavior

and then click on the "Capslock is disabled" option.

   Rico Silbar

---

### Post by PaulW2U on 2011-05-15
> **silbar said:**
> This issue is solved, for me at least.  I don't know where I found this, but it was probably somewhere on this forum:

System > Keyboard > Layouts > USA > Options > Capslock key behavior

and then click on the "Capslock is disabled" option.

That also works for UK keyboards and probably all other countries too. There's a lot of options there that could keep you amused for hours. But remember to take the lock off before changing the option, otherwise you'll be stuck in upper case like I was!

---

### Post by dr_leviathan on 2011-06-18
I spent a lot of time trying to disable the Caps Lock key in xfce and none of the xmodmap advice was working.  Eventually I found this forum thread with a real solution:

[http://ubuntuforums.org/showthread.php?t=1782212](http://ubuntuforums.org/showthread.php?t=1782212)

---

### Post by idoitprone on 2011-06-18
save the code to a file of you choice

```
! xmodmap file
! for me only linux blah
 
! change Caps_Lock to Shift
 
 
clear Lock
keysym Caps_Lock = Shift_L
add shift = Shift_L
```

```
xmodmap filename
```

If programmer made all the decisions, we might as well be use dvorak keyboard. Stupid corporations and typewriters

---

