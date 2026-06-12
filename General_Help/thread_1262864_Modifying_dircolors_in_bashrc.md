---
title: "Modifying dircolors in bashrc"
date: 2009-09-10
forum: General Help
---

### Post by ecmatter on 2009-09-10
I'm having trouble altering the colors used by 'ls'.  I think the error resides in the ~/.dircolors file that I created, but before I tackle that, I want to make sure that I fully understand the modifications to bashrc which call the file. 

Here's the portion of my bashrc dealing with dircolors:

```

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

```

And here's the altered bashrc entry pulled from [HERE](http://ubuntuforums.org/showthread.php?t=41538).

```

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    [ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors"
    [ -e "$DIR_COLORS" ] || DIR_COLORS=""
    eval "`dircolors -b $DIR_COLORS`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

```

**Questions**
1. Where would I look to find information on the '-x' option in the second line of the first entry, and the '-e' option in the third and fourth lines of the second entry?  I'm assuming that the '-x' option is asking if the file exists, and the '-e' option evaluates what follows, but I have no idea where to look to confirm that.  Google has been no help.

2. What does the value "dumb" refer to?  Login shells?

---

### Post by Penguin Guy on 2009-09-10
In an if statement -e means exist and -x means executable.

if [ -e file ]     # If file/folder exists
if [ -x file ]     # If file is executable

---

### Post by ecmatter on 2009-09-10
Thank you.  I was looking for '-x' and '-e' as parts of conditional statements and getting nowhere.  

Here's a table with all of the options:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

---

