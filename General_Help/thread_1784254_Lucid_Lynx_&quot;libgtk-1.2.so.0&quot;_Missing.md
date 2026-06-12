---
title: "Lucid Lynx &quot;libgtk-1.2.so.0&quot; Missing"
date: 2011-06-16
forum: General Help
---

### Post by Zodiacprince on 2011-06-16
So, I'm trying to run Ultimate Duke Nukem 3D for Ubuntu, when I find out I'm missing libgtk-1.2.so.0. I've tried googling it, and every thread in this forum seems to be useless to me (e.g. E: Couldn't find package libgtk1.2). So I was wondering what I need to do to get the libgtk-1.2.so.0 for Lucid.

---

### Post by Toz on 2011-06-16
Lucid uses the newer libgtk2. Just did a google search ([https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/478219]("https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/478219")) and found a PPA that has lucid gtk+1.2 binaries: [https://launchpad.net/~adamkoczur/+archive/gtk1.2]("https://launchpad.net/~adamkoczur/+archive/gtk1.2")

To install:
```
sudo apt-add-repository ppa:adamkoczur/gtk1.2
sudo apt-get update
sudo apt-get install gtk+1.2
```

---

### Post by Zodiacprince on 2011-06-16
> **Toz said:**
> Lucid uses the newer libgtk2. Just did a google search ([https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/478219](https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/478219)) and found a PPA that has lucid gtk+1.2 binaries: [https://launchpad.net/~adamkoczur/+archive/gtk1.2]("https://launchpad.net/%7Eadamkoczur/+archive/gtk1.2")

To install:
```
sudo apt-add-repository ppa:adamkoczur/gtk1.2
sudo apt-get update
sudo apt-get install gtk+1.2
```

I don't think I can download them from the site, or do I have to click on the dude's name? Also, when I used the terminal commands it said "E: Couldn't find package gtk+1.2
"

---

### Post by Brushstroke on 2011-06-16
> **Zodiacprince said:**
> I don't think I can download them from the site, or do I have to click on the dude's name? Also, when I used the terminal commands it said "E: Couldn't find package gtk+1.2
"
Run in terminal: 

```
sudo add-apt-repository ppa:adamkoczur/gtk1.2 && sudo apt-get update
```That adds that dude's repository into your available packages. Go into Synaptic and look for gtk+1.2 then and it should be there. Or just run "sudo apt-get install gtk+1.2"

---

### Post by Toz on 2011-06-16
Try:```
sudo apt-get install libgtk1.2
```

---

### Post by Zodiacprince on 2011-06-17
> **Toz said:**
> Try:```
sudo apt-get install libgtk1.2
```
I'm a futzing idiot.... I should have thought of that... Well, anyway, thanks mate. Duke Nukem is working fine now (just need to find a disc...).

---

### Post by Toz on 2011-06-17
Glad to hear. If you don't mind, can you flag this thread as solved (from Thread Tools above) in case anyone else is looking for a similar fix?
Thanks

---

