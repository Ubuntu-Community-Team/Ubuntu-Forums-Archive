---
title: "Where is gksu gparted in ubuntu 11.04 ?"
date: 2011-10-08
forum: General Help
---

### Post by gaastra on 2011-10-08
Hi

I upgraded from older ubuntu version to ubuntu 11.04. Installed it on my USB, then booted it up.

Ubuntu launced.

But I can not find the place where to type in 'gksu gparted' in this new ubuntu version.In old version t was in the top menu, but this version has only left menu.

If this feature is not available in this ubuntu version, please tell me the last ubuntu version with this feature & top menu.

One more thing I would like to ask is that I saw a workspace changer in Ubuntu 11.04. I tried to swap my workspace & created a new file on it. Then I swapped back the the main workspace & this new file was created in every workspace. How is this useful? 

I mean I would find it useful, if you can only modify the current workspace. I dont get the purpose of this feature.

---

### Post by WasMeHere on 2011-10-08
Gparted is available to select in the Unity menu system (just by clicking, you need no command line). But you can also open a terminal with *ctrl + alt + t* and then write *sudo gparted*.

In the live system gparted is present at the very beginning because often you edit partitions from a live system. But in the installed Ubuntu system you have to install gparted before using it.
```
sudo apt-get install gparted
```

---

### Post by gaastra on 2011-10-08
> **Olle Wiklund said:**
> Gparted is available to select in the Unity menu system (just by clicking, you need no command line). But you can also open a terminal with *ctrl + alt + t* and then write *sudo gparted*.

In the live system gparted is present at the very beginning because often you edit partitions from a live system. But in the installed Ubuntu system you have to install gparted before using it.
```
sudo apt-get install gparted
```


Thanx I found it. It was hidden under applications lol,  had to use search to find it.

wonderful :)

---

### Post by Rubi1200 on 2011-10-08
Glad you got things sorted out.

Please mark this Solved using the Thread Tools near the top of the page.

Thanks.

---

### Post by WasMeHere on 2011-10-08
I'm glad you found it :-)
Please mark the thread SOLVED
Have fun
Olle

---

### Post by CatKiller on 2011-10-08
You created the file on the Desktop. You have access to your Desktop from any workspace because presumably those are files you want to hand. Workspaces are for organising open windows.

---

