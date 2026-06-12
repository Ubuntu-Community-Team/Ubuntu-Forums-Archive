---
title: "Run script in response to keypress"
date: 2009-11-08
forum: General Help
---

### Post by pmooney78 on 2009-11-08
I'd like to define a key combination that runs a bash script. Is this possible?

I'm running Ubuntu 8.10 on a Dell Latitude D420.

Thanks in advance.

---

### Post by thegreenblob on 2009-11-08
I believe you can go to System-->Preferences-->Keyboard Shortcuts

And then click "Add", pick a name, and the command will be "/home/location/of/the/bash/script"

And then it should be added, scroll down and click on the shortcut to choose a key combination and all set, should work fine.

If it doesn't work make sure the script is executable with,

```
sudo chmod +x /home/location/of/script
```

Hope this helps.

---

### Post by pmooney78 on 2009-11-08
Thank you ... but I don't show an "Add" button in the dialog.

---

### Post by thegreenblob on 2009-11-08
So there's no add button? (I took a screenshot)

[[IMG]http://img200.imageshack.us/img200/4840/screenshotkeyboardshort.th.png[/IMG]](http://img200.imageshack.us/img200/4840/screenshotkeyboardshort.png)

If not, is there anything similar? If so try that. If not I'm not sure, and I guess you'll have to wait til someone that knows specifically how to do it with 8.10 comes along.

---

### Post by VCoolio on 2009-11-08
I've seen the missing button problem before, maybe it wasn't there yet on Intrepid. Anyway, if you don't have the 'add' button, do one of the following:
1. define keybindings in compiz settings manager if you use compiz
2. define keybindings in gconf-editor (at apps > metacity > global_keybindings (for the keys) and keybinding_commands (for the script command) )
3. install xbindkeys and configure ~/.xbindkeysrc, especially recommended if you use a lot of keybindings.

Also, if the script is in your /home/user part, you don't need to use 'sudo' before chmod.

---

### Post by pmooney78 on 2009-11-08
> **thegreenblob said:**
> So there's no add button? (I took a screenshot)

[[IMG]http://img200.imageshack.us/img200/4840/screenshotkeyboardshort.th.png[/IMG]](http://img200.imageshack.us/img200/4840/screenshotkeyboardshort.png)

If not, is there anything similar? If so try that. If not I'm not sure, and I guess you'll have to wait til someone that knows specifically how to do it with 8.10 comes along.

Nothing... darn it. I wonder whether there's some way to install the 9.04 version of the keybinding preferences? Otherwise, like you say, I'll have to wait until someone who uses 8.10 comes along with an idea.

---

### Post by pmooney78 on 2009-11-08
VCoolio, it looks like xbindkeys will work for me. Now I just have to tweak the script. Thank you!

---

