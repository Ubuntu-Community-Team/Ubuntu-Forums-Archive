---
title: "Songwrite"
date: 2011-05-12
forum: General Help
---

### Post by teejayuu on 2011-05-12
Hi
I've just installed the Songwrite application using Ubuntu Software Centre onto my Dell 10v Mini running Natty Narwhal (11.04).  When I click on Applications > Sound & Video > Songwrite nothing happens - no spinning cursor, no nothing!  Have I missed something?

Cheers
Tony

PS I am relatively new to Linux!

---

### Post by cymbaline42 on 2011-05-12
It might not have installed correctly.  Did you try uninstalling and re-installing?

---

### Post by neclepsio on 2011-05-27
Same problem here.

From the command line:


neclepsio@neclepsio-HP-620:~$ songwrite
Traceback (most recent call last):
  File "/usr/bin/songwrite", line 134, in <module>
    import main
  File "/usr/bin/../share/songwrite/main.py", line 21, in <module>
    import globdef, song, player, ui
  File "/usr/bin/../share/songwrite/song.py", line 1352, in <module>
    END_TRACK = struct.pack(">bbb", 0xFF, 0x2F, 0x00)
struct.error: byte format requires -128 <= number <= 127


replacing >bbb with >BBB seems to work

---

### Post by samwaithaka on 2011-08-17
Just how did you figure this out! It worked for me too. Thank you very much.

---

### Post by Dscottmc7 on 2012-05-28
Had the same error.
I opened: sudo gedit /usr/bin/../share/songwrite/song.py
saved to "song.py-2"
closed, (opened -sudo gedit)  /usr/bin/../share/songwrite/song.py

set preferences to "view line numbers"
Scrolled down to line 1352...

the byte format in (bbb) is >=127. 
I simply changed that to (BBB) which is >127, (i.e. >=128), 
saved closed and restarted.  Perfect!
Thank you...

---

### Post by oldos2er on 2012-05-28
Old thread closed.

---

