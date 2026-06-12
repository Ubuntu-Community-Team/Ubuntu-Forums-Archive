---
title: "ICEauthority issue"
date: 2009-10-16
forum: General Help
---

### Post by Enigmapond on 2009-10-16
Greetings!

I have a small issue when starting my computer. After the login, a warning comes up stating," Unable to update ICEauthority" and then lists the path, which is my home folder. The system then starts up ok and there doesn't seem to be any issues arising from this.

My question is then how can I stop this warning and is this a serious problem?

Thank you in advance!:)

ps. in reviewing there is a .ICE folder that's empty and a file .ICEauthority 17kb in size but states it's an unknown file type and Wine loader tried to open when I clicked...but couldn't...

---

### Post by nothingspecial on 2009-10-16
Try openinig a terminal and typing

```
chmod 644 /home/username/.ICEauthority
```

Might help, won`t harm

---

### Post by Enigmapond on 2009-10-16
Actually that did it...:) Very simple fix and I thank you!

Cheers!

---

### Post by nothingspecial on 2009-10-16
No problem :)

---

