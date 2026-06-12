---
title: "Hotkeys in Terminal?"
date: 2011-08-07
forum: General Help
---

### Post by ghost25 on 2011-08-07
Hey guys, got another question for ya... not a big deal if this isn't possible, just something I got to wondering about tonight.

I'm aware of a lot of Terminal commands, and am pretty comfortable with doing stuff that requires CLI input. Probably my biggest "annoyance" though is when I'm navigating around multi-deep directories, i.e. dir/dir1/dir2/dir3/dir4/dir5/dir6 ad nauseum, and I then have to hit "cd ../" 3 or 4 times just to back up so I can, in /dir2/, go instead into /dirB/dirC etc. I'm just wondering, is there any way that I could assign a keyboard shortcut or macro, like maybe have it so that if I hit "Alt" and some number key, it would automatically enter "cd ../" until I am back at the level where I want to be? (I don't even know if that makes sense haha!)

Basically, I guess I want to know if there is any option that allows me to take common commands such as "ls -a", "cd ../", or something similar, and convert that action into a "shortcut" key, kinda like you might in a word document or something? Thanks for any help you can provide in this matter.

---

### Post by cbennett926 on 2011-08-07
You can go into key board shortcuts and configure your own short cut!

---

### Post by whatthefunk on 2011-08-07
Or you can make your own commands and save them in your .bashrc file under aliases.

---

### Post by ghost25 on 2011-08-07
> **cbennett926 said:**
> You can go into key board shortcuts and configure your own short cut!

I tried looking under that option, but (unless, and this is very possible, I missed something...) I didn't see any option to do this. Do I need to deactivate or deselect some option before I can create my own?

> **whatthefunk said:**
> Or you can make your own commands and save them in your .bashrc file under aliases.

Can you give me either a brief walk-through on this, or point me in the right direction? I've never heard of this level of Linux... and this actually embarrasses me, considering I've been using Linux itself for about 10 years and Ubuntu for the past 4 :redface:

Thanks though, for the quick replies! Looking forward to optimizing my Terminal Fu lol!

---

### Post by whatthefunk on 2011-08-07
> **ghost25 said:**
> I tried looking under that option, but (unless, and this is very possible, I missed something...) I didn't see any option to do this. Do I need to deactivate or deselect some option before I can create my own?



Can you give me either a brief walk-through on this, or point me in the right direction? I've never heard of this level of Linux... and this actually embarrasses me, considering I've been using Linux itself for about 10 years and Ubuntu for the past 4 :redface:

Thanks though, for the quick replies! Looking forward to optimizing my Terminal Fu lol!

Your .bashrc file is located at ~.bashrc.  You can see it in the terminal by doing
```
ls -a
```

At the end of the .bashrc file are aliases.  These are a way to make custom commands or to turn on switches for normal commands.  You can also write simple scripts and store them in your .bashrc.

I would recommend putting these three in yours.

```
alias cp='cp -v -i'
alias rm='rm -i'
alias mv='mv -i'
```

They are safety features and turn on warning prompts for the rm, cp and mv commands.

This is also a good one

```
alias reload='source ~/.bashrc'
```

It reloads your .bashrc file.  Every time you change it you have to reload for the new lines of text to take affect.  

You are looking for these ones

```
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'
```

This makes it so that if you want to go up one directory, you press '..'  For two levels up, ..., three levels up, .... etc.

Have a look here for more examples:
[http://ubuntuforums.org/showthread.php?t=679762&highlight=.bashrc](http://ubuntuforums.org/showthread.php?t=679762&highlight=.bashrc)

Dont forget that when you edit it the first time, youll have to close down your terminal and then open it back up for it to reload.

---

### Post by ghost25 on 2011-08-07
Thanks, funk, that seems like it'll help me out a lot. I'll have to give it a shot when I get a moment. I'll be back to ask for more help if I can't figure this out.

---

### Post by Habitual on 2011-08-07
CLI Companion

[https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

---

