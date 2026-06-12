---
title: "equivalent location in linux?"
date: 2012-04-15
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2012-04-15
Is there an equivalent location for windows user/AppData/Roaming in Linux?

---

### Post by raja.genupula on 2012-04-15
i didn get actually what you want , give more information .

---

### Post by 3Miro on 2012-04-15
What is in Roaming? Linux applications usually store their settings in various folders in your /home/your_user_name. Those are usually hidden folders, you can see them if you press "Ctr + H".

For example: /home/3miro/.mozilla holds my Firefox settings, /home/3miro/.config/xfce4 holds the settings or my desktop environment and so on.

---

### Post by CharlesA on 2012-04-15
It's basically the %APPDATA% folder on Windows ([see here for more info]("http://superuser.com/questions/21458/why-are-there-directories-called-local-locallow-and-roaming-under-users-user")), so on Linux, it would be your home directory.

---

### Post by haqking on 2012-04-15
roaming is usually used in a domain and Windows stores in roaming or in local.

equivalent would be something like, though no direct quivalent

```
/home/user/.<application>/profiles/
```

where configuration is usually in a hidden folder.

peace

---

### Post by ihatetryingtopickaloginna on 2012-04-15
Ok thanks for the replies. I'll look for the hidden folders.

---

