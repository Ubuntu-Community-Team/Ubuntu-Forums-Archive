---
title: "cannot add/edit shortcuts!"
date: 2010-08-29
forum: General Help
---

### Post by ropa8942 on 2010-08-29
Hi all,

I'm a xubuntu 10.04 user and i recently tried to create a keyboard shortcut to launch the Terminal. I went into Settings -> Xfce Settings Manager -> keyboard
I chose the "application shortcut" tab and there I realized that the "add" function behaves very strangely. A window pops upp with a text entry that lets me add a command name, but nothing to enter the shortcut's name. Anyhow, whatever I write in there, the window closes when I enter OK and nothing more happens.
I also tried to change the shortcuts from the Window Manager and nothing can be edited there either. 

I read about people experiencing similar problems with xubuntu lucid, but so far I found nothing about how to solve them.

any help is very welcome

 Thanks

---

### Post by David Andersson on 2010-08-29
> **ropa8942 said:**
> 
I chose the "application shortcut" tab and there I realized that the "add" function behaves very strangely. A window pops upp with a text entry that lets me add a command name, but nothing to enter the shortcut's name. Anyhow, whatever I write in there, the window closes when I enter OK and nothing more happens. 


What you should get when you click OK after entering the command is a new dialog "Command Shortcut" that simply will record the key combination you type next. It has a Cancel button if you regret.

If you can not get it to work, you may use xbindkey as a workaround. Install xbindkey and create a file ~/.xbindkeysrc containing (for example) the text:

```

"xfce4-terminal"
  control+shift + F11

```

(Xbindkeys should reload ~/.xbindkeysrc automatically when it changes, but I have to restart it using "pkill xbindkeys" and "xbindkeys".)
(Xbindkeys can bind keyboard and mouse buttons.)

---

### Post by ropa8942 on 2010-08-30
Thanks Daid for your answer.

It works wonderfully with xbindkeys. :D So, that was a good tips you gave to me.

Still, I wonder why the editing is impossible using the nice user-friendly ui that is provided by xfce. :confused:
Does anybody experience the same problem? Is there a way to fix it up?

Cheers
     \Romain

---

### Post by ropa8942 on 2010-08-30
Hi again,

ok, I moderate my enthusiasm for xbindkeys. You have to run the "xbindkeys" command in the terminal at least once before the shortcuts you edited start to be active. 
In my case I want to run the terminal, so I first have to open it from the Accessories, run the command, close the terminal window and open it again with the shortcut :tongue:
 
Did I miss something? I guess the developers of this xbindkey app are smarter than me, so it should be one.

Any clue?

thanks

---

### Post by David Andersson on 2010-08-31
> **ropa8942 said:**
> 
In my case I want to run the terminal, so I first have to open it from the Accessories, run the command, close the terminal window and open it again with the shortcut :tongue:


Yes, isn't it wonderful, the terminal. I *love* it. :)

You can autostart xbindkeys either
1) add this line to the file **~/.xinitrc** (the & is important):
```
xbindkeys &
```
2) **or**, goto **Settings > Session and Startup > Application Autostart** and add xbindkeys.

(I have not tried them. I *love* to start xbindkeys from the terminal.)

---

### Post by ropa8942 on 2010-09-02
Tack för tipset!

> I *love* to start xbindkeys from the terminal.I have a hard time to determine wether this is ironic. :-s
However it works and I'm thankful for that.

I'm still open for any explaination about why the setting's manager doesn't work properly.

Cheers

---

### Post by David Andersson on 2010-09-04
> **ropa8942 said:**
> Tack för tipset!

För all del. Varsågod!

> **ropa8942 said:**
> 
I have a hard time to determine wether this is ironic. :-s


You'll never know :)

[QUOTE=ropa8942]
I chose the "application shortcut" tab and there I realized that the "add" function behaves very strangely. A window pops upp with a text entry that lets me add a command name, but nothing to enter the shortcut's name. Anyhow, whatever I write in there, **the window closes when I enter OK and nothing more happens**.
[/QUOTE](My bold)

That window *should* close, but you *should* get a *new window*, that picks up the next key or key-combination. If you don't, I don't know why. Speculation: maybe it is hidden behind something. Have you installed another window manager, that handle focus differently, or configured focus in unusual ways?

---

### Post by ropa8942 on 2010-09-06
Hi,

> That window *should* close, but you *should* get a *new window*, that picks up the next key or key-combination.

Yes, I get that! But there is no text box or anything that would allow me to chose a key-combination.
My only option there is to press the cancel button. then nothing...
So, the window is not hidden it is only plain-non-functional.

> Have you installed another window manager, that handle focus differently, or configured focus in unusual ways? 	

 Not as far as I know. I can't think about any time when I could have done that by mistake. I installed Xubuntu recently and havn't done anything far above my understanding.

Well, thank you again David for keeping that thread alive.

---

