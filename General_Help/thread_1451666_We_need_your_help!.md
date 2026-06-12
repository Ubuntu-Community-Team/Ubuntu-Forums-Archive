---
title: "We need your help!"
date: 2010-04-10
forum: General Help
---

### Post by AldenIsZen on 2010-04-10
*I hope this is an appropriate forum, as it is entitled "General Help". *

This issue is dear to me, not because I am affected (I can work around it...) but because I think it hampers adoption of Ubuntu and sheds negative light on an OS and by extension ideals (FOSS) that I love. So I am here to please with anyone reading this on information on how to get the issue resolved for everyone involved.

 This issue I am speaking about is selecting the window to resize, and there only being a few pixels (or even 1!) to grab a hold. It can be very frustrating to a first time user who is not aware of the other ways to go about doing this. If you are not able to effectively use the OS, then you _will not_ use it. It turned me off at first, but I wanted to find more about Ubuntu and Linux so I stuck with it. I am more technically inclined then my friends and I know they would not have, even if they were open to trying something new.

 In the [Launchpad.com]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311") bug report it has been blamed on themes,  Metacity, user ability, etc. I think it affects high resolutions much more, and laptop trackpad users as well. We (users) need a fix in order to use Ubuntu adequately. I realize that it does not seem to be a high priority, but as long as this bug has been around I think it should be bumped up especially considering each new release promises better usage. Lucid has new theming, etc, but we need this fixed.

 I realize that I could code a fix myself, if I knew how to program. But, we need eyes and discussions on this issue since there have been countless ones already on the best way to fix it. We need to have the different maintainers come together I guess.

 So, does anyone have any ideas on how to get this done, so that we can not turn off future Ubuntu users and have a little more sanity ourselves in day to day usage?

 Thank you all for taking the time to read this and anything you can contribute to this cause.

 Alden

edit/ Please take the time to go to Launchpad.com and click this  "[This bug affects you and...]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311/+affectsmetoo")" link so that we can  better get an idea of the numbers that are affected.

---

### Post by misterbk on 2010-04-10
I 100% agree.  The default window border is difficult to select even for me, and few ordinary humans can match my leet mousing skillz.

---

### Post by blueridgedog on 2010-04-10
You can do this.

Let's say you are using the Human theme and want fatter window boarders for resizing.

You need to edit the theme's metacity XML file. For Human it is:
/usr/share/themes/Human/metacity-1/metacity-theme-1.xml.  Other themes are in a similar location, just change the theme name:

so, 

```
gksu gedit /usr/share/themes/Human/metacity-1/metacity-theme-1.xml
```

then change these:

```
  <distance name="left_width" value="3"/>
  <distance name="right_width" value="3"/>
  <distance name="bottom_height" value="3"/>
```

to something that suits you, try 8 to start:

```
  <distance name="left_width" value="8"/>
  <distance name="right_width" value="8"/>
  <distance name="bottom_height" value="8"/>
```

Save, then apply the theme again by selecting another, then going back to the one you edited.

I strongly suggest you make a backup of the file before you mess with it.

such as:

```
sudo cp /usr/share/themes/Human/metacity-1/metacity-theme-1.xml /usr/share/themes/Human/metacity-1/metacity-theme-1.xml.back
```

Note that if you made a custom theme based on one of the original ones, will need to edit the theme you started with.

---

### Post by AldenIsZen on 2010-04-11
> **misterbk said:**
> I 100% agree.  The default window border is difficult to select even for me, and few ordinary humans can match my leet mousing skillz.

Thank you for your support. I am going to edit my original post asking thost that have this issue to click the "[This bug affects you and...]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311/+affectsmetoo")" link so that we can better get an idea of the numbers that are affected.

> **blueridgedog said:**
> You can do this.
Sure I can. Should everyone that is affected by this issue have to? It is my most sinscere belief that many are affected and do not know how to fix it, get help, or even bother continue experiminiting with Linux or Ubuntu. Since they can't do something effectively which should be easy that affects productivity, it will hurt continue to damage Ubuntu's reputation of professionalism, speed, easiness, etc. This isn't a get my obscure hardware working request, this is a hey I can't even set out my workspace effectively request. It may be a small one, but I feel for far too long it has been seen as a lesser deal than it may be.

 Thank you for taking the time for a response and a fix. Do you feel we should focus on a permanent solution?

---

