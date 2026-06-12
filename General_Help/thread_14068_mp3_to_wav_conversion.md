---
title: "mp3 to wav conversion"
date: 2005-02-04
forum: General Help
---

### Post by uberlinux on 2005-02-04
hey all,
I'm new to linux and was wondering if there was an apt that would convert mp3s to WAV format so that I can burn them with k3b
thanks in advance

---

### Post by uberlinux on 2005-02-04
***UPDATE***
audacity seems to do this...wish k3b did it automatically tho....

---

### Post by ilari on 2005-02-04
[QUOTE=uberlinux]***UPDATE***
audacity seems to do this...wish k3b did it automatically tho....[/QUOTE]
 mpg312 should be able to do it. It resides in the universe-repository. The syntax for converting mp3-file to wav-format is 'mpg321 -w new_name.wav old_name.mp3'

---

### Post by CowPie on 2005-02-04
[QUOTE=ilari]mpg312 should be able to do it. It resides in the universe-repository. The syntax for converting mp3-file to wav-format is 'mpg321 -w new_name.wav old_name.mp3'[/QUOTE]

is htere anyways to change change the bitrate using this program?

---

### Post by rkn on 2005-02-04
>  
is htere anyways to change change the bitrate using this program? 

you can change the bitrate ('resample' or 'polyphase') if you use sox.
** man sox **

Bob

---

