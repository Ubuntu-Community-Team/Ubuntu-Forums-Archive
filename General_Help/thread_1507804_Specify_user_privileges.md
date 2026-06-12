---
title: "Specify user privileges"
date: 2010-06-12
forum: General Help
---

### Post by Felystax on 2010-06-12
Hello, 

I have a small problem on ubuntu 10.04, of which i know it can be solved. However, i'm not sure how to. The problem is; I need one user to be able to install updates, but not give it any other privileges. I have been messing around with the "sudoers" file in /etc a bit, and thought i needed to use the "NOPASSWD" But i'm not sure what to do after that. If someone could help me it would be greatly appreciated.

Thanks in advance

---

### Post by doas777 on 2010-06-12
according to this:
[https://wiki.ubuntu.com/Security/Privileges](https://wiki.ubuntu.com/Security/Privileges)

you should be a member of the admin group to install updates, but it appears that that group grants a great deal of other privileges as well. I'm sure there must be a way to get more granular control, but I'm not sure what it is. you can remove some admin priv from the users/groups applet, by selecting a user and clicking Advanced Settings, but "Administer the System" is still pretty broadly defined. 

i personally would probably configure the machine to install security updates automatically, and periodically log in to get the software updates, but if you want to do the learning, I'm sure theres a way.

edit:
it looks like you may be able to get what you want, by configuring sudo to allow the user to run a specific set of apps that you define, and blocking the rest, but it doesn't seem to be a trivial task. 
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Felystax on 2010-06-12
Thank you very much, but the problem with giving administrator privileges to that specific user means that it is able to run the terminal and thus install programs on there. And this is what want to prevent :)

Edit: Thank you, this may be what I was looking for!

---

### Post by doas777 on 2010-06-12
thats the crux of it. in order to upgrade software, the system has to be able to do (in your name) the task assigned. since updating and installing software both require write access to systemspace, granting one, is granting the other. additionally the app used to perform updates is the same as the one used to install software (apt-get or aptitude) it would seem pretty hard to divorce teh two. 

but then again, I have no specific experience with this issue, so it may be quite possible.

---

### Post by Felystax on 2010-06-12
Does anybody else have any ideas on how to solve this? It's still a pretty big issue to me :) 

Thanks in advance! ):P

---

