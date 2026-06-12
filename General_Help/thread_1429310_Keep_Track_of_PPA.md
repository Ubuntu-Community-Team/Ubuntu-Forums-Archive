---
title: "Keep Track of PPA"
date: 2010-03-13
forum: General Help
---

### Post by Jason Cook on 2010-03-13
I have found it really difficult to keep track of my PPA when installing on multiple computers. One way to keep track of the is to copy them into a text file and then add them put that takes time. You can set your computer to do this automatically by creating a bash script containing to following and placing it in ~/.scripts/ppa:
```

#!/bin/bash
echo "Adding PPA to ~/Documents/ppa..."
echo $@ >> ~/Documents/ppa
echo "Adding to Reporitory..."
echo `sudo add-apt-repository $@`

```
Run the command:
```

echo alias add-apt-repository="~/.scripts/ppa" >> ~/.bashrc && source ~/.bashrc

```
Now every time you add a PPA you will get a list of all of your PPA in ~/Documents/ppa.

---

