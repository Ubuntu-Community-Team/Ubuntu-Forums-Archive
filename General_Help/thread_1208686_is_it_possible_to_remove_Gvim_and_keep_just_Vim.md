---
title: "is it possible to remove Gvim and keep just Vim?"
date: 2009-07-09
forum: General Help
---

### Post by Ascenti0n on 2009-07-09
Hi all,

I had installed Gvim
> sudo apt-get install vim-full

is it possible to remove Gvim and just have a full copy of Vim?

It's not a major deal, I'd just rather not have something on my system I no longer have a need for. Unless Gvim is embedded within Vim-full.

---

### Post by geirha on 2009-07-09
The package vim contains the regular vim, while vim-gnome contains the graphical vim that vim-full depends on. So, uninstall vim-full and install [vim](apt:vim) (if uninstalling vim-full also uninstalled vim along with it).

---

### Post by Ascenti0n on 2009-07-09
I tried:

> sudo apt-get remove vim-full

and

> sudo apt-get autoremove vim-full

and whilst I saw a lot of libs being removed (including java libs?) Gedit was still available to the system.

Any ideas?

---

### Post by geirha on 2009-07-09
Gedit? That's a dependancy of ubuntu-desktop. I wouldn't advice removing it. What vim packages do you currently have installed now though?
```
aptitude search '~i ^vim'
```

---

### Post by Ascenti0n on 2009-07-09
Here is the terminal output:

> i   vim-common                      - Vi IMproved - Common files                
i A vim-gnome                       - Vi IMproved - enhanced vi editor - with GN
i A vim-gui-common                  - Vi IMproved - Common GUI files            
i A vim-runtime                     - Vi IMproved - Runtime files               
i   vim-tiny                        - Vi IMproved - enhanced vi editor - compact

---

### Post by geirha on 2009-07-09
Hm, you still have vim-gnome, but not vim. I would've thought uninstalling vim-full would also uninstall vim-gnome, but anyway, uninstall vim-gnome then, and install vim.

---

### Post by Ascenti0n on 2009-07-09
OK that seems to have done it - thanks.

Just 2 more things:

1. does vim really rely on java libs?

2. do you the know the command to add to a panel Icon, to launch vim in a terminal? or isn't that possible?

---

### Post by Slim Odds on 2009-07-09
Why do you care if Gvim is installed?

If you want to use vim, just use vim.

---

### Post by Ascenti0n on 2009-07-09
> **Slim Odds said:**
> Why do you care if Gvim is installed?

If you want to use vim, just use vim.

see my previous post

plus, you comment was unhelpful.

---

### Post by geirha on 2009-07-09
Setting the comamnd to "gnome-terminal -x vim %F" should do it.

---

### Post by Ascenti0n on 2009-07-09
> **geirha said:**
> Setting the comamnd to "gnome-terminal -x vim %F" should do it.

I tried that and it didn't work :(

---

### Post by geirha on 2009-07-09
> **Ascenti0n said:**
> I tried that and it didn't work :(

I just tried it myself, and double-clicking it gave me a gnome-terminal with vim ...

---

### Post by Slim Odds on 2009-07-09
```

```> **Ascenti0n said:**
> see my previous post

plus, you comment was unhelpful.

I read your previous posts and was not satisfied with your reason. I was looking for more.

Why don't you like Gvim? What **really** is the problem?

I have used both for quite a while on a number of platforms (including Windows using cygwin) and I just don't see your problem.


P.S.```
sudo apt-get remove vim-full
sudo apt-get install vim
```

---

### Post by Ascenti0n on 2009-07-09
> **Slim Odds said:**
> I read your previous posts and was not satisfied with your reason. I was looking for more.

Why don't you like Gvim? What **really** is the problem?

I have used both for quite a while on a number of platforms (including Windows using cygwin) and I just don't see your problem.

This is a quote from my original post:
> It's not a major deal, I'd just rather not have something on my system I no longer have a need for.

Your comments are still not helping, where as Geirha's have been.

As I said in my OP, if it can't be done, no biggey, but it can be done, it has been done and Geirha helped me do it.

---

### Post by Slim Odds on 2009-07-09
```
sudo apt-get remove vim-full
sudo apt-get install vim
```

---

### Post by geirha on 2009-07-09
Does it work if you run ```
gnome-terminal -x vim
``` from a terminal?

---

### Post by Ascenti0n on 2009-07-09
> **geirha said:**
> Does it work if you run ```
gnome-terminal -x vim
``` from a terminal?

yes it does

---

### Post by geirha on 2009-07-09
Then putting it in a launcher should work too ... Do you get any error messages when you try running the launcher? Do you see any related error messages in ~/.xsession-errors?

---

### Post by Ascenti0n on 2009-07-09
no error messages. When I click the icon, I don't even see a terminal open up.

---

### Post by statistic on 2009-07-09
I just wanted to say say this is relevant to my interests, I have tried to do this in the past as well, I'm not sure if it's possible  as vim-full comes with the graphical interface, but installing vim alone only installs vim-tiny from what I remember.

---

