---
title: "bashrc isn't reading correctly in 11.10"
date: 2011-10-25
forum: General Help
---

### Post by rifak on 2011-10-25
Hey everyone,
So I finally did a fresh install of 11.10 (coming from 10.04) and am only having one problem. I have an edited bashrc file from my 10.04 installation. I simply copied the aliases and PS1 assignment to the new bashrc of 11.10, however, it is not recognizing my PS1 assignment (color assignment of terminal prompt). The aliases are working fine, so I know its registering the bashrc file..it just isn't seeming to pick up on my prompt coloring variables. Here is the relevant portion:

```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[$(tput setaf 5)\]\u @\h\[\033[00m\]:\[$(tput setaf 1)\]\W\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt
```

---

