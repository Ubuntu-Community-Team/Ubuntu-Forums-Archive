---
title: "Terminal at startup!"
date: 2010-01-17
forum: General Help
---

### Post by Moustaffa on 2010-01-17
Hi,

I'm experience a very annoying problem: when I boot my laptop it goes to a Terminal screen, before reaching the Ubuntu login screen (somtimes I'm even stuck at the Terminal screen and have to reboot and hope I'll get to the login screen the next time).

At the Terminal screen it asks me to login; after I do so, it gives a few lines of output and then waits for me to enter another command line in the Terminal.
Doing ALT+F7 doesn't take me to the login screen.

What the **** am I supposed to do??? This is really driving me insane!

---

### Post by cariboo on 2010-01-17
It sounds like you have a video driver problem.

When you are at the prompt what happens when you type:

```
startx
```

Also could you provide some details, like what graphics adapter you computer has.

---

### Post by Moustaffa on 2010-01-17
> **cariboo907 said:**
> It sounds like you have a video driver problem.

When you are at the prompt what happens when you type:

```
startx
```

Also could you provide some details, like what graphics adapter you computer has.

I doubt it's a video driver problem: on another forum they thought the same thing and I messed up my graphcard with their command tips, and made it work again after a long session of stressful searching and typing and booting. I have Compiz fusion working perfectly, I seriously doubt it's the graphcard...

When doing startx I get one of 2 things: either it's a white screen, or it's a black screen. Never the desktop or GDM

---

### Post by zero-n on 2010-01-17
Try the recovery mode and choose fix x (i don't remember it well )

then at the login screen choose gnome as your session



i hope this will work for you

---

### Post by Moustaffa on 2010-01-18
> **zero-n said:**
> Try the recovery mode and choose fix x (i don't remember it well )

then at the login screen choose gnome as your session



i hope this will work for you


On another forum I posted the same problem, there someone told me I should go to System > Preferences > Startup programs > Options
and make sure "remember ... " is crossed out.
Well, in my case it was in fact crossed, so I crossed it out and now we play the waiting game.
So far I rebooted once and I went straight to the GDM; so far so good.

If I don't post anything anymore, it means it worked and you can see this as fix as a good solution if you would ever experience this problem!

Greets

---

### Post by Barriehie on 2010-01-18
When you get it to boot likes it's supposed to I'ld save the session!

---

### Post by zero-n on 2010-01-18
[]("http://ubuntuforums.org/member.php?u=745082")Moustaffa if you problem is solved please mark your thread as SOLVED

---

