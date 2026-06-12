---
title: "Why is &quot;Install RELEASE&quot; in System&gt;Release"
date: 2010-10-29
forum: General Help
---

### Post by Jetso on 2010-10-29
Today I was going to Synaptic when I realised that there is a new entry in my System>Administration. It is called "Install RELEASE" and when I click on it, it tries to go through the steps like I was doing a fresh install of Ubuntu... What does this mean, and how do I remove it/ do whatever I need to make it go away?

---

### Post by Jetso on 2010-11-20
Bump

---

### Post by dcstar on 2010-11-20
> **Jetso said:**
> Today I was going to Synaptic when I realised that there is a new entry in my System>Administration. It is called "Install RELEASE" and when I click on it, it tries to go through the steps like I was doing a fresh install of Ubuntu... What does this mean, and how do I remove it/ do whatever I need to make it go away?

AFAIK that should only be there on Live CD/USB boots.

---

### Post by Jetso on 2010-11-20
Well it's here... Any suggestions, it's not a LiveCD boot or anything, just a true Ubuntu 10.10/Vista dual boot.

---

### Post by PRC09 on 2010-11-21
You can right click System in the task bar, select edit menus, left pane scroll down and select  administration, then in the right pane un-check Install Release....,
I have seen this on some installs and not on others but I have been playing with 10.04,10.10 an 11.04 so not sure which ones it was in.....

---

### Post by Jetso on 2010-11-21
Well that worked. It's fine just as long that there is nothing wrong with system.

---

### Post by lightpriest on 2011-05-01
This is a file that is included by the package "Ubiquity" - The Ubuntu installer.
Once this installer finishes its job, you don't need it on your machine. You can safely remove it and it will remove this icon.

This action should be taken by the upgrade process' cleanup.

As a side note, you don't really have to remove it as it doesn't really do anything after it has completed its task (installing ubuntu).

---

