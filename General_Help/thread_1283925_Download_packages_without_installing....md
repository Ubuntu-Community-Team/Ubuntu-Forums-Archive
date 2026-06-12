---
title: "Download packages without installing...?"
date: 2009-10-06
forum: General Help
---

### Post by prasadbrg on 2009-10-06
Hello everyone,
  I need to have multiple backup systems, i.e. notebooks running Ubuntu with the same applications as my current notebook (I'm a musician and use audio applications for live performances). Apart from the installation DVD/CD/USB stick, I'd like to have my favourite applications already downloaded on to a memory stick, so that I don't need to download them to install, every time I make a backup (I have a fairly sizeable list of essential applications/packages). 
Would installed applications be already there on my system, as installable 'packages' (.deb files?) ? If so, where do I look for them? If not, how do I download them? And finally, is there some way I can automate the process of installing my list of packages on other systems?
My apologies for the long list of questions! I'd appreciate any help in this regard. Thanks in advance...
Cheers,

Guru

---

### Post by dcstar on 2009-10-06
> **prasadbrg said:**
> 
.........
If not, **how do I download them**? And finally, is there some way I can automate the process of installing my list of packages on other systems?
My apologies for the long list of questions! I'd appreciate any help in this regard. Thanks in advance...


[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by slakkie on 2009-10-06
```

aptitude --download-only install <package> <package2> <package3> ....

```

This will only download them, including any dependency they might have, and place them in /var/cache/apt.

```

# Get package list on pc A
dpkg --get-selections > list_of_installed_packages

# On a clean system
sudo dpkg --set-selections < list_of_installed_packages
sudo apt-get dselect-upgrade

```

Hope this answers all of your questions.

---

### Post by Bonster on 2009-10-06
APTonCD if u want to save ur debs ez

---

### Post by prasadbrg on 2009-10-06
Thanks to everyone who replied!
Thanks, slakkie, that does answer all my questions... I had expected that there would be a neat command line solution, exactly on the lines of what you have suggested. 
OTOH, I was pleasantly suprised by AptOnCD. It seems tailor-made for my requirements, and is remarkably convenient. :D Thanks bonster!
Cheers,

Guru

---

