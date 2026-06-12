---
title: "Acroread installation problem"
date: 2011-09-30
forum: General Help
---

### Post by avrsarma on 2011-09-30
After installing adobe acroread with
apt-get install acroread
the acroead got installed:
But when I invoked acroread command in the commandline, the following error message appears on the screen. KIndly let me know how to debug this problem

Message:


Acroread was unable to create the directory .adobe in your home directory.
There may be a permission problem with the parent directory.
Acroread was unable to create the directory /home/avrs/.adobe in your home directory.
There may be a permission problem with the parent directory

---

### Post by dino99 on 2011-09-30
sudo chown user:user /home/avrs/*

where user is yours (avrs i suppose)

---

### Post by avrsarma on 2011-10-02
The problem still persits:

It is giving the following message:
Internal error:


Could not launch Adobe Reader 9.4.2. Please make sure it exists in PATH variable in the environment. If the problem persists, please reinstall the application.

---

### Post by Lars Noodén on 2011-10-02
Acrobat Reader is rather insecure and, as you are finding out, prone to a lot of other problems.  

Try Evince or Okular instead.  If you have tried them, what was missing?

---

### Post by philinux on 2011-10-02
> **avrsarma said:**
> The problem still persits:

It is giving the following message:
Internal error:


Could not launch Adobe Reader 9.4.2. Please make sure it exists in PATH variable in the environment. If the problem persists, please reinstall the application.

I've never had any trouble launching this from the menus. Apps>Office is where it goes. And I've had zero problems with it.

---

