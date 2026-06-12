---
title: "Weird font problem???"
date: 2010-05-24
forum: General Help
---

### Post by JordanMaster22 on 2010-05-24
I noticed some programs, such as Terminal, would instead of having the default font, all the characters were boxes (as if they were undefined chars). Then I restarted and then ALL TEXT ON UBUNTU WERE []S. I can't even read what anything says. I'm in Windows now posting this because I can't read anything on Ubuntu.

How can I fix this font issue? (Preferably without reinstalling?) I noticed using recovery mode I can use a non-GUI version of Ubuntu which is basically Terminal as an OS in which I can actually see the font.

---

### Post by inso_741 on 2010-05-24
did you install any new font before you got this problem...did you try to change any fonts?

---

### Post by JordanMaster22 on 2010-05-24
> **inso_741 said:**
> did you install any new font before you got this problem...did you try to change any fonts?

All I did was watch a movie in VLC, watch a video on YouTube in Firefox and install DeVeDe.

---

### Post by inso_741 on 2010-05-24
can you boot into recovery kernel?

---

### Post by JordanMaster22 on 2010-05-24
> **inso_741 said:**
> can boot into recovery kernel?

Everything else is fine except I can't see the text in the GUI version. The CLI version is good.

---

### Post by inso_741 on 2010-05-24
then try running 'sudo apt-get upgrade' this might fix broken packages if any...

---

### Post by wojox on 2010-05-24
Try updating your font cache:

```
sudo fc-cache -f -v
```

---

### Post by JordanMaster22 on 2010-05-24
> **inso_741 said:**
> then try running 'sudo apt-get upgrade' this might fix broken packages if any...

> **wojox said:**
> Try updating your font cache:

```
sudo fc-cache -f -v
```

I tried both these but no luck. :(

---

