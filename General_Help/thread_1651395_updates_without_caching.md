---
title: "updates without caching"
date: 2010-12-23
forum: General Help
---

### Post by sandsjh on 2010-12-23
Greetings to all. 

I want to create a USB key that installs updates, but does not use the USB for browser cache, etc.

I know casper-rw allows a user to save files and preferences but, again, I do not want to use the USB for browser caching, nautilus caching, etc.

Thanks in advance for you assistance.

---

### Post by sandsjh on 2011-08-04
?

---

### Post by sandsjh on 2011-08-29
any thoughts?

---

### Post by dcstar on 2011-08-30
> **sandsjh said:**
> any thoughts?

Go into the Firefox preferences and disable caching, there are hundreds of HOWTOs easily searchable on this.

---

### Post by sandsjh on 2013-01-21
Eighteen months later, the answer to this question is to copy the files in /var/cache/apt/updates to a folder on your USB. Once you boot, copy them back to the mentioned folder. Run 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get autoclean
and then copy to a new folder on USB. Redo as necessary, but I've found just copying the adobe and firefox updates does what i need.

---

### Post by sffvba[e0rt on 2013-01-21
> **sandsjh said:**
> Eighteen months later, the answer to this question is to copy the files in /var/cache/apt/updates to a folder on your USB. Once you boot, copy them back to the mentioned folder. Run 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get autoclean
and then copy to a new folder on USB. Redo as necessary, but I've found just copying the adobe and firefox updates does what i need.

Awesome, glad a solution was found.

**Closed.**


404

---

