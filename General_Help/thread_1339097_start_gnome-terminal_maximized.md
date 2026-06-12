---
title: "start gnome-terminal maximized"
date: 2009-11-27
forum: General Help
---

### Post by Andreas1 on 2009-11-27
i would like gnome-terminal to be maximized when i start it. any way to do that? trying google i couldn't find anything.

just to be clear:
NOT fullscreen NOT almost maximized NOT using compiz

---

### Post by QLee on 2009-11-27
[QUOTE=Andreas1]i would like gnome-terminal to be maximized when i start it. any way to do that? trying google i couldn't find anything.[/QUOTE]

Wow, that is perplexing, when I googled it I got lots of hits, including some from the Ubuntu forum. I would expect that you would find some if you used the search function of the forum.

[QUOTE=Andreas1]just to be clear:
NOT fullscreen NOT almost maximized NOT using compiz[/QUOTE]

You can specify whatever geometry you want for the terminal if you start it with the "--geometry=" option.

It doesn't occur to me what you would want with a terminal covering all your screen space if you have a fairly modern monitor, and there's no reason I need to know, but you could do it if you choose to.

---

### Post by Andreas1 on 2009-11-27
> **QLee said:**
> Wow, that is perplexing, when I googled it I got lots of hits, including some from the Ubuntu forum. I would expect that you would find some if you used the search function of the forum.

yes, i got lots if hits, mainly people asking the same question, and the only solution i found is what you too suggested:

> **QLee said:**
> You can specify whatever geometry you want for the terminal if you start it with the "--geometry=" option.

It doesn't occur to me what you would want with a terminal covering all your screen space if you have a fairly modern monitor, and there's no reason I need to know, but you could do it if you choose to.

that's what i meant by "almost maximized", the --geometry option only allows for numbers specifying the size of an unmaximized window, not the same, as can be seen in the screenshot:

---

### Post by sisco311 on 2009-11-27
[uhelp]community/Devilspie[/uhelp]

Install it:
```
sudo apt-get install devilspie
```

Create a rule for gnome-terminal:
```
mkdir ~/.devilspie
gedit ~/.devilspie/gnome-terminal.ds
```

```
(if (is (application_name) "Terminal")
  (begin
    (maximize)
  )
)

```

Go to gnome-terminal -> Edit -> Profile Preferences -> Title and Command tab and set the *Title* to *Terminal* and *When terminal commands set their own titles* to *Prepend initial title*.

Press Alt+F2 and run:
```
devilspie
```

Go to System -> Preferences -> Startup Applications and add devilspie to the startup apps.

---

