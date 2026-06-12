---
title: "Ubuntu 11.10 is not remembering anything."
date: 2012-04-01
forum: General Help
---

### Post by MamboKing on 2012-04-01
I have encountered a most unusual bug with Ubuntu 11.10. I did a fresh install the other day and loaded up all of my favorite applications. Everything in Ubuntu was going great until I decided to log out and log back in. Firefox cannot find its profile and can only be opened in a terminal with sudo firefox. Thunderbird cannot remember my email information and opens up prompting me to enter everything in all over again. Pidgin isn't working properly anymore and refuses to connect or acknowledge anything IRC chat related. Tomboy notes is working, but is not listing the new notes that I create, I have to search all notes to get it to list what I have written. Keepass2 is not remembering where my key information is located and I have to physically tell it where it is. I am sure there are more problems like this regarding applications not being able to access essential information, but there are way too many apps installed to for me to want to log all the memory absence issues I am experiencing. 

This is definitely not my first time wiping my hard drive and loading up Ubuntu again on my computer, but it is the first time in awhile that I chose to encrypt it when I was given the option when installing the operating system. Overall I am extraordinarily confused, very frustrated, and I don't even know where to begin solving these problems of amnesia with Ubuntu 11.10. 

Anyone....please.....help!!!!!!!!!!!!!!

---

### Post by electrojustin on 2012-04-01
Maybe ubuntu isn't decrypting properly? That would make sense seeing as you wouldnt be able to read anything on the partition if that were to happen. Sort of odd you can't open firefox...do you have a seperate home partition?

---

### Post by 2F4U on 2012-04-01
Is your /home partition mounted read-only instead of read-write?

---

### Post by MamboKing on 2012-04-01
I switched it from access files to create and delete files permissions for the home folder. I am not sure what it did, but now firefox loads up with a different kind of error message. 

"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

I have no clue what I just did or what the permissions should be set to. I do not believe I have a separate home partition.

---

### Post by electrojustin on 2012-04-02
Maybe try: 
```
 
chmod -R +rwx ~

```

---

