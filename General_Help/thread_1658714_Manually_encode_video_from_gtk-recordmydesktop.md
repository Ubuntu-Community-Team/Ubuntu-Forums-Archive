---
title: "Manually encode video from gtk-recordmydesktop"
date: 2011-01-03
forum: General Help
---

### Post by JohnElway on 2011-01-03
I was recording my desktop when my graphical environment, along with all my open programs, crashed. After I logged back in, I went to my /tmp folder and found the folder in it that holds the files from gtk-recordmydesktop. It has the following contents:

```
audio.pcm  
img.out
img.out.1  
img.out.2
img.out.3  
img.out.4
img.out.5
specs.txt
```

Does anyone know how to turn these files into a video, i.e. is there a way to manually encode these files the way that gtk-recordmydesktop would have had it not crashed?

---

### Post by JohnElway on 2011-01-06
Anyone?

---

### Post by aeilos on 2011-03-25
I have the same problem. Recordmydesktop stopped encoding at 30% of my screencast, and I would like to know if there's a way to take the unencoded files that recordmydesktop creates and encode them myself. 

Otherwise, I'll have to do my hour+ screencast again, which is something I'm not looking forward to. (This is the second fail I've had with recordmydesktop).

---

### Post by aeilos on 2011-03-25
Ok, so I don't know if this will work yet, but:

recordmydesktop has a rescue option. You need to use the terminal.

```
recordmydesktop --rescue PATH/TO/YOUR/DATA
```

I think by default the data is in /tmp/rMD-session-SOMENUMBER

---

### Post by JohnElway on 2011-05-02
> **aeilos said:**
> Ok, so I don't know if this will work yet, but:

recordmydesktop has a rescue option. You need to use the terminal.

```
recordmydesktop --rescue PATH/TO/YOUR/DATA
```I think by default the data is in /tmp/rMD-session-SOMENUMBER

I just had the opportunity to try this, and it works perfectly. Thanks!

---

