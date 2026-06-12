---
title: "Synaptic only from terminal"
date: 2011-06-06
forum: General Help
---

### Post by knutschr on 2011-06-06
This is not a big problem, but a while ago Synaptic stopped starting from menu.
I have to start terminal and there type 
```
sudo synaptic
```
How can i repair this?

---

### Post by sisco311 on 2011-06-06
What happens when you run:
```
gksu synaptic
```?

---

### Post by knutschr on 2011-06-06
I think you could have a clue there!
gksu has stopped  working too.

---

### Post by knutschr on 2011-06-06
I now reinstalled gksu and libgksu-2.0
Still same problem:-)

---

### Post by sisco311 on 2011-06-06
Does the authentication window pop up? Do you get any error messages or warnings?

---

### Post by knutschr on 2011-06-06
Nothing happens

---

### Post by ajgreeny on 2011-06-06
Let's see your /etc/sudoers file with ```
sudo cat /etc/sudoers
``` to see if anything is wrong there.

I am not sure about natty, but previous versions of ubuntu had an entry in **gconf-editor->apps->gksu** which enabled or disabled sudo as the backend of gksu (see screenshot).  I'm not even sure if that place exists in ~/.gconf in natty, as I know a lot of changes are, or have already happened, and some of the configuration has gone I think to ~/.config/dconf, perhaps this is one of those things.  Search around and see if it helps you in any way.  I have not moved to natty, and don't think I shall be, so can't help further, I'm afraid.

What happens if you use **gksudo synaptic** instead of gksu synaptic?

---

### Post by knutschr on 2011-06-21
Just posting reply in case someone searh this later.
```
sudo gedit /etc/hosts
```
The name in second line was wrong.
I edited, and all got right :-)

---

