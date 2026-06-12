---
title: "Help! Deleted Nautilus?"
date: 2010-07-07
forum: General Help
---

### Post by Evilhugbear on 2010-07-07
Hopefully this is the right place to post this.

 I tried to install covergloobus with this command : ```
sudo apt-get update && sudo apt-get install covergloobus gloobus-preview 

```

And it said this after doing its thing : 
The following packages have unmet dependencies:
  gloobus-preview: Depends: libgvfscommon0 but it is not going to be installed

So I typed ```
sudo aptitude instal libgvfscommon0
```

And it said it was removing a whole lot of stuff and one of them was nautilus, and when I try to open my home folder or anything it says : could not open location; no application is registered as handling this file

Did I just destroy ubuntu? :( 

This is ubuntu 10.04 32-bit.

Please Help!

---

### Post by DrMelon on 2010-07-07
Just do "sudo apt-get install nautilus". It should handle the dependencies itself. This will have the side effect of stopping gloobus from working - but this is better than the alternative.

---

### Post by kerry_s on 2010-07-07
did you try reinstalling nautilus?

---

### Post by Evilhugbear on 2010-07-07
That worked :D. I don't know why I didn't think of that lol...

So I have to reinstall all the other stuff it removed?

---

### Post by Leppie on 2010-07-07
you do not necessarily have to...
in synaptic there should be some kind of history of what's been installed/removed.

---

### Post by Evilhugbear on 2010-07-07
One of the things removed was gnome-panel.

Does that mean If I restart my panel won't be there?

---

### Post by Evilhugbear on 2010-07-07
> **DrMelon said:**
> Just do "sudo apt-get install nautilus". It should handle the dependencies itself. This will have the side effect of stopping gloobus from working - but this is better than the alternative.

So how do I use gloobus? :(

---

### Post by energybeing on 2010-07-07
> **Evilhugbear said:**
> One of the things removed was gnome-panel.

Does that mean If I restart my panel won't be there?

Yes.  You need to install gnome-panel again I think.

---

