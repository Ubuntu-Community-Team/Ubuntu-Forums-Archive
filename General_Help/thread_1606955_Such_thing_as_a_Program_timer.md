---
title: "Such thing as a Program timer?"
date: 2010-10-27
forum: General Help
---

### Post by TheGreatBunghole on 2010-10-27
I frequently use the command:  Sudo shutdown -h <00:00>  to shutdown my entire ubuntu system, but I was wondering if there was a program out there that I could set a timer for closing a running program?  I usually listen to streaming audio in VLC when I go to sleep because I have sleeping problems, but I don't want to have to shutdown my computer to make the music shutoff by itself... Is there an existing program out there somewhere?   ...Or do I have to wait 2 years until I am finished with my AAS in computer science to write the program myself?   Thank you for you're help in advance. :)

---

### Post by cogier on 2010-10-27
If you open Terminal with [Ctrl] + [Alt] + T and then type ```
man shutdown
``` details of how to set the time to shutdown are detailed.

---

### Post by nothingspecial on 2010-10-27
Loads of ways to do this
```

sleep 60m && killall vlc
```

Will kill vlc after 60 minutes

---

