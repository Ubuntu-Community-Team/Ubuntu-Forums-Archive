---
title: "Take ownership of previous install's files"
date: 2012-06-21
forum: General Help
---

### Post by Agent_Riot on 2012-06-21
Hey. Simple question for a terminal expert. I recently upgraded my system and copied over all my old documents. To copy them however, I needed to open up the source and destination windows as Root/Admin. My question is this. Is there a command I can use to make all the folder/subfolders of my home folder(pictures, music, docs, etc...) become owned by my new user? I really hate getting permission errors, and I couldn't even get my "pictures" to show up as desktop bg choices due to ownership. Gah!
 
To state the question in layman's terms I want all the stuff in my home folder to be considered as if my current user created it. I know about single files, but is there a command (probably with wilcards *'s) that can do this?
 
Thanks,

---

### Post by dino99 on 2012-06-21
use chown command when you are logged as "user"

sudo chown youruser:youruser ~/youruser/*

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Agent_Riot on 2012-06-21
> **SeijiSensei said:**
> That's a bit complex. How about this?
 
```

sudo su -
[enter password]
cd /home
for U in *
do
chown -R $U.$U $U
done
exit

```
 
The first line lets you run the remaining commands as root without dealing with sudo each time.
 
 
This sounds like what I need. Edit: I ran the command last night and it didn't work. It listed  off every folder in my home (pictures, videos, music, etc...) and said in layman's terms that it couldn't touch those folders. Now my friend who's taking certs test from the Linux Pro Institute tells me that the third $U of the chown line isn't needed, and said I could eliminate the first sudo su and just pust sudo infront of the chown. I tried that, and got the same error. If the above code from SeijiSensei is right, and i ran it from my username's home folder, did I do something else wrong?

---

