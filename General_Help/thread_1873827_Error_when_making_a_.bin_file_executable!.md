---
title: "Error when making a .bin file executable!"
date: 2011-11-02
forum: General Help
---

### Post by Huntereb on 2011-11-02
Hello! I am not sure where to put this post, so I just put it in general, please read!

Today I installed Ubuntu Server 10.04 with LXDE, in fact i'm using it now. I am trying to install a server for use with video games like "Counter-Strike Source", but in order to install the required files, I have to make "hldsupdatetool.bin" executable. When I try to do this, it seems that it instantly deletes the file because when I type, **"chmod +x hldsupdatetool.bin"** then type **"./hldsupdatetool.bin"** it responds with this, **"bash: ./hldsupdatetool.bin: No such file or directory"**.

Why is this happening? I even tried making the files executable by all users from the Properties menu in PCFile manager, it still responds saying the file does not exist. I deleted, and tried this again multiple times.

So does anyone know how to do this without deleting the file automatically? Or am I just doing something wrong with this new OS?

Here is the text that is helping me install: [http://www.gamebanana.com/threads/107809](http://www.gamebanana.com/threads/107809)

Thanks! And I hope this is fixable...

---

### Post by gsmanners on 2011-11-02
I think this is the problem you may be running into:

[http://forums.steampowered.com/forums/showthread.php?t=524675](http://forums.steampowered.com/forums/showthread.php?t=524675)

You're on a 64-bit system, right?

---

### Post by Huntereb on 2011-11-02
Oh thank god. Yes it worked, thank you very much! :P

---

