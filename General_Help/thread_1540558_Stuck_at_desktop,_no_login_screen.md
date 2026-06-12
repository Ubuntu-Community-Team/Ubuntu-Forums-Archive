---
title: "Stuck at desktop, no login screen"
date: 2010-07-28
forum: General Help
---

### Post by thecypher on 2010-07-28
Hey all,

My first time posting here, thanks for all the amazing threads which have often had the answers I'm looking for.

I recently updated to Ubuntu 10, and I am having a problem getting to the login screen. I've been able to login many times, and after turning my computer on this evening, it boots to the splash screen but does not display the login prompt or any message. To be clear I do get to the splash screen (the default purple background), but no login box appears.

Any ideas how I can debug this from recovery mode or anything?

Thanks for any help,
TheCypher

---

### Post by thecypher on 2010-07-28
Wow fixed.. It was due to installing zlib 1.2.5 from source. Who would've thought?

---

### Post by linux18 on 2010-07-28
thats just crazy! lol

---

### Post by deostroll on 2010-08-08
what?? really?? uninstalling zlib helps?!

---

### Post by Mathew Roy on 2010-09-08
Well even I did have the very same problem. But any idea why it happens? Well I want to install zlib because I need it in my programming (it is required to install libpng).. Plz help me, I have no idea what to do...

---

### Post by Mathew Roy on 2010-09-08
Hai guys, I got the solution for installing zlib without crashing the system.
Try this, it worked well with me.
go to
System->Administration->Synaptic Package Manager
search for zlib1g-dev and install the package. (My system didnot crash  this time.)
Simple as that...

---

### Post by Jozza The Wick on 2010-09-11
Yes, I had this problem too. Installed zlib from source, on next reboot got to desktop, mouse cursor responsive but no login screen. To fix:

1. Hit Ctrl-Alt-F1 to get to a tty screen & login
2. delete  /usr/local/lib/libz.* and  /usr/local/include/zlib.h (assuming you installed with make ; make install - if you installed in a different place, remove them from where you put them..
3. Profit!!

Turns out I don't need zlib so I can't comment on what happens with the dev package from the package manager...

---

### Post by user696 on 2011-01-24
> **Jozza The Wick said:**
> Yes, I had this problem too. Installed zlib from source, on next reboot got to desktop, mouse cursor responsive but no login screen. To fix:

1. Hit Ctrl-Alt-F1 to get to a tty screen & login
2. delete  /usr/local/lib/libz.* and  /usr/local/include/zlib.h (assuming you installed with make ; make install - if you installed in a different place, remove them from where you put them..
3. Profit!!

Turns out I don't need zlib so I can't comment on what happens with the dev package from the package manager... 

^THIS THIS THIS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

You sir are a saviour. I salute you. Rock on, rock on!!!!!!!!!!!!!!!!!

All hail Jozza The Wick, he'll probably never even read this, he'll never know........ :-(

---

