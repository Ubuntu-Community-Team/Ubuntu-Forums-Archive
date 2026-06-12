---
title: "Geeky  tty mode mouse + grapics web brower"
date: 2011-03-05
forum: General Help
---

### Post by highspider on 2011-03-05
OK so I have sick desktop effects with Cairo, screenlets, comiz-fushion sphere ect...

 But for some reason I want my links2 to work tt1 with a colorful web and mouse
 aka ctrl+alt+f1 at login screen and go online surf net with out X 

OK what ive done
killed services start up network manger
using /ect/network/interfaces and /ect/resolve.conf for net
set about:config to get rid Firefox start in offline mode 
toolkit.networkmanager.disable = true
install gpm (tty general purpose mouse) 
installed links2

ok links2 works fine with mouse at tty1 in normal mode!
```
links2
```and links2 works in tty1 with graphics just fine !
well as root grrr flipping ubuntu changes to get rid of 40-permissions.rules
```
links2 -g -mode 800x600x256
```however, the mouse don't work with graphics mode

I try editing the libvga.config
```
gedit  /etc/vga/libvga.config
```but even one set mouse to none i get mouse error with no mouse in -g graphics mode

since I use gpm I shouldn't even need libvga.config for mouse in links2

---

### Post by highspider on 2011-03-05
got lucky 
 non of guides tell you to  comment out 
```

#mouse unconfigured

```
sudo gedit /etc/vga/libvga.config

---

