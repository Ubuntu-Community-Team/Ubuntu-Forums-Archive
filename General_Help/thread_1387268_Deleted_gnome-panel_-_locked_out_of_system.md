---
title: "Deleted gnome-panel - locked out of system"
date: 2010-01-21
forum: General Help
---

### Post by allsaythat on 2010-01-21
Right. I feel a bit of an idiot.
I followed some badly-spelled online instructions to get rid of the last panel (because I'm using Avant Window Navigator instead), which had me do this:
> 
Ok some people relize that the gnome panel in ubuntu is very annoying and if your like me you dont wnat it there anymore, so you wnat to get rid of it ( only suggested if you have something like AWN ), ok first push alt+f2, then in that type gconf-editor inside of it. Now in that a box should apear. Click on apps, thenGnome, then session, then required sessions. Then there should be a file called gnome -panel right click it then choose edit, then make it empty. then save it press ctrl+alt+delete, then it should not be there but if it is run killallgnome-panel, and to run it again type in gnome-panel. Hope this helped :D

I did it, and now I cannot startup. ( I just get a 'busy' cursor on a blank screen.) How could I fix this?
Thanks.

And next time I think I'll search these forums.

---

### Post by jflaker on 2010-01-21
can you get to terminal?

---

### Post by nothingspecial on 2010-01-21
Try Ctrl-Alt F1 ```
sudo sevice gdm restart
```

or```
 sudo service gdm start
```

or ```
gnome-panel
```

and if you want to get rid of the panel either autohide it or

```
sudo mv /usr/bin/gnome-panel ~/.panel
```

and if you want it back```


sudo mv ~/.panel /usr/bin/gnome-panel 
```

and reboot.

---

### Post by sisco311 on 2010-01-21
run:
```
gconftool-2 --unset /desktop/gnome/session/required_components/panel
```

to restore the original value of the gconf key.

---

### Post by allsaythat on 2010-01-21
OK thanks.
Um, I can get to terminal by entering 'recovery mode.'
I'll give it a go, and see what happens.

I think I'll just set it to 'auto-hide' but only to un-auto-hide after a minute or so.

---

### Post by sisco311 on 2010-01-21
> **allsaythat said:**
> OK thanks.
Um, I can get to terminal by entering 'recovery mode.'
I'll give it a go, and see what happens.

I think I'll just set it to 'auto-hide' but only to un-auto-hide after a minute or so.

In Recovery Mode you are logged in as root, but you have to run the gconftool-2 command as your user:
```
sudo -i -u **username** gconftool2 --unset /desktop/gnome/session/required_components/panel
```
replace username with your login name.

---

### Post by allsaythat on 2010-01-21
Thanks sisco.
Unfortunately it didn't work. I got the error message:
```
(awn:1364): Gtk-WARNING **: cannot open display:
/home/ [my username] /profile: line 24: :wq: command not found
```

What does this mean, and what can I do about it?

---

