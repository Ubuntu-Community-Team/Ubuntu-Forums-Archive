---
title: "Has my system been compromised...?"
date: 2010-11-08
forum: General Help
---

### Post by GhostC10 on 2010-11-08
Today I booted my machine to find that all the folders in my Places menu now open in VLC. Nautilus works if I start it through the terminal or Applications menu, but if I click a folder in Places, it opens it in VLC. Also, I don't know if this could be related, but when I click on the battery indicator, it doesn't come up. It changes to the pressed-down button look, but it doesn't show the information bubble. I suspect there won't be a fix short of a reinstall, as I can't find a way to change the Places menu options and suspect that even if I did, it wouldn't do much good. I'm not sure how I would have been compromised, I use fairly strong passwords intermixed with punctuation, they'd take quite some time to bruteforce and I surf as safely as one can.

I must sound like a complete moron, but I'm no slouch when it comes to basic security practices. I'm kinda surprised this could happen. Is there any information I could post that could be of use to anyone looking as this thread?

---

### Post by searchfgold6789 on 2010-11-08
Your system has not been compromised.
I have seen this problem occur many times, with files always being opened by *x* program instead of their designated program. I will keep searching and will point you to a thread if I see one.

---

### Post by GhostC10 on 2010-11-08
Thank you for taking a load off my mind. I'm not new to computers but I've only had Linux for a couple years, most of which it was mostly a curiosity. Only within the past six months have I switched pretty much entirely from winXP. I only keep the partition around for games. I've been so thrilled by linux's sheer power and customisability, it's what I always wanted in an OS. Only recently have I gotten into shell scripting, and now the only reason I use the GUI is for brasero, mplayer and FF. I registered to the forums not long ago, and the community has proven more helpful (and accepting of nublets) than any other I've met. Just wanted to thank you for giving your time to help me out.

---

### Post by nothingspecial on 2010-11-08
You need to go ~/.local/share/applications and check the default.list and mimeapps.list configs

You probably have vlc in there to open directories.

You can either edit them or just delete them and log out and back in and they will be recreated.

---

### Post by nothingspecial on 2010-11-08
> **nothingspecial said:**
> 

You can either edit them or just delete them and log out and back in and they will be recreated. 

No they won`t, but the fact that they are gone should nt present you with a problem. Better just to remove vlc from the files.

---

### Post by Verbeck on 2010-11-08
hi, 
create a new folder on your desktop, right click it>open with other application>select file browser

---

### Post by GhostC10 on 2010-11-08
That did it. I'm kinda embarassed I didn't think of that. Thank you very much!

---

### Post by madmax75 on 2010-11-08
> **GhostC10 said:**
> I'm kinda embarassed I didn't think of that.

No need to feel that way :)

There are no such things as "stupid" questions + nobody is perfect :)

---

### Post by Verbeck on 2010-11-08
you're welcome.
there's been a lot of posts lately with the same problem..

---

