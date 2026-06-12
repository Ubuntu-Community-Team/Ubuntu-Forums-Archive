---
title: "know what RAM I have?"
date: 2009-08-27
forum: General Help
---

### Post by m4lte on 2009-08-27
simple question:
Is there a way how I can see what kind of RAM is built into my machine? (e.g. DDR2 or DDR3, etc...)

cheers!

---

### Post by scragar on 2009-08-27
```
sudo lshw | grep -m 1 -A 25 "*-memory"
```
For explanation, lshw stands for **l**i**s**t **h**ard**w**are, and spits out page after page of information on all the hardware in your machine, this information is then sent to grep, which searches for a key word. I have set a few flags for it, _-m 1_ which limits the search results to one, saving some time finding additional results when there is only ever going to be one in the hardware output, and _-A 25_ which sets the number of lines of output after finding the search term to 25(default 0, which wouldn't help here). "*-memory" is there because this is our search term.

Do let me know if this works for you, I can't imagine why it wouldn't.
Oh, and you'll need to run it as root to get the information you want, without running it as root the output would not include the ram speed and type.

---

### Post by serpantman on 2009-08-27
that or you could read the sticker on the side of the ram

---

### Post by scragar on 2009-08-27
> **serpantman said:**
> that or you could read the sticker on the side of the ram

Which means opening up the case, when you could run a single line and find out far more than the sticker could tell you, without having to shut down the machine or go poking around inside the case. I know which I recommend.

---

### Post by scratman on 2009-08-27
My preferred method is to go to System > Administration > System Monitor > Resources  and look at the middle row.

---

### Post by scragar on 2009-08-27
> **scratman said:**
> My preferred method is to go to System > Administration > System Monitor > Resources  and look at the middle row.

That would show you size and nothing else, which for the most part is what most people would want, but the OP wants to know the TYPE of ram, not the size.

---

### Post by m4lte on 2009-08-27
thanks scragar. Worked great!

---

