---
title: "Software Center only showing a few programs"
date: 2011-10-04
forum: General Help
---

### Post by soraxd on 2011-10-04
hello, ive used ubuntu in the past, so i know what the software center SHOULD look like. but i just installed 10.10 on my Aspire One D255E netbook, and am only seeing a few programs show up.. when i click "Internet" only 1 program shows up, when i click other areas, only 20 or so show up.. normally there will be thousands. what can i do?

---

### Post by drs305 on 2011-10-04
The two things I'd check would be:
1. Make sure you haven't inadvertently entered something in the search box that would filter the results.
2. Check your repositories to make sure they are enabled and update them. There should be a link in your version of Software Center to access Software Sources (Settings or Edit > Software Sources).

---

### Post by soraxd on 2011-10-05
theres nothing in the search bar. since i install ubuntu this morning, ive reset my computer a few times, and tried 4 different networks, ive updated everything i can find that can be updated.. i tried a bunch of different servers..
 im very inexperienced in linux, so please spell everything out for me, as i probably have no idea how to try your suggestions. but yeah, no idea whats causing this.. 

something possibly note worthy, when i clicked Help>report problem, i got this
"The problem cannot be reported: This is not a genuine Ubuntu package"

what could cause this error? it makes me think maybe reinstalling the software center could fix this issue. is there a way to do such a thing?

---

### Post by drs305 on 2011-10-05
The first thing you could try to do would be to reinstall Software Center and update the package index and list of packages. Open a terminal and run these commands:
```
sudo apt-get install --reinstall software-center
sudo update-apt-xapian-index
sudo apt-get update
```
If you haven't run sudo commands in the terminal: You will be asked for your password. You won't see it as you type; just press ENTER when you've typed it in.

If it still isn't working, you can check the Repositories:
```
gksu software-properties-gtk
```
This should open Software Properties. Click on the Ubuntu Software tab and make sure the top four items are ticked. If you make any changes, run:
```
sudo apt-get update
```

---

