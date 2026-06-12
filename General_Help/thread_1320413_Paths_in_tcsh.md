---
title: "Paths in tcsh"
date: 2009-11-09
forum: General Help
---

### Post by Dfr0st on 2009-11-09
Hi,
I'm using tcsh shell and I'm having difficulty adding a program to my PATH. In my csh.cshrc file (in /etc/) I have added the names of the folders that I want to add to the PATH and when I use echo $PATH they are added to the list, however, when I try to run the scripts in the file I get the "command not found" error. I have tried closing the terminal and restarting the computer but I can't seem to get anywhere.
Can someone please help?
Dan

---

### Post by Giblet5 on 2009-11-09
If the directory containing your scripts is in $PATH, and you get the 'not found' error, then the scripts are not set as executable, or the PATH variable is boogered.

Bring up a terminal window.

Run ```
echo $PATH
```

Verify the spelling of the script directory's path, and the absence of garbage that won't make sense outside a specific environment: eg, entries like "~/bin" - use the full path). Make sure that the directories are delimited with a single ':' and not a semicolon ';'.

Pick a script (eg, "/home/dx/bin/myscript")

Run ```
ls -l /home/dx/bin/myscript
```

Is it executable?

Run ```
chmod +x /home/dx/bin/myscript
```

Now, try to run it ```
myscript
```

---

### Post by Dfr0st on 2009-11-09
Hi,
Thanks for your reply but I'm still having problems. The scripts are executable if I type their full address but they won't run when I just type their name.
I ran "echo $PATH" and this gave me:

"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/dan:/usr/lib/gmt:/usr/lib/gmt/bin:/home/dan/Documents:"

/home/dan, /usr/lib/gmt and everything after are the files I'm trying to add.
(I tried with and without the final colon with no change)


My csh.cshrc file contains:

"# /etc/csh.cshrc: system-wide .cshrc file for csh(1) and tcsh(1)

if ($?tcsh && $?prompt) then

    bindkey "\e[1~" beginning-of-line # Home
    bindkey "\e[7~" beginning-of-line # Home rxvt
    bindkey "\e[2~" overwrite-mode    # Ins
    bindkey "\e[3~" delete-char       # Delete
    bindkey "\e[4~" end-of-line       # End
    bindkey "\e[8~" end-of-line       # End rxvt

    set autoexpand
    set autolist
    set prompt = "%U%m%u:%B%~%b%# "

set PATH = (${PATH}:/home/dan:/usr/lib/gmt:/usr/lib/gmt/bin:/home/dan/Documents:)

endif"

---

### Post by Dfr0st on 2009-11-10
Bump, sorry, still need help.

---

