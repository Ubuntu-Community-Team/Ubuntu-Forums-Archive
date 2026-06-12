---
title: "Ubuntu and parents"
date: 2009-09-15
forum: General Help
---

### Post by Fc1032 on 2009-09-15
Hello all,

I'm a major fan of using ubuntu, I've put it on all my computers, but in the end my family cannot cope with such a different OS.

They arent power users, just the occasional web browser.

So i would just like to know how i can get ubuntu to look EXACTLY like vista (oh the hate messages from this request :P). Basically, I would like to be able to skip grub completely and have the general vista look. 

I would like to teach them to use ubuntu. But it took them 3 years to learn windows. I thought it would be easier if they had the same interface, it wouldnt be so intrusive for them.

Thanks in advance!

---

### Post by alienclone on 2009-09-15
if it took them 3 years to learn windows, just let them stay with windows if they are happy.

---

### Post by theozzlives on 2009-09-15
If all they use is web browsing, have them use FireFox. Install the User Agent Switcher that allows Firefox to look like MSIE to web sites. A Browser is a browser, plus they have the added security from malware that Ubuntu provides.

---

### Post by zeroseven0183 on 2009-09-15
As far as customisation is concerned, Ubuntu is very easy to personalize. What you need to do, I think, is ask your parents the things they needed most when they are using the computer. And have it automatically load or create an icon in the desktop for easier access.

---

### Post by Fc1032 on 2009-09-15
hmmmmm. So your saying that i shouldn't have ubuntu on the comps?

I guess its the best way though, that means i wont get to use ubuntu =( (i know i can dual boot, but parents sometimes use the comp when i walk away, and their first reaction is "whats this? where the internet??)

I'm not using ubuntu on my laptop because battery life under ubuntu is less than vista...

=) thanks for the advice =)

---

### Post by ndefontenay on 2009-09-15
This is someone who enjoys using linux and wants to share his passion with his family.

Switching directly to linux is a bit cold turkey though.

Oddly enough what you are facing from your family members is cold the super user syndrom. They know how to do things on windwos and when they changed to linux it was not quite the same. I've had the same when I switched people from win 98 to XP 6 years ago...

It does take time and patience to answer their questions. 

What exactly do they miss from windows? If they just browse the web it shouldn't be that hard a switch.

---

### Post by Fc1032 on 2009-09-15
oh im such a slow typer XD theres been so many responses already!!

I could just teach them where the internet is. That would be the easiest option?

Last question then =) Im seriously not a fan of grub, i'll be using ubuntu as the main OS, is there a way to configure it so i dont see it at all??

I want to skip directly to the loading =)

---

### Post by Fc1032 on 2009-09-15
@ndefontenay

Well, i guess they don't really miss anything, its just that slight learning curve they face.

So i do guess teaching is best way then =) they have been using firefox for a long time.. IE isnt the best =P 

I look forward to teaching them =) ubuntu FTW =)

---

### Post by zeroseven0183 on 2009-09-15
I also dual-boot on my other laptop. What I did was to set the timeout to 0 seconds.
To do this,

```
 sudo gedit /boot/grub/menu.lst 
```

Scroll down to the section where you see

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

