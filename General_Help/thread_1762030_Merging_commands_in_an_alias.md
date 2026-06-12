---
title: "Merging commands in an alias?"
date: 2011-05-18
forum: General Help
---

### Post by ianc1 on 2011-05-18
Hi

To keep this simple what I would like to do is```
sudo apt-get install package-name
echo "package-name" >> packages_installed.txt
```I know I can use "^^" to replace text so that I can do```
sudo apt-get install package-name
^sudo apt-get^echo
```to print the package name but how do I add the redirect to file to that second command without it becomming part of the text that replaces "sudo apt-get" and how do I merge the two commands into one command to form an alias?  I have aliases in my .bash_aliases file so can set them up but have never merged to commands using an argument from the first in the second.

Hmm, not sure that was simple after all.  Hope it can be understood.  I would really appreciate any help.

Now my reasoning:
I want to log all packages I install in a file.  I understand that this can be done at any point in time using```
dpkg --get-selections > packagelist.txt
```However this list contains all items installed by the OS not me and all dependencies and verison numbers.  Which I assume means the when the reverse is done ie I apply these packages to a fresh install issues may arise.  I have written a bash script employing aptitude to solve this but wish to learn a neater way and more about aliasing.

Thanks in advance for your time.

---

### Post by sisco311 on 2011-05-18
You could write a bash function. Something like:
```

install ()
{
  sudo apt-get install "$@"
  echo "$@" >> file
}
```

[http://mywiki.wooledge.org/BashGuide/CompoundCommands](http://mywiki.wooledge.org/BashGuide/CompoundCommands)

---

### Post by ianc1 on 2011-05-18
Many thanks for the solution.  So many things to learn I'm sure each time one new thing goes in I forget something I once knew.

Can I make such functions permanent by appending them to my .bashrc file or making a .bash_functions file and appending the following to my .bashrc file?

```
if [ -f ~/.bash_functions ]; then
    . ~/.bash_functions
fi
```Thanks again.

By the way excellent bash link a great reference may thanks.

---

### Post by sisco311 on 2011-05-18
> **ianc1 said:**
> Many thanks for the solution.  So many things to learn I'm sure each time one new thing goes in I forget something I once knew.


You are welcome! but... you're wrong. :evil:

> **ianc1 said:**
> 
Can I make such functions permanent by appending them to my .bashrc file or making a .bash_functions file and appending the following to my .bashrc file?

```
if [ -f ~/.bash_functions ]; then
    . ~/.bash_functions
fi
```Thanks again.


Yes, of course. Both methods are viable. I prefer the second one.

> **ianc1 said:**
> 
By the way excellent bash link a great reference may thanks.

Indeed. (Unfortunately) It's the only one I can recommend.

And you don't have to learn everything from the guide. Just bookmark it (alongside with the BashFAQ and BashPitfalls from the same site) and use it whenever you need. :p

---

### Post by ianc1 on 2011-05-19
Excellent.

Many thanks again, all is now sorted and I'm working on some other useful functions.

---

