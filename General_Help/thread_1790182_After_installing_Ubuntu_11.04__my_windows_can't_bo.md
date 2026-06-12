---
title: "After installing Ubuntu 11.04  my windows can't boot again"
date: 2011-06-24
forum: General Help
---

### Post by Chibuzo on 2011-06-24
I'm not sure if here is the right place to ask this. After installing Ubuntu 11.04 my windows 7 installation can't boot again. I installed ubuntu on a different partiton. I can see the windows partition on my ubuntu, from the disk utility, the partition type is unknown(0x42), trying to change it gives me error. Please what do I do? Thanks

---

### Post by Rubi1200 on 2011-06-24
Hi and welcome to the forums ::-)

Do not try and change the partition type!!!

Instead, do this from inside the working Ubuntu install so we can see what is going on:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by kleovoulinos on 2011-06-24
> **Chibuzo said:**
> I'm not sure if here is the right place to ask this. After installing Ubuntu 11.04 my windows 7 installation can't boot again. I installed ubuntu on a different partiton. I can see the windows partition on my ubuntu, from the disk utility, the partition type is unknown(0x42), trying to change it gives me error. Please what do I do? Thanks

I am sure that Rubi's Suggestion was really helpful, but what I would like to tell you is to always backup your before doing either a small or big change. There are many guides available on the web to help you do that in (Ubuntu) Linux.

---

