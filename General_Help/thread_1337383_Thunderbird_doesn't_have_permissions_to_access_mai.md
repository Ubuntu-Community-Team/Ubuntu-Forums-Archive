---
title: "Thunderbird doesn't have permissions to access mail folder?"
date: 2009-11-25
forum: General Help
---

### Post by AxAeo on 2009-11-25
So I managed to transfer my Thunderbird profile from my Windows box to my Ubuntu one, and set everything up. Worked beautifully the first time I opened it last night.

Today I turned on Thunderbird, and my inbox was inaccessible for all my accounts, no folders, nothing. I did some investigation, and found that if I ran Thunderbird as root, it ran perfectly again. Basically, Thunderbird does not have permissions to access the mail folder in my profile. (It explicitly told me this as well when I tried to change the local folder directory).

I also found I can't even cd into that folder through the terminal unless I am root. I find this odd, as I'm pretty sure I have all permissions set up for it (chmod 022).

If anybody could help me sort this out I would be quite grateful!

---

### Post by ricardo.gloe on 2009-11-25
If you have to access the folder and thunderbird through root, then the files/folder are most likely set to root ownership. 

If you change the folder/files to your user, they should work.  

If I'm not mistaken 

```
sudo chown -R yourusername:username /folder
```

"R" option changes all files within the folder

the username repeat separated by ":" changes the user and group

---

### Post by cariboo on 2009-11-25
My ~/.mozilla-thunderbird directory has permissions of 755. I would suggests you open a terminal and type:

```
chmod -R 755 ~/.mozilla-thunderbird
```

to set the proper permissions.

---

### Post by AxAeo on 2009-11-25
> **cariboo907 said:**
> My ~/.mozilla-thunderbird directory has permissions of 755. I would suggests you open a terminal and type:

```
chmod -R 755 ~/.mozilla-thunderbird
```

to set the proper permissions.

This did it. Thanks so much!

---

