---
title: "Change tty font colour"
date: 2010-10-31
forum: General Help
---

### Post by Righard on 2010-10-31
Can anybody tell me if it is possible to change the colourscheme for the tty terminals (those that do not use X).

I want to change it the way you change it for terminal-emulators using X, i.e. If you change blue to green, everything that was blue becomes green (even when using ncurses)

And if it is possible, can you point me in the right direction.

Thx,
Righard

---

### Post by Righard on 2010-10-31
Figured it out myself,

You can use the escape sequence ESC ] P nrrggbb... for example, the set the background color to green type:

echo -e '\033]P000FF00'

thx anyway!

---

### Post by phantom_ on 2011-01-14
thanks for the info, this enabled me for further customization of *tty* terminals. here is my contribution;

just the bare *echo -e “\033]P000FF00”* escape sequence command is not adequate for system wide customization.

info about escape sequence can be found by *man console_codes*.

there are different code sets. the one that i preferred is **ECMA 48 CSI** sequence denoted by character "**[**". thus, my sequences start with *\033[*.

so you can type ```
echo -e “\033[1m”
``` to set the foreground color to bold (or bright white, if you were at the default tty color settings).

however, color scheme resumes to default after using commands like *ls* which uses different color settings for the console output. in order to make the customization permanent, export the command prompt environment variable with; ```
export PS1="\033[1m"$PS1
``` in your *.bashrc* profile file.

the above color customization is also valid for terminal screens running at X.

---

