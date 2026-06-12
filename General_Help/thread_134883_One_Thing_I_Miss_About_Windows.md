---
title: "One Thing I Miss About Windows"
date: 2006-02-22
forum: General Help
---

### Post by Mark76 on 2006-02-22
Is having the option of having my IM clients start automatically whenever I booted up.

---

### Post by Vladimirm on 2006-02-22
You can do that, i know you can in Gaim and in Kopete,
What IM are you using?

---

### Post by suRoot on 2006-02-22
From the menu, go System -> Preferences -> Sessions.  Click the startup programs tab & click add... add the command you want to have start up.  For example, gaim would be /usr/bin/gaim.  Probably want to leave the order at default or maybe a little higher.

Hope that helps.

Edit:

If you aren't sure of the location of a program, you can type

```
which [progname]
```
...to get the location on the filesystem...

for example,
```

echo-base:/home$ which gaim
/usr/bin/gaim
```

of course this should be totally unnecessary if the program is in your path, but just in case you have some oddball app that isn't.

---

### Post by bored2k on 2006-02-22
[QUOTE=suRoot]From the menu, go System -> Preferences -> Sessions.  Click the startup programs tab & click add... add the command you want to have start up.  For example, gaim would be /usr/bin/gaim.  Probably want to leave the order at default or maybe a little higher.

Hope that helps.[/QUOTE]
Using gaim instead of /usr/bin/gaim works.

---

### Post by Mark76 on 2006-02-22
Not for me it wouldn't.

And, yes it did work. Ta Su. \\:D/

---

### Post by z_diver on 2006-02-22
How about logging in, starting up gaim... then logging out and selecting "Save current setup" on the logout screen?

Edit: Nevermind.  I think I mistook the order of your answers.  I guess it's already working for you.

---

### Post by Mark76 on 2006-02-23
I also added Opera.  So now when I turn my computer on my IM client and my favourite browser both start up automatically :D

---

### Post by annsachd on 2006-02-23
That's funny.

---

### Post by Mark76 on 2006-02-23
Well, you certainly can't do that in Windows, unless it's an option (add to systray) in the application.

---

### Post by MasJ on 2006-02-23
Actually, you can. You can add it to the "Startup" program group. However, I find that scheduling commands on linux is awesome in comparison to Windows. Windows doesn't schedule stuff that well =/
I think that's because the linux commandline is very powerful in comparison to Windows, you can do almost everything from the commandline, hence the utility of scheduling the way you want :).

---

### Post by Mark76 on 2006-02-23
The session thingy helps too :)

---

