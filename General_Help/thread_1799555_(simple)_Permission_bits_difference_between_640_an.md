---
title: "(simple) Permission bits difference between 640 and 600"
date: 2011-07-07
forum: General Help
---

### Post by Matt Pellegrini on 2011-07-07
If i am the owner of all my files and am looking to change recursively the permissions of my home folder to something more secure than 644 (the default). What is the difference between 640 and 600. I know that the middle digit refers to the group, but what exactly will this mean for me? It seems i can r/w no problem without root password regardless of whether it's 640 or 600.

Thanks in advance for any help

Matt

---

### Post by JC Cheloven on 2011-07-07
If you're the only user of your computer (as I assume), it should make no practical difference, as there aren't other users that could belong to your group. Even if you make another user but don't add it to the group of your current user, there would be no difference in changing that second figure.

Hope to correctly undertand your question.

---

### Post by Habitual on 2011-07-07
644 is secure, else it wouldn't be the default. ;)
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by Matt Pellegrini on 2011-07-08
644 is really not that secure with 'others' being able to read any of my documents, I'd hardly call that secure.

My question was really, what's the difference between making the files only accessible by me compared to me and my group.

I suspect the answer is that there is no difference if i am the only member in my group as Cheloven hinted at.

If this is the case, how can i see who is in my group and how are people added to the group? Will i always be aware if someone is added to the group? If not then surely 600 is more secure.

Thanks
Matt

---

### Post by Yellow Pasque on 2011-07-08
Is your /home a separate partition and is that partition encrypted?

---

### Post by Matt Pellegrini on 2011-07-08
It is on a separate partition to windows. I don't know if it's encrypted, how would i find out?

---

### Post by Morbius1 on 2011-07-08
> 644 is really not that secure with 'others' being able to read any of my documents, I'd hardly call that secure.What you said is true only if "others" can get to your file. Your home directory has ownership = you, group = you, and permissions of 755. The last "5" means anyone can open your home directory and access it's contents. But you could make your home directory 750. The last "0" will prevent anyone except "you" and anyone in the "you" group to gain access.

---

### Post by Matt Pellegrini on 2011-07-08
> **Morbius1 said:**
> What you said is true only if "others" can get to your file. Your home directory has ownership = you, group = you, and permissions of 755. The last "5" means anyone can open your home directory and access it's contents. But you could make your home directory 750. The last "0" will prevent anyone except "you" and anyone in the "you" group to gain access.


Exactly, so my question is why would i change to 750 rather than go all the way to 700 for directories if i am the only member of my group? (640 compared to 600 for files)

Thanks
Matt

---

### Post by Morbius1 on 2011-07-08
I've learned from embarrassing posts that I have made never to make absolute statements so let me give you the safest answer I can think of:

Look at /etc/group and find your group name. If anyone or anything other than you is listed as a member then leave it at 750. If not then make it 700.

---

### Post by Matt Pellegrini on 2011-07-08
Thanks, that was the sort of answer i was after.

Just in case someone reads the whole thread. I should just summarise here:

to see who is in your group see /etc/groups and find your group name

if you are the only member in your group then there should be no difference between 640 and 600 as the group permissions are overridden by the owner permissions, this is assuming you own all your files and won't change your group at a later date.

If you aren't the only member in your group 640 will allow others in the group to read but not write or execute your files.
Whereas 600 will only allow you to read and write your files.

Directories should be put as 750 or 700 depending on the same reasoning as above. This is because, without the execute bit set you won't be able to access the directory.

I hope this is all correct, but it has all been learned recently through trial and error so if your not sure don't take this as solid fact. Open to corrections. Thanks all for your help with special thanks to Morbius1

I'll mark as solved as i think we've made significant ground towards understanding.

---

