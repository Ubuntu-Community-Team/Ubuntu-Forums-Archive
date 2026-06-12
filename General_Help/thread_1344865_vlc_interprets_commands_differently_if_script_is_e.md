---
title: "vlc interprets commands differently if script is executed by scheduled-tasks-manager"
date: 2009-12-03
forum: General Help
---

### Post by maweki on 2009-12-03
Hello,

**My problem in short:**
I have a script which executes vlc. vlc interprets its parameters correctly if the script is executed from the command line. When it is executed from the scheduled-tasks-manager (german installation, don't know its english name, but the gnome gui for cron), vlc interprets the commands differently, leading to wrong behaviour.

**Now the long version:**
I have a vanilla karmic installation. I try to record some 5 hours off of a local radio station. Took me some time to figure out which commands the vlc-record-button invokes, but it worked. And now I have a working script which reads as followed:
```
#!/bin/bash
vlc http://www.fritz.de/live.wax --sout file/asf:/home/maweki/shellscripts/ken.asf &
pid=$!
sleep 19000s
kill $pid
sleep 15s
kill -9 $pid
sleep 5
```

When I execute this script from the terminal, it works perfectly with the following output:
> VLC media player 1.0.2 Goldeneye
[0xb6f00940] main interface error: no interface module matched "globalhotkeys,none"
[0xb6f00940] main interface error: no suitable interface module
[0x924d140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x924d140] main libvlc: vlc wird mit dem Standard-Interface ausgeführt. Benutzen Sie 'cvlc', um vlc ohne Interface zu verwenden.
[0x958c3c8] access_mms access: selecting stream[0x1] audio (47 kb/s)
[0x958c3c8] access_mms access: connection successful


When executed from the gnome-cron-gui, the script throws following output:
> VLC media player 1.0.2 Goldeneye
[0x987a188] main interface error: no interface module matched "globalhotkeys,none"
[0x987a188] main interface error: no suitable interface module
[0x97b8140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x97b8140] main libvlc: vlc wird mit dem Standard-Interface ausgeführt. Benutzen Sie 'cvlc', um vlc ohne Interface zu verwenden.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Can't stat --sout
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[0x9adff88] access_file access error: cannot open file --sout (No such file or directory)
[0xb7009730] main input error: open of `--sout' failed: no suitable access module
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open file/asf:/home/maweki/shellscripts/ken.asf with libdvdcss.
libdvdread: Can't open file/asf:/home/maweki/shellscripts/ken.asf for reading
libdvdnav: vm: failed to open/read the DVD
[0x9af44f8] access_file access error: cannot open file file/asf:/home/maweki/shellscripts/ken.asf (No such file or directory)
[0x9ace5b8] main input error: open of `file/asf:/home/maweki/shellscripts/ken.asf' failed: no suitable access module


As I see it, now vlc tries to open "--sout" (for example) as a file which it is not.
Frankly, I do not understand it.

Does anybody know, why vlc interprets that differently? I first thought, it was a different shell, but i explicitly stated which shell to use.
Is this behaviour repeatable? Does it lie with the cron-gui?


And to something not completely different:
I live at CET (atm UTC+1). Are my cron settings in utc or local time? (again, I have a vanilla installation and only used the gui for cron)

I hope, anybody can help me.

Greetings
maweki

---

### Post by jegerjensen on 2009-12-03
This is a long shot, but do you think the warning about using cvlc has anything to do with it?  When you run the script from crontab it will probably run with different environment variables.  Have you tried starting cvlc instead of plain vlc?

---

### Post by maweki on 2009-12-03
> **jegerjensen said:**
> This is a long shot, but do you think the warning about using cvlc has anything to do with it?  When you run the script from crontab it will probably run with different environment variables.  Have you tried starting cvlc instead of plain vlc?

This warning is only that I could use cvlc if i don't want an interface. Sorry for not translating it.

But I tried it and it exactly shows both behaviours. One wrong (from the gui) and the right one (from the terminal).

I have really no idea why vlc should interpret its parameters differently. If you or anybody had to guess:
Lies the problem with vlc, the cron-gui, cron itself or inherently in the script (then this would be "expected behaviour", which, I guess, it is not)?

---

### Post by maweki on 2009-12-04
so I posted in the vlc forums and those guys sent me to the gnome people. I hope I can find some answers there.

---

