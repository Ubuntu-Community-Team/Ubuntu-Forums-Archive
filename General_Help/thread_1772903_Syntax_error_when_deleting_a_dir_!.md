---
title: "Syntax error when deleting a dir ?!?"
date: 2011-06-01
forum: General Help
---

### Post by WoGGo on 2011-06-01
I am trying to delete a dir (with the CLI), that contains many sub dirs and files:

Hello - DE Important Files Stuff (0000-0001)

I am using the command: [PHP]sudo rm -rf Hello\ -\ DE\ Important\ Files\ Stuff\ (0000-0001)/[/PHP]But I keep getting this error: [PHP]-sh: Syntax error: "(" unexpected[/PHP]Obviously I am a noob to Linux.. what am I doing wrong?

The \ between the spaces in the file name isn't showing in the PHP code?!?

---

### Post by hwttdz on 2011-06-01
It's complaining because ( is a special character in bash, so it needs to be escaped.  The easy route is to just double-tab to autocomplete assuming there is only one directory named "Hello...", or even easier would be to rm Hello* again assuming only one directory.  The alternative is to escape the argument (or quote it).  i.e.

sudo rm -rf 'Hello - DE Important Files Stuff (0000-0001)'
sudo rm -rf Hello\ -\ DE\ Important\ Files\ Stuff\ \(0000-0001\)

Where in the second I have escaped all the spaces to let bash know that it's a space and not separating arguments (otherwise it will run rm on "Hello", "-", "DE", "Important"... which is not what you want.  I have also escaped the ( and ) because otherwise the shell will interpret them as special characters.

---

### Post by WoGGo on 2011-06-01
sudo rm -rf 'Hello - DE Important Files Stuff (0000-0001)'

This worked perfectly.... and saves me typing out the whole thing and adding \'s.

Much appreciated.

---

### Post by linkageless on 2011-06-01
Another way - tab complete in bash and some other shells helps lots for those sort of annoying chars that need escaping. Just type the first few chars and hit tab a couple of times, if that is sufficient to be unique it will fill in the rest for you.

---

### Post by WoGGo on 2011-06-01
Sounds good, sounds very good.

This can be done via SSH?

---

### Post by WoGGo on 2011-06-01
> **linkageless said:**
> Just type the first few chars and hit tab a couple of times, if that is sufficient to be unique it will fill in the rest for you.

Hmm, just tried this via SSH and it did not work.

The dir did not have and special characters or spaces either.

---

### Post by hwttdz on 2011-06-02
I always get confused as to what gets sourced on a ssh login.  Anyways, you need to make sure in your .bash(rc|_profile|_login), one of those that is running on the opening of the tty that you are sourcing /etc/bash_completion. Usually shows up in one of those as something along the lines of:

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

Also, I misspoke before, a doubletab will show you all your options, i.e. if I'm in my home directory and type:
"cd Docu[tab]" it will make "cd Documents/" on the command line, but if I "cd D[tab][tab]" it will show me that "Desktop/ Documents/" are both valid completions to the command.

---

### Post by linkageless on 2011-06-03
Sorry if my suggestion was a little brief, as hwttdz suggests a .bashrc or similar would normally set up your tab completion for you, and this would normally be run whether you are through ssh, console, or otherwise. I'm assuming your shell is actually bash (to find out: echo $SHELL) and that you've not altered the default shell profile.

In case you're still wondering how you can use it, here's a better explanation than I can provide:

[http://www.ice2o.com/bash.php](http://www.ice2o.com/bash.php)

Once you get used to it, you'll wonder how you ever coped without!

---

