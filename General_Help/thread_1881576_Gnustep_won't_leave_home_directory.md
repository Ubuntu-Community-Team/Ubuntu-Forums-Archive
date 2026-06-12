---
title: "Gnustep won't leave home directory"
date: 2011-11-15
forum: General Help
---

### Post by Townley89 on 2011-11-15
Hey guys,

So I wanted my computer to say stuff aloud a la 'espeak' but i forgot what the program name was so upon trying "say 'hello'" in terminal, I was told I needed to install GNUstep. I did so, and it installed a folder into my home directory called gnustep. When I realized this wasn't what I wanted, I tried to uninstall gnustep (sudo apt-get remove gnustep) but it tells me the package has been uninstalled. Still, this folder persists in my home directory right next to Documents. I try moving it to the trash, but it comes back. I move it around and it returns back to the home directory. I can't do anything to get rid of the folder. It's the folder from hell. Any idea how I can get rid of this blight upon my Home directory once and for all?

Many thanks,
Robert

---

### Post by gordintoronto on 2011-11-16
I would install it in Synaptic Package Manager, then "mark for complete removal," and then "apply."

---

### Post by Sephiac on 2012-07-04
Same problem here. I tried installing and removing from synaptic package manager, but to no avail. I also tried sudo apt-get autoremove to make sure that I didn't have anything lingering, but nothing.

---

