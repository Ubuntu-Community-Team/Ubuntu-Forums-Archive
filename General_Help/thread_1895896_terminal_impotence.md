---
title: "terminal impotence"
date: 2011-12-15
forum: General Help
---

### Post by China Helene Catron on 2011-12-15
Okay, 
             So, I'm using the terminal in Ubuntu... I&#7743; trying to change the permissions of an application I downloaded. I enter the sudo chmod + myfilesname.bin .....and then, hit enter. As expected, I am asked for my password. Only, the only input that is accepted, is enter; The reply is, this is not China&#347; password, etc, etc. What is the deal, here?

---

### Post by oldos2er on 2011-12-15
If the bin file is in your home folder, there's no need to use "sudo".

---

### Post by oldfred on 2011-12-15
In terminal, it does not show characters typed when asking for password for security reasons. You just have to blind type password & hit enter, then it should work. (Hope your password is not real long:))

---

### Post by idoitprone on 2011-12-15
```
 chmod u+x myfilesname.bin
```

this is the command to add user execute permission to the file

All the info you need is in the wikipedia
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

