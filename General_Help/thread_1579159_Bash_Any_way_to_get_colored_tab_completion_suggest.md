---
title: "Bash: Any way to get colored tab completion suggestions?"
date: 2010-09-21
forum: General Help
---

### Post by sayeo87 on 2010-09-21
I have general color working, but say I input **cd ~/D<tab>** I want the suggestions **Desktop/ Documents/** and **Downloads/** to show up as light blue, executable files to show up as light green and so on. Is there any way to achieve this in bash? Here are the relevant sections of my .bashrc:


```
# set a fancy prompt (non-color, unless we know we "want" color)
  case "$TERM" in
      xterm-color) color_prompt=yes;;
  esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

  if [ -n "$force_color_prompt" ]; then
      if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
      else
    color_prompt=
      fi
  fi

  if [ "$color_prompt" = yes ]; then
      PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
  else
      PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
  fi
  unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
# (SUAN changed to curdir (without path))
  case "$TERM" in
  xterm*|rxvt*)
      #PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
      #;;
      PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\W/\a\]$PS1"
      ;;
  *)
      ;;
  esac

# enable color support of ls and also add handy aliases
  if [ -x /usr/bin/dircolors ]; then
      test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
      alias ls='ls --color=auto'
      #alias dir='dir --color=auto'
      #alias vdir='vdir --color=auto'

      alias grep='grep --color=auto'
      alias fgrep='fgrep --color=auto'
      alias egrep='egrep --color=auto'
  fi
```

Thanks!

---

### Post by sayeo87 on 2010-09-27
No bites? Give a shout if you think this would be useful, maybe its time to suggest a new feature...

---

### Post by StuartN on 2010-09-27
> **sayeo87 said:**
> No bites? Give a shout if you think this would be useful, maybe its time to suggest a new feature...

Yes, certainly. **man bash** does not show any color option (as opposed to ls, grep, etc), and I guess that is where coloured tab-completion would reside.

---

