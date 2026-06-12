---
title: "Unwanted Visual Effects"
date: 2010-06-01
forum: General Help
---

### Post by Greasyfingers on 2010-06-01
Using Lucid.

I prefer a simple desktop, without any visual effects, so I have Appearance -> Visual Effects set to 'None'.

But suddenly, all my windows have a shadow around them, and panel launchers visually 'ping' when I click on them. This is as if I had changed the Visual Effects setting, which I haven't, and I can't think of anything else that I changed when this started happening.

I'm guessing this means that Compiz has somehow stepped in as my window manager. I've tried [FONT="Courier New"][SIZE="2"]$ metacity --replace[/SIZE][/FONT] to no effect, and I've tried selecting the other options in Appearance -> Visual Effects, and then re-setting it to 'None', but it doesn't get me back to the plain-and-simple desktop I prefer.

Is there a configuration file I can alter, or some other way of rectifying this?

---

### Post by HereInOz on 2010-06-01
Have you tried uninstalling Compiz?  It is installed by default, but that doesn't mean you have to leave it there.  to my knowledge there are no ill effects felt from removing it.

---

### Post by Greasyfingers on 2010-06-01
I've just uninstalled everything compiz related in Synaptic - 8 packages[*] - but the problem remains, so I guess I was wrong to assume it was a compiz issue.

But I'm puzzled - I didn't think Metacity had any visual effects like these, but System Monitor says that it is Metacity running, and when I kill it, the effects disappear, but so does any window management. Restarting Metacity gets things working again, but with the additional visual effects.

I can probably live with the window shadows, but I shall go mad if the panel launchers 'ping' at me for much longer.

[*] compiz, compiz-plugins, compiz-gnome, compiz-core, compiz-fusion-plugins-main, compiz-config-backend-gconf, libcompizconfig0, libdecoration0

---

### Post by dino99 on 2010-06-01
change the look and feel by changing the used theme

---

### Post by Greasyfingers on 2010-06-01
Thanks, but the theme isn't the issue, it's the Visual Effects.

---

### Post by stinkeye on 2010-06-01
> **Greasyfingers said:**
> Thanks, but the theme isn't the issue, it's the Visual Effects.

If you have compositing manager enabled for metacity, this will draw shadows, and give panel launchers a visual ripple effect.

gconf-editor > /apps/metacity/general/compositing_manager

Some of the docks (eg Docky) require compositing to run.

---

### Post by Greasyfingers on 2010-06-01
That's fixed it.

Thanks for that - much appreciated

---

