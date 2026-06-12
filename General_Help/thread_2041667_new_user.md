---
title: "new user"
date: 2012-08-13
forum: General Help
---

### Post by marjenni on 2012-08-13
Hi,
   I have created a new user, but when I login as that user, the prompt is '$' and tab complete does not work.
 
when I login as root, the prompt ends with '#' and tab complete works. How do I fix this for the new user?
 
many thanks
 
Mark

---

### Post by Savio2010 on 2012-08-13
Please give more info about your system. specially which version are you using. 11.04 or 11.10 or 12.04. Server edition or desktop edition. is it kubuntu or some other distro. etc.

The root user has a # prompt .............Ok
The normal user has a $ prompt ............OK

To my knowledge I hit tab twice for completion.

---

### Post by Nardon on 2012-08-13
Think that's because of the environment that the new user is using. You got two by default: /bin/sh which is a very simple terminal (note you wont see your current directory and stuff in the prompt) and /bin/bash which is more advanced and supports things like tab completion. the first one is set as default when you create a new user with the useradd command.

You can change that this way, first open /etc/passwd as root in your favorite text editor.

```
sudo nano /etc/passwd
```

You will see a whole list with user accounts. Locate the newly created user and change ```
<other stuff>:/home/bart:/bin/sh
``` to ```
<other stuff>:/home/bart:/bin/bash
```

---

### Post by marjenni on 2012-08-13
Yup that did it!
 
Many thanks
 
Mark

---

### Post by Nardon on 2012-08-13
No problem! Glad it worked! :)

I don't know how you created the user, but if you want to avoid this in the future, create a user with adduser instead of useradd.. :P I know it's confusing, but the other one sets the environment to bash by default.

---

