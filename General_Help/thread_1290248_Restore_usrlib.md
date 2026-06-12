---
title: "Restore usr/lib"
date: 2009-10-13
forum: General Help
---

### Post by fowie on 2009-10-13
I'm an idiot.  I know.  I'm sorry, but I am.  I was trying to compile some software and the libraries were installed into my local directory instead of to /usr/lib, so I tried to make a symlink.  There were a few .a files, so instead of doing them one by one I tried:
```

sudo ln -s *.a /usr/lib/

```
(You're probably already laughing, I know).  That didn't work, it just made a *.a file in my /usr/lib/ folder.  Without thinking (here's the idiot part) I decided to get rid of that file by typing (drumroll please)
```

sudo rm /usr/lib/*.a

```
and realized my folly immediately _after_ pressing Enter.  

So, is there any way to restore my /usr/lib/*.a files?  I haven't rebooted yet for obvious reasons...

---

### Post by Intrepid Ibex on 2009-10-13
Humm.. can't think of anything else than reinstalling every package on your system.. with ubuntu especially that's gonna take some time ^^.

Ps. No, you are not stupid. There are much much bigger "stupidities" done by thousands of linux users - including me.

If you must know *\and even if you don't want to, I'll tell it anyway ^^\*, my biggest mistake was actually running "[COLOR="Red"]*[SIZE="2"]rm -rf *[/SIZE]*[/COLOR]" from / (as root - if I'd have done this on the other terminal where I was logged in as user, I'd have done that command from the right place and even with the correct permissions.. even though it wouldn't have mattered anyway) .. :-k.

Quite frankly it is funny to remember that kinda stuff.. I did that again 2 months ago with ubuntu (this time I WANTED TO :D) because I got fed up with it so badly, now using Arch and loving it - but I mean this was just my story, I'm not telling you or anyone to start hating Ubuntu or even to switch to Arch as it really does require huge amount of learning for most users (for everybody else it requires "only" 'a lot' of learning) because you basically build the system from scratch. You only have kernel, package manager, internet and that kinda critical stuff (the idea is "freedom of choice", not "haha, build me yourself") :).

**OBS.** To prevent any damage, new users **DO-NOT** run that command(!). It will recursively remove every single file you have on the folder you are running the command from (so **never** run that command, unless you **really** know what you are doing).

---

### Post by fowie on 2009-10-13
Sounds like fun.  I know someone who did that as a student employee at the university on the server hosting all of the faculty backups...he quit.

Since I didn't delete the entire lib directory, and in fact only deleted the .a files, I'm thinking I might actually be ok.  .a files are only used to link into files while compiling, they're not used by precompiled programs, so I should be fine, and I'll just run into problems of not finding libraries when I try to do a compile--at which point I can reinstall the packages relating to the missing files...right?

---

### Post by Intrepid Ibex on 2009-10-14
Uh, I red/remembered you deleted _every_ file in '/usr/lib'.

Also it sounds like a pretty good idea to me that you would reinstall the packages when you need them because you probably won't need them on the booting process.. and of course you will actually get the other ones in the end anyway by updating and stuff like that.

---

