---
title: "launching command question"
date: 2011-01-13
forum: General Help
---

### Post by searayman on 2011-01-13
I am trying to make a custom launcer for a playlist file to open in VLC player. In the command part I have the path to the file like this;

/home/mike/Videos/newTv.m3u

what am I doing wrong cause when I try and launch it I get this error:

Details: Failed to execute child process "/home/mike/Videos/newTv.m3u" (Permission denied)

---

### Post by mc4man on 2011-01-13
If vlc can open the .m3u then the command for the launcher should be
```
vlc /home/mike/Videos/newTv.m3u
```

If needed open a terminal and paste above in, it it works then it will work in a launcher (assuming desktop type launcher - you can set either  'application' or 'application in terminal' as desired

---

### Post by searayman on 2011-01-13
> **mc4man said:**
> If vlc can open the .m3u then the command for the launcher should be
```
vlc /home/mike/Videos/newTv.m3u
```

If needed open a terminal and paste above in, it it works then it will work in a launcher (assuming desktop type launcher - you can set either  'application' or 'application in terminal' as desired

thanks, worked perfectly!

---

