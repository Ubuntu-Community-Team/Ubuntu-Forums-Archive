---
title: "copy batches of 10,000 files from a folder..."
date: 2012-09-13
forum: General Help
---

### Post by sohlinux on 2012-09-13
How can I copy 10 batches of 10,000 images from a folder containing 100,000 images into 10 new sub folders?

I have a folder containing 100,000 images and I want to take the first 10,000 images and move them into a sub folder called folder1 then take the next 10,000 images and move them into folder2 etc until there are 10 new sub folders each having 10,000 images inside.

we must take into account that the images are named 0-100000 so the first batch moved would be image1.jpg to image10000.jpg, they must be in number order.

thanks

---

### Post by steeldriver on 2012-09-13
You can use the bash {m..n} sequence generation syntax to construct the filenames - however a simple 'mv image{1..10000} folder1/' command *might* barf due to the number of files in the list, so to be safe you could pipe through xargs - something like

```

echo image{1..10000} | xargs mv -t folder1
echo image{10001..20000} | xargs mv -t folder2

```etc.

Obviously you could do a for loop instead but I think xargs will be more efficient in a case like this (I just tried it after creating 20000 empty files with 'touch' and the xargs version was significantly faster).

I'm sure the real bash experts will have other ideas though

---

### Post by sohlinux on 2012-09-13
> **steeldriver said:**
> You can use the bash {m..n} sequence generation syntax to construct the filenames - however a simple 'mv image{1..10000} folder1/' command *might* barf due to the number of files in the list, so to be safe you could pipe through xargs - something like

```

echo image{1..10000} | xargs mv -t folder1
echo image{10001..20000} | xargs mv -t folder2

```etc.

Obviously you could do a for loop instead but I think xargs will be more efficient in a case like this (I just tried it after creating 20000 empty files with 'touch' and the xargs version was significantly faster).

I'm sure the real bash experts will have other ideas though

hey thanks, that worked fine and very fast! :P

---

