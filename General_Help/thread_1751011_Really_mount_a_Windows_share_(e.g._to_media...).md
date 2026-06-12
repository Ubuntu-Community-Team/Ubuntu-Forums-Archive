---
title: "Really mount a Windows share (e.g. to /media/...)"
date: 2011-05-06
forum: General Help
---

### Post by mwildam on 2011-05-06
I am currently in a more mixed environment as I desire and I need to mount samba shares because I need to work with the data. I noticed that nautilus does not really mount the shares and some applications cannot deal with smb urls.

I searched and found this old thread: [http://ubuntuforums.org/showthread.php?t=289918&page=2](http://ubuntuforums.org/showthread.php?t=289918&page=2)

Is it possible that after all these years, this is still unchanged?

To permanently mount on boot time is not an option for me as the drive will not always be available - already changes when I move within the office from fixed to WLAN (e.g. when going to a meeting and vice versa).

Best regards,

Martin.

---

### Post by Morbius1 on 2011-05-06
> I noticed that nautilus does not really mount the shares and some applications cannot deal with smb urls.Nautilus does indeed mount the remote shares it's just in a very unusual place:
> /home/your-user-name/.gvfs/share-name on server-nameYou will notice that it is in a "hidden" directory ( .gvfs ). Most applications can access that directory but you need to enable "show hidden files" both in Nautilus and one of the applications. Enabling "show hidden files" in one application should enable it in all.

---

