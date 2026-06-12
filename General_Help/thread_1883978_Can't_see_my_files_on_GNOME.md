---
title: "Can't see my files on GNOME"
date: 2011-11-20
forum: General Help
---

### Post by Inphi on 2011-11-20
I am running a dual-booted Ubuntu 10.04 (w/ Win7). Whenever I create a file on the terminal to a folder like ~/usr/Desktop I can't see the file on GNOME (the file browser). But, the file comes up when I run ```
ls
```
NOOOOO, I do NOT have the Show Hidden Files button unticked, nor is the folder set up in any way to hide files and folders.
So why can't I see my files on the file browser?

---

### Post by fdrake on 2011-11-20
> **Inphi said:**
> I am running a dual-booted Ubuntu 10.04 (w/ Win7). Whenever I create a file on the terminal to a folder like ~/usr/Desktop I can't see the file on GNOME (the file browser). But, the file comes up when I run ```
ls
```
NOOOOO, I do NOT have the Show Hidden Files button unticked, nor is the folder set up in any way to hide files and folders.
So why can't I see my files on the file browser?
are you sure you are using the same user when creating a file in the terminal and when browsing?
also "~/usr/Desktop" is not really correct , maybe yo meant ~/Desktop or /home/usr/Desktop. check you path directory!
creat a file with the terminal then in the same terminal write
```

nautilus . 

```and see if you see the files

---

### Post by Inphi on 2011-11-20
Of course I have the correct path. 
But I recently discovered that the files showed up on Nautilus, but not on GNOME. I'm still stumped.
EDIT: The files come up on Nautilus only when sudo'd.

---

### Post by fdrake on 2011-11-20
> **Inphi said:**
> Of course I have the correct path. 
But I recently discovered that the files showed up on Nautilus, but not on GNOME. I'm still stumped.
EDIT: The files come up on Nautilus only when sudo'd.
the fact that you need sudo to see it in nautilus means makes me think to a permission issue. can you run gnome with sudo or even better gksudo? I do not use gnome file browser so i do not know the name of the program(you can check with apropos or with ps while its running)

---

### Post by Inphi on 2011-11-20
Yeah, it was a permission issue. 
It's solved kinda. 
But, on GNOME, a "redirect" mini-icon appears on top of my file icons. But they are not there on nautilus. It's not gonna prevent me from working. But is there a way to remove it?

---

### Post by fdrake on 2011-11-20
> **Inphi said:**
> Yeah, it was a permission issue. 
It's solved kinda. 
But, on GNOME, a "redirect" mini-icon appears on top of my file icons. But they are not there on nautilus. It's not gonna prevent me from working. But is there a way to remove it?

i am not sure about it since i have never used it I hope some one else knows how to remove it. I think it is a way to describe the file (maybe it's a link or a location-launcher script). have you tried with right click the icon > properties> emblems? just guessing here...

---

