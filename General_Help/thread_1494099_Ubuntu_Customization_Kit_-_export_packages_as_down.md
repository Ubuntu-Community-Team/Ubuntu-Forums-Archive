---
title: "Ubuntu Customization Kit - export packages as download script"
date: 2010-05-26
forum: General Help
---

### Post by rbaleksandar on 2010-05-26
Hi, guys.

  I want to make a smaller version of Xubuntu for my laptop and maybe for the PC at home. So I removed many packages all of which I find unnecessary and won't harm the system to remove them. But just to be sure and have a list of all packages I've included, I want to make a download script that will obtain all these packages. I can do this by hand of course but since Synaptic has the ability to do that for me, I don't see why shouldn't I use it. ;) Alas, the UCK package manager has this ability but it seems it doesn't work. When I click on **Generate package download skript** all I get is a 10KB shell script file that has nothing in it except one single line:
```

#!/bin/sh

```

  **The question - as you might have already guessed - is: why does this happen?**

  I can use 
```
dpkg --get-selections > installed-packages
```
and than 
```
dpkg --set-selections < installed-software
dselect
```
but this can happen only when I start the Xubuntu. And it is possible that I've missed something and thus made a big mistake resulting in system crash or something like that. In such cases I won't be able to do the commands mentioned above. That's why I want to be prepared and have them all lined up in a file so that I can add them and than others if something goes wrong.

Cheers,
rba

---

