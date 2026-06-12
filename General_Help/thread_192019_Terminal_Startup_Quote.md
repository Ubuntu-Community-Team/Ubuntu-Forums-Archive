---
title: "Terminal Startup Quote"
date: 2006-06-08
forum: General Help
---

### Post by Lunar_Lamp on 2006-06-08
I remember on my old SUSE box I had the terminal setup so that when I opened a new terminal window, I would be greeted with a random quote from a stored database.

I have done a search in synaptic, and not particularly surprisingly I couldn't find it - as I don't know what it was called.

Does anyone know what it was/is called - and would you point me in the right direction please!

---

### Post by Kilz on 2006-06-08
[QUOTE=Lunar_Lamp]I remember on my old SUSE box I had the terminal setup so that when I opened a new terminal window, I would be greeted with a random quote from a stored database.

I have done a search in synaptic, and not particularly surprisingly I couldn't find it - as I don't know what it was called.

Does anyone know what it was/is called - and would you point me in the right direction please![/QUOTE]
Do you mean a "tip of the day"? If so I think Konsole dose that, its the KDE terminal.

---

### Post by Lunar_Lamp on 2006-06-08
No, not a tip of the day, but a similar sort of idea.

It was text within the terminal, so the terminal when opened would like:

```
"Amusing quote here" by The Person Who Said It.
user@box~$
```

---

### Post by thingy on 2006-06-08
The program is called "fortune-mod" in the normal repositories and "fortunes" in the universe repository.

To get it to output a random fortune, just run the program. To get it to do it when you start a console, add a line like /usr/blah/bin/fortune  to your ~/.bashrc (or the config file for what ever shell you use)

jin

---

### Post by thasheep on 2006-06-08
There's a fortune-like prog called sex that spurts random vulgar and potentially amusing messages. You can download the source from [http://spatula.net/software/sex/](http://spatula.net/software/sex/) but I've compiled it. Download [http://213.100.40.206/ubuntu/sex-1.0/sex](http://213.100.40.206/ubuntu/sex-1.0/sex) and move it and make it executable```
sudo mv /path/to/sex /usr/local/bin/
sudo chmod 755 /usr/local/bin/sex
sex
sex -w
```-w wraps the display.
Another 'useful' app is cowsay, it puts some message in a speech or thought (read the man page) bubble from an ascii cow. Useful if you want to blame someone else "the cow said it!". eg ```
fortune | cowsay
 -----------------------------------------
/ But if you wish at once to do nothing   \
| and to be respectable nowdays, the best |
| pretext is to be at work on some        |
| profound study.                         |
|                                         |
| -- Leslie Stephen, "Sketches from       |
\ Cambridge"                              /
 -----------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

---

