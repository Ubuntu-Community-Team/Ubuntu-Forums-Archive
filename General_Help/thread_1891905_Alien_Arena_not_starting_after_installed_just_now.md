---
title: "Alien Arena not starting after installed just now"
date: 2011-12-06
forum: General Help
---

### Post by slixz85 on 2011-12-06
hi as title says i just cant get alien arena to start playing, i installed it through synaptic it is in the applications games just not starting when I clicked it. I reinstalled it also and still does the same thing. synaptic said it installed everything it depends on. i clicked the mark now button to install the other packages that alien arena wanted.

that is error i get when trying to start

ace@ThinkCentre:~$ alien-arena
ln: creating symbolic link `/home/ace/.config/alien-arena/data1': Permission denied
using /home/ace/.config/alien-arena/arena for writing
Could not exec default.cfg
Could not exec config.cfg
Console initialized.
--------- [Loading Renderer] ---------
Master server at 69.136.224.226:27900
Sending shutdown to 69.136.224.226:27900
recursive shutdown
Error: Couldn't load pics/colormap.pcx

it doesnt do anything different when ran as root as it says permission denied above.

---

### Post by slixz85 on 2011-12-06
i figured it out. i just had to install package libkrb53 which is available in 11.10 and wasnt in karmic as this bug shows. [https://bugs.launchpad.net/getdeb.net/+bug/480928](https://bugs.launchpad.net/getdeb.net/+bug/480928)

i still would like to know however how i can make the menu link for the alien arena game work. with this libkrb53 package installed it works but only from terminal still and won't run under normal privelege it wants sudo -i then alien-arena.

the bug page said sound for karmic wouldnt work without the libkrb53 package but my speakers are blown lol so i gotta get some to even see if the sound works now.

thanks

---

### Post by kydd on 2011-12-06
i've had the same problem as well. glad it's been fixed.

---

### Post by engla on 2012-01-28
"Real" workaround (no dumb sudo tricks): Remove the symlink at ~/.config/alien-arena and put a folder in its place.

```
rm -v ~/.config/alien-arena
mkdir -p ~/.config/alien-arena
```

---

### Post by cbennett926 on 2012-07-22
> **engla said:**
> "Real" workaround (no dumb sudo tricks): Remove the symlink at ~/.config/alien-arena and put a folder in its place.

```
rm -v ~/.config/alien-arena
mkdir -p ~/.config/alien-arena
```


FANTASTIC!!!

Please someone mark this as solved!

EDIT:

Noticed it was solved.... Guess I was too excited!

---

