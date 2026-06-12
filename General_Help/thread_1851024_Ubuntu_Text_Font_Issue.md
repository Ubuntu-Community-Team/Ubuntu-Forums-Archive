---
title: "Ubuntu Text Font Issue"
date: 2011-09-27
forum: General Help
---

### Post by sauce345 on 2011-09-27
I was on 10.04 and after restarting my computer one day I noticed that all my system fonts had changed.  So I went to were you can change system fonts and tried to change it between different fonts with no success.  Whatever font I put it on does not matter and its always the same.  And yes people I logged out n back in to make it take effect.

Most third party applications fonts are still fine and its just the system applications its really effecting.  For example if you do an ls in a terminal all the folder names show up with the top of the folder name dropped to where the bottom of the folder name should be. It looks terrible and some keys I press I get really funky character outputs.

What I have tried: Upgraded to 11.04 over the weekend hoping that would fix it but it did not.  I did notice tho the upgrade had some errors about not being able to load a font config token or something like that?

Anyway I have searched around for text problems and their is lots of information out there just can't seem to find anything that pertains to me.

Help!!

---

### Post by ajgreeny on 2011-09-27
I have no idea how your problem occurred in the first place but I have my system fonts set as shown in the screenshot.  I think I have probably changed all of these from the default that was there at installation, though I can not remember for certain.

Everything looks great on my machine now, however, even better than it did originally, I think.

---

### Post by sauce345 on 2011-09-27
Thanks for the screen shot!! This is what I was talking about where I had already tried changing those settings around.  The thing is, it doesn't matter which font I pick.  It always stays the same and is messed up as described before.

---

### Post by Krytarik on 2011-09-27
Try this:
```
sudo fc-cache -fv
```
If this doesn't help, and you have a directory "~/.fonts" in your home directory, try renaming those. The same for "~/.fontconfig".

Hope it works!

---

### Post by sauce345 on 2011-09-28
Thanks for the reply.  I ran the command ```
sudo fc-cache -fv
``` and it spit out the error I was referring to in my original post. But it still ran the command and gave me a succeeded status.  Here is the error it gives me:

> Fontconfig error: line 3: not well-formed (invalid token)
Fontconfig error: Cannot load default config file

Now I googled around a bit to see what I could find and the only thing i got out of it is that it can parse a font config file correctly.

Also I tried renaming the folders you mentioned but I didn't have the first in my home directory.  I rename the second one and still it did not help.

This is sooooo annoying and I;m about to the point of just reformat/reinstall. blurg!!

---

### Post by Krytarik on 2011-09-28
> **sauce345 said:**
> Also I tried renaming the folders you mentioned but I didn't have the first in my home directory.  I rename the second one and still it did not help.
Ok, then also check for the file "~/.fonts.conf", and if present, try renaming it as well.

---

