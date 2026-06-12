---
title: "How to boot with minimal graphics settings?"
date: 2009-09-29
forum: General Help
---

### Post by butterbridge on 2009-09-29
I am running 9.04 and was fiddling with the visual effects settings to make things look pretty and I think I messed it up :( I was playing with effects in the CompizConfig Settings Manager.  When i selected the blur windows option, every window turned into a black box so I can't see what i'm clicking and now have no way to disable the blur windows setting which is causing me trouble.

Is there a way to force ubuntu to boot into safe mode like windows with minimal graphics settings?  If I can boot into ubuntu with the visual effects set to low, I hope I could go into CompizConfig and hopefully turn off the blur windows effect.
If need be I can reinstall ubuntu, but id rather not.  I dont have too much data id loose since most of it is backed up on my windows partition, but still it is a hassle to reinstall an OS especially with midterms later this week.
Any help would be appreciated, thanks :)

I am a noob so you have to break down the instructions, and I doubt I can acess a terminal easily.  If i can manage to click blindly in the menu and open one I can't see what is in the window so unless its a simple command I probably won't be able to use a terminal.  
btw, is there a keystroke that can open the terminal instead of having to go through the main menu each time?

---

### Post by tom66 on 2009-09-29
Press Alt-F2, you'll probably get a black window, then type exactly "metacity --replace", press enter, you're now in basic graphics mode, disable blur, then press Alt-F2 and type "compiz --replace" and press enter.

Make sure you don't typo it, because otherwise it won't work...

---

### Post by butterbridge on 2009-09-29
thank you thank you thank you! :D
Problem solved!
I'm slowly learning little by little...

---

