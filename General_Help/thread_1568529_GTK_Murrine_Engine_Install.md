---
title: "GTK Murrine Engine Install?"
date: 2010-09-05
forum: General Help
---

### Post by jinba.ittai on 2010-09-05
Went to the site and downloaded the latest version(second file down), extracted and its just a text file. What do i do next?

Tried downloading the first file but got an error when trying to extract

---

### Post by Irony on 2010-09-05
This is in the repository, search for gtk2.

---

### Post by jinba.ittai on 2010-09-05
Currently following [This post]("http://ubuntuforums.org/showthread.php?t=1563411&highlight=murrine") seeing as it has to deal with the same theme i am trying to install. Its just the same terminal commands as the one on gnome look but i keep getting errors with 10.10

---

### Post by Lateralis on 2010-09-05
sudo aptitude install murrine-themes

or

sudo aptitude install gtk2-engines-murrine

---

### Post by jinba.ittai on 2010-09-05
After the second command, i hit the AMD64 Package succesfully, then prompted these errors 

```
N: Ignoring file 'am-monkeyd-nautilus-elementary-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'elegant-gnome-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'murrine-daily-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by jinba.ittai on 2010-09-05
Closed the synaptic and re opened it, then the engine didnt show up at all.

---

### Post by Jesus_Valdez on 2010-09-05
Do you have all the repositories enable?

---

### Post by jinba.ittai on 2010-09-05
> **Jesus_Valdez said:**
> Do you have all the repositories enable?

I believe so, how would i know?

---

### Post by jinba.ittai on 2010-09-05
```
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
N: Ignoring file 'am-monkeyd-nautilus-elementary-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'elegant-gnome-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'murrine-daily-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```



After running 
```
sudo add-apt-repository ppa:elegant-gnome/ppa
sudo apt-get update && sudo apt-get install elegant-gnome
```

---

