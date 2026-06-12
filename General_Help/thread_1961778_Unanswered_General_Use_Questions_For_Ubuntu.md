---
title: "Unanswered General Use Questions For Ubuntu"
date: 2012-04-19
forum: General Help
---

### Post by More or Less on 2012-04-19
**SHORTCUTS**

So, how do people normally use 11.10 and higher?  As it is out of the box, you have to go to the upper left and click the circle button.  Then, you type in the program name.  However, a text editor like GEDIT won't come up unless you know the name of the program.

My solution on Windows is to create a shortcuts folder and put it on the desktop.  Each time I use a program I like, I add a shortcut to that folder.  Then, when I use the computer next time I can just go to the shortcuts folder, two clicks is a lot easier than what I am faced with here in 11.10. 

As for the launcher pad on the left, it has its merits but you can't put too many icons there without it filling up and it just takes up screen space.  With 11.10 it is fine in conjunction with a shortcuts folder, but in 12.04 I found it better to just remove it entirely.  Basically, it's a no go for me.
  

**ICON SIZE**

My screen resolution options are 1024 x 768 (too big), 1152 x 864 (suitable but still bigger than need be), and 1280 x 1024 (decent area of space, but the lighting messes with my eyes)

Unless I find a solution with my current monitor or get a new one, I am content using the 1152 x 864 setting.  However, the icon size is not only huge for each icon, but they vary from one icon to the next. Ideally, I would like to see the same icon size for all icons and to have them smaller.  Right now, the only way I see to change the size is to edit each icon individually.

Is there a way to edit a default icon size for all?  Bonus would be to have them the same size too.


**UPGRADE TO 12.04**

In 12.04 I was unable to get programs downloaded completely.  I switched to 11.10 and now I have the first set of programs I want to use.  So, is it possible to now migrate to 12.04?

Can I do this without having to make another 12.04 USB installation?  Can I upgrade using 11.10 (like through the download center or system settings)?  I will probably just make another 12.04 USB installation, but I was curious how Ubuntu deals with this because right now it says my upgrades are up to date, but I am not on 12.04.  I understand it's a "new" or significant upgrade from 11.10, but it seems like there should be a message to either wait until 12.04 becomes available or an option to download and  the beta through 11.10.

---

### Post by 3Miro on 2012-04-19
12.04 is still in Beta stage, it hasn't been released for general use yet. It is currently buggy and it will be buggy for some time after the release. It is normal to experience issues.

On 11.10, you can install CompizConfig-Settings-Manager and from CCSM you can find the experimental settings of the Unity plugin and adjust the icon size. In 12.04 you can adjust the icon size from the appearance menu. (this is assuming you have good enough video card and you are running Unity 3D)

For the screen resolution, you should always try to use whatever is  native for your monitor. I am not sure exactly what you problems are and how to fix them, perhaps if you elaborate more.

