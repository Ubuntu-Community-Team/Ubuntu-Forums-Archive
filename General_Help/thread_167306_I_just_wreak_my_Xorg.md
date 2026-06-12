---
title: "I just wreak my Xorg"
date: 2006-04-28
forum: General Help
---

### Post by Kakason on 2006-04-28
Hello Everyone. Today is a nice day until......
I was experimenting with Xorg by editing it files ( and forgot to backup - how silly ) anyways, I edit so much things and save it all, then I press ctrl + alt + backspace, then my X restarted. For some reason it couldn't start anymore, and I get an error. So I was wondering how do I reinstall my X?

Thanks

Murakami Kakason

---

### Post by Pablo El Vagabundo on 2006-04-28
Hey, 

Not to worry.. 

You can re configure your Xorg using the command:

sudo dpkg-reconfigure xserver-xorg

And it should be working for you.

Pablo

---

### Post by Kakason on 2006-04-28
I just tried that T.T and it didn't work. I think I installed something.

I get this error 
```

XFCom_i810 Version 3.3.6 / X Window System
( protocol Version 11, revision 0, under vendor release 6330 )

Operating System Linux 2.2.14-5.0 i686 [ELF]

Configured drivers
SVGA: server for SVGA graphics adaptors
i810, 810-dc 100, i810e, i815, generic
(using VT volume number 7)

Could not find config file
- Tried
 /etc/XF86Config
 /usr/X11R6/lib/X11/XF86Config.ubuntu
 /usr/X11R6/lib/XF86Config

Fatal server error:
No config file found!
Note the X server no longer try look for XF86 Config in $HOME

```

EDIT: Does someone know how to reinstall X? If you know can you show/tell me how

---

