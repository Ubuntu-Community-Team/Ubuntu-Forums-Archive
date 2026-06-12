---
title: "Need help making an alias permanent"
date: 2009-07-23
forum: General Help
---

### Post by Volume on 2009-07-23
I made an alias for my MATLAB executable, so that I can type "matlab" and it will run.  The alias works fine, but I can't figure out how to keep the alias permanent (i.e. after restart).  I was googling around, and saw some things about a .bashrc file, but I don't really see where in that file I would put something like an alias.

Steve

---

### Post by Q345 on 2009-07-23
In your home directory there's a .bashrc file.  Uncomment the following lines (remove the leading '#'):

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

Then create a .bash_aliases file in your home directory (touch ~/.bash_aliases).  Open the file with gedit (gedit ~/.bash_aliases) and add your alias xxx='yyy' line.  Then run 'source .bashrc'

---

### Post by Volume on 2009-07-24
Thanks Q345!  Everything went ok but one thing.  When I get to the step to run the source.bashrc, I get the following message:

```
mokrunka@Engineer:~$ source.bashrc
bash: source.bashrc: command not found
```

What am I doing wrong?

---

### Post by aesis05401 on 2009-07-24
There should be a space between 'source' & '.bashrc' ;)

---

### Post by Volume on 2009-07-24
Nice, Thanks for all the help, guys!

---

### Post by Volume on 2009-07-24
What did that command do?  Fixing things is great, but I also like to know what I'm doing...:popcorn:

---

### Post by aesis05401 on 2009-07-24
> **Volume said:**
> What did that command do?  Fixing things is great, but I also like to know what I'm doing...:popcorn:

Glad to see you ask.  

The first command sequence translates to 'if there is a file in your home directory named .bash_aliases then source .bash_aliases.

The 'source' command is interesting because there is no 'man' entry for 'source.'  

The secret to this command is actually in the 'man bash' help file.  There you will find that 'source' followed by a filename and optional arguments tells bash to execute the specified file within the current shell... 

So you are simply telling your shell to implement the instructions located in .bashrc which checks for the file ~/.bash_aliases, and sources it if it exists.

---

### Post by rbc on 2009-07-24
Sorry for jumping in uninvited but I found this fascinating and I was reading this:
[http://ss64.com/bash/source.html](http://ss64.com/bash/source.html), and oscillating between “Of course, that makes perfect sense” to “Huh? That makes no sense”
So, if I had aliases in the bash_aliases file to start 1) start Firefox, 2) run an executable that starts a script, 3) unmounts an external hard drive (all just examples), running *source .bashrc *would run all the aliases? At the same time? Consecutively? Or would it just hose things up?

---

### Post by aesis05401 on 2009-07-24
> **rbc said:**
> Sorry for jumping in uninvited but I found this fascinating and I was reading this:
[http://ss64.com/bash/source.html](http://ss64.com/bash/source.html), and oscillating between “Of course, that makes perfect sense” to “Huh? That makes no sense”
So, if I had aliases in the bash_aliases file to start 1) start Firefox, 2) run an executable that starts a script, 3) unmounts an external hard drive (all just examples), running *source .bashrc *would run all the aliases? At the same time? Consecutively? Or would it just hose things up?

Running 'source ~/.bashrc' or '. ~/.bashrc' causes the assignments in the ~/.bash_aliases file to be loaded in the current shell context, not necessarily run.  

So if you set ~/.bashrc to check for and source ~/.bash_aliases as in the above example, then make a ~/.bash_aliases entry to launch firefox with special options, then source ~/.bashrc you will end up not with a running firefox session, but with an alias that is accessible from within your terminal session that will allow you to launch Firefox using the commands you specified in ~/.bash_aliases.

If you are configured properly the user would then enter the alias into the terminal to perform the task of launching firefox with your options set.

---

### Post by redmk2 on 2009-07-24
> **aesis05401 said:**
> Running 'source ~/.bashrc' or '. ~/.bashrc' causes the assignments in the ~/.bash_aliases file to be loaded in the current shell context, not necessarily run. ...

Aliases in this sense are memory variables (See the parameters section of *man bash*).  When you source the aliases in either the ,bashrc or the .bash_aliases you are loading them into RAM for execution later.

---

### Post by Volume on 2009-07-26
> **aesis05401 said:**
> Glad to see you ask.  

The first command sequence translates to 'if there is a file in your home directory named .bash_aliases then source .bash_aliases.

The 'source' command is interesting because there is no 'man' entry for 'source.'  

The secret to this command is actually in the 'man bash' help file.  There you will find that 'source' followed by a filename and optional arguments tells bash to execute the specified file within the current shell... 

So you are simply telling your shell to implement the instructions located in .bashrc which checks for the file ~/.bash_aliases, and sources it if it exists.

Ahh.  That makes perfect sense!  Thank you.  You were right, I had tried the man page first, but to no avail, that's why I asked the question!  Really appreciate your response.

---

