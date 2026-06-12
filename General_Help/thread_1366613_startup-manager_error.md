---
title: "startup-manager error"
date: 2009-12-28
forum: General Help
---

### Post by warlock85 on 2009-12-28
Hello, I have been trying to use startup-manager to change my ubuntu 9.10 Usplash and everytime i boot instead of the Usplash image I wanted it has this weird thing with colors all around it. Its hard to explain what it looks like. So my questions is how do I get it to use the usplash theme I wanted? 

if it helps everytime i open up startup-manager is has an error like this:
An error occurred while loading or saving configuration information for startupmanager. Some of your configuration settings may not work properly.

---

### Post by oldos2er on 2009-12-28
If you're using grub2, not all the options in startupmanager have been upgraded to work with it yet.

---

### Post by warlock85 on 2009-12-29
How do I find out which version of grub I am using?
And how do I change the Usplash if I can't do it with startup-manager?

---

### Post by dato1989 on 2009-12-29
> **warlock85 said:**
> How do I find out which version of grub I am using?
And how do I change the Usplash if I can't do it with startup-manager?
you can find version of your grub by open the terminal and type this

grub-install -v
sorry about second question i dont know  how is it exactly i will  try to find it for you

---

### Post by oldos2er on 2009-12-29
> **warlock85 said:**
> And how do I change the Usplash if I can't do it with startup-manager?

[https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming)

---

