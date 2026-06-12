---
title: "Can't use Root Password?"
date: 2010-07-13
forum: General Help
---

### Post by Cam! on 2010-07-13
I'm installing Doom 3. It tell me to enter my password to run as root, or press enter to install as a user.

I keep typing in my password, but I don't think the app is recognizing it. I enter the PW, and press "Enter". Then, it says I don't have the permission to create a new folder in usr/local/games.

---

### Post by snowpine on 2010-07-13
Hi, this is a pretty common misunderstanding about Ubuntu. :) The root account is locked, and we use "sudo" instead (with the regular user password; there is no root password). For example:

```
sudo apt-get install doom3
```

More info here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

As to your specific question, I am not familiar with the Doom 3 install process, but if you want to copy & paste the instructions here, I'm sure someone can translate them to Ubuntu-talk for you. :)

(edit) see Jan Dahl's post below!

---

### Post by Jan Dahl on 2010-07-13
There's actually a help article on that:

[https://help.ubuntu.com/community/Doom3](https://help.ubuntu.com/community/Doom3)

Note that it assumes you have the game CD.

---

