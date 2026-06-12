---
title: "Colours in Zsh"
date: 2010-07-02
forum: General Help
---

### Post by chaosx9 on 2010-07-02
Hi everyone

Well I chose to switch to Zsh, and after being a complete amateur at configuring it, i've hit a snag. Basically, I want it to change colour or something when it's a root shell (like, running sudo zsh, to give an indication) but i can't get it to do so.

Anybody good with it who could give me some help?

---

### Post by stlsaint on 2010-07-02
Do you want all type of different colors or what? Exactly what are you looking to make different colors? attach a text doc of what your current zshrc is.

---

### Post by bodhi.zazen on 2010-07-02
Try this :

[http://bodhizazen.net/adblock/zshrc](http://bodhizazen.net/adblock/zshrc)

save it as ~/.zshrc

that file has a few applications you may not use including most (colored man pages) and[FONT=monospace] [/FONT]display-dhammapada (see the comments at the top of the file).

So, if you wish, 

```
sudo apt-get install most [FONT=monospace][/FONT]display-dhammapada
```

Or edit the file and make any changes you wish.

enjoy =)

---

### Post by stlsaint on 2010-07-02
@bodhi...
LOL...i was going to provide them with that for editing.

---

### Post by chaosx9 on 2010-07-03
Here's my current config file (made it myself, quite minimalist)

```
#!/bin/zsh

#completion
autoload -U compinit
compinit

# other options
#corrections
setopt correctall
#auto cd added when looking for dirs
setopt autocd

#histories
export HISTSIZE=2000
export HISTFILE="$HOME/.zsh/history"
export SAVEHIST=$HISTSIZE
setopt hist_ignore_all_dups

#prompt
PROMPT="%m:%~%% "
```

---

