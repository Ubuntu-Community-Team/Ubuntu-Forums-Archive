---
title: "Nautilus problems - simple commands"
date: 2009-12-10
forum: General Help
---

### Post by MiCK.ca on 2009-12-10
I have been experiencing various problems with Nautilus. I will try to rename a folder and i get a message saying that 'this folder can't be rename in it's current location' and then Nautilus will move it to the trash! I workaround this by creating a folder...naming it what i want and move files into the 'new' folder. 

also. if i do ANY photo editing, Nautilus will not update the 'thumbnail' or even display the file. if i move the folder to a different location (an external drive) then the images return and all good. 

any ideas?

---

### Post by Chesamo on 2009-12-10
It sounds like a permission problem. If this is happening in your Home folder (ie. /home/username), then you might have a problem. In the Terminal, type "sudo nautilus /home" (sans quotes), right-click on your Home Filer, and hit Properties. In the Permissions tab, change yourself back to being the Owner with Read-Write privelages. Make sure you have it apply to everything inside the folder as well.

---

### Post by MiCK.ca on 2009-12-10
thanks for that. i have done that. My thought was that, i keep a separate /home directory. reinstalls don't affect it...(i thought) apparently it does. i have had to change this in past. 

however, the arbitrary moving files to the trash is spooky! I have all permissions. Basically the same as root. 

Now it's even doing it on my external drive...so i think this is a nautilus thing...correct?

---

### Post by MiCK.ca on 2009-12-10
UPDATE:

the error says: "there is no (folder or file name) in this folder. Perhaps it was just moved or deleted" 

yeah..Nautilus deleted it!!

---

### Post by blur xc on 2009-12-10
> **Chesamo said:**
> It sounds like a permission problem. If this is happening in your Home folder (ie. /home/username), then you might have a problem. In the Terminal, type "sudo nautilus /home" (sans quotes), right-click on your Home Filer, and hit Properties. In the Permissions tab, change yourself back to being the Owner with Read-Write privelages. Make sure you have it apply to everything inside the folder as well.


gksu nautilus /home/username


BM

---

### Post by MiCK.ca on 2009-12-10
Ok...think i solved it. somehow under startup programs the service called "users folder update" was turned off! I turned it on, rebooted and so far so good...

I won't have to put a shortcut to the trash can on my desktop to access my files now...(lol)...what others services (being turned off) could perhaps cause this?

---

### Post by MiCK.ca on 2009-12-11
{update} Nope...still doing it...rename a folder and it moves it to the trash! What is causing this?

---

