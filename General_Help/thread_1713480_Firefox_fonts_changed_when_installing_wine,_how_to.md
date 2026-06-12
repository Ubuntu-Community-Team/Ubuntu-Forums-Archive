---
title: "Firefox fonts changed when installing wine, how to change back?"
date: 2011-03-24
forum: General Help
---

### Post by Arndt on 2011-03-24
I use Ubuntu 10.04. I'm not sure what other info is relevant, Gnome, I suppose.

Yesterday I installed wine-1.2 (using Synaptic), in order to be able to build programs for Windows. This in itself seemingly succeeded, but as a result of the installation, fonts in Firefox changed (one can say immediately - when the installation was done, the fonts had changed).

For example, in this forum, the non-monospaced font changed in some way I can't put my finger on. Right now, posts feel less readable, but getting used to it may just be a question of time.

Some other pages (in existing tabs, and when looking them up again) changed the font size, some increased the size, some decreased it. This can be fixed by using Ctrl-+ or Ctrl-- quite easily, but <whine> I would like these kind of changes not to happen at all </whine>.

I uninstalled wine (not removed completely - I don't know what the difference is), but this didn't undo the font change.

The font settings within Firefox (Preferences) don't seem to have been changed.

The point of this post is to ask what may have happened, where such dependencies between fonts are stored, and how to undo the change, in case I'd like to.

---

### Post by Arndt on 2011-03-25
bump

---

### Post by ~Plue on 2011-03-25
maybe because wine pulled in ms truetype fonts? try removing those

---

### Post by Arndt on 2011-03-31
> **~Plue said:**
> maybe because wine pulled in ms truetype fonts? try removing those

Thanks for the suggestion. I find that something called ttf-mscorefonts-installer was installed. I removed it, and nothing much happened (my gnome-terminals did redraw themselves, but with no visible change there or in Firefox). I suppose removing the installer didn't remove the fonts themselves. Can you suggest how to do that?

---

### Post by Arndt on 2011-03-31
> **Arndt said:**
> Thanks for the suggestion. I find that something called ttf-mscorefonts-installer was installed. I removed it, and nothing much happened (my gnome-terminals did redraw themselves, but with no visible change there or in Firefox). I suppose removing the installer didn't remove the fonts themselves. Can you suggest how to do that?

I'm sorry, it does seem that the fonts were removed. What I had to do was refresh the pages in question.

Thanks for the help!

---

