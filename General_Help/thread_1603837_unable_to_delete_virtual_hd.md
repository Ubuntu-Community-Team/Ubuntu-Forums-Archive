---
title: "unable to delete virtual hd"
date: 2010-10-23
forum: General Help
---

### Post by ArbiterOfTruth on 2010-10-23
Good day,

As you all know, since it was you guys that helped me do it, I recently installed VirtualBox onto my netbook.
Everything went well & I installed Windows XP on my virtual hard drive. I was able to boot into about 6 times, then one day I was not. The installation was not shown instead somehow completely vanished.

When I tried to create a new install, I attempted to use the virtual 10 GB partition I had XP on & it would not let me. 

[IMG]http://i894.photobucket.com/albums/ac143/Tru3b0rn/no_INSTALL.png[/IMG]

When I tried to delete the partition it also would not let me.

[IMG]http://i894.photobucket.com/albums/ac143/Tru3b0rn/not_removing.png[/IMG]

I looked over the notes to see if I had done anything wrong during installation & I did see I left out a part where I was supposed to go to the Admin section & check off an option. I have now done so. I just need to delete this partition.

Thanks in advance,
ArbiterOfTruth

---

### Post by Irony on 2010-10-23
Just navigate your way to;
```
/home/oldtimeveteran/.VirtualBox/HardDisks
```
and delete the WinXP.vdi file.

---

### Post by ArbiterOfTruth on 2010-10-24
How? Please also keep in mind I am on the netbook remix edition.

---

### Post by Irony on 2010-10-25
I'm not sure what you mean... you just go to your home folder, click view to see hidden folders and delete the necessary file, just like you would delete a file in any other folder.

Or just paste the /home/oldtimeveteran/.VirtualBox/HardDisks path in your address bar of your windows manager and delete the file, just like you would delete a file in any other folder.

---

### Post by ArbiterOfTruth on 2010-10-28
Thanks a lot for the explanation. I'm not a Ubuntu expert so I didn't know about the View> Show Hidden Files thing & the netbook edition doesn't have the location bar to type in. Thanks again!

---

