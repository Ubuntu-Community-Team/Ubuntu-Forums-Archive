---
title: "Problem with UTF-8, finch and Putty"
date: 2010-10-27
forum: General Help
---

### Post by Pacane on 2010-10-27
Hi,

I have a problem when I ssh to my Ubuntu server with Putty and try to use finch (console based pidgin...)

The lines are drawn like this:
[IMG]http://imgur.com/rdcUt.png[/IMG]

when I'm using putty's translation option, set to UTF-8.

When I'm using ISO-XXXX-Western, the lines are drawn correctly, but I can't see accentuated characters (And since my main language is french, it's not really cool...)

Not only this happens on finch, but on other applications too, like tmux.

I've been trying different fonts (ie courier new, lucida console...) but that didn't work.

I've been trying to change my environment variables:
$LANG, $LC_ALL to en_US.UTF-8.. (I've seen it somewhere on Google), but it didn't work...

Right now my environement variables are set to nothing...
I used:```

export LANG=
export LC_ALL=

```

Note1: Works fine on gnome-terminal (draws lines + accentuated characters fine), using ssh, on my other linux desktop... (LANG = "nothing" and LC_ALL="nothing" too...)


So, I'm here to ask for new ideas, since I've been looking forward to fix this for hours now.

---

### Post by Pacane on 2010-10-28
Could a moderator move this to the correct section if it's not well classified, and if someone could tell me if there's a place for putty support (irc channel, etc...) thanks.

---

### Post by Toadicus on 2011-01-26
Did you (or anyone else reading this) ever find a solution to this?  I would love to get both UTF-8 and pretty lines in finch over putty.

Thanks!

---

### Post by Pacane on 2011-01-26
Negative, I'm still looking for a solution unfortunately. I've even been on the finch support channels on IRC and nobody has been able to find a solution.

---

### Post by eskarion on 2011-01-30
If you start finch in screen, it should work properly. 

```
screen -S finch finch
```

---

### Post by Pacane on 2011-01-30
Indeed it works... Although I'm using TMUX, I'll try to find a similar switch for TMUX, thanks A LOT though :)

---

### Post by Hossbeast on 2011-09-23
Yes, pidgin/PuTTY with UTF-8 translation + screen makes it work !

---

