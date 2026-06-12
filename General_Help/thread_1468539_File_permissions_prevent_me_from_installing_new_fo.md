---
title: "File permissions prevent me from installing new fonts"
date: 2010-05-01
forum: General Help
---

### Post by jrela2000 on 2010-05-01
A tutorial says in order to add new fonts, take you font file and put them into a newly created directory inside your home folder and name it ".fonts". Reset and they will be ready to use.

I'm not able to do this from Nautilus View because of the error that I do not have permission to do so.

I have made the dir in terminal using sudo mkdir

I need help moving the actual fonts from my desktop into the actual folder. I don't know how to do it.

Or if there is another way I should be doing it.

---

### Post by prshah on 2010-05-01
> **jrela2000 said:**
> I have made the dir in terminal using sudo mkdir

You should have made it with just mkdir, no need for the sudo. Easy fix:```
sudo rm -rf /home/username/.fonts
mkdir ~/.fonts
``` 
More complex, but safer fix:```
sudo chown username:username /home/username/.fonts
chmod 755 ~/.fonts
```

(Replace "username" with your actual username)

Please be careful when using the rm -rf command; a mistype can possibly delete everything.

---

### Post by jrela2000 on 2010-05-01
> **prshah said:**
> You should have made it with just mkdir, no need for the sudo. Easy fix:```
sudo rm -rf /home/username/.fonts
mkdir ~/.fonts
``` 
More complex, but safer fix:```
sudo chown username:username /home/username/.fonts
chmod 755 ~/.fonts
```

(Replace "username" with your actual username)

Please be careful when using the rm -rf command; a mistype can possibly delete everything.


Thanks

---

