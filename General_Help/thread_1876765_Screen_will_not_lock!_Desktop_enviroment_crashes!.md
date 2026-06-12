---
title: "Screen will not lock! Desktop enviroment crashes!"
date: 2011-11-06
forum: General Help
---

### Post by Finitemight on 2011-11-06
Hey all,

I have two more problems with this distribution...

1) The Screen will not lock when i press "Ctrl+alt+L". When I do press those together, i get the message as follows:

"Couldn't execute command: gnome-screensaver-command --lock
Verify that this is a valid command."

2) Sometimes the desktop explorer crashes. The best way I can describe it is by comparing it to the windows "Explorer.exe" process that runs in windows. Normally in windows if this happened (if the desktop environment crashed), i would simply go to "run" and then type in "explorer.exe" to get it functioning again.

Please help!

---

### Post by Finitemight on 2011-11-08
Anyone?

---

### Post by Rodney9 on 2011-11-08
To lock your screen you can follow this tutorial -

[http://forum.lxde.org/viewtopic.php?f=8&t=31300](http://forum.lxde.org/viewtopic.php?f=8&t=31300)

and for many other how-to's, faq and screen-casts for Lubuntu look here -

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

as to the desktop crashing we will have to wait for someone with further knowledge than I, you could post this problem in the above Lubuntu One Stop Thread.

Rodney

---

### Post by Finitemight on 2011-11-09
Read the thread, and found out how to lock the screen... it is fairly simple to do, but it requires you to actually alter code. Hopefully it will be default in a future incarnation.

Desktop environment does still on occasion randomly stop functioning properly. The tool bar at the bottom will sometimes have the icon on it disappear.

Thanks for the help nonetheless

---

### Post by Rodney9 on 2011-11-09
Your welcome, if you keep having that problem post in the Lubuntu One Stop Thread, where other Lubuntu users may help.


Rodney

---

### Post by amjjawad on 2011-11-09
> **Finitemight said:**
> 2) Sometimes the **desktop explorer** crashes. The best way I can describe it is by comparing it to the windows "Explorer.exe" process that runs in windows. Normally in windows if this happened (if the desktop environment crashed), i would simply go to "run" and then type in "explorer.exe" to get it functioning again.

Please help!

Hi there,

Are you referring to PCManFM or Openbox? I'm sorry but could you please be more specific? 
I understand you are trying to make it easier by explaining it in Windows way but for me, that made it more hard to understand - sorry.

---

### Post by amjjawad on 2011-11-09
> **Rodney9 said:**
> if you keep having that problem post in the Lubuntu One Stop Thread, where other Lubuntu users may help.
Rodney

@OP

Since you already have started a thread (this one), then keep it running and me and Rodney are already on it. More could jump in to help if needed.

In future, please start a new thread and post **the link (NOT the problem itself)** on [Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755"). Or, feel free to start a new thread and PM me ONLY the link of your thread and I'll be more than glad to help :)

Thank you!

---

### Post by Finitemight on 2011-11-09
Ok i will try to post the link within the lubuntu one stop thread in the future.

I really am unsure as to whether it is open box or the PCManFM (think it might be PCManFM). 

I included a picture and circled the places in which the problem would occur.

The circled  icons (in red) are the icons that would either disappear or be totally unclickable. I would have to reboot or log out and log back in in order to get them to function properly. I will try and get a picture of them when they are improperly functioning.

The icons would also be slightly askew in their position, or disappear entirely whenever this random trouble occurred.

---

### Post by whatthefunk on 2011-11-09
That would be an LXpanel bug I believe.  Next time it happens, open a terminal and type the following:
```
lxpanelctl restart
```
That might prevent you from having to restart.

---

### Post by amjjawad on 2011-11-09
> **whatthefunk said:**
> That would be an LXpanel bug I believe.  Next time it happens, open a terminal and type the following:
```
lxpanelctl restart
```That might prevent you from having to restart.

+1

Let's go for this first and then see what else we can do. I haven't heard about that before as far as I can remember.

---

### Post by amjjawad on 2011-11-09
> **Finitemight said:**
> Ok i will try to post the link within the lubuntu one stop thread in the future.
Thank you :)

