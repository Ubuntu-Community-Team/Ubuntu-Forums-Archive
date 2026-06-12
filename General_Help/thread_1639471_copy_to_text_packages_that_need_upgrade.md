---
title: "copy to text packages that need upgrade"
date: 2010-12-06
forum: General Help
---

### Post by orlandold on 2010-12-06
Hello, 

I will like to get a txt file of the packages that need to be updated in my ubuntu 9.10 machine. 

The thing is that I previously did an update an its made my Zoneminder setup fail, and now I want to double check prior to doing a full upgrade. 

If anybody could provide me with a command in the terminal or event synaptic, which could help get a printout or export to text file, the current version in my system with said that need to be updated to, for every packages. 

any suggestions, are welcomed. 

Thanks,

---

### Post by iiiears on 2010-12-06
apt-get i think will let you use --dry-run as an option.
synaptic just doesn't have the option to do it. (shrug)
maybe this will work.

sudo echo apt-get upgrade --dry-run > ~/Dry_run.txt

---

### Post by orlandold on 2010-12-16
> **iiiears said:**
> apt-get i think will let you use --dry-run as an option.
synaptic just doesn't have the option to do it. (shrug)
maybe this will work.

sudo echo apt-get upgrade --dry-run > ~/Dry_run.txt
unfortunately the proposed didn't worked on my system. any other suggestions are welcomed. 

Thanks,

---

