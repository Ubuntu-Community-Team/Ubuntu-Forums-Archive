---
title: "Skype notification icon not showing up in natty."
date: 2011-04-30
forum: General Help
---

### Post by StrongJinx on 2011-04-30
Hello I am fairly new to Ubuntu and I am loving it!!!!! But I am having an issue with Skype on Ubuntu 11.04 natty. I am running it in classic the unity UI just isn't my cup of tea. When i start up Skype it don't show the icon that shows your status and where can right click on it and change your status also ill close the buddy list and ill open skype and it says im already signed in is any body else having this issue and how can I fix it.?

---

### Post by xaitax on 2011-05-01
Here:
[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

Chapter: **Install dconf-editor to tweak some more settings**

Changing that value to **['all']** worked for me.

---

### Post by gszyszka on 2011-05-01
The same here with natty 64bit.
I've tried changing systray-whitelist, however for both cases: default and changed to 'all' my skype icon in systray is 1 pixel wide. It looks like white dot on dark panel :) interesting ...
Any other ideas?

Thanks
Grzegorz

---

### Post by Hotshot5000 on 2011-05-01
What is horrible is that they actually solved the bug in one update but another update got the bug back in.....It's almost three weeks now...still no fix for this.

---

### Post by gszyszka on 2011-05-01
This seams like systray bug. As a temporary solution you can do: ```
killall gnome-panel
``` but next time you reboot/restart skype the problem is back.

---

### Post by timgood on 2011-05-01
> **gszyszka said:**
> This seams like systray bug. As a temporary solution you can do: ```
killall gnome-panel
``` but next time you reboot/restart skype the problem is back.

Not any more: killall gnome-panel results in 'gnome-panel: no process found'.

Natty Dread!

---

### Post by gszyszka on 2011-05-03
[QUOTE=timgood;10751301]killall gnome-panel results in 'gnome-panel: no process found'./QUOTE]

Are you using classic gnome or new ubuntu unity shell?

---

### Post by timgood on 2011-05-03
> **gszyszka said:**
> [QUOTE=timgood;10751301]killall gnome-panel results in 'gnome-panel: no process found'./QUOTE]

Are you using classic gnome or new ubuntu unity shell?

Problem is with Skype in Unity - on login the icon will sometimes show, sometimes not. Sound is sometimes corrupted, sometimes not. In Unity gnome-panel is there no longer. But the problem also occurs in Classic. 

Problem is more fully explained here: [http://teknology.blogspot.com](http://teknology.blogspot.com)

Hope this helps.

---

### Post by st0kes on 2011-05-03
Just adding another 'me too' to this thread. 

Running Natty, Ubuntu "classic mode". If I do killall gnome-panel it does give me the skype icon back. I guess it's ok as a workaround. 

Link to the Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/764828](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/764828)

