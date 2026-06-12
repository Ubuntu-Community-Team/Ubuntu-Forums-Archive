---
title: "Flash and I have fallen out and flash is winning"
date: 2010-04-10
forum: General Help
---

### Post by aquafocus on 2010-04-10
Can someone please help.

I'm running opera and although flash works on some pages it doesn't on others. e.g. my wife plays farmville a lot and the game will open but will do nothing else. If you click on the screen, nothing happens.

This happens on all flash games.

I've tried switching user, tried firefox but can't get it to work.

PLEASE can someone help because this is driving me insane!

Cheers

Simon

---

### Post by aquafocus on 2010-04-10
A bit of an update. It appears that flash is working but the mouse is 'out of sync' i.e. the desktop cursor is in one place and the flash cursor is somewhere else.

Can anyone help please?

---

### Post by thadacto on 2010-04-10
I had the same type of problem when I wrote a small educational game and then gave it to a friend to try. The problem was the screen resolution and although the mouse was over an object and he clicked the mouse it didn't actually activate the object. We changed the resolution and bingo - it all worked. However, it wasn't with flash.

---

### Post by Agent ME on 2010-04-10
I had a similar problem before. (Are you on a 64-bit system by chance? The default flash on there is a bit less than perfect. Either way, I think this should help.) I fixed it by using a newer (beta) version of flash from this [repository](https://launchpad.net/~brandonsnider/+archive/experimental-flash).

You can install it by copying and pasting this terminal command into a terminal, and then exiting and restarting your browser if it's open. You might have to confirm the upgrade by typing y or yes in the terminal.
```
sudo sh -c "add-apt-repository ppa:brandonsnider/experimental-flash && apt-get update && apt-get upgrade"
```

If Flash works worse after that, you can revert by disabling the experimental-flash repository in Synaptic Manager under Settings->Repositories->Other Software and unchecking it, hit close, hit the reload button, search "flash", and remove "flashplugin-installer", and then install it again.

---

### Post by aquafocus on 2010-04-10
Thanks for the replies.

I've tried doing exactly what you said Agent, and it installed something but still doesn't work.

Does this mean that Opera is still using flash and not this new alternative?

---

### Post by Agent ME on 2010-04-10
It's just a slightly newer version of Flash (and on 64-bit machines, it's the proper 64-bit version instead of just a wrapper around the 32-bit version). I would imagine Opera uses it too. You must've had a slightly different problem than me if that didn't fix it.

---

### Post by aquafocus on 2010-04-10
Thanks for trying to help Agent but it's still not working.

---

### Post by NCLI on 2010-04-10
Try another browser, like Firefox, to see whether it's just a problem with Opera.

---

### Post by aquafocus on 2010-04-10
I'm only using opera as of today because firefox crashed everytime I tried to view a page with flash on.

---

### Post by aquafocus on 2010-04-12
If anyone is interested, here's what happened:

[http://ubuntuforums.org/showthread.php?p=9112946]("http://ubuntuforums.org/showthread.php?p=9112946")

All fixed now :)

---

