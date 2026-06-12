---
title: "Administriation trouble"
date: 2006-04-15
forum: General Help
---

### Post by JoeeT on 2006-04-15
I want to perform some administration on Ubuntu.

I log in on my account, the only account, which I believe is set up to be admin when Ubuntu installed.

I got to system -> Administration

Then, when I select anything from this menu, I am asked for my password, so I input my password.
However, once the password dialog closes, nothing happens. So I try again. System -> Administration, then when I click on anything, nothing happens at all.

Is something wrong with Ubuntu here or is there soething wrong with the password I input? It is the same password I use for logging in.
Can anybody shed some light on this matter please? It would be much appreciated.

---

### Post by Ramses de Norre on 2006-04-15
Does sudo -v work in terminal when you put in your user password?

---

### Post by JoeeT on 2006-04-15
I just tried that.

I get an error "Sorry, user joee may not run sudo on localhost"

---

### Post by Ramses de Norre on 2006-04-15
You'll need to boot into recovery mode because it seems there is something wrong with /etc/sudoers and only root can read/write that file.
sudo nano /etc/sudoers or sudo vi /etc/sudoers
If your user is member of the admin group you should add a line ```
%admin  ALL=(ALL) ALL

```
If not it might be easier to add a line ```
user_name    ALL=(ALL) ALL

```

---

### Post by JoeeT on 2006-04-15
Sorry, I didnt understand that last reply... I am completely new to using Ubuntu or any form of Linux at all.

Can you please give me step by step instruction of what I need to do?

EDIT: sorrry, I missed a line there in your reply. Give me a sec. I'll try that now.

---

### Post by JoeeT on 2006-04-15
What do I do then? I input the extra line... but now what? Like I say, I'm completely new to this!

---

