---
title: "256 color support for vim background in tmux"
date: 2012-03-10
forum: General Help
---

### Post by winchendonsprings on 2012-03-10
while using vim within tmux I can see that 256 color support is enabled. with $tput colors

However changing the colorscheme in vim while in tmux will change the colorscheme on a per line basis but not the entire background. see screenshot [IMG]http://i.stack.imgur.com/Owf4x.png[/IMG]

Here is a snippet of the my .vimrc file for example. My original colorscheme is solarized dark and then after running :colorscheme molokai you see what happens.

info

 - gnome-terminal
 - bash

in my ~/.tmux.conf

```
         set -g default-terminal "screen-256color"
```in my ~/.vimrc

```
         set t_Co=256
```in my ~/.bashrc
```

    # ryan
    export TERM="xterm-256color"
    # ryan
    alias tmux="tmux -2"

```in my ~/.profile
```

    # ryan 256 color support
    if [ -e /usr/share/terminfo/x/xterm-256color ]; then
        export TERM='xterm-256color'
      else
        export TERM='xterm-color'
      fi
```Any ideas how I can get a full colorscheme change in vim? Are all my snippets from the files looking good?

---

### Post by winchendonsprings on 2012-03-11
See the answer here - [http://superuser.com/questions/399296/256-color-support-for-vim-background-in-tmux/399326#399326](http://superuser.com/questions/399296/256-color-support-for-vim-background-in-tmux/399326#399326)

---

