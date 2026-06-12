---
title: "unistalled evolution - now ubuntu not working - help, please"
date: 2011-01-24
forum: General Help
---

### Post by kismul on 2011-01-24
To make more room on the drive, I decided to remove evolution, which I don't use.  I searched for Evolution in Synaptic and marked each installed part for "removal" (but not "complete removal") in .  With some of the  marks, I got a dialog box stating that certain other files needed to be marked as well and offering the option of marking them.  I did so.

I then ran Synaptic.  When I rebooted my PC, it won't boot into Ubuntu (9.10, at the moment),  It goes through into the initial menu (giving the login options for each of the three users) but, when I select me and type in my password, instead of the normal screen, I get what appears to be a white terminal dialog (although without any menus) in the top left hand corner, with a command prompt.  I can't get it to go to Ubuntu.

Can anyone suggest what I've done wrong and how to fix it.  It's soooo frustrating.

Many thanks

Jim

---

### Post by sikander3786 on 2011-01-24
Did you try re-installing evolution?

Press Ctrl + Alt + F1 at the login screen and log in to tty1 using your credentials.

```
sudo apt-get install evolution
```

```
sudo apt-get install -f
```

```
sudo apt-get update && sudo apt-get upgrade
```

It might have happened that when you remove evolution, some dependencies were removed which included some important packages.

If you are running out of space, you can free up some space by cleaning the apt cache.

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

---

### Post by cpmman on 2011-01-24
When I tried to uninstall evolution it wanted to uninstall ubuntu-desktop as well - I didn't do it.  You might try

```
sudo apt-get install ubuntu-desktop
```

---

### Post by kismul on 2011-01-24
Many thanks for these suggestions.  I'll give them a go and report back.

---

### Post by kismul on 2011-01-24
> **cpmman said:**
> When I tried to uninstall evolution it wanted to uninstall ubuntu-desktop as well - I didn't do it.  You might try

```
sudo apt-get install ubuntu-desktop
```

This worked!  Although, from what I could read of the code that went past on the screen, it was installing other things as well, as I've re-installed Evolution - so it may be that I've inadvertently followed Sikander's suggestion as well!  

No matter - I'm back in the saddle and smelling the coffee .... Not above mixing the metaphors either! 

For us novices, this forum is like having a crowd of mates just waiting to help.  Many many thanks for your help, guys.  :D

---

### Post by ajgreeny on 2011-01-24
The ubuntu-desktop package is of little consequence itself.  It is a meta-package and merely ensures that all the packages on which the ubuntu gnome desktop system depends, are installed.  You can remove it and will see little difference to your system until you try to do a distro upgrade, eg from 10.04 to 10.10.

However there are several packages of the gnome desktop that both gnome and ubuntu can not function properly without, including, as you unfortunately found, evolution, and several other packages which are in their own way, dependent on evolution and so are removed as well when evolution is removed.

I realise that you have already solved this main problem, but just added this post as a warning to others to make sure they know what they are really doing before simply clicking to remove a whole mass of packages.

---

### Post by kismul on 2011-01-24
> **ajgreeny said:**
> The ubuntu-desktop package is of little consequence itself.  It is a meta-package and merely ensures that all the packages on which the ubuntu gnome desktop system depends, are installed.  You can remove it and will see little difference to your system until you try to do a distro upgrade, eg from 10.04 to 10.10.

However there are several packages of the gnome desktop that both gnome and ubuntu can not function properly without, including, as you unfortunately found, evolution, and several other packages which are in their own way, dependent on evolution and so are removed as well when evolution is removed.

I realise that you have already solved this main problem, but just added this post as a warning to others to make sure they know what they are really doing before simply clicking to remove a whole mass of packages.

Your warning is well-made and others should take note.  The problem is that it's  nigh on impossible to find these things out without going through what I did.  Nothing I could find suggested I might encounter this type of problem.  

I'll think twice before removing software in future.

---

