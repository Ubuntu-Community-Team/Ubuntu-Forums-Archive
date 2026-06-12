---
title: "what is the user-name and password for the super user on the ubuntu Live cd?"
date: 2012-01-16
forum: General Help
---

### Post by Adam Shar on 2012-01-16
Hi everyone.

I am using  ubuntu from a live CD and I am trying to install some software. For it to be installed, I need to log into the terminal as a super user but I dont know its username and password

Can anyone tell me what is the user-name and password for the super user on the ubuntu Live cd?

Thank you

---

### Post by nothingspecial on 2012-01-16
I don't think there is a password. Just prefix the commands with sudo and leave the password blank.

---

### Post by imagecko on 2012-01-16
I believe the username is "ubuntu" and the password is just blank.

---

### Post by lisati on 2012-01-16
Take a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by coffeecat on 2012-01-16
Hi, the username and password are "ubuntu" and blank (that is, nothing) respectively. However, you do not need the password if you need to invoke sudo privileges in the live session terminal. Just use "sudo apt-get" as normal and it will work without any password prompt.

Also - take care when using sudo in the terminal in the live session. Since you don't have to enter a password there is the potential to unintentionally do real damage if you have - say - an internal hard drive mounted.

---