In general, the default Ubuntu Unity interface is only one option of many. You can try xfce, lxde or even kde, as well as Gnome-shell and Gnome-classic (also known as Gnome-fallback). Check on how to transition between DE.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by audiomick on 2012-04-19
> **More or Less said:**
> **SHORTCUTS**
The dash opens when you press the key that microsoft likes to call the Windows key. My experience is that the search box is pretty good at "guessing" what you want. I get hits when I type &#347;tuff in in English, even though the system language is German. For gedit, have you tried typing "editor"?
> 
**ICON SIZE**
You can do a bit of adjusting with myunity
[https://launchpad.net/~myunity/+archive/ppa]("https://launchpad.net/~myunity/+archive/ppa")
You have to install a PPA for 11.10, but I gather it will be installed by default in 12.04. I also expect that it will be able to make more adjustments as time goes by

> **UPGRADE TO 12.04**
As far as I know, 12.04 isn't out yet. Another week or so, I believe.
The update manager will offer it for upgrade as soon as it is officially released.

---

### Post by MonkeyPaw on 2012-04-19
> **More or Less said:**
> **SHORTCUTS**

So, how do people normally use 11.10 and higher?  As it is out of the box, you have to go to the upper left and click the circle button.  Then, you type in the program name.  However, a text editor like GEDIT won't come up unless you know the name of the program.


Yes, that can be tricky. The key is to type a keyword for the thing you are wanting to do. So if you want a text editor, you start typing "Text" or "Writer" and you'll see your options. Same for spreadsheets or office, or image editors. 

For programs I use extensively, they are locked to the launcher. Pretty rare that I need to go deep into the menus for much.

> 
My solution on Windows is to create a shortcuts folder and put it on the desktop.  Each time I use a program I like, I add a shortcut to that folder.  Then, when I use the computer next time I can just go to the shortcuts folder, two clicks is a lot easier than what I am faced with here in 11.10. 

As for the launcher pad on the left, it has its merits but you can't put too many icons there without it filling up and it just takes up screen space.  With 11.10 it is fine in conjunction with a shortcuts folder, but in 12.04 I found it better to just remove it entirely.  Basically, it's a no go for me.


That can work too, I suppose. Again, lock to the launcher if you like it and use it a lot. Some programs don't need to be locked since you access them via opening documents/pictures/movies. Also, you can shrink the icon size in the Launcher by going to System Settings-->Appearance-->Behavior. A smaller launcher fits more icons vertically.
  

> 
My screen resolution options are 1024 x 768 (too big), 1152 x 864 (suitable but still bigger than need be), and 1280 x 1024 (decent area of space, but the lighting messes with my eyes)

Unless I find a solution with my current monitor or get a new one, I am content using the 1152 x 864 setting. 


That all depends on your monitor and your preference. The best practice for an LCD monitor is to run at the native panel resolution. Any other resolution will result in aliasing, blurring, and blending that just looks terrible. What is the native resolution of your monitor? Is it a 4:3 or 16:9 panel? Do you have a graphics driver installed?

Also, it might be good to find your screen reset option on your monitor. It makes it redetect the optimal width, height, and screen positioning for a given resolution. It might clear up your picture quality.

 
> 
However, the icon size is not only huge for each icon, but they vary from one icon to the next. Ideally, I would like to see the same icon size for all icons and to have them smaller.  Right now, the only way I see to change the size is to edit each icon individually.

Is there a way to edit a default icon size for all?  Bonus would be to have them the same size too.


I think some of this could be fixed if we knew more about your monitor and graphics situation. Personally, I don't have an issue with the icon sizes on my machine.

---

### Post by grahammechanical on 2012-04-19
Which icons are you talking about when you say that they are too large? The ones in the launcher or the ones you put on the desktop?

You can change the size of the launcher icons in 12.04 by going to System Settings>Appearance. You can also set the launcher to auto-hide.

On 11.10 you need to install CompizConfig Settings Manager and click on the ubuntu Unity Plugin to do the same thing. Be careful that you do not untick the plugin. You will lose the desktop user interface.

As for upgrading 11.10 to 12.04 that is not only possible but it is the usual way. When 12.04 is officially released Update Manager will have a button that will let you upgrade to 12.04. In fact you may receive on screen messages inviting you to upgrade. That upgrade button does not need to be there until the 12.04 release is officially available. do you not agree?

I am at this moment testing the upgrade path to 12.04 from 10.04 and 11.10. It will take about 70 to 80 minutes for the upgrade to complete.

You should make sure that 11.10 is fully updated before you start.

You will notice that as you put icons in the launcher then the icons will fold up at the bottom of the launcher and as you use the mouse to scroll down the launcher the icons will open out.

Regards.

---

### Post by More or Less on 2012-04-20
Some of you have replied with the same answer, so instead of quoting I'll just address the same issues with more information that you asked for or stated.


**ICONS**

Some of you stated I could change the icon size in 12.04.  I was in 11.10 when I started the thread.  I have now installed 12.04 and I am upgrading now.

As it is now, I can't change the desktop icons.  The launcher icons do change, but when this is ready, I won't be using the launcher at all, only shortcuts on the desktop.  It's just too cumbersome to use and in the way for me.  I like and need my left to right space.

That's why I want to change the icons on the desktop to be smaller.  I like having project folders and current files right there.  When I receive files from people I like to have them go directly to the desktop so I am not searching around.  Then it's usually a temporary thing and I just delete.At these times, I don't see the point in going through the trouble of having 100 icons on the launch thing on the left.  There isn't enough space, even with the smaller icons on the launcher.

[B]
MONITOR ISSUES[/B]

I only brought up monitor issues because it can make the icons smaller if I change the resolution.  I don't have an LCD monitor, it's one of those old TV like ones.  I don't know how to find a default setting for the resolution.  I just plug the monitor into the computer and Windows, or in this case, Ubuntu has resolution settings.  There is nothing that declares one resolution as being "THE DEFAULT". 


**SEARCHING FOR PROGRAMS**

Even if I could get a program to load based on typing the right keyword, that still takes longer than clicking a shortcuts folder and choosing the program.  I only need about 10-30 stored, so scrolling is not much of an issue.  However 30 on the launcher on the left makes it unrealistic to use.  I am curious how others make use of the launcher because I can't see how useful it is.

One suggestion would be to add other keywords.  For example, if you used notepad in Windows and are using Ubuntu for the first time, you could type notepad in and see the same kind of program in Ubuntu. It would probably be Gedit, right?  If you typed in "Microsoft Office" then "Libre" would come up.  This is more of the use I would think the search function would deal with than rather everyday use.  


> You can try xfce, lxde or even kde, as well as Gnome-shell and Gnome-classic (also known as Gnome-fallback).I have no idea what those are.  Are there screenshots to see what they look like?  Do any of them have a launcher not on the left or right?  I would prefer using stuff which loads from the top or bottom, not left like in the current version.


> You should make sure that 11.10 is fully updated before you start.Before I start what?  I did have 11.10 fully updated and used it for 2 days.  Then, I had these questions and figured I might as well test 12.04 again.  I don't want to get too involved in 11.10 if I can't transition to 12 (whatever version of 12) when it becomes a full release to the public.

If you meant starting a program, please let me know which program.

> You will notice that as you put icons in the launcher then the icons will fold up at the bottom of the launcher and as you use the mouse to scroll down the launcher the icons will open out.Yea, I don't like that.  It's much easier on my eyes to scan a page of icons from a shortcuts folder.  I can see about 30 at a time without working in the confined narrow space the launcher takes up.  

I used to use wikispaces and now they have the same kind of thing in the upper right.  It's a rather ugly addition to wikispaces pages and it slides out (hidden) when you scroll down.  So, if you want to sign in or you want to use one of the options in that bar you constantly have to move your mouse.  I moved my stuff over to weebly because of it.

With 11.10 it's tolerable, but in 12.04 for some reason I can't get it to appear when I want it to.  I have to literally slide the mouse across the mouse pad like I am bowling.

I can't understand why this has been made.  In a paint/photo editing program like photoshop, gimp, or even an html editor I can understand putting buttons on the left.  However, English readers read left to right.  There should be NOTHING on the left, and if you really want to click something on the sides it should be on the right.  I prefer having a taskbar on the bottom or top.

At least I would like the option to put the launcher where I want it.  I definitely don't like on the left.

---

### Post by 3Miro on 2012-04-20
> **More or Less said:**
> 
I have no idea what those are.  Are there screenshots to see what they look like?  Do any of them have a launcher not on the left or right?  I would prefer using stuff which loads from the top or bottom, not left like in the current version.


Since you are messing with your system a lot anyway, it is a good time to try different Desktop Environments. A DE is a collection of applications that give you panels, menus, settings tools, etc. Under Linux, you have the power of choice, some DE would work better for you, some not so much. This depends both on your hardware as well as the way you want to use your computer.

Ubuntu comes by default with Gnome 3 environment plus the Unity interface. Gnome has two other interfaces, Gnome-shell and Gnome-classic (I think if you install Gnome-shell, then you get both). You can then select which interface you want from the login screen.

KDE is the other big player and the main competition of Gnome. KDE is the most easily customizable environment, at first it looks a lot like Windows, but it has so many more options.

XFCE is what I use, you can Google screenshots. I have a bunch of rather small launchers (as small as I want them) at the top of the screen as well as a menu similar to what you will see in Windows XP (except it is better, because it has nice categories). Overall XFCE is very customizable, but not quite as easy to setup.

LXDE is the lightest and fastest of the environments. It is missing some features, but it is blazing fast and if you don't  need those features, LXDE is awesome.

You can Google image of all DE, but there is really no good way to describe them all. You just have to install them and play around with every one of them. Then pick what works best.

---

### Post by More or Less on 2012-04-20
Ok, so how do I get them? I only see information on them and some link  to other sites.  On one of those pages there were 3 download links for  KDE.  One was called Rawhide, but when I read further it said not to  download for day to day use.

So, where is an EXACT location I can download KDE?

Thanks for the explanation.

---

### Post by More or Less on 2012-04-20
Nevermind, I think I found a site which explains it.

[http://news.softpedia.com/news/How-to-Install-KDE-SC-4-8-on-Ubuntu-11-10-248829.shtml](http://news.softpedia.com/news/How-to-Install-KDE-SC-4-8-on-Ubuntu-11-10-248829.shtml)

If this isn't right, then please let me know.

---

### Post by MonkeyPaw on 2012-04-20
You might also try "Cinnamon" for your desktop environment.

[http://cinnamon.linuxmint.com/](http://cinnamon.linuxmint.com/)

From what I gather, you can install it under Ubuntu and try it out from the login screen. Problem is, Cinnamon is still fairly young and might have some issues here and there. I tried it under Linux Mint with a decent amount of success.

---

### Post by audiomick on 2012-04-20
That site looks to be for the absolute latest KDE. That will possibly give you a newer version than is in the Repositories.

Via the software center, you can load the package "kde-standard", which I believe will give you the complete KDE desktop. You can then choose to log-in to this at log-in time instead of gnome.

Likewise, there is a package in there for LXDE and I am sure there is one for XFCE as well, although I couldn't find that so quickly.

---

### Post by 3Miro on 2012-04-20
Here is how you get different DE:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Stick to the Software Center, even if the program is a little older, it will probably work better for you. You should install things from outside of the Software Center only if there is a good reason, like something is horribly not working or the program is missing.

---

### Post by More or Less on 2012-04-20
Wow!!! All I can say, it's like I went out and bought a new monitor or something.  Thanks guys.  I guess I'll stop now with this desktop and do the same with my netbook.

---

### Post by More or Less on 2012-04-20
I tried putting "SOLVED" in the right place, but I am not sure where to put it.  It appears in the original post, but in the forum list it doesn't.  Is this something that moderators have to add?

---

### Post by 3Miro on 2012-04-20
> **More or Less said:**
> I tried putting "SOLVED" in the right place, but I am not sure where to put it.  It appears in the original post, but in the forum list it doesn't.  Is this something that moderators have to add?

Scroll up to the red letters where it says "Thread Tools". You can mark the thread as "Solved" from there.

---

