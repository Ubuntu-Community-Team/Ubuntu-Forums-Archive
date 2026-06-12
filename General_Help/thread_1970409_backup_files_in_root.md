---
title: "backup files in root"
date: 2012-05-01
forum: General Help
---

### Post by Achilles124 on 2012-05-01
I switched from Ubuntu 10.04 to Xubuntu 12.04. But before I did that, I made a backup of my files on DVD's.

After installation of Xubuntu, I put them all back on my harddisk, but to my big surprise, they were all in root.

I googled a bit and understood that there was a workaround by using chown. 
This is what I did:
```
sudo -i
sudo chown ecmporter -R /Images 
```

I received the error: file or map Images not discerned or something like that.
```
sudo chown ecmporter -R Images
``` didn't work either.

Then I did something wrong. I lost control of sudo and su and I had to reinstall xubuntu again.

So, I have two questions for the community:
1. Why are the images, musicfiles and documentfiles burned in root?
2. Please give me the correct code so that I don have to reinstall everything again.

Thanks in advance.

---

### Post by Achilles124 on 2012-05-01
I have been extremely clumsy. I wanted to change ownership of files and folders I already had ownership of. And that didn't work out very well, of course. :lolflag:

---

### Post by LewisTM on 2012-05-01
Deleted

---