Nothing at all is explained on [http://teknology.blogspot.com](http://teknology.blogspot.com) ...

---

### Post by timgood on 2011-05-03
> **st0kes said:**
> 
Nothing at all is explained on [http://teknology.blogspot.com](http://teknology.blogspot.com) ...

I beg to differ. Problem is.

---

### Post by TedinOz on 2011-05-04
[PHP]Running Natty, Ubuntu "classic mode". If I do killall gnome-panel it does give me the skype icon back. I guess it's ok as a workaround.[/PHP]

If this is only a temporary solution I find it easier to open the Skype interface click the 'S' at bottom left where all options are displayed, including quit which prevents it from continuing to run in the back ground and allows re-sign-in as needed. No icon I know but this at least is reliable.

---

### Post by ilantal on 2011-05-04
I looked at the post:

Nothing at all is explained on [http://teknology.blogspot.com](http://teknology.blogspot.com) ...
I beg to differ. Problem is.

I comes out almost a blank screen. That is the reason for the comment "Nothing at all is explained".

In any case I have the same problem with skype. Yesterday I was coming up in the notification area, but today it is gone. I have 2 monitors where the notification bar is repeated on both monitors. When the skype icon was there, it was only on the primary monitor. Not that I really care as long as it is at least on ONE monitor, but has gone back to ZERO.

How come this thread is marked as solved??? It anything but solved.

Ilan

---

### Post by gilnarya on 2011-05-04
I think I found a solution.
The problem is the area dedicated to app icons: it is not resized automatically, when a new icon comes (for instance skype's icon). 

on the top panel: 
-> Unlock notification area applet
-> resize it manually
-> lock it again

Then it works.

---

### Post by acidicX on 2011-05-04
not for me, it aint. Already tried moving the panel (you can't resize it really).

Please join the bug discussion on launchpad about this.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/775717](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/775717)

---

### Post by gilnarya on 2011-05-04
You don't have to move the panel but the Notification Area. 

The configuration of my top panel is [from left to right]:

[Main Menu] [ Notification Area] [Indicator Applet Complete]

The key point is the Notification Area. If it is not locked you can move it. If you give it enough space to display the skype icon, it will appear. The problem is that it doesn't move/resize automatically. Try it. It worked for me.

Does it work for you?

N.B. It's not dynamic, you have to quit skype and open it again.

-> I joined in the discussion on launchpad

---

### Post by timgood on 2011-05-04
> **ilantal said:**
> I looked at the post:

Nothing at all is explained on [http://teknology.blogspot.com](http://teknology.blogspot.com) ...
I beg to differ. Problem is.

I comes out almost a blank screen. That is the reason for the comment "Nothing at all is explained".

Oh me oh my! My bad! Should be [http://teknolegy.blogspot.com](http://teknolegy.blogspot.com)

Velly velly solly!

---

### Post by Beanmonster on 2011-05-04
I can confirm gilnarya's method works:

Unlock applets on panel space them out, restart skype. :)

---

### Post by Ubuntnux on 2011-05-04
I am using Natty (amd64) with Gnome (Ubuntu Classic). 

I realized that restarting the panel or unlocking the applets was not consistently bringing the icon back, however I found a workaround: 

You can start Skype (normally) and click on "Options">"General" and select "Start Skype minimized  in the system tray". 

Now every time I start Skype the icon is there. :)

---

### Post by gilnarya on 2011-05-04
Not just unlocking, try also to move the notification area to give it more space

---

### Post by TedinOz on 2011-05-04
> **gilnarya said:**
> I think I found a solution.
The problem is the area dedicated to app icons: it is not resized automatically, when a new icon comes (for instance skype's icon). 

on the top panel: 
-> Unlock notification area applet
-> resize it manually
-> lock it again

Then it works.

I think I am missing something :( How do I 'Unlock the notification area applet' please? I feel a bit like a goose having to ask this.

---

### Post by Ubuntnux on 2011-05-04
Just click with the right mouse button in the notification area and unselect "Lock to Panel". Then, you may click on "Move" and create space for the Skype icon. 

However, this approach does not seem to work for me all the time. The most consistent solution was tell Skype to always start minimized in the system tray as I explained above.

---

### Post by avongil on 2011-05-04
> **Ubuntnux said:**
> I am using Natty (amd64) with Gnome (Ubuntu Classic). 

You can start Skype (normally) and click on "Options">"General" and select "Start Skype minimized  in the system tray". 

Now every time I start Skype the icon is there. :)


This worked for me! Thanks.

---

### Post by TedinOz on 2011-05-04
> **Ubuntnux said:**
> Just click with the right mouse button in the notification area and unselect "Lock to Panel". Then, you may click on "Move" and create space for the Skype icon. 

However, this approach does not seem to work for me all the time. The most consistent solution was tell Skype to always start minimized in the system tray as I explained above.

Hmm. It seems what works on one system doesn't on another. The 'minimise to system tray' doesn't work here. When I open Skype, rather than get an icon in the panel, I get an infinitesimal dot like a distant star barely visible and if I can accurately aim the cursor arrow at it, it is actually the Skype icon and it does show Skype info but you can't see the icon just the dot. 
[PHP]Just click with the right mouse button in the notification area and unselect "Lock to Panel"[/PHP] only works if I aim the cursor at an existing icon. If I do it on a blank area of the panel I get...

"Add to Panel
 Properties
 Delete this Panel" etc

When I aim at a specific icon, I AM able to unlock and move that icon but it makes no difference to the skype icon. If I aim at the skype . (dot) icon, I can move that but it doesn't change to a real icon.

So still as confused as ever :(

---

### Post by ghoulsblade on 2011-05-07
removing the whole notification area and re-adding it (both via rightclick menu in the area or on the move-handle rather than on an icon)
did the trick for me.
Not sure if i'll have to do it again after reboot though.

found in :
[http://forum.skype.com/index.php?showtopic=103174](http://forum.skype.com/index.php?showtopic=103174)

---

### Post by littleoak on 2011-05-08
I have the same problem , didn,t happen on last version of ubuntu. I really would like to fix  this problem.

---

### Post by littleoak on 2011-05-09
Been playing around and I seem to have fixed the problem. remove everything from the right side of the panel. notification area, dateand time, stop button, which all seem to be seperate. also anything else you find there.

add new item complete notification area.. Bingo It worked for me.:D

---

### Post by astraluxkl on 2011-05-09
[B]Ubuntu 11.04 Natty[COLOR=Silver]* -- _Solution_*[/COLOR]
[/B][INDENT]**Solution for "gnome-panel » notification area applet » icons bug"**
[/INDENT][INDENT]Add to:[INDENT]System » Preferences » Autostart Applications[U][I]

application/command[/I][/U] "gnome-panel --replace"

[/INDENT][/INDENT]

---

### Post by -Rif- on 2011-05-11
> **astraluxkl said:**
> [B]Ubuntu 11.04 Natty[COLOR=Silver]* -- _Solution_*[/COLOR]
[/B][INDENT]**Solution for "gnome-panel » notification area applet » icons bug"**
[/INDENT][INDENT]Add to:[INDENT]System » Preferences » Autostart Applications[U][I]

application/command[/I][/U] "gnome-panel --replace"

[/INDENT][/INDENT]

thanks :D
it really works for me

---

### Post by amanetta on 2011-05-11
> **astraluxkl said:**
> [B]Ubuntu 11.04 Natty[COLOR=Silver]* -- _Solution_*[/COLOR]
[/B][INDENT]**Solution for "gnome-panel » notification area applet » icons bug"**
[/INDENT][INDENT]Add to:[INDENT]System » Preferences » Autostart Applications[U][I]

application/command[/I][/U] "gnome-panel --replace"

[/INDENT][/INDENT]

Is this solution only for gnome panel?

---

### Post by exiztone on 2011-05-11
Just to say this is also a problem for me. Ubuntu 11.04 x86-64

:'(

---

### Post by astraluxkl on 2011-05-12
> **astraluxkl said:**
> [B]Ubuntu 11.04 Natty[COLOR=Silver]* -- _Solution_*[/COLOR]
[/B][INDENT]**Solution for "gnome-panel » notification area applet » icons bug"**
[/INDENT][INDENT]Add to:[INDENT]System » Preferences » Autostart Applications[U][I]

application/command[/I][/U] "gnome-panel --replace"

[/INDENT][/INDENT]
IF this doesn't help you, For example BUG didn't disappear. the solution is similar ..[INDENT]you should thing how to execute this command some seconds later 
after desktop Loads
[B]» you can do it MANUAL using
[/B][INDENT]**ALT+F2 and type *"gnome-panel --replace"***
[/INDENT]OR
**»** you can set a timeout

[/INDENT][INDENT]Add to:System » Preferences » Autostart Applications[U][I]

application/command[/I][/U] "**sleep 5 && gnome-panel --replace**"
[/INDENT]

---

### Post by amanetta on 2011-05-12
> **astraluxkl said:**
> IF this doesn't help you, For example BUG didn't disappear. the solution is similar ..[INDENT]you should thing how to execute this command some seconds later 
after desktop Loads
[B]» you can do it MANUAL using
[/B][INDENT]**ALT+F2 and type *"gnome-panel --replace"***
[/INDENT]OR
**»** you can set a timeout

[/INDENT][INDENT]Add to:System » Preferences » Autostart Applications[U][I]

application/command[/I][/U] "**sleep 5 && gnome-panel --replace**"
[/INDENT]
Is this solution only for gnome panel?

---

### Post by idovecer on 2011-05-13
I must submit the same bug here.
Only what it helps to show skype icon is to type gnome-panel in terminal.

Any other solutions?

---

### Post by giovannif on 2011-05-14
In my case only the manual solution worked. I tried also the sleep command to introduce a delay, but I did not have any success.
Applying that command is quite annoying. Can anybody find another solution?
Is this problem related with Skype or Ubuntu? What if I install an old version of skype?

Thanks
gio

---

### Post by cpickeri on 2011-05-19
Same problem. 
Running 11.04 64 bit and latest skype for ubuntu.

---

### Post by Janoka on 2011-05-25
I use Natty64 with Ubuntu classic (gnome) desktop.
As I see the main problem is not only the Skype, qBittorrent etc.. icons in the notification area, but there's no possibility to use the good old drag&drop function on the top bar. For example when you put the media player (totem) icon to the top bar, you can drag media files (or directory) onto the icon, and it opens the totem and starts playing music. I changed to the UBUNTU CLASSIC WITH NO EFFECTS in the System/Administration/LoginScreen. Since then everything works fine!!! (Skype, qBittorrent, drag&drop...)

As a conclusion I suppose that the problem must be somewhere around Compiz and it's desktop effects... Until the problem is solved I have to avoid the desktop effects and use Natty without them.

---

### Post by joris1977 on 2011-05-25
Why the hell is this marked as solved?

There is nothing solved in this thread, only less than very uncomfortable workarounds are mentioned!

Please unmark it, because this is stupid.

And I really hope this is not what the future of the gnome2 panel in Ubuntu looks like. Yes you can still use the classic interface if you really miss a panel at the bottom in Unity, but you will have very annoying bugs that get no priority to be fixed....

---

### Post by Janoka on 2011-05-25
Yes, I agree wit you **joris1977**, nothing is solved, everybody is waiting for the result of the game between Gnome and Compiz developers (as I have read before, none of them can really find their problem), I don't know why this topic is marked "SOLVED" either... We can reach only half-solutions...

---

### Post by rizos on 2011-05-29
+1 agrre remove unsloved from this therad.

---

### Post by del_Brujo on 2011-05-29
> **astraluxkl said:**
> IF this doesn't help you, For example BUG didn't disappear. the solution is similar ..[INDENT]you should thing how to execute this command some seconds later 
after desktop Loads
[B]» you can do it MANUAL using
[/B][INDENT]**ALT+F2 and type *"gnome-panel --replace"***
[/INDENT]OR
**»** you can set a timeout

[/INDENT][INDENT]Add to:System » Preferences » Autostart Applications[U][I]

application/command[/I][/U] "**sleep 5 && gnome-panel --replace**"
[/INDENT]

This does not fix the problem for me. But killall gnome-panel yes.
I agree that it's not solved it yet.

---

### Post by foxy123 on 2011-06-02
The icon works for me in Unity but not in the Classic interface :( It used to work a few days ago.

---

### Post by Juand_au on 2011-06-09
I just added the notification area applet and it fixed it. The new ubuntu classic comes with another one called indicator applet as default, just add notification area. right click->add to panel->notification area. That seemed to fix it for me

---

### Post by Liova99 on 2011-06-12
A Solution is to unlock from panel  all the applications: righ klik "unlock from panel"  ( time.. shutdown mail etc. ) \\:D/

---

### Post by foxy123 on 2011-06-13
> **Liova99 said:**
> A Solution is to unlock from panel  all the applications: righ klik "unlock from panel"  ( time.. shutdown mail etc. ) \\:D/

does not work for me :(

---

### Post by creontu on 2011-06-16
Ubuntu 11.04 natty x64. Used to get my skype icon back just by restarting skype(actually it was disappearing from the panel but was still present on the desktop - if I switched to desktop selection view(Workspace switcher) i could see the icon.). Now this does not help. However logging out and logging in and doing a few restarts of skype help. Also I see the second skype icon always(if I launch another skype). Still works that way except now after reboot it always started first time without the icon.

---

### Post by creontu on 2011-06-17
FYI. as of today's updates I have no more problems with this.(there were lots of compiz updates today):KS

---

### Post by abrigard on 2011-08-08
In my case, I am with gnome clasic, there are two different applets that are similar but not. Skype is shown in the Notification Area, which is different from the Indicator Applet which shows dropbox, battery, network and volume.

I solved it adding the Notification Area applet.

---