> I really am unsure as to whether it is open box or the PCManFM (think it might be PCManFM). 

That should be LXPanel as you explained.

> I included a picture and circled the places in which the problem would occur. 
The circled  icons (in red) are the icons that would either disappear or be totally unclickable. I would have to reboot or log out and log back in in order to get them to function properly. I will try and get a picture of them when they are improperly functioning.

Only these icons? what about the desktop? is it functional? when does it happen? anything specific you do which can produce this issue? a bug must only be addressed as a bug if someone else can produce it. I need more details so I can try to produce it.

---

### Post by Finitemight on 2011-11-09
> **amjjawad said:**
> Thank you :)


That should be LXPanel as you explained.



Only these icons? what about the desktop? is it functional? when does it happen? anything specific you do which can produce this issue? a bug must only be addressed as a bug if someone else can produce it. I need more details so I can try to produce it.

It happens randomly, so i am unsure as to how to reproduce it. As of late, nothing has occured (maybe it had something to do with the recent updates?).  When it does happen , now that i know i have a place to come to actually have the problem solved, I will take screen caps (if possible) and go from there.

---

### Post by Finitemight on 2011-11-10
Ok I got the desktop toolbar to (unfourtunately) crash... Though I still am unsure as how I came to it.
I will note that the battery was towards the end of dying on me, if that is at all relevant. Also noteworthy: Two battery icons are perpetually shown even though my ipod has been disconnected. I did not connect my ipod during this. I have not connected my ipod for days now, and yet the second battery icon (which when clicked on said it was reading the ipod power remaining when I had it connected days ago) is still prominently displayed.

I attached some photos.

_In example 5:_ The environment goes all kinds of crazy. I try to click on the calendar button, and i get shown a grey box. The folder that contains the movie "shutter island" is not minimize correctly at all within the bottom toolbar. Although I could not screen capture this, whenever I clicked on the firefox button, it would instead open up the folder containing the "shutter island" movie.

_In example 4_: Nearly all icons have dissapeared at this point. Clicking on the far right of the blank toolbar does (thankfully) allow me to get to the prompt to logout and log back in. I decide not to, so I can continue taking photos. I was unable to capture this as well, but canceling the prompt made half of the bottom screen turn Grey!

_In example 3_: The folder for "shutter island" is opened up. I had to click random spots on the toolbar in order to get this folder back open from the minimized version in the toolbar. 

_In example 2_: Firefox and the folder are still opened, but are not indicated on the bottom toolbar at all.

_In example 1:_ Randomly clicking on the far right of the toolbar to try and log out. The grey bar is what I can only imagine to be the calendar pop out.

I was still able to click on the word documents and the folders to open them, amazingly. 

I wonder what the problem is? I hope I helped in elucidating my quandry a bit further

---

### Post by amjjawad on 2011-11-10
I was about to suggest these two commands:

```
ubuntu-bug lxpanel
```and

```
ubuntu-bug pcmanfm
```But something is telling me it's a bad install. Some questions and answers will enlighten us:

1- Is this a fresh new installation? or is it an upgrade from 11.04?

2- After downloading lubuntu image (iso file), have you checked MD5SUM? Lubuntu One Stop Thread > Section G
If you still have the lubuntu iso, please check MD5SUM.

3- In case this is a new fresh installation, what kind of media have you used to install? Live-CD or Live-USB?

4- Have you tried the suggested solution in [post #9]("http://ubuntuforums.org/showpost.php?p=11442132&postcount=9")?

5- What are the hardware specifications of your machine? 

Thank you!

P.S.
Kindly run the above two commands and describe your problem in details but try to make it as short as possible but in the same time, informative as possible :)

---

### Post by Finitemight on 2011-11-10
> **amjjawad said:**
> I was about to suggest these two commands:

