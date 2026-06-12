---
title: "SSH Font color (via system?)"
date: 2010-06-01
forum: General Help
---

### Post by champi0n on 2010-06-01
I want to change the default SYSTEM font color so that when I ssh into various linux boxes, the font color in my terminal is that of which I set system side.

*(I do know that I can manage profiles via ssh client, change colors there etc... but this doesn't work if I'm ssh'd from a different "client" machine, as the profiles are only saved on the client desktop.*

So I'm wondering if I can (on my server itself), declare the font color to be red, blue, green, or whatever.

I'm usually ssh'd into 5-10 servers at a time and color coding easily helps identify which server is what. But there are often times which I have to use a different machine, and I don't want to keep going thru the hassle of creating client side profiles if there is a way I can do it server side.

Thanks.

---

### Post by sdennie on 2010-06-01
I have this in ~/.bashrc for all the boxes I use:

```

if [ -z $SSH_TTY ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:%\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\[\033[01;31m\]%\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
fi

```

If I'm logged in locally to the box, it displays the prompt as all green.  If I'm logged in via ssh, it displays it as a green username and red hostname.  If you removed the very last color change ("\[\033[00m\]"), the prompt and text would also be red.  Hopefully that's a push in the right direction.

---

### Post by geirha on 2010-06-01
I use this in my .bashrc
```

user_color=$(tput setaf 2)
pwd_color=$(tput setaf 4)
bold=$(tput bold)
reset=$(tput sgr0)

host=$(( (${#HOSTNAME}+0x$(hostid)) % 15+1))
host_color=$(tput setaf $((host%8)))
(( host > 7 )) && host_color=$bold$host_color

prompt=(
    "\[$user_color\]"       '\u'
    "\[$bold\]"             '@'
    "\[$reset\]"
    "\[$host_color\]"       '\h'
    "\[$reset\]"            :
    "\[$bold$pwd_color\]"   '\w'
    "\[$reset\]"
    '\[$((($?)) && tput setaf 1)\]'
                            '\$'
    "\[$reset\]"            ' '
)
printf -v PS1 "%s" "${prompt[@]}"
unset user_color pwd_color bold reset host host_color prompt

```

It sets the color of the hostname to one of 15 colors based on hostid(1) (though some of the boxes I most commonly ssh into got the same color so I added the length of HOSTNAME to the equation). It also sets the color of \$ to red if the previous command failed ($? > 0), regular color otherwise.

---

### Post by champi0n on 2010-06-01
Awesome, does the job i need.

Where might i find out a list of colors/color codes?

---

### Post by geirha on 2010-06-01
A typical terminal emulator today supports at least these 16 colors
```

for i in {0..7}; do 
  tput setaf "$i"; printf "%d %-8s" "$i" dark
  tput bold; printf "%d %-8s\n" "$i" bright
  tput sgr0 
done

```
My prompt chooses between all of those except "0 dark", since that one doesn't show very well on the black background I use.

See
[http://wiki.bash-hackers.org/scripting/terminalcodes](http://wiki.bash-hackers.org/scripting/terminalcodes)
«man tput» and «man 5 terminfo»

---

