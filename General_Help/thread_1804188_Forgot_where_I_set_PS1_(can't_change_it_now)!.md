---
title: "Forgot where I set PS1 (can't change it now)!"
date: 2011-07-14
forum: General Help
---

### Post by MkJackson on 2011-07-14
Hey folks, 
So a little while back I went with a minimalist approach and made my PS1="$" but after some time I've decided to modify this to something a bit more robust. 

I've added the following to the end of my .profile file: export PS1="[\D{%a %y%b%d}@\t \W] $"

Unfortunately this just won't take. I've checked my .bashrc file to no avail and I'm wondering where else I might have made that change. :-/ Any ideas? Is there a location where scripts/files are automatically run or any other locations where the terminal checks for PS1?

TIA

---

### Post by Dave_L on 2011-07-14
It might be /etc/profile, /etc/skel/.bashrc or /etc/skel/.profile.

---

### Post by matt_symes on 2011-07-14
Hi

Have a look in 

```
~/.bashrc
```That is where is should be, in your home folder.

/etc/skel/.bashrc. This is the skeleton file(s) used during creation of new user accounts. Hopefully you did not put it in there.

Kind regards

---

### Post by MkJackson on 2011-07-20
Definitely not in any of the /etc/skel files nor is it in ~/.bashrc. 

I'm also noticing that LD_LIBRARY_PATH is being somehow unset (meaning that I set it in the .profile file but when I log in and go to a terminal echo returns nothing for it). Could there be another script being triggered and if so, is there any way to figure out what they are?

---

### Post by matt_symes on 2011-07-21
Hi

> 
I'm also noticing that LD_LIBRARY_PATH is being somehow unset (meaning  that I set it in the .profile file but when I log in and go to a  terminal echo returns nothing for it).Export this from your .bashrc file.

```
export LD_LIBRARY_PATH="Your value"
```For PS1 check your .bash_profile file if you have one. If you really cannot find it (as you could have created and sourced your own file) then grep your hard drive.

```
grep -R PS1 /
```You can narrow down the search path if you have some idea where you made the change. This will bring up a number of false positives but should also identify the file where you made the change.

I would suggest you document what you change and also be consistent where you make the changes.

Read

```
man bash
```to see how the initialisation files are called for a console and virtual terminal. (invocation section).

Kind regards

---

### Post by MkJackson on 2011-08-15
Thanks but no love. "grep -r PS1 /" brought up so many things that I might as well have just opened each file one at a time. Gonna check out "man bash" but for now I've got bigger fish to fry. Thanks anyways and I'll update if I ever resolve this...

---

### Post by AlphaLexman on 2011-08-15
There is NO reason to search from the '/' (root) directory...

The prompt variable '$PS1' could be set and re-set thousands of times, but only the last occurrence is important!

If you are using bash (the default) and not ksh or zsh then try this...
```
for FILE in ~/*bash*; do grep -r PS1 $FILE; done
```and then compare the output to...
```
echo $PS1
```Good Luck!

---

