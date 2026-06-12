---
title: "ATI cards not working with ubuntu?"
date: 2012-08-15
forum: General Help
---

### Post by ZepFloyd on 2012-08-15
so I installed a new graphics card into an old computer that needed one, figured I would just install that and then do a dual boot with windows/ubuntu. problem is I installed ubuntu and for whatever reason the desktop wont load. I get to the login screen but beyond that nothing.

searching around it looks like ATI vid cards seem to not work very well with ubuntu/linux. whats the deal with that? I mean I had to completely get rid of ubuntu because it just wouldnt load the desktop at all. 

i'm sure theres work arounds, but i'm a total linux newb thought ubuntu might be the easiest of the distros to install/play around with. to be fair the installation was rather simple, but yeah..cant use ubuntu on this machine i guess. 

i'm just kind of curious, has it been this way for awhile? I started thinking even if I had gotten ubuntu to work, what would happen if I had went to upgrade/update it might not work and then i'd be dealing with the problems all over again.

---

### Post by Aubergines on 2012-08-15
Really difficult for anyone to help without any specifics, all we have is:

a) you have an ATi card
b) it doesn't work

Not a whole lot to go by. It's a bit like saying "I have a car, and it doesn't work, how do I fix this?" Might be better if you mentioned what ATI card is it, whether the login screen was graphical or the commandline, whether there was any error messages appearing upon login etc etc, the more details you give the more chance someone can help.

---

### Post by ZepFloyd on 2012-08-15
> **Aubergines said:**
> Really difficult for anyone to help without any specifics, all we have is:

a) you have an ATi card
b) it doesn't work

Not a whole lot to go by. It's a bit like saying "I have a car, and it doesn't work, how do I fix this?" Might be better if you mentioned what ATI card is it, whether the login screen was graphical or the commandline, whether there was any error messages appearing upon login etc etc, the more details you give the more chance someone can help.


my bad,

graphics card is radeon 6670, login screen was graphical, though could see the screen getting some streaks/lines early, as it came up on the screen but would go away. i type in my password hit enter and then boom nothing. just the background and nothing else.

no error messages popped up or anything at any point. like i mentioned before even during the install everything went smoothly. the wizard/guide thing came up fine and everything. 

maybe that helps? i'm not too worried, i can always try another linux distro, from my google searches it seems ATI cards tend to cause problems with linux, i was just kind of curious if thats just the case across all distros and why that might be. thats all.

anything else? i can try to answer. thanks for the reply, appreciate it.

---

### Post by quadproc on 2012-08-15
> **ZepFloyd said:**
> 
i'm just kind of curious, has it been this way for awhile? I started thinking even if I had gotten ubuntu to work, what would happen if I had went to upgrade/update it might not work and then i'd be dealing with the problems all over again.

I have been using ATI cards (dual HD4870 in crossfire mode) for several years without any undue problems.  However, there is a release note for 12.04 that says that ATI's proprietary driver (fglrx) does not work correctly with 12.04.  So I never tried to use fglrx on 12.04 - I am waiting until this problem gets fixed, maybe in 12.04.1.

In the meantime, I am using Linux Mint 13.  This is almost the same as Ubuntu 12.04 except that Mint does not use Unity; I find that Unity is like a rowboat - I can't see where I am going and it takes a lot of motion on my part to achieve anything.  Mint 13 appears to be using fglrx according to xorg.conf but I don't yet have all of the graphics set up the way that I like.

One thing to note: if you do install fglrx then you _must_ uninstall it before installing a new one.  If you don't then you will run into bizarre problems ranging from peculiar behavior to a black screen and the need to reinstall the graphics stuff.

quadproc

---

### Post by ZepFloyd on 2012-08-15
> **quadproc said:**
> I have been using ATI cards (dual HD4870 in crossfire mode) for several years without any undue problems.  However, there is a release note for 12.04 that says that ATI's proprietary driver (fglrx) does not work correctly with 12.04.  So I never tried to use fglrx on 12.04 - I am waiting until this problem gets fixed, maybe in 12.04.1.

In the meantime, I am using Linux Mint 13.  This is almost the same as Ubuntu 12.04 except that Mint does not use Unity; I find that Unity is like a rowboat - I can't see where I am going and it takes a lot of motion on my part to achieve anything.  Mint 13 appears to be using fglrx according to xorg.conf but I don't yet have all of the graphics set up the way that I like.

One thing to note: if you do install fglrx then you _must_ uninstall it before installing a new one.  If you don't then you will run into bizarre problems ranging from peculiar behavior to a black screen and the need to reinstall the graphics stuff.

quadproc

i see..yeah i actually read that KDE desktops tend to jive with ATI cards, so i downloaded fedora 17 KDE and that booted right from the live cd. currently downloading mint 13 KDE. i'll see if that works.

but like you said, i'd love to be able to try out ubuntu 12.04 if i could get it working. i'd like to dabble with all different types of desktops/distros so i could determine what i might like best, if possible.

so did you just download mint 13 normally and its worked with your ATI cards? or it doesnt and you had to tweak to get it to work?

---

### Post by quadproc on 2012-08-16
> **ZepFloyd said:**
> 

so did you just download mint 13 normally and its worked with your ATI cards? or it doesnt and you had to tweak to get it to work?
I did a normal download of Mint 13 with MATE (personal preference here) and that worked normally.  I believe that the OS came up using the open source driver.  So, after a few days of other customizing to the OS setup, I downloaded a fresh copy of ATI's latest driver (now a bit over 100 MB) and installed that.  The graphics continue to work, but I have not yet found out how to enable wobbly windows or the rotatable cube.

I do know that the driver is working - for example, I can run fgl_glxgears at a dizzying speed.  But I have apparently not yet figured all of the details on the display setup.

I did encounter one thing about the Mint display - when I do the menu, sometimes the Applications section will rapidly alternate between two different lists of choices.  This can be stopped by putting the cursor in the right place.  This appears to be a bug, but before I report one I want to see if I can figure out what causes the problem.

quadproc

---

### Post by QIII on 2012-08-16
"ATI doesn't work with Linux."

Balderdash.  Stuff and nonsense.  FUD.  Internet myth persisting from a time long past.

I have ATI cards running on. Ubuntu, Xubuntu, Kubuntu, Fedora, etc.

On break and on my cellphone right now.  Can help you later tonight.  Don't bother with "nomodeset" option for now, but that would get you to the desktop to let you get set up.  If you are in no rush, I'll talk you through this later this evening if I can get to it.

---

