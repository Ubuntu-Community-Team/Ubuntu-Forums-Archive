---
title: "Change /media mount names"
date: 2010-02-18
forum: General Help
---

### Post by toaksie on 2010-02-18
I have weird names for my win partition when mounted it looks as follows:

/media/6B8ECA493C83793D 

whilst my android phone looks like this

/media/3338-6230

how can I change these names permanently to a more human readble/usable form (of my choosing preferably),

Thanks

Tom

---

### Post by nothingspecial on 2010-02-18
```
sudo apt-get install gparted
```
```

sudo gparted
```

Right click on the partition, disk etc you want to name and choose label.

I have no idea weather this would be a good idea on a phone or not --- I wouldn`t do it to your phone until you have further info.

---

### Post by toaksie on 2010-02-18
Any way of doing from the command line, I'm trying to get better at using it, thanks.

---

### Post by nothingspecial on 2010-02-18
Yes, see [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive")

---

