---
title: "Drop Down Menu"
date: 2012-07-19
forum: General Help
---

### Post by brain7734 on 2012-07-19
Hi everybody! I have deleted a few folders I did not need, now under _Applications, Places, and System_, the drop down menu still displays the icon of the folders I have deleted. Can someone tell me how to remove the unwanted icons from the drop down menu? I have Ubuntu 10.04 if that helps. I will greatly appreciate any help from you!!

---

### Post by dcsoldschool53 on 2012-07-19
> **brain7734 said:**
> Hi everybody! I have deleted a few folders I did not need, now under _Applications, Places, and System_, the drop down menu still displays the icon of the folders I have deleted. Can someone tell me how to remove the unwanted icons from the drop down menu? I have Ubuntu 10.04 if that helps. I will greatly appreciate any help from you!!

You can do one of two things, in a terminal, type```
alacarte
```Look through it and find what you want. Remove the check mark.
Or you can right click on Application > Edit menu. Look for the folder and remove the check mark.

---

### Post by brain7734 on 2012-07-19
So simple!! Thank you dcsoldschool 53!!

---

### Post by dcsoldschool53 on 2012-07-19
If you meant the folders under places then, in the terminal type ```
gedit ~/.gtk-bookmarks
```

---

### Post by brain7734 on 2012-07-19
Thank you. I have solved the problem.

---

