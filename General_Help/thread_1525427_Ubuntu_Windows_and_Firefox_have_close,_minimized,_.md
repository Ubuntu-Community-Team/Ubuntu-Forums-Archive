---
title: "Ubuntu Windows and Firefox have close, minimized, or restore on left instead of right"
date: 2010-07-06
forum: General Help
---

### Post by DWade on 2010-07-06
Ubuntu's windows and Firefox have close, minimized, and restore icons on left instead of right.

I am used to them being on the right, can someone tell me where to change them to the right.  This is the first time I have ever seen them on the left.

---

### Post by howefield on 2010-07-06
> **DWade said:**
> Ubuntu's windows and Firefox have close, minimized, and restore icons on left instead of right.

Wow, that's strange.

You might want to read the sticky in this forum (General Help).

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by Zorgoth on 2010-07-06
Are you using he default window decorator or emerald?

---

### Post by DWade on 2010-07-06
To answer the first reply --  Put the indicators on the left.!!!!!

the left has always been empty --- why use the right --- why change what has been for over 20 years...   (ya I know change is supposed to be good) 
..

for the second entry the default for now..


I have had some exchange students and computer problems so I've been stuck with windows.

I also had some issues with 9.04, and when 9.10 came out I give up and stayed with 8.04 lts.  I done something can't remember what but I got my modem (56k) to work, in it, but the newer versions no go. 

So, I just got In May a new Gateway NV7922U Laptop to replace my broken eMachine M6809.

The eMachine worked great until it started erasing the the first 2 gigs of the hard drive.  And then the video started failing by put vertical lines in it. 

At work I've had for a couple of years a Quad core Q6600 Intel. and I am always trying to run linux with a virtual machine of windows 98 which only works with microsof virtual pc or VM Ware or Windows XP. I gave up on 98 about 4 years ago. My graphics software crashes XP in about 6 months so I have to reload. Thanks to Acronis that's a snap.

I get up set every time there's a new release of software,  they change the function keys or what selects your tools. You try doing a job that worth money and every time you try to do something the wrong thing comes.
What should have been a money making job becomes a cost because you have dumbly installed the new version before checking to see if it had major changes.

This is supposed to be better user friendly, but those buttons on left for me is not user friendly.  Some major changes like this everyone on the forum should be emailed and asked what they think. (I know that will never happen)

So I have this question?  Other than taking up more user resources to power these window indicators. (Of Course as usual the more resources the more code to emplace.) [ ]
What functionality are these going to enhance.  Those Icons are already available in the top of the main screen which is always present?  or is there some thing I am missing.

---

### Post by ScarletWyvern on 2010-07-06
Geez, man. Calm down. We don't need a dissertation about your computer usage history. They're buttons. you're overreacting.

Assuming you're using Metacity, run:

```
sudo gconf-editor
```

Then go to Apps > Metacity > general

Change "button_layout" to menu:maximise,minimise,close

---

### Post by DWade on 2010-07-07
as per this post [http://ubuntuforums.org/showthread.php?t=1469475]("http://ubuntuforums.org/showthread.php?t=1469475")
under Minimize, Maximize and Close button placement.

Using gconf editor is not the way to do it.  will cause problems later on.

I am expressing a frustration.  :mad:

To begin with in 2005 my modem worked.  2006 my modem worked.  in 2007 it did not work  an still does not. Now the laptop does not work.
Got told I would have to get high speed.  well you tell me how to get high speed when there was none.  now there satelite or wireless.  Still no cable or DSL and Fios haa.... next century..  Oh by that time the have are wave rolling with 5g and no more landlines.  Those are out going because instead of keeping the price down the are raising the price 22.00 basic service no thrills and 10.00 taxes.  You can get a pay as you go cell phone cheaper than that and it has all the feature call waiting 3 way calling, caller id etc. Does my modem work on this new computer, I don't know lets see is it communications controller 5 Series/3400 Series Chipset HECI Controller?  If it's not then it's not listed and I have modem problem again.

Max frustration at work I have quad core intel with ati 2400hd graphics, can I get Ubuntu to work correctly no. I have to play with it and change some commands. I can load it found that section that is older versions, haven't tired this one 10.04 it did not give the choice to f4 change video mode to safe.  then install software - copy ati latest drivers for 2400 hd to partition. boot up choose  recovery mode, choose console and run the video driver or else you will never see any video but a black screen.

So how do you convert people to linux when a simple install is max complicated. Now take 300 plus people and tell them the have change there normal way of using windows.
How to do we convert people when simple usage gets changed and no one knows until they install.

Lets get real, I put a search in before posting for minimizing then maximizing and what came up everything but.
So I posted.

---

### Post by marshmallow1304 on 2010-07-07
Just switch to a theme that has the buttons on the right.  Here's a right-button clone of the default theme.

[http://gnome-look.org/content/show.php/Ambiance_R+%28Ambiance+Right+Side%29?content=123927](http://gnome-look.org/content/show.php/Ambiance_R+%28Ambiance+Right+Side%29?content=123927)

---

### Post by gansvv on 2010-07-07
From the Lucid Lynx workarounds page:

> 
Mark Shuttleworth explained that this was because "something" is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.


See. Perhaps its some cool change that they are hoping to bring about in window handling. Appreciate it!

BTW, can anyone comment on whats coming there? ;)

---

### Post by howefield on 2010-07-07
To answer the third reply.

What are you on about ?

That's a rhetorical question, needs absolutely no reply.

I think you said it best...

> **DWade said:**
> because you have dumbly installed the new version before checking to see if it had major changes.

There are plenty distributions out there that should keep  frustration levels within your limits., try some. Fedora recently released a new edition , and OpenSuse releases a new edition around the 15th of this month.

If I were a betting person, I'd put money on many more changes to come in Ubuntu, especially in the interface, bring it on. So if the thought of that doesn't float your boat, something a bit more conservative might suit you better.


> **DWade said:**
> So I have this question?  Other than taking up more user resources to power these window indicators. What functionality are these going to enhance.

[http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)

---

