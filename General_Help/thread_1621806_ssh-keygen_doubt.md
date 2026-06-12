---
title: "ssh-keygen doubt"
date: 2010-11-14
forum: General Help
---

### Post by mataug on 2010-11-14
Hi,

I was trying to setup automatic ssh login to a machine & have been able to do so using the commands provided here-
[http://ubuntu-tutorials.com/2007/02/05/unattended-ssh-login-public-key-ssh-authorization-ssh-automatic-login/](http://ubuntu-tutorials.com/2007/02/05/unattended-ssh-login-public-key-ssh-authorization-ssh-automatic-login/)

My doubt is this:
If somebody were to get hold of the contents of the file id_dsa.pub created in that link, would they be able to login to the machine in a similar fashion ?

One of the things that I observed while reading id_dsa.pub is that it has got some characters to start with & then ends with user_name@machine_name.

Thanks.

---

### Post by spiky001 on 2010-11-14
[LEFT]take a look here [[COLOR=#980101]**bodhi.zazen **[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")has a post in secruity forum [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)  
[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")[/LEFT]

---

### Post by mataug on 2010-11-14
thanks for the link spiky... very helpful!

---

### Post by spiky001 on 2010-11-14
if it's what you need all well and good

---

### Post by mataug on 2010-11-14
it gives me a better idea of how things work with private/public keys

Having posted a new thread, I now realize that I could have checked it myself by borrowing a machine from somebody, pasting the file in their .ssh folder & seeing if it works or not

---

