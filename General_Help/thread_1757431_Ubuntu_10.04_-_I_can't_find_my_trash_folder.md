---
title: "Ubuntu 10.04 - I can't find my trash folder"
date: 2011-05-13
forum: General Help
---

### Post by ClientAlive on 2011-05-13
This is so stupid. I've been there before and it was no problem. I hope something hasn't happened.

I accidentally deleted an important folder from my desktop and now need to get into the trash folder to restore it. I thought that it is found by opening my home folder (nautilus?) and that is shows up in the list in the pane on the left. Now I only see two items listed there - "Home Folder" and "File System," and the trash folder is not in either of them. Not even if I select to view hidden files.

I know how to get to it from the command line and view what is inside:

```
cd ~/.local/share/Trash/info; ls
```

But I would prefer to navigate to it in the gui.

Can anyone help? This folder contains work that I do for the company I work for.

Thanks

:confused:

---

### Post by tredegar on 2011-05-13
I don't use "Trash". It's either deleted or not. I decide, and then don't change my mind later.

**cd ~/.local/share/Trash/info; ls** Looks like some database - Yuk!

If you want to see what is in your trash then (for gnome2, you do not say what you are running) R-click your panel, Add to panel, "Rubbish bin", Close.

Open the new icon on your panel and you may be able to retrieve the file(s).

Meanwhile, try not to delete files / directories you do not want deleted. Did you not receive a warning? Did you not read or consider it?

Linux is an operating system. It (rightly) does as it is told, so you need to learn to be careful what you ask it to do, because it'll probably just go ahead and do what you ask of it, to the best of its abilities.

I prefer that behaviour, but maybe the above will help you recover from your mistake.

---

### Post by ClientAlive on 2011-05-13
> **tredegar said:**
> I don't use "Trash". It's either deleted or not. I decide, and then don't change my mind later.

**cd ~/.local/share/Trash/info; ls** Looks like some database - Yuk!

If you want to see what is in your trash then (for gnome2, you do not say what you are running) R-click your panel, Add to panel, "Rubbish bin", Close.

Open the new icon on your panel and you may be able to retrieve the file(s).

Meanwhile, try not to delete files / directories you do not want deleted. Did you not receive a warning? Did you not read or consider it?

Linux is an operating system. It (rightly) does as it is told, so you need to learn to be careful what you ask it to do, because it'll probably just go ahead and do what you ask of it, to the best of its abilities.

I prefer that behaviour, but maybe the above will help you recover from your mistake.


Thank you for your help sir. The problem is solved.

Have a wonderful evening.

:D

---

