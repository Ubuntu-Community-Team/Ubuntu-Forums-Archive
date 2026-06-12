---
title: "Path seems to be messed up?"
date: 2011-07-28
forum: General Help
---

### Post by jerome1232 on 2011-07-28
For some reason my $PATH is messed up, The only recent change I've made is upgrading from Gnome2 to Gnome3.

```
 cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

```
cat ~/.profile | tail -n 4
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

Yet when I check my path it doesn't include all those locations it should.
```
echo $PATH
/home/jeremy/bin:/usr/local/bin:/usr/bin:/bin

```
[/code]

---

### Post by AlphaLexman on 2011-07-28
Check for two more files...
[LIST]
[*]~/.bash_profile
[*]~/.bash_login
[/LIST]
Bash will ignore ~/.profile if either of the above files exist.

Your $PATH is probably set in one of those two files, or most likely in ~/.bashrc

---

### Post by jerome1232 on 2011-07-28
Neither of those files exist on my system and if I grab a sudo shell via sudo -i, my root users path is correct, however the only difference is it's .profile file doesn't check for ~/bin.


edit: When I search my ~/.bashrc there is no reference to PATH in it.

---

### Post by jerome1232 on 2011-07-29
bump

---

### Post by AlphaLexman on 2011-07-29
Why not just reset the $PATH environment variable to what you want / need in your ~/.bashrc ??

Or are you trying to find the stubborn file that changes the $PATH last-most ??

---

### Post by jerome1232 on 2011-07-29
I just want my path to get set correctly, takeing from what you said I set it in my ~/.bashrc like this and it works:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

It works, so I assume some file is changing my path after /etc/environment sets it, I just have no idea how to figure out what that file is... The current solution works good enough unless someone has an idea on how to find that file and fix it correctly.

---

