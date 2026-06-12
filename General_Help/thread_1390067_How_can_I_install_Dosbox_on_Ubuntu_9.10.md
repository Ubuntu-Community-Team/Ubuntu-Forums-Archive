---
title: "How can I install Dosbox on Ubuntu 9.10?"
date: 2010-01-25
forum: General Help
---

### Post by Allyanora on 2010-01-25
It was simple installing Dos-box in windows, but now that I've switched to Ubuntu, and I am new to it, I don't know how to install it.

should i download the win32 executable and run it with wine? or there is a simpler way to install it from terminal or download packages and... how?

I've looked on the Dos-box download page.. but i didn't understand a thing.

Any ideas?

---

### Post by Grenage on 2010-01-25
Looking at the website, there are dosbox versions for linux.  I recommend you download and install those, rather than use a windows binary through wine.

---

### Post by NEUR0M4NCER on 2010-01-25
Go to the Ubuntu Software Centre (in your 'Start' menu) and type in dosbox.

Click 'Install' - you're good to go.

---

### Post by anaconda on 2010-01-25
or type in terminal:
sudo apt-get install dosbox

and the easiest way to use dosbox is to  navigete to the folder where the dos-program is and then just right-click on the .exe or .bat or .com file and select open with dosbox...

---

### Post by Allyanora on 2010-01-25
wait. that easy? just sudo apt-get install dosbox?

ok, it seems I was just complicating myself :))

but another thing. I have a folder on the desktop, and i want it to be mounted. the problem is that the root name is / and it doesn't let me mount it like that. are there any solutions?

---

### Post by rCXer on 2010-01-25
It should be as simple as...
```

mount c "~/Desktop/YourFolder"

```

---

