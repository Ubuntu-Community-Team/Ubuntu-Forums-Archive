---
title: "I need some code to install gedit themes via the terminal!"
date: 2009-08-30
forum: General Help
---

### Post by Rytron on 2009-08-30
Hi.
I need some code to install gedit themes via the terminal. I know this can be done under
Edit -> Preferences -> Font & Colors -> Add
however I keep getting this message [image attached].

Would something like this be required?

```
sudo cp -v darkermate.xml $HOME/.gnome2/gedit/styles/
sudo chmod 777 $HOME/.gnome2/gedit/styles/darkermate.xml
sudo chmod -x $HOME/.gnome2/gedit/styles/darkermate.xml
```

Thanks.

---

