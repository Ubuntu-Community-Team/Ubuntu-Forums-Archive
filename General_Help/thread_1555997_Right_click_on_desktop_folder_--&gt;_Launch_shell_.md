---
title: "Right click on desktop folder --&gt; Launch shell from this location"
date: 2010-08-18
forum: General Help
---

### Post by TraderLars on 2010-08-18
Hey, thanks in advance for the help. First let me just say I've been using Ubuntu 10 for 1 day and its been a great day!!!!!!!!!!!!!!

I had a quick question, I would like to be a able to right click on a GUI folder and have the option of selecting "Launch shell from this location" or something like that. This would simply open a bash or default shell with the folder as the preconfigured path. This would save me some time. 

Kindly advise on how to accomplish this, please be nice, I've been using Linux/Ubuntu for only 1 day.

Thanks!!!

---

### Post by dagdeniz on 2010-08-18
With (at least standard) Nautilus, you cannot do that (may be with a script you can?). 
However, Pcmanfm does have such an option. Install Pcmanfm without extra dependencies:

```
sudo apt-get install --no-install-recommends pcmanfm
```

Using pcmanfm (will be seen as simply "file manager" under your menus), open "tools" and you'll see the option "open current folder in terminal" option.

---

### Post by dagdeniz on 2010-08-18
And for Nautilus scripts, look at these two:

[http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/](http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/)
[http://g-scripts.sourceforge.net/cat-executing.php](http://g-scripts.sourceforge.net/cat-executing.php)

They look nice, I'll try them too ;)

---

### Post by ranch hand on 2010-08-18
```

sudo apt-get nautilus-open-terminal

```
Will give you the option to open the terminal there in your right click menu.  Has for years.

---

