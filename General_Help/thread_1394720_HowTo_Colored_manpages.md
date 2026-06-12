---
title: "HowTo: Colored manpages"
date: 2010-01-30
forum: General Help
---

### Post by Barriehie on 2010-01-30
I find the generic white of a manpage display less useful than a colored one.  I've installed 'most' but then ran across a much less resource using option.  The termcap variables for defining your colors can be put in your ~/.bashrc file.  I prefer this to having another ~150K package installed on my machine.

Here's my addition to my ~/.bashrc
```

#
#    Colored manpages
#
export LESS_TERMCAP_mb=$'\E[01;31m'       # begin blinking
export LESS_TERMCAP_md=$'\E[01;32;5;74m'  # begin bold
export LESS_TERMCAP_me=$'\E[0m'           # end mode
export LESS_TERMCAP_se=$'\E[0m'           # end standout-mode
export LESS_TERMCAP_so=$'\E[38;5;246m'    # begin standout-mode - info box
export LESS_TERMCAP_ue=$'\E[0m'           # end underline
export LESS_TERMCAP_us=$'\E[04;36;5;146m' # begin underline

```

Attached is a small gif image of what escape codes yield what colors and another image showing what the above codes display.

Barrie

---