```

and change the number 3 to 0. Then set also the default kernel choice (see two lines above it) to 0.

---

### Post by zeroseven0183 on 2009-09-15
I have to go now. I hope and I believe you will get a lot of help in this thread.

Patience is a virtue. They'll learn and love Ubuntu. Trust me.

---

### Post by Fc1032 on 2009-09-15
@zeroseven0183

thanks for your input =)

i look forward to having ubuntu as the main OS at home =) we can get things done quicker =D

thanks everyone =) i'll take things step by step =)

---

### Post by earthpigg on 2009-09-15
be patient.

if it ain't broke, dont fix it.

windows will inevitably break, of course.

at that point, prior to them tossing it in the trash... intercept the computer, and fix it. 

present the computer -- now faster than it was before now that it has Ubuntu or a derivative on it -- back to them.

consider having firefox automatically run at login.

consider that gnome-panel is the among the least windows-like panel option available to you.

consider looking into LXpanel, or maybe even go entirely with LXDE.... the LXpanel/LXDE menu is closer to windows, and your existing GNOME knowledge will work with it pretty well.


this will demonstrate two tangible and clear benefits to the non-nerd-parents:

1) due to some form of sorcery and witchcraft, the item they where about to toss in the trash is now usable.
2) due to some other mysterious magic spell, it is not faster than it has been in years.

go ahead and point out to them, at this point, that this is partially because of how clever you are (parents like things that make them think their kids are clever), but mostly because of GNU/Linux and the [fundamental and basic freedoms]("http://en.wikipedia.org/wiki/The_Free_Software_Definition#The_definition") it granted you.

---

### Post by MelDJ on 2009-09-15
try this: [http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html](http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html)

---

### Post by ajgreeny on 2009-09-15
The easiest way to keep ubuntu and get it to look like windows and keep your family happy is

1-  get rid of the top panel, use the bottom one only, to which you will need to add the gnome main menu, clock, notification area, volume control, and any other applets that strike your fancy.

2-  Change the menu icon if you want to something else.  Attached is an icon I use that I downloaded from this forum a long time ago.  many thanks to who-ever it was who produced it in the first place.

3-  Go to System -Administration -Login Window and set the machine to auto login to their username, less secure but should be OK for their usage.

4-  Put launcher icons on the desktop for Firefox, Thunderbird or evolution whichever is used, but rename them Internet,  Email,  etc etc.  Same for OOo Writer.

5-  Edit the grub menu.lst file to hide the menu and set a short time to boot;  I suggest 1 sec, not 0, as you will find it a bit easier to get the grub menu up if needed by hitting Esc.

That should be a great start, and I suspect they will not really find it any more difficult to use, even if it looks a little bit different to the eye.

---

### Post by timjohn7 on 2009-09-15
Another transition approach, based on some assumptions:

1.  By "using the internet", I assume that they are using IE under Vista?
If so, install Firefox under Vista and convert them to browsing using Firefox first.  This browser will then ease the switchover because they will be familiar with it.

2.  I assume that they want the most convenient, quick access to what they want to do (surf, email etc).  If so, install Startup Manager, which is a GUI to adjust various startup options (like timeout referred to above) and add their preferred apps (Firefox, Evolution etc) Startup Applications list (Under System > Preferences > Startup Applications) so that they will be able to do what they want to without really even seeing which OS they are using, while getting all the Ubuntu benefits of speed, stability and partial security.

3.  If one of the points of familiarity is the frequent use of Ctrl Alt Del in Windows, tell them that although it works the same, they just wont have to use it for about the next 5 years! :)

---

### Post by lukjad on 2009-09-15
> **Fc1032 said:**
> [SNIP]my family cannot cope with such a different OS.

They arent power users, just the occasional web browser.

Here's the trick. Don't make Ubuntu look like Vista, make Vista look like Ubuntu. How do you do that? Simply uninstall Internet Explorer, and install Firefox. That way, they will get used to Firefox. Since that seems to be all they use a computer for, with a few extra tweaks like changing the background to one that is a non-Vista one, you will slowly get them used to using open source products, and eventually, you can switch to Ubuntu. If you put a shortcut to Firefox on the desktop, they don't even have to look in Applications->Internet for the Firefox Icon.

---

### Post by ianmillington on 2009-09-15
I suspect it'a a bit more than simply the browser, it's a GUI issue generally.

There will be lots who disagree with me here but if you want to ease the transition the desktop you need is KDE. Kubuntu Jaunty is now looking absolutely gorgeous and if you set it up right (say going for the classic kmenu and putting the favourite apps on the desktop and panel) they will adapt in no time.

---

### Post by yens on 2009-09-15
Hi,

I have the same issue with a colleague of mine, i.e. vista>>ubuntu switch.
Up to now there are mostly positive reaction from her, of course I helped a lot at the beginning cause it was little stressing.
Very nice vista looking software for ubuntu is the *screenlets* package. You can put on the desktop different clocks, trash basket, picture frames, slide show frame for pictures and many others. Just try it.

I also recommend you to check the following link:
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")
Firstly I was surprised how many analogs linux offers, especially for the common software like web browsers, mail clients, multimedia.

---

### Post by RJ12 on 2009-09-15
If they know XP they could also try this [http://www.xpde.com/](http://www.xpde.com/)
its a bit old but looks alot like XP

---

### Post by 3rdalbum on 2009-09-15
You'll come across the law of leaky abstractions.

You'll try to make your Ubuntu system look like Windows, but it won't actually act much like Windows (leaky abstraction)- so this might confuse your parents further. If you keep Ubuntu looking like Ubuntu, they will recognise that it's something different and not be so bamboozled when something doesn't behave how they expect.

---

### Post by Fc1032 on 2009-09-16
Oh, its nice to see that the thread continues after it was solved =)

Well, we use firefox ever since we had an issue with IE (which back then tended to crash ever 2 hours for some reason =S )

What i will be doing is *attempt* to get the windows look and slowly teach them the ubuntu ways =) 

@ajgreeny, thanks for your input, they are all very useful =)

@earthpigg, "1) due to some form of sorcery and witchcraft, the item they where about to toss in the trash is now usable.
2) due to some other mysterious magic spell, it is not faster than it has been in years." LOL 

Thanks again everyone!

---

