---
title: "Startup without windows' borders, shadows and title bar"
date: 2010-11-25
forum: General Help
---

### Post by typhoon_tip on 2010-11-25
I have searched around but did not find anything similar, so I make a new post.

I have installed Mac4Lin icons, theme and font, and I am using Emerald (with "emerald --replace" command in the window manager of compiz) and everythin is fine.

Some few times (every 4~5 days), when I start the system, it opens up as the title, like Emerald is not starting or something. If I logoff and then logon again, it is fine.

Not that is a serious problem... just annoying in case you want to demonstrate the "power of the system" in an important meeting and it shows up like that.

Anyone ever experienced this or any suggestion where to look for some log about this ?

Thanks,
S.

---

### Post by JustinR on 2010-11-25
Hi,

If you go to Applications > Accessories > Terminal:
```

emerald --replace

```

Does that fix things? I've had problems with Emerald not starting but not very often.

---

### Post by typhoon_tip on 2010-11-25
> **JustinR said:**
> Hi,

If you go to Applications > Accessories > Terminal:
```

emerald --replace

```

Does that fix things? I've had problems with Emerald not starting but not very often.

Yes, if I run in the terminal when there are no borders, it starts normally. But of course as soon as you close the terminal it quits. Looks like sometimes is not starting at all, even tough all the settings are correct.

Is not happening that often, more or less once a week.

I will try out something now: put a manual log message to see at which moment Compiz call the command, perhaps it has something to do with that (maybe starting too early or too late sometimes ?).

;)

---

### Post by JustinR on 2010-11-25
> **typhoon_tip said:**
> Yes, if I run in the terminal when there are no borders, it starts normally. But of course as soon as you close the terminal it quits. Looks like sometimes is not starting at all, even tough all the settings are correct.

Is not happening that often, more or less once a week.

I will try out something now: put a manual log message to see at which moment Compiz call the command, perhaps it has something to do with that (maybe starting too early or too late sometimes ?).

;)

You could try:
```

emerald --replace && exit

```

---

### Post by typhoon_tip on 2010-11-25
> **JustinR said:**
> You could try:
```

emerald --replace && exit

```

Thanks, this does the trick for the terminal ! Useful, so I don't have to logoff and logon again.

I noticed that if you run the command twice it doesn't have any effect, I could perhaps make it in autostart... so if one fail, the other one won't !

---

### Post by pholden on 2010-11-25
If you click on *System > Preferences > Startup Applications* you can create a new startup entry that sets your Emerald theme.

Click the *Add* button, enter a name for the entry and in the *Command* field enter "emerald --replace" :)

---

### Post by typhoon_tip on 2010-11-25
> **pholden said:**
> If you click on *System > Preferences > Startup Applications* you can create a new startup entry that sets your Emerald theme.

Click the *Add* button, enter a name for the entry and in the *Command* field enter "emerald --replace" :)

Yep, tks ! Did that, and called it Emergency Border Startup eheh

By the way, what's the difference between:

```

emerald
emerald --replace

```

In the help it says nothing. It works also without --replace... I am wondering it has something to do with "replacing" compiz borders.

---

