---
title: "Missing dependencies"
date: 2010-03-08
forum: General Help
---

### Post by Silvernail on 2010-03-08
If this needs to go to a different forum please let me know and I will post it there.
First missing:
```
sudo apt-get install gwenview
```
Then when I call 'gwenview' from a command I can see the these errors:
> "/usr/bin/gwenview(11719)" Error in thread 3056593776 : "Unsupported operation (2)": "Invalid model"
"/usr/bin/gwenview(11719)" Error in thread 3056593776 : "Unsupported operation (2)": "Invalid model"
"/usr/bin/gwenview(11719)" Error in thread 3056593776 : "Invalid iterator."
"/usr/bin/gwenview(11719)" Error in thread 3056593776 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
Where do I get 'nepomukstorage'?

Second missing:
When 'gimp' called from the command line I see these:
> (gimp:11768): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
/home/dave/.gimp-2.6/plug-ins/burnt-paper.scm: 1: Syntax error: word unexpected (expecting ")")

(gimp:11768): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
/home/dave/.gimp-2.6/plug-ins/glass-selection.scm: 1: Syntax error: ";" unexpected

I have placed 7 plug-ins in my plug-in directory and I am getting errors on all of them. These were downloaded from the 'gimp' plug-in source directory.

Anyone got an suggestion what else I need to install?

---

