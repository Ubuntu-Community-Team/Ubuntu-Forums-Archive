---
title: "Invisible cursor! (desperate, please help)"
date: 2009-11-23
forum: General Help
---

### Post by MindFusion on 2009-11-23
[B]Hello everyone! I need some urgent help here. I have an Acer Aspire (running ubuntu 9.04) laptop, which i plugged onto a Acer AL1721 monitor. Since Ubuntu automatically installs drivers, i thought i'd have no problem at all with just plugging on this monitor. However ...


When i booted up the laptop with the screen adapted to it, a grey monitor prompt pops up and dances on the screen saying: "Input not supported". 


My Ubuntu logging in screen then loads and i have no more messages, my USB keyboard works perfectly fine, but i have a problem with my mouse. My cursor is completely invisible! If i play around a bit with my mouse i can see that some areas on the screen gets highlighted, so the mouse IS supported but it DOESN'T show any cursors. I know use the function with Ctrl to show the cursor, but this only lasts 2 seconds and i cannot go on like this, especially because other family members need to use this computer ...


does anyone have any idea please????
[/B]

---

### Post by MindFusion on 2009-11-23
HELP ME 

i will keep spamming untill i get my answer

---

### Post by koenn on 2009-11-23
> **MindFusion said:**
> HELP ME 

i will keep spamming untill i get my answer

and I will ignore you when you behave like that.

---

### Post by MindFusion on 2009-11-23
Why? I really really need the help while there are less important subjects going on here... i know there are a lot of intelligent whizzkids on these forums and all i ask is some of their time. 

If i don't spam, then my topic will have no answer and then i'm stuck with this mouse problem, so how could you criticize me for behaving like that?

---

### Post by Cheesemill on 2009-11-23
What makes your problem more important than anyone elses?

We all volunteer our help in our spare time, I'm sure most people on here have more important things they could be doing.

PS - It is forum rules to only bump after 24 hours.

---

### Post by MindFusion on 2009-11-23
So do you know the answer or are you just randomly critisizing?

---

### Post by mrebanza on 2009-11-23
son of a Buntu - -  - - same problem . . . . . 9.10 - acer - plugged up to a phillis screen . . . . eveything working fine than BAM after reboot I get invisable mouse .. . . . . tabing around firefox to type this . . . . . looks like no help in sight . . . . reinstalll??? wtf y not

---

### Post by FreezWay on 2009-11-23
i dont know the solution but there are also some people who look for posts with 0 replies.

---

### Post by MindFusion on 2009-11-24
Well can you redirect me to someone who does know... i mean i'm sorry if i might sound rude but my sister is seriously pissed off on me because i told her ubuntu was so much better and now we don't even see the cursor! 

PLEASE HELP

---

### Post by Darael on 2009-11-24
Alright, look.  I can't say I condone spamming to get attention - it actually makes people less likely to respond - but I'll do my best to suggest something: try changing your cursor theme.  This may be a little tricky with an invisible cursor, but I'm sure you can do it!  You'll need to go system->preferences->appearance, and click the "customise" button near the bottom.  Then you'll need to go to the "pointer" tab, and choose another theme.  This will probably need an X restart to take effect, so log out and log in again, and see if the problem is fixed.

Oh, and if it's easier to use the keyboard, you can go <alt>+<f1>, <right>, <right>, <down>, <right>, <down>, <enter>, <alt>+u, <left>, <tab>, choose a new cursor theme, and <alt>+c.  Then you can log out, and in again.

That's the best I can come up with, if it doesn't work I have no idea, sorry.

---

### Post by screaminfakah on 2009-11-24
[http://bl1nk.com/2009/07/mini-note-video-with-ubuntu-9-0-4/comment-page-1/#comment-83](http://bl1nk.com/2009/07/mini-note-video-with-ubuntu-9-0-4/comment-page-1/#comment-83)

---

### Post by MindFusion on 2009-11-24
Appreciate the try, but that's the first thing i tried when i encountered the problem... didn't work for me as well.

Being a bit more specific: a monitor message pops up when booting up and on the logging in screen saying; INPUT NOT SUPPORTED, which then disappears when i'm logged on, but the mouse is gone nonetheless.

---

### Post by MindFusion on 2009-11-24
Oh sorry, didn't see that comment. What does he mean with 'section "device"' ?

---

### Post by Darael on 2009-11-24
The text in that comment (included below) needs to be added to the config file /etc/X11/xorg.conf.  You can edit this by pressing alt+f2 and running "gksu gedit /etc/X11/xorg.conf" - unless you're on Kubuntu, in which case replace "gksu gedit" with "kdesu kate".  The addition should be as follows:
```
Section &#8220;Device&#8221;
Identifier &#8220;Configured Video Device&#8221;
Option &#8220;ActiveDevice&#8221; &#8220;LCD, CRT&#8221;
Option &#8220;SWCursor&#8221; &#8220;on&#8221;
EndSection
```

---

### Post by MindFusion on 2009-11-24
*Adds you both to my official heroes list*

Thank you so much!!!!!!

---

### Post by Darael on 2009-11-24
1) You're very welcome.
2) I take it it worked, then?

---

### Post by screaminfakah on 2009-11-24
No problem.  I love Google!!

---

### Post by MindFusion on 2009-11-26
Yes, it did work (: The mouse is still a bit laggy though (it twitches a couple of times) but i'm glad it works, finally.

---

### Post by flomail on 2012-01-22
hello, same problem, it seems your solution worked for me too : thank you !

---

### Post by findelmundo on 2012-04-25
Hmmm... Had the same problem (Ubuntu 11.10 (32bit) on HP Compaq 6715b). 

Edited the xorg.conf file, as suggested, and now Ubuntu will not start (or it takes forever?). I figure the mahine is not really hanging, since pressing Ctrl+Alt+Del makes the machine restart, but it doesn't seem like anything is going to happen anytime soon. There is text on the screen, and the last line says: * Checking battery state...    [OK]

I hope I don't have to reinstall Ubuntu, but if I have to, I'll do it...
:confused:

---

