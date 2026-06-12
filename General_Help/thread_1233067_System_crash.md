---
title: "System crash"
date: 2009-08-06
forum: General Help
---

### Post by GoldNinja on 2009-08-06
Hi! I was randomly changing system settings for my Kubuntu and when I pressed 'apply', the computer froze. 
I of course turned the power off (from the power button in pc) and then tried restarting. 
It went on just fine, I could log in on my user account and then the splash screen appeared (with the stuff in the middle [I still haven't figured out what they actually do xD]) but then it freezes and doesn't proceed any further.
So my problem is, to put it simple, that my pc does not start. :confused: 
I know the fault is my settings (the fact that I changed them wrong (?)), but I have no idea of how to get the pc to a usable stage so that I could change them! 
I appreciate any help or advice you can give me! School's about to start again and I really need my pc to do my schoolwork properly. :(
 
EDIT// Oh when I say freezing, I mean that nothing happens but mouse can still move like it moves normally. It's just that nothing happens no matter what I click or what buttons I press.

---

### Post by GoldNinja on 2009-08-06
The settings I changed were desktop -settings. I believe I allowed special effects for the desktop and I picked a lot of those effects. I know it might've frozen because I picked so much stuff and that it would've taken a while to apply the changes but I didn't realise it yesterday when this happened so I kinda panicked and turned the pc off without waiting for the effects to be applied.
(I know it's selfish to make a new post just to get my thread back up in the threads list, but I really really need help)

---

### Post by GoldNinja on 2009-08-06
I will once more -in hope of some help- lift this topic up.. Please someone help me! I really am helpless when it comes to computer stuff.

---

### Post by gunksta on 2009-08-06
Let's take this one step at a time. Do you remember what settings you changed? This could be an important piece of information. Note: If you are "helpless" with computers, randomly fiddling with operational settings could be a high-risk hobby. I'm not going to tell you what to do, since it's none of my business, but it's something to consider.

I'd also like to figure out if the computer is freezing or is KDE? To find out, we're going to (try to) drop over to another tty.

Press **Ctrl-Alt-F1**

This may take a second or two (or 4 or 6), that's ok. It should eventually take you to a plain black screen with white letters. Try to log in with your user name and password (like you always do).

If you are able to get to this screen, your computer isn't entirely frozen, but KDE may be. This is bad but not as bad as a full system freeze.

If you are able to log in at the black screen (tty1) I want you to run the command 'ps'. At the command prompt you will type in:

```
ps
```

The top line or two are the applications / programs that are using the most system resources (processor, RAM). What are they? How much CPU time are they using?

To get out of ps, just hit the 'q' button.

I hope you are able to get to a tty, but if not, hopefully you will recall what you were playing with.

---

### Post by GoldNinja on 2009-08-06
> **gunksta said:**
> Do you remember what settings you changed? This could be an important piece of information. Note: If you are "helpless" with computers, randomly fiddling with operational settings could be a high-risk hobby.
 
If you are able to get to this screen, your computer isn't entirely frozen, but KDE may be. This is bad but not as bad as a full system freeze.
 
If you are able to log in at the black screen (tty1) I want you to run the command 'ps'. At the command prompt you will type in:
 
```
ps
```
 
The top line or two are the applications / programs that are using the most system resources (processor, RAM). What are they? How much CPU time are they using?

 
I changed some Desktop settings. I added some effects like window exploding when closed and window falling apart when closed and window shaking when moved and stuff like that. I know I shouldn't touch things but I honestly thought they weren't anything serious.
 
And I managed to get into that screen and was able to log in too. After writing that command 'ps', this is what showed up:
PID TTY TIME CMD
2779 tty1 00:00:00 bash
2693 tty1 00:00:00 ps

---

### Post by gunksta on 2009-08-06
> **GoldNinja said:**
> I changed some Desktop settings. I added some effects like window exploding when closed and window falling apart when closed and window shaking when moved and stuff like that. I know I shouldn't touch things but I honestly thought they weren't anything serious.

I may have been too harsh. Certainly changing some simple settings in Kwin should not cause the whole computer to melt. I was fishing to see if you'd adjusted something more significant. That being said, I think this is useful information.

 
> **GoldNinja said:**
> And I managed to get into that screen and was able to log in too. After writing that command 'ps', this is what showed up:
PID TTY TIME CMD
2779 tty1 00:00:00 bash
2693 tty1 00:00:00 ps

I'm glad you could get in. Unfortunately, I seem to have had a momentary loss of higher brain function, because ps isn't what I needed you to run.  (This is entirely my fault.) I actually need you to run 'top'

```
top
```And tell me what's across the top. 'ps' is a great tool but not for what we are doing. I'm going to go over in a corner now and feel silly.

I suspect that you will find xorg causing the problems, with a high CPU load. What sort of video card are you using? I wonder if perhaps you asked the video card to do something that it A) can't do OR B) the driver is a buggy piece of stuff and it's causing you heart-ache.

Either way very fixable. The nuclear option would be to delete the ~/.kde/ folder. But, I think we can be a little more selective than that, but before I give you the shell commands to clean out kwin's configuration I want to make sure that there is a good indication that this is in fact the problem.

---

### Post by GoldNinja on 2009-08-07
> **gunksta said:**
>  
 
I suspect that you will find xorg causing the problems, with a high CPU load. What sort of video card are you using? I wonder if perhaps you asked the video card to do something that it A) can't do OR B) the driver is a buggy piece of stuff and it's causing you heart-ache.
 
I wrote 'top' and the output was a list of commands as you said. But the list changed every 3 seconds so I couldn't copy it properly. Also the values for them changed a lot. But I picked up two %CPUs and they were;
0.3 Xorg
5-11 ath5k_pci
 
The values changed a lot, especially for that ath5k_pci and the list changed too. Nonetheless, none of the command %CPUs I saw were any bigger than 17 (I didn't see what command had that value though, the list updated too fast).
 
Oh and I'm sorry, but I don't know what kind of video card I have. I know nothing about that stuff. :( Uh, I'm not sure if it's of any help, but at least I know that my pc (or video card?) doesn't support OpenGL. Maybe that could help you with my video card? At least I thought it might have something to do with my video card.. Oh and I thank you for being able to put up with me and my problem! Really, thanks. :D

Oh and get back from that corner, no need to sweat over wrong one command! ;)

---

### Post by GoldNinja on 2009-08-07
Oh and I can always try and copy more commands and their CPU usage if those two weren't enough.. I can also try and check what video card I possess if necessary. :D

---

### Post by GoldNinja on 2009-08-08
I'm getting really desperate.. How do I delete that kde folder? And does my pc work properly after that or is there something else I have to do after that? And does it delete any other folders? I want to preserve everything I currently have in Public, Documents and Pictures folder. Oh and Kopete logs too. 

I don't care who will help me and you don't have to answer all questions, anything will do! Please someone help, I just might start crying otherwise. xD

---

### Post by gunksta on 2009-08-08
I wasn't really expecting you to copy the whole list. That would be pretty crazy. I just wanted to know what was consistently the top 1-2 items on the list.

This is what is happening, as I currently understand it. You boot your computer and KDM (the log-in manager) comes up. You type in your user name and password and try to log in. When you do that, the computer tries to start KDE but fails and the computer appears to hang. We know it's not completely frozen because you can log in via tty1, but something is preventing KDE from starting. 

If you can see the normal log-in screen, your video card driver is not the immediate problem. We'll play with that AFTER we get you back into KDE.

Assuming all of this is correct, here are two suggestions. Try #1 BEFORE you try #2.

**Idea #1**

[LIST=1]
[*] Boot the computer.
[*]When you come to the Log-in Screen, ignore it completely. Do **NOT**
[*]Ctrl-Alt-F1
[*]At the black screen enter your user name and password.
[*]Use the following commands:
[/LIST]

[LIST]
[LIST]
[*]rm ~/.kde/share/config/kwin*
[*]rm ~/.kde/share/config/session/kwin*
[/LIST]
[/LIST]


Now use Ctrl-Alt-F7 to return to the logn-in screen. Enter your user name and password.Hopefully this will work. If your computer still hangs, we can try something more aggressive.

**Idea #2**

[LIST=1]
[*] Boot the computer.
[*]When you come to the Log-in Screen, ignore it completely. Do **NOT**
[*]Ctrl-Alt-F1
[*]At the black screen enter your user name and password.
[*]Use the following command:
[/LIST]
 
[LIST]
[LIST]
[*]mv ~/.kde/ ~/kde-old
[/LIST]
[/LIST]

WARNING: This command will wipe out many of the customized KDE settings. If you've set up a calendar, it won't work anymore (until we fix it). If you've changed your theme, bookmarks in Konqueror, etc. All of this will be moved to ~/kde-old. If this gets you up and working, you can start moving the contents of 

~/kde-old/share/apps/*    to     ~/.kde/share/apps

You can use dolphin to do this. You just need to tell it to let you view hidden files first.

Let me know how this works for you.

---

### Post by GoldNinja on 2009-08-08
> **gunksta said:**
>  
Let me know how this works for you.
 
I am forever grateful to you! The first idea worked and I am now able to log in on KDE! Thank you so much, really! Thank you, thank you, thank you, thank you, thank you, thank you! Really, thanks!

---

