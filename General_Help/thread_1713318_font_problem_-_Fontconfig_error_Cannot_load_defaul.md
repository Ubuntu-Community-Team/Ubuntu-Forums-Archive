---
title: "font problem - Fontconfig error: Cannot load default config file"
date: 2011-03-23
forum: General Help
---

### Post by mrpeachy on 2011-03-23
I followed this guide
[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

but when i was done i didnt see any difference in the appearance of my fonts so i decided to remove all the files that i had extracted 
including deleting the files
alias.conf
local.conf
misc.conf
msfonts-rules.conf
from etc/fonts

leaving behind what was originally there (or what i thought was originally there) ie
2 directories
conf.avail and conf.d
and a file named fonts.dtd

ever since then i get this error
Fontconfig error: Cannot load default config file

which means (probably amongst other things) that i cant install new fonts
when i double click a ttf font and select "install font", it says the "install failed"

and when i try updating the font cache i get this 
```

mcdowall@mcdowall-desktop:~$ fc-cache
Fontconfig error: Cannot load default config file
/usr/share/fonts/truetype: failed to write cache


``` when i try
```

fc-cache -f -v

```it seems like it is working but i cant use any new fonts

anyone know what to do?  or is it reinstall time
i booted into recovery and ran the fix broken packages option, but it didnt fix this problem

using ubuntu 10.10

thanks

---

