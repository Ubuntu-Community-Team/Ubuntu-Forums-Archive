---
title: "I accidentally logged out during an update"
date: 2011-07-01
forum: General Help
---

### Post by linuxuser12345 on 2011-07-01
I recently logged out by accident during a system update. I am the system administrator.

Is there a way I can check my system for errors that may have been occurred, and is there a way I can fix these errors?

---

### Post by linuxuser12345 on 2011-07-01
Can anyone help me?
Sorry for posting so many stinkin' threads! lol

---

### Post by adam814 on 2011-07-01
I'd just try running the update again first.  I've had laptop batteries run out during updates and not cause a problem (especially if still downloading packages).  If it complains about broken dependencies I'd give this one a try:

```
sudo dpkg --configure -a
```

If that doesn't do the trick post the output from apt-get.

---

### Post by linuxuser12345 on 2011-07-01
I think it seems fine! :)
How do I do the apt-get process? (Sorry, I am really new to the terminal!)

---

### Post by nitstorm on 2011-07-01
> How do I do the apt-get process? (Sorry, I am really new to the terminal!)
You can resume your updates from the update manager itself. 

You can also go to the terminal and type this in

```
sudo apt-get update  // This is equivalent to clicking the Check Button in Update Manager

sudo apt-get upgrade       //This is equivalent to clicking Install Updates in Update Manager

sudo apt-get install package-name   //replacing the package-name with whatever package you want to install, example - gedit would be sudo apt-get install gedit

sudo apt-get remove package-name   //removes the packages (uninstalls)


```

---

### Post by linuxuser12345 on 2011-07-01
Oh, thank you! :D

---

