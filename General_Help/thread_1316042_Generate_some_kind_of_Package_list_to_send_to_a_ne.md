---
title: "Generate some kind of Package list to send to a new machine?"
date: 2009-11-05
forum: General Help
---

### Post by munkifisht on 2009-11-05
Hi there. I want to generate some kind of (hang on, all this is in the title).... Anyway, I am not keen on using APTonCD (sure it's grand, jsut not for me if pos) so what I want to do is generate a list of installed packages on one machine and send it (via email) to a new setup and install all the same programs all over again. BUT HOW you hear me ask.

I was looking at this thread

[http://ubuntuforums.org/showthread.php?t=144817](http://ubuntuforums.org/showthread.php?t=144817)

but I think that is not working for 9.10, but a variation I think is what I need.

---

### Post by sisco311 on 2009-11-05
[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/]("http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/")

---

### Post by rue1341 on 2009-11-05
You could :-
  synaptic package manager-file-save markings

put the saved file on the other computer and then:-
  synaptic package manager-file-read markings

---

### Post by munkifisht on 2009-11-05
I do fine up to this point:::
```

dpkg –set-selections  < ubuntu-files
 *NOTE: Wordpress interprets two dashes (- -) as one dash (–). When you’re putting this into your CLI, make sure it’s dropping two dashes ‘- -’ without the space between them.*
 Now you’ve told your system what it needs to install, so let’s install it all.
 [INDENT]sudo dselect
```
[/INDENT]I assume it's sudo dpkg –set-selections  < ubuntu-files but the dselect command is not found

---

### Post by sisco311 on 2009-11-05
yes it's *sudo dpkg --set-selections ....*

and yep, dselect is not installed by default:
```
sudo apt-get install dselect
```

---

### Post by Giblet5 on 2009-11-05
```
sudo dpkg -l | awk '{ print $2 }' | sed -e '1,5d'
```

---

### Post by dcstar on 2009-11-05
> **rue1341 said:**
> You could :-
  synaptic package manager-file-save markings

put the saved file on the other computer and then:-
  synaptic package manager-file-read markings

Too simple using the GUI apps - you need to recommend arcane command line stuff so people can remain stuck in that world.......     ;)

---

