---
title: "Downloading with apt-get advice"
date: 2006-06-08
forum: General Help
---

### Post by Damnation667 on 2006-06-08
Hi

If you use the command for example: sudo apt-get install acroread

It downloads and installs Acrobat Reader. 

1. Where do all those downloaded files get stored and do they get removed after being installed?

2. Can I use apt-get to download stuff without installing them and how do I do that?

I want to download all my codecs, etc and put all of that in one folder for later use, possible?

Regards

---

### Post by hvbakel on 2006-06-08
The downloaded files get stored at /var/cache/apt/archives. I wouldn't recommend deleting the packages directly there though, instead, use the command ```
apt-get clean
```

---

### Post by CronoDekar on 2006-06-08
1. The debs are kept /var/cache/apt/archives , and by default are kept unless the package is no longer available.  You can change this option to make them delete upon download in Synaptic by going to Settings > Preferences, and selecting the appropriate button.  If you want to immediately clear the cache, you'll find the button in the same place, or you can use:

sudo apt-get clean

2. Yup!  If you're in Synaptic, once you have your downloads and hit "apply," there'll be a checkbox to download the packages only.  When doing it from command line you just have to use the -d switch, as such:

sudo apt-get -d *packagename*

---

### Post by Damnation667 on 2006-06-08
Ok, thats nifty. 

So I can go and copy all those files in that folder on a CD and later when I maybe brake Ubuntu, I can install everything again from my CD?

---

