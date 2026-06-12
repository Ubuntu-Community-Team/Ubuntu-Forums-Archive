---
title: "AS/400 On Ubuntu 9.10?"
date: 2010-02-15
forum: General Help
---

### Post by BT1 on 2010-02-15
Okay so I know there are a few AS/400 threads but they're mostly ancient.

My store is interested in switching over to open source software because of the rising costs of licenses and whatnot. The only thing really keeping the store from changing over is the AS/400 issue, which we use extensively as a bookstore (over 13000 titles). I haven't discovered a way to use AS/400 on Linux, so I am asking here since this is where 99.9% of all my questions get answered by bigger nerds than me ;).

I want Ubuntu because it is easy for me and those who work with me who have switched over to Linux for their personal computers at home. It just works, and everyone loves it. Everyone hates windows at work ever since I showed them how much faster Linux runs on the same computers that Windows drags on. We're talking about over 60% faster compared to the Windows that is on their systems.

Since the mother company is cheap, most computers we own are ancient with around 512mg - 2gs ram, and a great deal of that is soaked up by an anti-virus that uses 100 Megs of ram, and a lot of processor power. We need a solution and the mother company says that if we can find a safe alternative that we can submit to their techies, they will seriously look into it and depending on if it is a great success or not, there is the possibility of incorporating it into other stores with lower end computers. I can't disclose the name of the company I work with, but that's the full enchilada so to speak.

Now, who knows if it will work with 9.10, and if it does, how simple is it to transfer over? If yes, is it the same general layout? Please help, this would be a great thing for Linux as this is a big company, and I mean big. Yet no one in my region has suggested Linux curiously. I'd think by now some Linux evangelist would have gotten the ear of someone in the upper ranks by now.

Thanks for your help!

---

### Post by mstephens on 2010-02-15
Not that simple. Although AS/400 (or iSeries as its been known for several years) can run unix applications ( IBM AIX binaries will run natively in its PASE subsystem ), you can't go the other way without a huge amount of effort.

Assuming your existing system is similar to most AS/400 setups, much of the program code will be in RPG2 or RPG3 or RPG4 which is a cross between a 4GL and assembler and the equivalent to shell scripts is yet another compiled language called CL (control language) with data storage in a tightly integrated DBMS.

---

### Post by The Cog on 2010-02-15
> I haven't discovered a way to use AS/400 on Linux,Depends what you mean by this. 

If you mean to run the AS/400 applications on Linux instead of on an AS/400, I can't help you. I don't know if it is possible or not.

If you mean just connecting to the AS/400 to talk to it, then you probably want a TN5250 client for Linux. This is the description for package **tn5250** in the Ubuntu repositories:
> tn5250 connects to an IBM iSeries (AS/400) running i5/OS and
emulates a 5250-compatible "green screen" terminal, or a printer
using SCS or Host Print Transform.  It runs on the Linux console, in
an xterm, or on any other character terminal.

To run in a window, the xt5250 script works best with xterm, but can
use any other program providing the x-terminal-emulator interface.


---

