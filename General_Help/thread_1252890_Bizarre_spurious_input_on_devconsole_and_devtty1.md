---
title: "Bizarre spurious input on /dev/console and /dev/tty1"
date: 2009-08-29
forum: General Help
---

### Post by Ubuntaqua on 2009-08-29
Hello all,

My ubuntu 9.04 x86_64 install is experiencing something very strange.

Every time I have a prompt (command line, Firefox adress bar, text editor, ...) a letter (letter "à") appears on the prompt, just as if I had typed it on my keyboard. a new one is typed every 3 seconds, very regularly.

This happens on every input field (even gksu), on virtual consols (ctl-alt-1/2/3...), but NOT when remotely logged in via ssh.

in a terminal :
```
sudo cat /dev/console
```
gives:
```
?
  ?
     ?
        ?
```with "?" being a strange ascii char I know nothing about.
(the same thing with sudo cat /dev/tty1

Nothing interesting to see in the logs.

Does anyone have an idea what this is all about?

Regards,

Olivier

EDIT : unplugging the keyboard has no effect whatsoever.

---

### Post by NoaHall on 2009-08-29
Try using ctrl + alt +1 and running a command from there, see if output is the same.

---

### Post by jon64 on 2009-08-29
Are you remotely accessing your ubuntu install through another machine or from the same machine? If you're remotely accessing your ubuntu machine from another machine try using a different keyboard on the ubuntu machine. Maybe their's something faulty with the hardware.

---

### Post by Ubuntaqua on 2009-08-29
Thanks for your rapid answers...
as already said in the first post :

- local tty (ctl-alt-X) have the same problem, with or without beeing logged in. (if not logged in, the "à" is type normally after "login:"
- the spurious inputs still come after unplugging mouse and keyboard. The keyboard itself is ok
- the spurious inputs do not happen in a ssh console, only when using a direct access (local tty, local gedit, ....)

---

### Post by jon64 on 2009-08-29
That really is odd.. and im definitly not no guru in linux lol... i guess if the keyboard is usb u can try a different port and if its ps2 u can use a ps2 to usb adapter and try that. sorry dood :(

---

### Post by Ubuntaqua on 2009-08-29
> **jon64 said:**
> That really is odd.. you nailed it :)

> **jon64 said:**
> and im definitly not no guru in linux lol... i guess if the keyboard is usb u can try a different port and if its ps2 u can use a ps2 to usb adapter and try that. sorry dood :(kbd is ps2 but thanks anyway. 

Breaking news: it also happens when booting from a xubuntu live CD.
So I guess I'm stuck with a hardware related issue. But I'm nowhere near finding out what exactly causes this.

---

### Post by jon64 on 2009-08-29
Hopefully someone will arrive with some answers for ya :)

---

### Post by Ubuntaqua on 2009-08-29
Thanks, but i nailed it down :
hardware failure :/

My dvb-t card is in the process of dying and is doing so by polluting tty...

rest in pieces..

---

