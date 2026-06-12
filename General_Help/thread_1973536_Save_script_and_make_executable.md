---
title: "Save script and make executable"
date: 2012-05-04
forum: General Help
---

### Post by kjbox on 2012-05-04
I need to add a workaround to get suspend working correctly with my ASUS Zenbook UX31.

I found the script to be added on the AsusZenbook-Community site. The instructions say:

**Save the following script as /etc/pm/sleep.d/20_zenbook (and make it executable):** 

I am new to linux and not sure of the commands to put into the terminal to save the script into the correct folder nor how to make it executable.

Any help greatly appreciated.

---

### Post by jerome1232 on 2012-05-04
There are 2 ways to do this, the gui way, and the terminal way.

gui way is to press alt+f2, type 'gksu nautilus' with no quotes, browse to your file, and copy it to /etc/pm/sleep.d/ make sure it's named 20_zenbook, right click it, click the permissions tab, check allow executing as a program. Close nautilus.


the cli way, first copy it your desktop (so that I know where it's at), and name it 20_zenbook.

```
sudo mv ~/Desktop/20_zenbook /etc/pm/sleep.d/
chmod a+x /etc/pm/sleep.d/20_zenbook
```

---

### Post by kjbox on 2012-05-05
Many thanks, I can now suspend myself happily!!

---

