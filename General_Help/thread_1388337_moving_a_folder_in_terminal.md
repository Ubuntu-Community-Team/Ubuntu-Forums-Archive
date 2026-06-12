---
title: "moving a folder in terminal"
date: 2010-01-23
forum: General Help
---

### Post by Keith Fox on 2010-01-23
I had a folder named "Rage Against the Machine" in my Home directory which contained a bunch of music files. I opened my Terminal window and planned on moving it to a folder named "Downloads" inside my home folder, so I used this command:
```
sudo mv "Rage Against The Machine" /Downloads
```Now I can't actually find the folder inside Downloads, which I think it should be. so I even tried running this to find it:
```
locate "Rage Against The Machine"
```and it couldn't find it either.

Where did it go?? :confused:

The folder size was approximately 837.6 MB in size total.

---

### Post by bogdan.veringioiu on 2010-01-23
Looking at your command, I see that you moved "Rage Against The Machine" in the / folder, and renamed as Downloads.

What you probably wanted to do was:
> mv "Rage Against The Machine" ~/Downloads

I don't understand why you wanted to use sudo....
Try to check:
> ls -l /Downloads
to see if there is your music.

Cheers.
Bogdan

---

### Post by Keith Fox on 2010-01-23
Ah thank you so much. It did rename the folder and threw it in root directory. So I used your command to rename it back and put it where I wanted, so thank you! The problem was I forgot the tilde (~) before the location to put it.
I had to use sudo because it said something about the permissions and didn't do it, so sudo fixed that.

---

### Post by fjf314 on 2010-01-23
You got a permission denied error because you were trying to create a new folder on root, even if you didn't mean to. Thus you were forced to use sudo.

When working within your home directory, sudo won't be required.

---

### Post by Keith Fox on 2010-01-23
> **fjf314 said:**
> You got a permission denied error because you were trying to create a new folder on root, even if you didn't mean to. Thus you were forced to use sudo.

When working within your home directory, sudo won't be required.

Good to know! Thank you all! :)

---

