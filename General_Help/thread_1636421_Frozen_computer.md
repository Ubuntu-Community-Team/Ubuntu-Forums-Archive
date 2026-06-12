---
title: "Frozen computer?"
date: 2010-12-03
forum: General Help
---

### Post by the lemming on 2010-12-03
Hello

Any ideas how you unfreeze a computer?

Last night I decided to download a few games using a different tool to the Synaptic Package Manager.  I can't think of its name at the moment but it gave a brief description of each app with a tiny screen-shot.  I'd like to find out its name but the only thing that will move is the mouse pointer.

I left the computer alone last night thinking that I'd given it too much to do and thought that it would resolve itself when I woke up.  Sadly the computer is still frozen with only the pointer moving around the screen.

Is there any way that I can get the computer back to life?

Or is my only option to hit the Off Button?

Cheers

---

### Post by TNT1 on 2010-12-03
can you "ctrl alt f1" to a tty?

---

### Post by the lemming on 2010-12-03
Something worked.

I got a black screen with text only. It asked me for my login and password. Once I correctly entered them some text came up explaining how lovely Ubuntu is and that its free.

Now I have a blinking curser waiting for me to enter another command.

Any ideas what to do next?

Cheers

---

### Post by TNT1 on 2010-12-03
Try typing ```
sudo /etc/init.d/gdm restart
```

To restart the x server and see id that works. If you can get into tty, then the computer as such isn't frozen, rather x is hanging.

---

### Post by the lemming on 2010-12-03
I am pleased to say that I am now typing this reply from my re-activated ubuntu laptop.  :-)



If I had chosen to hit the Off Button, rather than seek help to restore the desktop, would I have dammaged my operating system?

Cheers

---

### Post by TNT1 on 2010-12-03
> **the lemming said:**
> 


If I had chosen to hit the Off Button, rather than seek help to restore the desktop, would I have dammaged my operating system?



Depends what was cause x to hang. Probably not much damaged, but files can get corrupt or go missing with a hard reboot.

---

