---
title: "Red triangle icon - update information out of date"
date: 2011-03-24
forum: General Help
---

### Post by culfunius on 2011-03-24
I've been plagued with this problem now for months. Updates complete normally, but within an hour of booting my Ubuntu installation, a small, odious, snivelling icon appears in my system tray. It's a red triangle around an exclamation mark, and if I hover over it, it informs me:

> The update information is outdated. The may be caused by... etc etc...

I've followed it's advice I don't now how many times (to 'check for updates and see if any of the repositories fail). They never do, and it never goes away. 

Why is it there? Why does it stalk and pester me? How can I get rid of it?

---

### Post by Script Warlock on 2011-03-24
if you can post some of the errors..

---

### Post by mikewhatever on 2011-03-24
You may have a third party repository that returns errors. Can you post the output of the following command:
```
sudo apt-get update
```

---

### Post by mcduck on 2011-03-24
> **culfunius said:**
> I've been plagued with this problem now for months. Updates complete normally, but within an hour of booting my Ubuntu installation, a small, odious, snivelling icon appears in my system tray. It's a red triangle around an exclamation mark, and if I hover over it, it informs me:



I've followed it's advice I don't now how many times (to 'check for updates and see if any of the repositories fail). They never do, and it never goes away. 

Why is it there? Why does it stalk and pester me? How can I get rid of it?

Could you run the following commands in a terminal and post the output here? That should give as a bit more clear information about what's actually going on with your updates...
```

sudo apt-get update
sudo apt-get upgrade
```

---

