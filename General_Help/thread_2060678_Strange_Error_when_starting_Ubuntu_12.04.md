---
title: "Strange Error when starting Ubuntu 12.04"
date: 2012-09-20
forum: General Help
---

### Post by seraieis on 2012-09-20
I'm not even sure how to describe what happened. I just took my old computer, and was turning it into a file server / media center. I got Samba going, copied files from Windows, and everything was great! The next time I turned it on, the screen looked like the attachment. All the changes I made in smb.conf I reverted, but that didn't help.

Has anyone seen anything like this? I'd rather not reinstall the whole thing (thought Ubuntu Server might be a better choice). Thoughts?

---

### Post by pissedoffdude on 2012-09-20
What kind of graphics card do you have?  The only thing you did was update files, and no updates or anything like that?

You can try starting Unity in 2d mode or use Gnome classic for now.  If you have autologin enabled, hit ctrl+alt+f2, login, type ```
sudo killall lightdm
sudo lightdm
``` 

Then you should hopefully have the option of picking Unity2d.  If it still does autologin, after killing lightdm, run ```
sudo nano /etc/lightdm/lightdm.conf
``` and put a # at the start of each line that contains autologin

If you don't have Gnome classic installed and Unity2d is a no go, you can get it with ```
sudo apt-get install gnome-panel
```

---

### Post by seraieis on 2012-09-20
Editing /etc/lightdm/lightdm.conf did the trick! I even logged back out, switched it back to Unity, and it's working again.

Do you have any idea why this fixed it? Not knowing is driving me crazy!

---

### Post by BlinkinCat on 2012-09-20
> **seraieis said:**
> Editing /etc/lightdm/lightdm.conf did the trick! I even logged back out, switched it back to Unity, and it's working again.

Do you have any idea why this fixed it? Not knowing is driving me crazy!

Leave your thread as unsolved for awhile using thread tools and you may get an answer to your last question - Most will skip past if they see thread marked as solved - ;)

---

