---
title: "thunderbird lighting color is too dim"
date: 2011-05-25
forum: General Help
---

### Post by yangli on 2011-05-25
I installed lightning 1.0b2 in my Thunderbird 3.1.10 to have calendar and tasks. They works fine except the task color is too dim grey. It's REALLY hard to read. The complete and incomplete tasks all have the same dim grey color. I wonder if there is a way to change the font color and background color. Thanks.

[IMG]http://img.villagephotos.com/p/2010-12/1362592/Selection_001.png.jpg[/IMG]

---

### Post by yangli on 2011-05-25
I googled a workaround for this. Change Appearance -> Themes -> (Don't choose Ambiance).

---

### Post by Subito Piano on 2011-12-18
*If you can't read your tasks in lightning, but you wish to keep your theme, you can edit the task text color easily; put the following code in 'userChrome.css' *

.calendar-task-tree > treechildren::-moz-tree-cell-text(future) { 
  color: black !important; 
} 

[I]NOTE: 'userChrome.css' should be placed in a directory called 'chrome'  inside your user profile directory. If you don't have already it, create  it.
FWIW, i had to create both the file and the directory.  You can make the color whatever you wish, of course, not just black. [/I] [I]

Thanks to [/I] *[gofu99]("http://getsatisfaction.com/mozilla_messaging/topics/in_lightning_how_to_change_the_text_color_for_task_lists") for this tip.*

---

