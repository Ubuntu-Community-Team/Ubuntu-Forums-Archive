---
title: "Limiting users from using WINE"
date: 2010-06-28
forum: General Help
---

### Post by hellz99 on 2010-06-28
Whats the best way to exclude specific users from using Wine?

---

### Post by Paddy Landau on 2010-06-29
I'd love to know why you'd want such a thing!

This would be something to do with the *sudoers* file. Sorry, I hardly know sudoers at all, but here is what I can tell you:

[LIST]
[*]Create a group that is allowed to use Wine (call it, say, [FONT=Courier New]winers[/FONT]).
[*]Assign every user that is allowed to use Wine to [FONT=Courier New]winers[/FONT].
[*]Read up on sudoers. Either use Google or get into a terminal and type [FONT=Courier New]man sudoers[/FONT]. You want to find out how to disallow running [FONT=Courier New]/usr/bin/wine[/FONT] for everyone except those belonging to the group [FONT=Courier New]winers[/FONT].
[*]Important: Use [FONT=Courier New]sudo visudo[/FONT] to edit the sudoers file.
[/LIST]
Good luck.

---

### Post by hellz99 on 2010-06-30
Why? Well, I'm trying to prevent installing or running any windows program by anyone but me.  I have a couple of win apps that I want to run, but dont want  every random exe downloaded to be installed.  

Thanks for your help, I'll look into.  
Seems like I should be able to just make a "winers" user and group, set the /usr/bin/wine to be owned by winer and set all people that can use wine into the winers group.

I'll try that.

---

### Post by Paddy Landau on 2010-06-30
> **hellz99 said:**
> Seems like I should be able to just make a "winers" user and group, set the /usr/bin/wine to be owned by winer and set all people that can use wine into the winers group.
That won't quite work. You'd have to make the file executable by the group but not by everyone.
```
sudo chgrp winers /usr/bin/wine
sudo chmod o-x,g+x /usr/bin/wine
```That's a clever idea, and should eliminate the need to use sudoers.

But...

I'm not sure what will happen when the next Wine upgrade comes through...

It will be safer to use sudoers.

---

### Post by hellz99 on 2010-06-30
oh right, i didnt think about upgrades.

---

### Post by Paddy Landau on 2010-07-01
> **hellz99 said:**
> ... I'm trying to prevent installing or running any windows program by anyone but me.  I have a couple of win apps that I want to run, but dont want  every random exe downloaded to be installed.
I recommend that you install [PlayOnLinux]("http://www.playonlinux.com/"), and use that. It's a sort-of front-end to Wine, making it dead easy to install, uninstall and run Windows programs. It hides the complexity of Wine from you.

PlayOnLinux also separates each Windows program, so that none interferes with another. In other words, each Windows program is installed as though it were in a different machine (unless you choose otherwise).

Do you realise that when you install a Windows program, it's in your user's account and has nothing to do with any other user's account? Even if your other users installed lots of Windows programs, none of them would affect you -- even if they were the same programs as you'd installed. It's very safe, especially with PlayOnLinux.

---

