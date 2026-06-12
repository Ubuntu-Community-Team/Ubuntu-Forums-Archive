---
title: "May have ran a bad command..."
date: 2011-01-11
forum: General Help
---

### Post by Viridia on 2011-01-11
So I was trying to run this:

sudo apt-get update && sudo apt-get upgrade

But then it stopped working in the terminal, so i got this:

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So then I ran this:

sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock

Which blanked my screen. I booted to a terminal and I ran apt-get update and apt-get upgrade. 

All my files are there, I ran -ls. Any advice as to how to log on graphically again?

Also-when I turn on the computer, it says the screen graphics card and the like were not detected properly.

Thanks,
Nick

---

### Post by Viridia on 2011-01-11
Also, at points it's said that I cannot resort to a dependency based boot or something along those lines.

---

