---
title: "Restart XBMC at wake up/get rid of the cursor?"
date: 2011-04-09
forum: General Help
---

### Post by deckoff on 2011-04-09
I installed XBMC 10.1 “Dharma” on Xubuntu 10.04 with 2.6.38 kernel installed.
I got the cursor bug - when waking up the system from suspend, I got a  cursor stamp in the middle of the screen. I tried with unclutter, but I  cannot use my mouse that way, it keeps going back in the middle of the  screen. Editing xorg.conf makes XBMC run too slow. [IMG]http://forum.xbmc.org/images/smilies/frown.gif[/IMG] So , none of the methods I found solves my problem.
I want to kill XBMC at suspend and start it again at wake up( or kill it  and restart it at wake up). If I do it manually I get no cursor. I dont  know how to do it though, couldnt find any info that can elp me start,  and I am not very good at writing scripts anyway. Any help that can help  me do that or just get rid of the cursor is welcome
THANK YOU

---

### Post by deckoff on 2011-04-13
OK
My only goal now is to restart xbmc after resume. I try:

```
sudo touch /etc/pm/sleep.d/99_RestartXBMC
sudo chmod a+x /etc/pm/sleep.d/99_RestartXBMC
sudo nano /etc/pm/sleep.d/99_RestartXBMC
```

I create the following content:

```
#!/bin/bash
case "$1" in
    thaw)
       killall -9 xbmc.bin ;;
       sleep 5 ;;
       /usr/bin/xbmc ;;
    *)
        ;;
esac
exit $?
```

It does not work for me :(
Any suggestions how to fix this?

---

