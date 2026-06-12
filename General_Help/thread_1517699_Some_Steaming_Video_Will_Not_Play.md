---
title: "Some Steaming Video Will Not Play"
date: 2010-06-25
forum: General Help
---

### Post by jereece on 2010-06-25
I am dual booting Windows 7 and Ubuntu.  I like to watch the previous night's The Tonight Show when I get home from work.  However in Ubuntu the streaming video never starts.  I get the NBC Peacock image and it looks like it will start but never does.  There is a white line that is supposed to expand as the video is loading but I never see that in Ubuntu running Firefox or Google Chrome.  However, in Windows 7 using Firefox or Chrome I can watch the streaming video just fine.  In Ubuntu, I can go to other streaming video sites like Fancast and even other networks like CBS and watch steaming video just fine.  For some reason however the video will not load for The Tonight Show.  I have installed all the latest updates.  

Any suggestions?

Thanks,
Jim

---

### Post by mooreted on 2010-06-25
Well, that's odd. I went to the Tonight Show website and watched part of a full episode and it worked fine. Just to let you know it does work in Linux.

I thought it might be a Silverlight issue, but it's flash.

What flash player are you using and what version?

---

### Post by jereece on 2010-06-25
Adobe Flash Plugin version 10.0.45.2-1

---

### Post by lovinglinux on 2010-06-25
> **jereece said:**
> Adobe Flash Plugin version 10.0.45.2-1

That version has a critical vulnerability. Update to 10.1 r53.

---

### Post by jereece on 2010-06-25
This is probably a dumb question, but how do you do that?  I went into Software Center and went into installed software.  I double clicked on Adobe Flash and it gave me the option to uninstall but not update.  When I go to reinstall it says I have the latest version.  

Thanks,
Jim

---

### Post by lovinglinux on 2010-06-25
> **jereece said:**
> This is probably a dumb question, but how do you do that?  I went into Software Center and went into installed software.  I double clicked on Adobe Flash and it gave me the option to uninstall but not update.  When I go to reinstall it says I have the latest version.  

Thanks,
Jim

Go to "System >> Administration >> Software Updates".

---

### Post by Dustin2128 on 2010-06-25
If the version in the repos isn't recent enough, go to the adobe site, unpack the tar archive from the adobe website and drag the libflashplayer.so file to /usr/lib/firefox/plugins, applies it to all browsers for some reason and it worked for me.

---

### Post by lovinglinux on 2010-06-25
> **Dustin2128 said:**
> If the version in the repos isn't recent enough, go to the adobe site, unpack the tar archive from the adobe website and drag the libflashplayer.so file to /usr/lib/firefox/plugins, applies it to all browsers for some reason and it worked for me.

It simpler to get the deb file.

---

### Post by jereece on 2010-06-27
There is no "System >> Administration >> Software Updates".  There is a "System >> Administration >> Software Sources" and also a "Update Manager" but no "Software Updates".  I looked in both the Software Sources and Update Manager and saw no way to update Adobe Flash.  

I finally figured out how to download the deb file and that did work.  

Thanks for the help.

Jim

---

