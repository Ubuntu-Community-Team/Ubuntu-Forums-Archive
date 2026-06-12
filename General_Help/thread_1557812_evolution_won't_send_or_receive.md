---
title: "evolution won't send or receive"
date: 2010-08-21
forum: General Help
---

### Post by hubiedo on 2010-08-21
on ubuntu 8.04 and evolution has stopped sending or receiving when click send/receive button. it flashes something but too fast to read. i have renamed mail folder but no go. i have checked settings but no go. i have reinstalled evoulution from synaptic but no go. 

i think i have a corrupt file or something like that.

can anyone make a suggestion.

---

### Post by NCLI on 2010-08-21
Try opening a terminal and entering: 
```
sudo apt-get purge evolution && sudo apt-get install evolution
```

That command will also get rid of Evolutions configuration files.

---

