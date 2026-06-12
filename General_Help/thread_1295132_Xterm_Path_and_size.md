---
title: "Xterm Path and size"
date: 2009-10-19
forum: General Help
---

### Post by funky_D on 2009-10-19
Hi everybody!
I'm asking for some help about changing the path of xterm.

I use xterm alot, but everytime i open xterm it opens in a directory that i don't want.. and with a size that i don't want.. so i lose time typing and re-sizing.. 
does anybody knows what file i must edit and what must i write on that file?

thank you very much =)

---

### Post by ajgreeny on 2009-10-19
Surely it will always open in the root of the user who opens it.  I don't think there is any way to change that, but I may be wrong; perhaps a change of the opening command in some way will do it.

I have no idea about the size, it certainly does not understand the option I always add to gnome terminal to get it bigger ```
gnome terminal --geometry 100x36
```

---

### Post by funky_D on 2009-10-19
> **ajgreeny said:**
> Surely it will always open in the root of the user who opens it.  I don't think there is any way to change that, but I may be wrong; perhaps a change of the opening command in some way will do it.

I have no idea about the size, it certainly does not understand the option I always add to gnome terminal to get it bigger ```
gnome terminal --geometry 100x36
```

thanks for your reply,
but it does not opens in the home, it opens in a directory under home, like 

droliveira@metalgear:~/Documents$

and it's xterm not terminal... i think it's different isn't it?

thank you

---

### Post by ajgreeny on 2009-10-19
I was talking about xterm.  I just used the gnome-terminal example as something that might give a clue about how to change the size of the xterm for you.

xterm on my machine always opens in the root of current user, so I have no idea why yours opens in a sub-folder.  Very strange!

---

### Post by uncle-c on 2009-10-19
I'm unsure about how to run xterm  in a directory of your choice, but you can customise xterm colours, font, and size courtesy of the .Xresources file. 
[http://www.debian-administration.org/article/Customizing_your_xterm](http://www.debian-administration.org/article/Customizing_your_xterm)

---

### Post by trungd_t on 2009-10-20
I use -geom 140x40 to adjust the size that I want the window to start in. As for the path. I agreed with others that it always used my home root. However, I've used -ls to force xterm to auto source my bash env files. Try running "env | grep Document" and see if anything specific is pointing there.

Here's my xterm command.

/usr/bin/xterm -vb -sb -ls -sl 20000 -geom 140x40

Hope that helps.

---

### Post by funky_D on 2009-11-12
> **uncle-c said:**
> I'm unsure about how to run xterm  in a directory of your choice, but you can customise xterm colours, font, and size courtesy of the .Xresources file. 
[http://www.debian-administration.org/article/Customizing_your_xterm](http://www.debian-administration.org/article/Customizing_your_xterm)

great stuff! 
i still dont realize why it opens under /home/user/Documents ..

thank you!!! =)

---