```
ubuntu-bug lxpanel
```and

```
ubuntu-bug pcmanfm
```But something is telling me it's a bad install. Some questions and answers will enlighten us:

1- Is this a fresh new installation? or is it an upgrade from 11.04?

2- After downloading lubuntu image (iso file), have you checked MD5SUM? Lubuntu One Stop Thread > Section G
If you still have the lubuntu iso, please check MD5SUM.

3- In case this is a new fresh installation, what kind of media have you used to install? Live-CD or Live-USB?

4- Have you tried the suggested solution in [post #9]("http://ubuntuforums.org/showpost.php?p=11442132&postcount=9")?

5- What are the hardware specifications of your machine? 

Thank you!

P.S.
Kindly run the above two commands and describe your problem in details but try to make it as short as possible but in the same time, informative as possible :)


1) It is a fresh new installation. I did not upgrade from ubuntu or lubuntu 11.04. I formatted those drives, and then installed it. I wanted to make sure that there would be no errors.

2)I no longer have the lubuntu iso, but i will get on obtaining it when i can and doing that.

3)I utilized a cd to install.

4) The problem has not occured frequently enough for me to try out what was suggested in post 9. It occurs randomly, but i will write down and try and implement that suggestion when the error happens again.

5) Hardware specs:
Dell E1505 (Laptop)
500 GB HDD (@7200 RPM)
Screen: 1280x800
2GB Memory
Ati mobility x1400 Graphics chip
1.83 ghz Intel T5600 Processor

------

I attached three pictures (one, two, and three) showing what happened when i input _ubuntu-bug lxpanel_ into terminal

---

### Post by Finitemight on 2011-11-10
> **Finitemight said:**
> 1) It is a fresh new installation. I did not upgrade from ubuntu or lubuntu 11.04. I formatted those drives, and then installed it. I wanted to make sure that there would be no errors.

2)I no longer have the lubuntu iso, but i will get on obtaining it when i can and doing that.

3)I utilized a cd to install.

4) The problem has not occured frequently enough for me to try out what was suggested in post 9. It occurs randomly, but i will write down and try and implement that suggestion when the error happens again.

5) Hardware specs:
Dell E1505 (Laptop)
500 GB HDD (@7200 RPM)
Screen: 1280x800
2GB Memory
Ati mobility x1400 Graphics chip
1.83 ghz Intel T5600 Processor

------

I attached three pictures (one, two, and three) showing what happened when i input _ubuntu-bug lxpanel_ into terminal

Here are three more picture showing what happens when i input ubuntu-bug pcmanfm

---

### Post by amjjawad on 2011-11-10
Hi,

Could you please send me the link of these bugs?

Thanks :)

---

### Post by Finitemight on 2011-11-10
> **amjjawad said:**
> Hi,

Could you please send me the link of these bugs?

Thanks :)

Here is the link for the first: _ubuntu-bug lxpanel_ 

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/888729](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/888729)

Here is the link for the second: [U]ubuntu-bug pcmanfm

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/888733](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/888733)

[/U]Hope this helps.:confused:  

I have not a clue how this bug occurred, so describing it succinctly is kinda like a blind man trying to tell you about last nights game....

And me being a noob does not help that :). This has been one heck of a process though

---

### Post by amjjawad on 2011-11-10
> **Finitemight said:**
> Here is the link for the first: _ubuntu-bug lxpanel_ 

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/888729](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/888729)

Here is the link for the second: [U]ubuntu-bug pcmanfm

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/888733](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/888733)

[/U]Hope this helps.:confused:  

I have not a clue how this bug occurred, so describing it succinctly is kinda like a blind man trying to tell you about last nights game....

And me being a noob does not help that :). This has been one heck of a process though

Well done, thanks for reporting :)
However, please note that if no one else has the same issue and no one can re-produce that error which I still don't know what is the real cause of it, I don't think it will be considered as a bug. Anyhow, let's wait and see :)

---

