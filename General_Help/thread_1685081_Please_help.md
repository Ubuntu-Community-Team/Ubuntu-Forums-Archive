---
title: "Please help"
date: 2011-02-10
forum: General Help
---

### Post by dank91 on 2011-02-10
I'm on Ubuntu 10.10,not problem before,but don't know why few days ago,i just cannot right click on my folder,i can right click on my other files like pictures,video,music no problem,just folder.i can open the folder by double clicking it,but just cannot right click or delete it with delete button.help me~

---

### Post by Perfect Storm on 2011-02-10
How did you create the folder you want to delete?

---

### Post by dank91 on 2011-02-10
i can right click on the white space or desktop no problem just cannot right click on the folder icon

---

### Post by Perfect Storm on 2011-02-10
Can you please re-explain or rephrase what you're saying?

---

### Post by dank91 on 2011-02-10
Oh,sorry for my poor english.i mean i can right click and see the pop up on my desktop,or inside folder,you know ? but white blank background,i can right click there.i just cannot right click and get the pop up from any folder.

---

### Post by dank91 on 2011-02-14
*bump*

---

### Post by Iowan on 2011-02-14
Dunno if it will help, but [here]("http://ubuntuforums.org/showthread.php?p=10459147") is a thread that is *similar*.

---

### Post by WorMzy on 2011-02-14
I think s/he's trying to say that no context menu is appearing when right-clicking on a specific folder.

That's certainly not something I've ever experienced, but I would expect the problem to be caused by nautilus, or one of it's plugins.

You could try opening Synaptic Package Manager (System -> Administration -> Synaptic Package Manager), searching for "nautilus", and selecting all currently installed packages in the results and marking them for reinstallation (right-click -> Mark for reinstallation). Tell Synaptic to apply changes, wait for it to finish, then restart nautilus by pressing Alt+F2, typing "killall nautilus", and clicking "run".

---

### Post by dank91 on 2011-02-15
i did what [http://ubuntuforums.org/member.php?u=1062896](http://ubuntuforums.org/member.php?u=1062896) said,but it still doesn't work,yea.i had the problem that he said,nothing happen when i right click on a file

---

### Post by dank91 on 2011-02-15
its like this,when you click a folder and go Edit,you should be able to click on Cut Copy,but mine just like disabled.help help~

---

### Post by Perfect Storm on 2011-02-15
Can you make a new folder or file in there?

---

### Post by WorMzy on 2011-02-15
Can you open a terminal (Applications -> Accessories -> Terminal) and run the following:

```
ls -l ~
```

(I'm assuming that the file/folder is in your home folder)

EDIT: On closer inspection of your sceenshot, it's in the Music folder. Run

```
ls -l ~/Music
```

instead.

---

### Post by dank91 on 2011-02-15
Hey,i don't know what happened,last night i did what u guys told me and restarted doesn't help but this morning it just ok already,i can now right click my folder.haha thanks anyway guys

---

### Post by dank91 on 2011-02-15
NOOOOOOOOOOO,just right after i reply my previous msg then it doesnt work again..wtff

---

### Post by dank91 on 2011-02-15
why there's a green highlight ???

---

### Post by dank91 on 2011-02-15
ya,i can make a new folder there

---

### Post by dank91 on 2011-02-16
*bump*

---

### Post by WorMzy on 2011-02-16
> **dank91 said:**
> why there's a green highlight ???

Because that directory can be written to by anyone classed as "other" (not the owner ore a member of the owning group). You don't really need to worry about that, using "chmod 775" on it would fix it.

To be honest with you, I'm stumped. Your permissions are a bit wild, but there's nothing that I can see which would lock down the directory like that.

---

### Post by dank91 on 2011-02-16
Weird,but tonight i turned on and i can right click on my folders again.oh God

---

### Post by dank91 on 2011-02-16
quite wtf,just right after i reply msg then i cannot right click again ? oh man what's going on

---

### Post by dank91 on 2011-02-16
haiz,i think i just reinstall my ubuntu,duno why my computer always got so many problem.

---

### Post by dank91 on 2011-02-16
hey,i know the problem already.Once i connect to my wireless,then i won't be able to right click on my folders,if i disconnected from my wireless,then i'm able to right click on my folders again. help help~

---

### Post by dank91 on 2011-02-17
*bump*

---

