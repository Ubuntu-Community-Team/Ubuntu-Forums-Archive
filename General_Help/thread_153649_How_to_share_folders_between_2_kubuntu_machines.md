---
title: "How to share folders between 2 kubuntu machines"
date: 2006-04-01
forum: General Help
---

### Post by melonipoika on 2006-04-01
Hi all,

I have 2 kubuntu machines connected using a linksys switch, and I would like to shar folders between then. If I go to System settings -> Sharing -> share files and enter in the administrator mode, still I can't modify anything, it is in light gray. Does anyone know how to change this values? Do I need to install any extra packages? I couldn't find anything about this in the internet, just about samba, what I don't belive is my case.

Thanks for the help.

PS. I am using dapper, but I guess it is a general kubuntu topic.

---

### Post by sadjack on 2006-04-01
I had the same problem, in my case I found it was because the opened window was small, when I enlarged it to full screen the buttons appeared!

---

### Post by melonipoika on 2006-04-01
[QUOTE=sadjack]I had the same problem, in my case I found it was because the opened window was small, when I enlarged it to full screen the buttons appeared![/QUOTE]

Well, I think I have a diffierent problem... I can see the whole window, but it is not possible to make any change. Thanks for your answer anyway

---

### Post by Sod75 on 2006-04-02
not to do with the GUI issue you seem to have, but for sharing files between 2 *nix machines you shouldn't use samba(mostly for windows compatibility) , go for nfs instead which in native. (don't forget to install "portmap"though)

---

### Post by melonipoika on 2006-04-02
Hi sod75,

Thanks for your replay. I still have the gui problem, so do you know the configuration file I should edit to set the shared folders? thank you very much for your help.

---

### Post by GeneralZod on 2006-04-02
Firstly, make sure your system is completely up-to-date, as this "Administrator Mode" things was a bug in the first release of Kubuntu that was later fixed by an update.  You might want to log in and out of KDE after updating to make sure it's taken effect.

Secondly, press ALT+F2 and in the "Run" dialogue type

```

kcontrol

```

and see how you get on with that!

Hope this helps! :)

---

### Post by melonipoika on 2006-04-02
Hi,

Thanks. Yes, my system is updated, and in kcontrol I have exactly the same problem, I can't modify anything. I have tryed also running kcontrol as root, but it is the same. I am using Dapper, I did a clean install few days ago. I will ask in the dapper list if anyone else is having this problem. Thank you for your help.

---

### Post by melonipoika on 2006-04-02
ok, the problem with the gui has been solved by installing the package nfs-kernel. Thanks to the people that helped me, I didn't thought that it was necessary to install new packages...

---

