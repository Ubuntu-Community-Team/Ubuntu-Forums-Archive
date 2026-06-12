---
title: "vlc reinstall"
date: 2012-01-28
forum: General Help
---

### Post by cmitt10 on 2012-01-28
i have a problem with vlc.i downloaded a skin and iset it up from preferences.i had had put the file to 
Usr/share/vlc/skins2 .the previous time had worked. This time maybe i wrote something wrong because the whole interface dissappeared nd i cannot get it back.I tried to remove and install vlc again but nothing happened.(when i mean from preferences i wrote in the box for default usr/share/ vlc/skins2/dno_black.vlt
i am new to ubuntu.how can i install vlc again ?Software center 'sees' only its own vlc package.Can i down load a new vlc package?[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]

---

### Post by Double.J on 2012-01-28
Hi there and welcome to the forums!

I got a bit confused by the exact problem, but it sounds as though you removed and reinstalled but the probelm was still there?

This is usually caused by left behind configuration files (sometimes we want to removed a peice of software and install a different version/package that uses the same config's - so remove leaves these behind)

To fully remove a package, either use the synaptic package manager (pres windows key, then type "synaptic" and hit enter.) find the vlc package and rightclick - remove completely

Or from the terminal (CTRL+ALT+T)
```
sudo apt-get purge vlc && sudo apt-get autoclean
```

Then you can install again and hopefully it'll be back to default?

Please  let me know if I've misunderstood!

All the best :)

---

### Post by cmitt10 on 2012-01-28
[IMG]http://farm8.staticflickr.com/7027/6776547359_0b45d5a677_m.jpg[/IMG][COLOR=Red][SIZE=3]**N[FONT=Courier New]OPE *BUT THANKS:confused:*[/FONT]**[/SIZE][/COLOR]

---

