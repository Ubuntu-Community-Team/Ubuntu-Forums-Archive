---
title: "Help icon gone!"
date: 2006-05-15
forum: General Help
---

### Post by Morientes on 2006-05-15
My help icon has gone from the panel at the top of the screen! I have no idea what I have done to make it disapear! Also when I select help on the other screens it says "cannot display help document".
What has gone wrong?

---

### Post by aysiu on 2006-05-15
Try pasting this into a terminal: ```
sudo apt-get update
sudo apt-get install ubuntu-docs
```

---

### Post by Morientes on 2006-05-15
Yeah thanks, I figured out it was because I had uninstalled firefox and it had taken the yelp application with it...

---

### Post by TTN on 2006-05-20
Hello,
     I just replaced Firefox with Opera today and found the same problem with the Yelp.
I tried to reinstall Yelp but Synaptic said I had to install Firefox also.
I chose not to do the reinstall.

I cut and pasted the lines into terminal.
There were no errors but there was no change to the help icon.

Than you

---

### Post by Vich on 2006-11-04
You can easily re-create it via add to panel -> custom application
and enter the following data:
Name: Help
Command: yelp
Comment: Get help with Ubuntu
Icon: /usr/share/icons/Human/48x48/apps/gnome_help.png

My help icon recently disappeared simply when dragging icons around. I'm using edgy and have been able to recreate this glitch a couple of times. The icon being dragged becomes an orange trapezium with a black ? in it and no longer points to anything. Since I didn't do any installing/uninstalling to break my help icon, I rebooted off the cd and copied the params then did the above.

---

