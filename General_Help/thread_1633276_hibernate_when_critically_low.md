---
title: "hibernate when critically low"
date: 2010-11-29
forum: General Help
---

### Post by nathanateneoupxxx on 2010-11-29
i have a trouble whenever i unplug my laptop. my laptop suddenly hibernates/suspend/shutdown depending on the setting i chose  whenever i unplug the computer. ubuntu says that the computer will hibernate/shutdown/suspend because the battery is critically low. my question is . . . how can i SPECIFY the battery level when the computer will hibernate/suspend/shutdown? even though my laptop is still 50% charged, ubuntu automatically assumes the bettery is very low. i am using ubuntu 10.10

---

### Post by ajgreeny on 2010-11-29
Try this.
The 'critical power' criteria can be set to use the battery charge  remaining instead and there is a setting in the gnome-power-manager to  do that but it is not accessible from the normal GUI. You need to use a  terminal and run 
 gconf-editor
 The Configuration Editor can also be accessed by enabling it in  Applications - it is very powerful and you can easily make a system  unusable so it is hidden by default. To enable it Right Click on  Applications -> Edit Menus -> System Tools and tick the box beside  Configuration Editor. It will now be available under Applications ->  System Tools -> Configuration Editor.
 In Configuration Editor -> apps -> gnome-power-manager -> general and** untick 'use_time_for_policy'**
 It seems that a settling time was used in Hardy and Jaunty which is  not applied in  Lucid. The change should be  a permanent fix for each  user - it may need to be reapplied for other users.

---

