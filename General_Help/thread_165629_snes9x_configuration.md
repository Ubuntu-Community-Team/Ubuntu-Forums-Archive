---
title: "snes9x configuration?"
date: 2006-04-24
forum: General Help
---

### Post by dracule on 2006-04-24
Ive looked everywhere for a configuration meathod for snes9x. ok here is my snes emulation troubles.
snes9x- sound good, resolution is horrible when you "maximize" but found no fullscreen mode

zsnes-resolution is great on fullscreen mode but sound is crappy and plays the same track 2x overeachother about 2 seconds abart so that is crappy.

I found no way of editing snes9x. please help!!!

---

### Post by escape on 2006-04-25
Is this through wine or is it a native version of the snes emulator?

---

### Post by dracule on 2006-04-25
[QUOTE=escape]Is this through wine or is it a native version of the snes emulator?[/QUOTE]
got it through synaptic

---

### Post by dracule on 2006-04-26
Hello? anybody there? This is the first time my question hasnt been answered in under a day. please help me configure snes9x that i got through synaptic.

---

### Post by dracule on 2006-04-26
Hello? anybody there? This is the first time my question hasnt been answered in under a day. please help me configure snes9x that i got through synaptic.

---

### Post by DoktorSeven on 2006-04-26
Have you tried **gsnes9x** or **snes9express**, frontends for it?

They may be in the Multiverse repositories here so you may need to enable that in your Synaptic sources list... (search the board if you need help)

Edit: Interesting.  Both frontends error out when fullscreen box is checked.  The option may have changed which means that the frontends would only work if a proper source version is compiled.

---

### Post by dracule on 2006-04-26
i found out that those front ends need root access in order to do fullscreen. i was trying them forever untill i found that out. ill try and enable root access and get back to you whether it worked or not.

---

### Post by dracule on 2006-04-27
the code in the readme wont work. please point me to a code that can enable root privalages for gsnes and snes9x

---

### Post by Trevor2004 on 2006-04-27
[QUOTE=dracule]Ive looked everywhere for a configuration meathod for snes9x. ok here is my snes emulation troubles.
snes9x- sound good, resolution is horrible when you "maximize" but found no fullscreen mode

zsnes-resolution is great on fullscreen mode but sound is crappy and plays the same track 2x overeachother about 2 seconds abart so that is crappy.

I found no way of editing snes9x. please help!!![/QUOTE]

I'm suprised you even got snes9x to display in fullscreen mode, from things that i have read on the snes9x fourms, fullscreen mode is broken (or at least mostly) in the latest versions 1.42-1.43

this post states that you must use a real root account to use fullscreen mode and ubuntu's root account is disabled by default
[http://www.snes9x.com/phpbb2/viewtopic.php?t=1081](http://www.snes9x.com/phpbb2/viewtopic.php?t=1081)

when i compiled the 1.43 source everything worked great but i couldnt use fullscreen. maybe i'll play with the synaptic version and see what happens.

---

### Post by dracule on 2006-04-27
i didnt get it to full screen mode. all i did was stretch it out to use the whole screen, but it was still in the window.... but when i stretched it out it stretched the pixels too. i kinda fixed this problem with the SuperEagle2x filter but the enlarged pixels are still there. 
do you think running the windows version under wine would help? or would it be too slow. 
I enabled the root account. even tried logging in graphically(which was fine untill the screen started disenagrating). but logging in graphically still didnt solve the problem it would start the game and then exit. I changed all the "owner" to my account and that didnt help. 

I would use other emulators but there are worse problems than just bad pixelization. 

ZSnes: sound "echoes" over itself and is unbarably bad. 
Xmess: have no idea how to work it. i try to start it in terminal and just about everywhere else but it doesnt start up. so not having it start up is an extremely bad problem....

if anyone knows how to solve those emulation problems please help me!!!!

im just about ready to try another distro!!!!

---

### Post by Trevor2004 on 2006-04-27
dont even bother with XMESS for SNES emulation, it is still in the preliminary stages of development, meaning most roms wont work, and the ones that do probally wont have sound. 

I couldnt get ZSNES to compile correctly on my Athlon 64 i kept getting some error saying the code was incompatible with the "x86_64" architecture.

I am pretty sure that snes9x has some scaling modes that might make your streched game look better but i may be thinking of the filter you applied
this thread might help
[http://www.snes9x.com/phpbb2/viewtopic.php?t=1380](http://www.snes9x.com/phpbb2/viewtopic.php?t=1380)

i gave up on all of thoes, sometime this week i am planing on trying BSNES it is somewhat of a new emulator it has VERY high system requirements because is focuses on game accuracy rather than speed and compatibility 
[http://byuu.cinnamonpirate.com/?page=bsnes](http://byuu.cinnamonpirate.com/?page=bsnes)

the problem isn't really with ubuntu its with the emulator, some emulators are coded for windows systems then ported over to linux, which just dosent always work properly. and emulators in general dont get much devlopment attention, usually 1-3 people coding in their spare time. and they usually dont have a wide hardware platform to test with. that among other things is the real problem.

---

### Post by Artemis3 on 2007-05-01
> **dracule said:**
> zsnes-resolution is great on fullscreen mode but sound is crappy and plays the same track 2x overeachother about 2 seconds abart so that is crappy.

I found no way of editing snes9x. please help!!!

I found the solution for zsnes: you need to install the package **libsdl1.2debian-oss** this will uninstall libsdl1.2debian-alsa.

This also fixes the noise crackling problem with Battle for Wesnoth and probably all sdl programs.

---

### Post by naaman on 2007-12-16
I got rid of the crackly, jumpy sound by upping the rate using snes9express to 29300 Hz (option 5 ie. snes9x -r 5 -pal -y3 ROMFILE)

---

### Post by picometer on 2007-12-16
Try this:

[http://www.snes9x.com/phpbb2/viewtopic.php?p=22874](http://www.snes9x.com/phpbb2/viewtopic.php?p=22874)

---