### Post by blueridgedog on 2010-04-12
Since we have deduced where the issue lies and that it is within the theme which is made by individuals (there are many themes and all are generally made by volunteers see - [http://gnome-look.org/](http://gnome-look.org/)) and it is in fact a matter of interpretation as to what is "right" for a boarder thickness, I can't say that I would file a bug report on this.

It is the preference of the theme designer.  If you don't like the theme then use another (there are over a thousand on gnome-look).

If you can't find one you like, then make one that suits you.  This is an open source product and there are no real "vendors" or "suppliers" in the typical sense.  People are not paid to make the themes so if they want a 3 pixel boarder - that is what you get.  If you happen to like an 8 pixel one - it is not a bug but an opportunity to make your own theme or customize theirs and post the customized one on your website as a new version of their theme.  That is the cycle.

---

### Post by oldos2er on 2010-04-12
I've come up against this problem in Lucid too. In addition to changing the theme to have wider borders, you can also use keyboard controls to resize windows. Alt-Space should give you a window menu, choose Resize. Alt-F10 will switch between maximized and original size.

And of course all of these key combos are editable via Keyboard Shortcuts.

---

### Post by AldenIsZen on 2010-04-13
> **blueridgedog said:**
> Since we have deduced where the issue lies  and that it is within the theme which is made by individuals (there are  many themes and all are generally made by volunteers see - [http://gnome-look.org/](http://gnome-look.org/))  and it is in fact a matter of interpretation as to what is "right" for a  boarder thickness, I can't say that I would file a bug report on  this.

 I am not sure that we can blame it on just the theme by looking at all  of the discussion in the bug report. That is one way to tackle it  however.

 Look, I don't want to take away the ability to have someone customize a  1 pixel border, if that is what they want. What I am saying is, out of  the box it should not be so difficult for many in Ubuntu's customer base  to adjust a window. Would you agree?

 We can blame this on it being a open source project, but let's be  honest here. Ubuntu is trying to sell you something, and they should  make a (business) decision on this in everyone's best interest since _they_  in fact, have final say so.

 Perhaps getting another theme is the answer, and I will look at doing  just this. It was understanding however that this was bad for others,  etc. All I know is, if Microsoft can make this issue non-existent no  matter the resolution size, we can do the same. Using the defalut theme  should never be an issue IMHO with something like this. What if you in  fact, like the default theme?

> **oldos2er said:**
> I've come up against this problem in Lucid too. In addition to changing the theme to have wider borders, you can also use keyboard controls to resize windows. Alt-Space should give you a window menu, choose Resize. Alt-F10 will switch between maximized and original size.

And of course all of these key combos are editable via Keyboard Shortcuts.

 Yup, I have seen these work-arounds, thanks. I ask you, what the point is a feature, if it doesn't work? If one is expected to use keyboard shortcuts, why not just nix the border control? Because it works (for some), that's why. But for many of us, it doesn't, but it could and I feel should.

---

### Post by blueridgedog on 2010-04-13
> **AldenIsZen said:**
> Look, I don't want to take away the ability to have someone customize a  1 pixel border, if that is what they want. What I am saying is, out of  the box it should not be so difficult for many in Ubuntu's customer base  to adjust a window. Would you agree?

I agree that tastes and expectations vary, that you have a high expectation that Ubuntu will be targeted at a wide audience of users, that this expectation is reasonable and that the default width is amazingly small.

I have not seen this issue before.  I noticed your post, researched the resolution, tested it on my system and posted it so you could use your PC as you see fit.  In many ways that is the Ubuntu model and the purpose of these forums.  This discussion may lead to a theme that is suitable to your needs and in the end is still part of the cycle.  Ideally someone like you (or me?) would notice this and rework the Human theme to make things a bit more suitable, then post that theme to gnome-look.org, or volunteer to do so for Canonical and become part of the development process.  The important thing to keep in mind is that there is no "other" in GNU/Linux.  If there is a problem, it is "our" problem to address.  We are the community that makes free and open source software work.  We are the ones in control.  

A bug report is part of that process, but I think there is a big difference between thinking of things as broken when they were simply designed with other goals in mind.  You are right that MS would not allow such a thing because they write software to sell.  The themes you have had issues with were written mostly to enjoy...and probably by younger eyes and hands than you and I!

By focusing our discussion here on a solution rather than on a problem, we have added to the knowledge base.  Instead of a general "hey this isn't right" we now have a specific statement that the boarder width specified in the metacity-theme-1.xml file shipped with most default themes in Ubuntu 9.10 is 3 pixels and that a minimum should be 5, or the user should be able to configure it based on personal preference.  This is a much more actionable item from a development standpoint and would be a great thing to put into a bug report.  That is type of bug report I would support in this case and is the type I generally try and file.

---

### Post by J V on 2010-04-13
This should be added to the accessibility menu, not everyone is in windows rehab...

---

### Post by AldenIsZen on 2010-04-13
> **J V said:**
> This should be added to the accessibility menu, not everyone is in windows rehab...
Please try to be constructive. I understand that many are fine with Windows users staying on "their" side. However I feel the world should be liberated and Ubuntu embodies that. Windows users are users to, besides the fact that grabbing a Window with a mouse is intuitive, yet so difficult is the point.

---

### Post by blueridgedog on 2010-04-13
> **J V said:**
> This should be added to the accessibility menu

Any place would probably work...and that is a natural fit.  I still think we need a graphical tool to fully customize the gnome environment.

---

### Post by Ubunthree on 2010-04-14
I was having trouble with this too. Trying to grab the window edge was like trying to thread a needle while wearing mittens. Now I have a six-pixel border and everything is good. Thanks for the solution.

Now of course I have to make yet another note in my how-to folder; otherwise I'll have no hope of remembering how to do this the next time...

---

### Post by IanVaughan on 2010-11-20
this is quite annoying, for me I can edit these files, but my Wife/other users are not going to like such a small grab size! Think UX people!

I am using Ambiance, so I edited /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml, and set :
```
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="false" rounded_bottom_right="false">
 	<distance name="left_width" value="4"/>
	<distance name="right_width" value="4"/>
	<distance name="bottom_height" value="4"/>
```

Then changed they theme away and back again, and it worked...

But now I have fat ugly borders! 

I was hoping that the trigger for the resize grab would be invisible, like a +-pixels from the border edges.

Anyway, sorta solved for now, but not happy that I'd have to do this for future/other themes I use, and for other users I want to promote Ubuntu to, and not happy about having fatter border...

---

### Post by BuddyThirteen on 2010-11-20
^This.
I think that the "grab area" should be defined differently from the actual visible border. Although I could see how this might be a problem with interfering with the scrollbar. But surely there's some way to do this...

---

### Post by s1baker on 2010-11-26
I was just about to post about this very thing.
I have been using Ubuntu for about 2 weeks now, and I am starting to find my way around on the system and getting use to the various features and such, and one of the first things I noticed was the difficulty in picking the window resize hotspot in the lower right corner of the windows. I think I am not that much different from other users, in that in the course of working with the system I am constantly moving and resizing windows, and this is an annoyance.

---

### Post by AldenIsZen on 2010-11-26
We have raised the "This bug affects me..." numbers by at least 100. Please continue to do this, as I have emailed Mark Shuttleworth's secretary (this is how he reccomends being contacted on his website) letting him know this is killing us. A link was provided to the bug issue on launchpad.

 Thank you all for taking a moment to make what you use a bit better.

---

### Post by Tanner1294 on 2010-11-26
I believe the developers of GNOME need to do what KDE's did. They made it so that each theme can have an actual configuration menu of it's own. In other words, you can set settings specific to the theme. Gnome does not have this and therefore, you have to screw with the configuration files (as mentioned above) and/or choose a different theme. GNOME is more stable than KDE, and KDE is more beautiful which is what turns most people towards GNOME. KDE looks as if it's just meant to be pretty, but alot of it's prettiness allows it to be a good work enviroment. The reason KDE is still unstable is because you can configure and change almost ANYTHING to the way the user wants it without typing files.

GNOME needs to start focusing on simple things like configuration capabilities or else users will be turned away towards KDE.

---

### Post by AldenIsZen on 2010-12-01
FYI guys, on the bug thread they have asked for no more comments. I was tempted to anyway, but they have it posted already. I recevied a response from Mark Shuttleworth's secretary (Claire) and was told a fix is coming for 11.04 Natty. In the bug report on Launchpad it states that it will be focused on making the grip work with all programs without causing problems, and a border approximately 3 pixels wide. I hope it was more like 4-5, but that is better than 1.

 This is great news, as the bug was filed in Nov. of '07, over 4 years ago! I know I was affected before that. Hurray!

 Watching the Ubuntu and other teams do their thing, while Ubuntu gets better! :popcorn:

 Reading back over the thread, I hear you blueridgedog, Ubuntu is us! However, when the resize, restore and close buttons were moved to the left side, Mark Shuttleworth was quoted as saying "This isn't a democracy." We all contribute, but what makes it in the end is what we can convince Canonical of putting into Ubuntu. We can change Ubuntu as we wish, but the defaults should be no matter what, easy. I can live with buttons on the left, however as I am used to the right (and someone else was used to them being on the left I suppose...), I moved them back. A thing I like about Ubuntu and Linux in general is that it has taught me how to problem solve and run down the answers, which isn't necessarily a bad thing. (but for some it does take up time unnecessarily) But if I am doing that constantly, I never get anything done. Especially if I (or new users) can't even move windows around. ; )

---

