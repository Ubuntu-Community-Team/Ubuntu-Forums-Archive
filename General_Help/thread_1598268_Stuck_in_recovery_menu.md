---
title: "Stuck in recovery menu"
date: 2010-10-16
forum: General Help
---

### Post by rouwad on 2010-10-16
Hi, I've upgraded to ubuntu 10.10 and now I can't get into it I'm stuck at the recovery menu, selecting resume or failsafeX will eventually bring me back to it, if I select root then I wouldn't know what to do except for typing Sudo reboot which brings me back to the to the Recovery menu, I'm stuck in a loop.

Also, at boot time  I get something like VGA 773 is deprecated  set gfxpayload=1024x768 before linux command
I have an Nvidia GTX285 card and had already installed the latest driver I think it is 260 something
I should mention that i have a double boot system with windows 7 which starts just fine when selected
I'm new to ubuntu, started about 3 month ago and don't know much about it, is there a way to reinstalling it from the command line?

Any help will be greatly appreciated.

---

### Post by rouwad on 2010-10-16
I'm still stuck in that loop :)
Is there a way out, like using a generic VGA driver just to get in.

---

### Post by P4man on 2010-10-16
Did you ever got to boot in to 10.10 or did the upgrade go wrong?
Is this a wubi install (installation launched from within windows, and ubuntu installed on the windows partition) or a regular one?

Anyway, it wont hurt to try this in a the root terminal:

```
dpkg --configure -a
```

---

### Post by rouwad on 2010-10-16
Hi P4man, and thanks for looking into this.

it's not a wubi install, I did an upgrade install from 10.04 and everything went thmoothly except that the system would hang every few minutes for a few seconds so I updated my Nvidia driver and that's when the problem started.

In the past few minutes I was able to find a solution (I think)  what I did is

```

sudo nano /etc/grub.d/00_header

```Looked for


```
if [ ${recordfail} = 1 ]; then      set timeout=-1  else     set timeout=${GRUB_TIMEOUT}  fi


```changed it to

```
#if [ \${recordfail} = 1 ]; then    #    set timeout=-1    #else        set timeout=${GRUB_TIMEOUT}    #fi 
```then I did
```
sudo update-grub 
```I got this info from [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail)


I'm not sure what this does or if I need to change it back (uncomment it) but at least now I'm out of the loop and everything seems to work normally, I still need to test it further

---

### Post by P4man on 2010-10-16
cool, nice find. 

What that change seems to do is disable a grub feature that detects a failed boot and force you in to recovery mode. Dont undo that change before clearing the (erroneous) failed boot flag by running

```
sudo grub-editenv unset recordfail
```

That said, Id just leave it like that. Sounds like another attempt to idiot proof something that ends up making it less usuable. Isnt there a saying, if you make something idiot proof, only an idiot will want to use it ? :)

---

### Post by rouwad on 2010-10-16
When it comes to Linux I am an Idiot, and it did not proof with me :)
Damn I've been fiddling with this for about 6 hours before I found something that worked.
I think this issue is solved for now.
Thanks again P4man

---

