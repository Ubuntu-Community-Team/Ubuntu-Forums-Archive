---
title: "Acer Aspire 5532 overheats"
date: 2011-04-26
forum: General Help
---

### Post by DJ . on 2011-04-26
As you can tell by the title, my Acer Aspire 5532 (with a Logitech cooling pad) keeps overheating. I have Ubuntu 10.10 64 bit with Windows 7 64 bit. With Windows, It never overheated. With Ubuntu, it overheats too much. When in idle, my computer is around 60-63[COLOR=#000000]°[/COLOR]C and Internet browsing with firefox 4 (the most updated version of 4) is around 64[COLOR=#000000]-70°C. Running a game or watching a long youtube video brings it to overheating. The fan seems to be running at a very slow rate so I cleaned it but the fan is still going very slow, and the logitech fan isn't helping so what should I do?[/COLOR]

---

### Post by KegHead on 2011-04-26
Hi!

I noticed you're using 10.10.

When was the last time you updated your kernel?

KegHead

---

### Post by KegHead on 2011-04-26
Hi DJ!

Try:

sudo apt-get update 

sudo apt-get install linux-image -f

Restart.

Your kernel manages many parameters.

KegHead

---

