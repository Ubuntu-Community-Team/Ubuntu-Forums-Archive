---
title: "DVD Playbck"
date: 2010-04-30
forum: General Help
---

### Post by ez4u2sa67 on 2010-04-30
Hey, 
I can't seem to get DVD playback to work. I installed Ubuntu restricted extras and I mad sure that libdvdread4 and libdvdnav4 were both installed and still no luck. Movie Player says there is an error when trying to play and VLC does nothing at all. The disc does appear on my desktop and I can go through its contents. Anyone got an idea of what to do?

---

### Post by StuartN on 2010-04-30
> **ez4u2sa67 said:**
> I can't seem to get DVD playback to work.

Try **sudo /usr/share/doc/libdvdread4/install-css.sh** to enable css decryption

---

### Post by 73ckn797 on 2010-04-30
Try the instructions at this link:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ez4u2sa67 on 2010-04-30
> **StuartN said:**
> Try **sudo /usr/share/doc/libdvdread4/install-css.sh** to enable css decryption

Nope, that did not work. I keep getting the same error.

---

### Post by ez4u2sa67 on 2010-04-30
> **73ckn797 said:**
> Try the instructions at this link:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

There we go, that did it. Just for the record since I'm new to this, I could have typed in a part of that code (the URL) into the Software Sources and still have had Medibuntu as a source, right?

---

### Post by 73ckn797 on 2010-05-01
> **ez4u2sa67 said:**
> There we go, that did it. Just for the record since I'm new to this, I could have typed in a part of that code (the URL) into the Software Sources and still have had Medibuntu as a source, right?
I have not tried that before so I could not comment on it. The instructions have always worked so I let that do the configuring.

Glad it worked.

---

