---
title: "Ubuntu crashes when loading due to X config file"
date: 2006-04-20
forum: General Help
---

### Post by tLove on 2006-04-20
So I finally got ubuntu really up and running, everything was great for like 4 hours. I went to reboot, to do some stuff in windows, and I wasn't paying attention and it went back into Ubuntu. Turns out it had screwed up big time. The screen was all blue, and there was some fuxed up formatting with the letters and it gave me this error about X config file being corrupted somehow.

Now, I know made a backup file of the Xconfig in the same folder labeled whatever it wanted to default to. The whole reason its probably screwed up is I had to make it recognize my monitor and my default res of 1440X900.

So how do I restore the old file? Also there are 2 new logins for grub...  neither work. Any help appreciated, and btw, I'm totally new to Linux in general so speak to me like a small child. Thanks!

---

### Post by dermotti on 2006-04-20
goto command line and run **sudo dpkg-reconfigure xserver-xorg** then restart X

---

### Post by tLove on 2006-04-20
[QUOTE=dermotti]goto command line and run **sudo dpkg-reconfigure xserver-xorg** then restart X[/QUOTE]

I ran that command after I clicked ok for the errors and it just brought me to a screen with text. I went through the config thing twice and moslty did default settings and I still can't get it to work. Is there anyway to write the original file or restore the backup thats stored where the file is?

I don't want to give up yet because I wasted so much time on this yesterday and to reinstall would be pointless.

---

