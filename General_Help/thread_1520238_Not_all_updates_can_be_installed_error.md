---
title: "Not all updates can be installed error"
date: 2010-06-29
forum: General Help
---

### Post by Crazy K on 2010-06-29
Just today I decided to check if there was any updates, so I go to the update manager and I get this message when it loads up:

[http://imgur.com/umZ8F.png](http://imgur.com/umZ8F.png)

It asks me to do a partial upgrade, what's this about? Should I do the partial upgrade? Will it mess with anything on my computer? What exactly is a partial upgrade? It wont upgrade to the next version of Ubuntu will it? Should I just close it and try to install the updates?

Sorry for all the questions, I just want to be sure.

UPDATE:

After I clicked close I get this error message: 

**Software Index is Broken:**
*It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.*

---

### Post by philinux on 2010-06-29
> **Crazy K said:**
> Just today I decided to check if there was any updates, so I go to the update manager and I get this message when it loads up:

[http://imgur.com/umZ8F.png](http://imgur.com/umZ8F.png)

It asks me to do a partial upgrade, what's this about? Should I do the partial upgrade? Will it mess with anything on my computer? What exactly is a partial upgrade? It wont upgrade to the next version of Ubuntu will it? Should I just close it and try to install the updates?

Sorry for all the questions, I just want to be sure.

Close the update manager. Try this first from a terminal.
```

sudo dpkg --configure -a 

then

sudo apt-get update && sudo apt-get upgrade
```

Post back with any errors.

---

### Post by Crazy K on 2010-06-29
It seemed to go well, didn't seem to encounter any errors. Should I run Update manager again?

---

### Post by MarkieB on 2010-06-30
no longer participating in ubuntuforums.org

---

