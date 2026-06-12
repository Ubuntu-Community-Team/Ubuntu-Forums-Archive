---
title: "Bash shell: Split window?"
date: 2010-03-11
forum: General Help
---

### Post by Systix on 2010-03-11
Hello,

Is it possible to split a bash terminal window in to two colums so you can run and see multiple commands at once instead of having to flick between?

Thanks

---

### Post by nothingspecial on 2010-03-11
```
sudo apt-get install dvtm
```

```
dvtm
```

Press Ctrl+G

Then press C

Now you have two shells in one screen

You can split it multiple times. I like to have 4 "windows"

Once you have 4 press Ctrl+G then G and they will move into a nice little grid fomation.

dvtm has mouse support but you can switch between windows using Ctrl+G then either K or J to toggle forwards and back.

Type man dvtm into one of the windows and have the instructions right infront of you as you use it.

---

### Post by mcduck on 2010-03-11
Another option is to install Terminator, probably a bit more modern approach than dvtm is, as Terminator is based on Gnome-terminal.

[http://www.tenshu.net/terminator/]("http://www.tenshu.net/terminator/") (and yes, it's in Ubuntu's repositories. :))

---

### Post by DaithiF on 2010-03-11
and another option is screen, which is a fantastically useful terminal multiplexer (and which allows for splitting the screen too, either horizontally or vertically)

---

### Post by nothingspecial on 2010-03-11
> **DaithiF said:**
> and another option is screen, which is a fantastically useful terminal multiplexer (and which allows for splitting the screen too, either horizontally or vertically)

Yes, you have tty1-6 + screen + dvtm

It get`s very confusing, esspecialy if you are logged in to multiple ssh sessions on multiple boxes - fun though :p

---

