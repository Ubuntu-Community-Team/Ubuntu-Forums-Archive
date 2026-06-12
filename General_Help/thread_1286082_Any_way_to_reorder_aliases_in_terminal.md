---
title: "Any way to reorder aliases in terminal?"
date: 2009-10-08
forum: General Help
---

### Post by danger pigeon on 2009-10-08
I'm still a relatively new user but I've started using the terminal a lot and actually prefer it to GUI frontend programs most of the time. Because of this I've got quite a few aliases that i use for common commands. However I don't use the terminal often enough to have the 20 or so aliases memorized.

In my .bash_aliases file I have them organized well so its easy to find what i need and where to add a new command if necessary, but if i just type "alias" into the terminal it always shows them alphabetically with no spaces, making it difficult ot quickly find the one I'm looking for. Is there any way to reorder the display output or even change its format to make it easier to find what i'm looking for??

---

### Post by unutbu on 2009-10-08
```
grep alias ~/.bashrc
```
You can alias that command too if you wish :)

---

### Post by danger pigeon on 2009-10-08
That gives me this output but i'm not sure what to do with it exactly.


shawn@shawn-laptop:~$ grep alias ~/.bashrc
# ~/.bash_aliases, instead of adding them here directly.
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
# enable color support of ls and also add handy aliases
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'
    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'
shawn@shawn-laptop:~$

I tried uncommenting some of the lnes but nothing really happened

---

### Post by unutbu on 2009-10-08
Oh, sorry -- I missed that you put your aliases in ~/.bash_aliases. In that case, try
```

grep alias ~/.bash_aliases
```

---

### Post by danger pigeon on 2009-10-08
No that's still the same basic list as when enter in "alias". Do i maybe need to add a line in my .bash_aliases saying what should be displayed?

---

### Post by unutbu on 2009-10-08
Could you post your ~/.bash_aliases and how you would like them displayed?

---

### Post by danger pigeon on 2009-10-08
Here's my .bash_aliases. I don't know if you needed this or the file itself. Let me know.

# System
alias s='sudo'
alias task='gnome-system-monitor &'
alias syn='sudo synaptic &'    

alias sag='sudo apt-get'
alias update='sudo apt-get update'
alias search='sudo apt-cache search'
alias upgrade='sudo apt-get upgrade'
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'

# Xbox
alias live='./xboxliveup'
alias lived='./xboxlivedown'
alias 360='cd /media/mybook/x360'

# Misc
alias archive='tar cvpzf'
alias edit='sudo gedit'
alias delete='sudo rm -r'

# Programs
alias steam='env WINEPREFIX="/home/shawn/.wine" wine "C:\Program Files\Steam\Steam.exe" &'
alias word='ooffice -writer &'
alias ppt='ooffice -impress &'
alias xl='ooffice -calc &'
alias draw='ooffice -draw &'
alias fire='firefox -profilemanager &'
alias thun='thunderbird &'
alias pid='pidgin &'

---

### Post by Slim Odds on 2009-10-08
> **unutbu said:**
> Oh, sorry -- I missed that you put your aliases in ~/.bash_aliases. In that case, try
```

grep alias ~/.bash_aliases
```

How about making it a little easier and more complete?
```
alias | grep {whatever you're looking for}
```

Then you don't need to know where the file is located.

---

### Post by unutbu on 2009-10-08
Would you like the output to look exactly like the contents of ~/.bash_aliases? In that case, try
```

cat ~/.bash_aliases
```

PS. There is a subtle problem that is caused by using "sudo" with some graphical apps. The general rule is to use "gksu" with graphical apps and "sudo" with command-line apps. So you may want to change
```

alias syn='sudo synaptic &' 
```

to 
```

alias syn='gksu synaptic &' 
```

and 
```

alias edit='sudo gedit'
```

to

```
alias edit='gksu gedit'
```

Edit: SlimOdds, that's a good idea. I think danger pigeon wants the comments and blank lines too however.

---

### Post by m_duck on 2009-10-08
Add a new alias of:```
alias alias='cat ~/.bash_aliases'
```That will print the contents of your ~/.bash_aliases file to the terminal window, as formatted in said file when you type *alias* into the terminal. Using the grep method you lose the comments and blank lines as they do not contain the word 'alias'.

EDIT: Oh my, faaaar to slow.

---

### Post by kerry_s on 2009-10-08
:lolflag:
the point of an alias is to be something you remember easily.
if you can't remember them why bother.

mine:
```
alias !='sudo'
alias ?='dpkg -l | grep'
alias c='sudo apt-get clean;sudo apt-get autoremove'
alias ch='clear;rm -f ~/.bash_history;history -c'
alias grep='grep --color=auto'
alias i='sudo apt-get install --no-install-recommends'
alias ls='ls -a --color=auto'
alias r='sudo apt-get purge'
alias s='apt-cache search'
alias u='sudo apt-get update;sudo apt-get upgrade'


```

---

### Post by danger pigeon on 2009-10-08
I remember the ones i use a lot, like the apt-gets and the programs, but theres some commands i only use once every few weeks or months, and its a real hassle to have to go online and look up the tutorial again, and hope it's still up.

This is a pretty good idea:
> Add a new alias of: 	Code:
 	alias alias='cat ~/.bash_aliases' 
That will print the contents of your ~/.bash_aliases file to the terminal window, as formatted in said file when you type *alias* into the terminal. Using the grep method you lose the comments and blank lines as they do not contain the word 'alias'.

But if you're gonna do that you can't make the alias for it alias. It cause some kind of loop i guess and every time you open a terminal it just runs that command a few dozen times till the screen is full, then none of your aliases work. Just make it something different and it works fine. I used :
```
alias alt='cat ~/.bash_aliases'
```

Thanks for the help, this is just what i was looking for

---

### Post by Slim Odds on 2009-10-08
> **danger pigeon said:**
> But if you're gonna do that you can't make the alias for it alias. It cause some kind of loop i guess and every time you open a terminal it just runs that command a few dozen times till the screen is full, then none of your aliases work.

There is a bash command called command that can be used to call the default alias command.

Like```
command alias
```This will run the original shell command called alias, not the aliased one.

---

