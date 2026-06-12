---
title: "Bad Indicator-applet experience"
date: 2010-04-30
forum: General Help
---

### Post by EtherBunny on 2010-04-30
Here's my thought process as I configured my new 10.04 install.

1. [IMG]http://i848.photobucket.com/albums/ab44/etherbunnys/ubuntu/one-1.png[/IMG]

Gee, that message icon is spaced awkwardly. Why is it so far from the volume control?
  I'll just move it closer *right-clicks* oh.. can't do that
  Fine, I'll delete it then *right-click - remove from panel*
     poof, message *and* volume icons disappear

Sorry if I can't express this in a more eloquent or useful way at the moment, but the fact that these two completely unrelated functions are tied into the same tray applet strikes me as so utterly STUPID, that I had to come here and complain.

WHY? Who makes these design decisions? (don't answer that, I already saw the post about UI consistency in the panel, but I disagree vehemently.) 
It was fine the way it was.

So, after waaaay too much reading, I learned that you can remove the message part of the applet by **uninstalling a package**. That's right, you have to apt-get remove indicator-messages if you want to get rid of it. I don't know about you, but back in my day panels were configurable. If you didn't like something, you right clicked on it, and hit "remove from panel", or failing that, went into some menu and unchecked the "display annoying icon" box. You don't uninstall a freaking package! This is such a hack it's not funny, and I expect better from a distro like Ubuntu.

2. [IMG]http://i848.photobucket.com/albums/ab44/etherbunnys/ubuntu/two-1.png[/IMG]

Next, I tried learning to live with the new applet. Like its predecessor, you can scroll the mouse wheel over it to raise and lower the volume. Great. I like this feature, and use it often. *Unlike* its predecessor, when you click on the icon to see the volume bar, the scrolling stops working. So, you can scroll to change the volume, but you can't see what you're changing while you change it. Ridiculous.

Try it yourself if you want - run gnome-volume-control-applet to start up the old one.


At this point, I've had it with the entire indicator-applet system. I want it gone now. I was just about to remove it from the panel when my power cord came unplugged and .. guess what else is part of indicator-applet...

3. [IMG]http://i848.photobucket.com/albums/ab44/etherbunnys/ubuntu/three-1.png[/IMG]


All I ask is that it's possible to configure it the way it was in the last release without too much of a hassle. This was frustrating and not at all intuitive.

---

### Post by Georgie-o on 2010-04-30
I'm glade you posted.  I have been using Ubuntu since the 5 series and am shocked and dismayed by the quality of 10.04.  My notifications applets (basically everything in the upper right-hand corner) disappears or doesn't work and I can't get stuff back.  The network applet is gone, the on-off switch disappeared, everything else seems to jump around or have duplicate images...I am just floored by how this is working.  

In addition to that sometimes when I hit "switch user" it goes to a black screen and crashes.  I need to turn in off by holding the power button.  This release is unusable.  My wife, who has used ubuntu for years (at my urging) is looking at me like I'm an idiot.  She says "can't we just have a computer that works..."  The stability and quality get worse on every release.  I had to bypass 9.10 because it would not install/work on my dell desktop or my netbook!!!!   This is ALPHA software not an LTS release!

---

### Post by CptSkippy on 2010-04-30
I'm pretty much fed up with the applet as well.  I installed Netbook remix this evening and have spent several hours trying unsuccessfully to remove the envelope and chat bubble icons from the indicator while retaining the other options.

To add insult to injury, if I remove the indicator panel then every time I start up I get errors because the indicator panel doesn't properly remove itself from the GNOME Panel configuration.

---

### Post by DeMus on 2010-04-30
> **Georgie-o said:**
> I'm glade you posted.  I have been using Ubuntu since the 5 series and am shocked and dismayed by the quality of 10.04.  My notifications applets (basically everything in the upper right-hand corner) disappears or doesn't work and I can't get stuff back.  The network applet is gone, the on-off switch disappeared, everything else seems to jump around or have duplicate images...I am just floored by how this is working.  

In addition to that sometimes when I hit "switch user" it goes to a black screen and crashes.  I need to turn in off by holding the power button.  This release is unusable.  My wife, who has used ubuntu for years (at my urging) is looking at me like I'm an idiot.  She says "can't we just have a computer that works..."  The stability and quality get worse on every release.  I had to bypass 9.10 because it would not install/work on my dell desktop or my netbook!!!!   This is ALPHA software not an LTS release!

So I am not the only one who complains that every Ubuntu release is worse than the one before. I used Hardy for a year and it was great, skipped Intrepid because it was unusable, did have Jaunty which was great, Karmic had to many complications and now I installed Lucid but fighting with it.
I don't have a loudspeaker icon at all. What I miss completely is the soundmixer I had in Jaunty: I need it. Can somebody tell me where to find it here in Lucid?
I wrote other threads here in the past about the alpha and beta releases of Lucid but it seems I have to do the same about the final release. It's simply not good.
Things which work are taken out (Gimp), other stuff gets in which I don't need/want (social networking programs, buttons on the wrong side of the screen). No Ubuntu is going down hill and that is a shame.
It's time fore something else. Any ideas?

---

### Post by EtherBunny on 2010-04-30
> **DeMus said:**
> 
I don't have a loudspeaker icon at all. What I miss completely is the soundmixer I had in Jaunty: I need it. Can somebody tell me where to find it here in Lucid?
I wrote other threads here in the past about the alpha and beta releases of Lucid but it seems I have to do the same about the final release. It's simply not good.
Things which work are taken out (Gimp), other stuff gets in which I don't need/want (social networking programs, buttons on the wrong side of the screen). No Ubuntu is going down hill and that is a shame.
It's time fore something else. Any ideas?

If you run "gnome-volume-control-applet", it should give you the old icon back, but I can't figure out how to permanently add it to the panel so that it appears on bootup.

I agree on the other points. I used to like Ubuntu because it was easy to "de-configure" anything I didn't like. This release needs a lot of work.

---

### Post by korrosiv on 2010-04-30
Same here,

I think I got a workaround. After trying to configure unsuccessfully the indicator applet through config files and/or gconf editor, read somethign in a post about this package.
To remove the envelope uninstall in synaptic package manager the package called "indicator-me" and restart the computer/session. There are also other packages called indicator-something which are meant to add/remove funcionallity to the indicator applet.

Hope this helps.

---

### Post by robert shearer on 2010-04-30
> **korrosiv said:**
> Same here,

I think I got a workaround. After trying to configure unsuccessfully the indicator applet through config files and/or gconf editor, read somethign in a post about this package.
To remove the envelope uninstall in synaptic package manager the package called "indicator-me" and restart the computer/session. There are also other packages called indicator-something which are meant to add/remove funcionallity to the indicator applet.

Hope this helps.

The "indicator-me" package relates to the social networking applet - (gwibber,etc) and not the > envelope.

If you right click on the > envelope and click on 'about' you will see it is the Indicator Applet.

---

### Post by korrosiv on 2010-04-30
> **robert shearer said:**
> The "indicator-me" package relates to the social networking applet - (gwibber,etc) and not the .

If you right click on the  and click on 'about' you will see it is the Indicator Applet.

Well, my fault then. Uninstall instead "indicator-messages" and the envelope should be gone next boot.
Sorry (I just uninstalled both).

---

### Post by wilee-nilee on 2010-04-30
I you open startup manager and put gnome-volume-control-applet in the command the volume control will be there on startup. I also think some of you don't realize that the offending volume and email icon are in the notification area, your battery shows there as well without the volume and email icons.

---

### Post by jpmaglutac on 2010-04-30
Totally agree with your sentiments. Sure, this release seems to be "social from start", but what about those who are not social? As I was using 10.04 a while ago, it seemed as if Ubuntu was FORCING me to use Empathy.

After installing pidgin, I tried using the quick status changer, and to my surprise it worked! But when I changed my status to "Available", instead of changing it on pidgin, it disconnected pidgin and connected it to empathy...


Really, I thought we were supposed to have more freedom in the applications we choose :(

---

### Post by Wrinkliez on 2010-04-30
> **jpmaglutac said:**
> Really, I thought we were supposed to have more freedom in the applications we choose :(

that 100% expresses how I feel.  this indicator applet nonsense is shameful and forced me to move to Kubuntu.  if kubuntu doesn't cut the mustard (and things arent looking bright) ill just move back to windows :(

---

### Post by magnus0 on 2010-04-30
> **Wrinkliez said:**
> that 100% expresses how I feel.  this indicator applet nonsense is shameful and forced me to move to Kubuntu.  if kubuntu doesn't cut the mustard (and things arent looking bright) ill just move back to windows :(

If i don't get a solution to this problem, I'll also move to Kubuntu. That really made me hate Ubuntu now -.-

---

### Post by poliltimmy on 2010-04-30
How do you add back the network applet. The one that allows you to modify your DNS and all?

---

### Post by jpmaglutac on 2010-04-30
OKAY COOL!

I uninstalled empathy, and while using pidgin, when I change the status using that status picker whatever, IT STILL DISCONNECTS PIDGIN!




It's like Ubuntu is telling me I must use Empathy for some reason :o

---

### Post by mixmaster on 2010-04-30
Hmmm.  I don't need the me-menu/social stuff and I'd prefer to avoid all the notification stuff but I don't like kubuntu.  Does anyone know if xubuntu still stays with the older system?

---

### Post by sobolosrios on 2010-04-30
I'd like to add something for the gnome applet to scale cpu frequency and lcd brightness (I'm on a netbook and care about power management) but can't seem to figure out how to do this.  

Narrowly defined I agree with the previously expressed sentiments.  I actually think that 10.04 is a great release and I like most of what has been done with it.  I would however be interested in knowing how to configure the indicator-applet.  I appreciate the move toward consistency that Ubuntu is trying to implement, but the indicator applet seems (to my knowledge--maybe I'm missing something) be notably less configurable than the traditional gnome panel.  Perhaps that is a temporary development constraint that will be fixed.  I hope that the lack of configurability is not a deliberate choice toward making Ubuntu less configurable (and more suited to those who don't like to tinker) in favor of providing a smoother out-of-the-box experience.

---

### Post by wilee-nilee on 2010-04-30
> **sobolosrios said:**
> I'd like to add something for the gnome applet to scale cpu frequency and lcd brightness (I'm on a netbook and care about power management) but can't seem to figure out how to do this.  

Narrowly defined I agree with the previously expressed sentiments.  I actually think that 10.04 is a great release and I like most of what has been done with it.  I would however be interested in knowing how to configure the indicator-applet.  I appreciate the move toward consistency that Ubuntu is trying to implement, but the indicator applet seems (to my knowledge--maybe I'm missing something) be notably less configurable than the traditional gnome panel.  Perhaps that is a temporary development constraint that will be fixed.  I hope that the lack of configurability is not a deliberate choice toward making Ubuntu less configurable (and more suited to those who don't like to tinker) in favor of providing a smoother out-of-the-box experience.

There is a cpu control applet in add to panel, screen brightness is hold down Fn and use the arrow/triangle symbol keys that are on the bottom right of the keyboard generally. And for the rest of you in the whiners club, get over it and buy MS or Apple. Free software that doesn't do exactly what you want, now where is that tiny little violin.

---

### Post by poliltimmy on 2010-04-30
> **wilee-nilee said:**
> There is a cpu control applet in add to panel, screen brightness is hold down Fn and use the arrow/triangle symbol keys that are on the bottom right of the keyboard generally. And for the rest of you in the whiners club, get over it and buy MS or Apple. Free software that doesn't do exactly what you want, now where is that tiny little violin.

I figured it out. I just forgot how to get to it.

---

### Post by sobolosrios on 2010-04-30
> **wilee-nilee said:**
> There is a cpu control applet in add to panel, screen brightness is hold down Fn and use the arrow/triangle symbol keys that are on the bottom right of the keyboard generally. And for the rest of you in the whiners club, get over it and buy MS or Apple. Free software that doesn't do exactly what you want, now where is that tiny little violin.

Your response was not very useful.  Perhaps it is because I have not stated my position clearly enough.  Here is my second try:

By "add to panel" what do you mean?  Typically one would add something to the panel by right clicking on the panel.  As far as I can tell, on netbook remix there is no way to right click on the panel since it is entirely covered by either Window Picker or the indicator-applet.  Also, the LCD brightness keyboard shortcuts are not working and I am trying to debug the cause of this problem.  As such, it would be convenient to have easier access to the LCD brightness applet.    

I am not asking for the software to do exactly what I want right out of the box, as a careful reader would have deduced.  I use linux because I want the ability to tinker and don't mind searching through files and editing things to get what I am looking for.  The point of my comment was that indicator-applet has (to my knowledge--again if you have _useful_ information please share it) no clear way to configure or alter, short of recompiling.  Is this incorrect?  Having to recompile  software every time you need to make a config change is possible but is less desirable than having access to options through config files.  Again, perhaps all of this ability exists but hasn't been either documented or developed enough to use.  I am fine with that, but would like to know what is intended for further development.  If it is not very configurable and not likely to become so, then yes, I will consider whether this warrants changing my desktop environment and/or distribution, as you so snarkily suggested.

---

### Post by EtherBunny on 2010-04-30
Oh, and another thing that sucks: There's no tooltip when you hover over the power or sound icons.

---

### Post by priegog on 2010-05-01
Agh I agree with everything that is written on this thread so much that it is ridiculous. 
@jpmaglutac: You need to uninstall telepathy-butterfly (to prevent msn from logging on in the headless empathy). you might also want to rmeove telepathy- whatever other protocols you use, to prevent your computer from logging on to those when you don't want them to. Or in the case of jabber, to prevent the messages from your friends from being routed to your non-existent empathy program. 

This is all just SAD. I get Mark's (and the design team's) ideas of a great Linux future where everything is integrated and working flawlessly; but in the meantime we get stuck with half-assed solutions and regressions that actually make life harder. The empathy decision has me particularly bugged, for instance. 
But meh, all I (and we) can (and should) do is file (and subscribe to) bug reports, continue giving feedback and hoping for the best. Luckyly most of us are proficient enough in Linux so as to make our lives easier in the aspects where we disagree with the default desing... But all in all I think (and hope) these nuisances will eventually get ironed out.

---

### Post by Mike.lifeguard on 2010-05-02
> **EtherBunny said:**
> If you run "gnome-volume-control-applet", it should give you the old icon back, but I can't figure out how to permanently add it to the panel so that it appears on bootup.

I agree on the other points. I used to like Ubuntu because it was easy to "de-configure" anything I didn't like. This release needs a lot of work.

gnome-volume-control-applet is ugly and less usable though :(

---

### Post by Mike.lifeguard on 2010-05-02
> **jpmaglutac said:**
> Totally agree with your sentiments. Sure, this release seems to be "social from start", but what about those who are not social? As I was using 10.04 a while ago, it seemed as if Ubuntu was FORCING me to use Empathy.


I agree. Desktop integration with social networking tools is something to be avoided (not by default, certainly).

---

### Post by OzzyFrank on 2010-05-04
> **EtherBunny said:**
> If you run "gnome-volume-control-applet", it should give you the old icon back, but I can't figure out how to permanently add it to the panel so that it appears on bootup.

**[COLOR="Red"]System > Preferences > Startup Applications[/COLOR]**. Simply add it there and it should load automatically after rebooting.

Now, I actually had possibly the smoothest upgrade yet - with the exception of the missing volume icon, and having to add an Indicator Applet to get it (which I can now remove from the system tray since you guys gave me the package name of the old volume button app - THANKS!).

But I totally agree the Indicator Applet sucks camel gonads, mostly because of lack of customisability, and also because of the horridly large (and unconfigurable) spacing between the notifiers! I mean, seriously, what's up with that?? I heard the aim was to help clean up the panel/system tray, but this spacing - call me weird - seems counter to that aim.

Anyway, now that I've found **[COLOR="Red"]gnome-volume-control-applet[/COLOR]** (thanks once again to you guys), I've removed that stupid indicator. Might look into it again when you I configure it to my liking. Cheers

---

### Post by Whise on 2010-05-05
i hate this applet, just the fact i have to click on emesene icon and then select hide/show just to do a simple show or hide is just incredibly stupid

i want the chance to just remove this applet and still have full notification area funtionality..

that does it im changing to kde

---

### Post by Mike.lifeguard on 2010-05-05
> **Whise said:**
> i hate this applet, just the fact i have to click on emesene icon and then select hide/show just to do a simple show or hide is just incredibly stupid

I only had that behaviour while the emesene version from the PPA was installed. I downgraded to the lucid version, and now show/hide works as normal. Can you check what version you have installed?

I certainly agree, that kind of change in behaviour would be a clear usability regression.

---

### Post by Whise on 2010-05-05
yes im using the latest version from the ppa, but thats not the point this still occours in other apps like rithmbox and transmition.

the full single click specification of the indicator applet sucks

i want to be able to click on the icon and have it show the app, like it always have been in any decent OS.

---

### Post by Mike.lifeguard on 2010-05-05
> **Whise said:**
> yes im using the latest version from the ppa, but thats not the point this still occours in other apps like rithmbox and transmition.


Yes, I can't reproduce this behaviour on both Rhythmbox and Transmission - and I too consider it a major usability regression. Now: Does anyone know if this has been reported to Launchpad?

---

### Post by w1ll1am on 2010-05-06
Hello all I started using Ubuntu with Jaunty and I loved it I upgraded to Karmic and it was still good but I could not get the 64-bit to install with out some sort of error message but I was good with the 32. I now have my netbook and desktop running on Lucid my netbook has the netbook edition desktop with 64. I am having a problem with my battery indicator. I have it configured to always show an icon but when I start up it shows just a lightning bolt no battery info but what is strange is if I close my laptop and then wake the computer back up the battery works perfect I am not sure what to do it really sucks not being able to no how much battery I have. Any help would be great thanks.

---

### Post by Mike.lifeguard on 2010-05-06
> **Mike.lifeguard said:**
> Yes, I can't reproduce this behaviour on both Rhythmbox and Transmission - and I too consider it a major usability regression. Now: Does anyone know if this has been reported to Launchpad?
I've filed bugs for:

* Transmission: [https://bugs.launchpad.net/ubuntu/+source/transmission/+bug/576762](https://bugs.launchpad.net/ubuntu/+source/transmission/+bug/576762)
* Rhythmbox: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/576765](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/576765)
* Emesene: [https://bugs.launchpad.net/ubuntu/+source/emesene/+bug/576766](https://bugs.launchpad.net/ubuntu/+source/emesene/+bug/576766)

---

### Post by eval- on 2010-05-28
I removed this POS applet because it steals away key bindings from compiz, and the only current solution is to comment out a line in the source and rebuild the indicator-applet .deb yourself.  For real.  I'd go back to Xubuntu in a heartbeat if the xfce4-panel worked as it should.  I don't understand how Canonical keeps making Ubuntu less pleasant to use.  First the osd-notify BS, now this.

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/558581](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/558581)

---

### Post by corvus85 on 2010-05-29
perhaps canonical has figured they'll make buku bucks? Users say what they like and canonical just starts ******** with it so someone will buy support? Get a bunch of non-technical users (read me) devoted and trapped then start releasing pos so that they may charge the lazy and uninclined to fix what they themselves *ahem* broke. With user input you could figure out a lot...

P.S. those ********* took away my chess! how else am I going to waste time!

---

### Post by Jerrac on 2010-05-29
I totally agree with the opening post. The usability has definitely regressed. I just submitted an idea to Ubuntu Brainstorm about it since all the bug reports were pretty much set to "Won't Fix".

[http://brainstorm.ubuntu.com/idea/24984/](http://brainstorm.ubuntu.com/idea/24984/)

---

### Post by teachop on 2010-05-30
This input was provided in the Lucid development/testing process, and was not taken then, so don't expect it to change now.

Beyond this, I have a fear that mouse interfaces will be dumbed down, hovers and tool-tips and right click will be de-emphasized, due to rise of the touch screen interface.  I mean what other possible reason could there have been for removing tool-tips on things like volume, battery, music players?  I don't see how it conflicted with anything.

Hope I am wrong (often I am).

---

### Post by Ichido on 2010-05-30
> **EtherBunny said:**
> If you run "gnome-volume-control-applet", it should give you the old icon back, but I can't figure out how to permanently add it to the panel so that it appears on bootup.

Right Click on empty place on your Panel and choose "add to Panel".
Highlight "Custom Applications Launcher" and click the "Add" Button.
Type: should be "Application in Terminal".
Name: "Volume Control"
Command: "gnome-volume-control-applet" (without the quotes).
Last, click the "OK" Button.

Move the Applet Icon to where you want it then Right-Click and choose "Lock to Panel".

---

### Post by Ichido on 2010-05-30
> **corvus85 said:**
> 

P.S. those ********* took away my chess! how else am I going to waste time!

Have you tried [www.Chessworld.net?](www.Chessworld.net?)

---

### Post by surruk51 on 2010-06-20
I want to add my voice to the torrent of dislike for this applet.

I also wanted to pass on a bug (which I have reported). I tried using it to change my status from away to online. Whatever it then did, both aMSN and Pidgin were logged out of their respective on line accounts.

Personally, I'd vote in favour of a better menu manager that included the Gnome Panel as its top level and integrated the ability for applications to raise notifications.

Would that I had the time and knowledge to write such a thing.

---

### Post by tamashumi on 2010-06-21
I installed 10.04 yesterday.
I'm rather happy with it but this indicator stuff is much regression.

Spacing between icons is insane. I have 4-5 icons there and it takes sooo much space on my 13.3" laptop screen :(

> **EtherBunny said:**
> Oh, and another thing that sucks: There's no tooltip when you hover over the power or sound icons.

Totally agree!
Besides one could also on mouse over see song name played by rythmobox, also could play/stop by clicking with middle mouse button on player (I loved this one) icon and mute/unmute by clicking on volume control.
Also when one clicks with 1st mouse button on player icon, that brings player window - normal behavior but now it's gone :/
It was so much better functionally than Windows. Was...
Now it gets too "clickologic" and not configurable. It's wrong way, please!

This whole social crap, icons on the left side of window and lack of gimp I can get use to (window icons), skip using (social) or install
on my own (gimp) but why do they make regress in such basic functionality like "systray".
It's pointless.

Where can I post/write to reach Ubuntu decision makers?

---

### Post by temporos on 2010-06-21
> **tamashumi said:**
> Where can I post/write to reach Ubuntu decision makers?

The "Ubuntu decision makers" already know about the overwhelming disdain for the new indicator applet.  Whether they will decide to fix it (read, make it like it was in 9.10) is unknown.

Like you, I would simply write a better applet myself, if I had the time and knowhow.

---

### Post by tamashumi on 2010-06-23
Well I'm not sure if I have proper know-how.

I'm software developer though so maybe I can try.

Where can I get the source of indicator applet? I would try to modify at least those insane spacing. It can't be so hard, can it?

---

### Post by temporos on 2010-06-23
> **tamashumi said:**
> Where can I get the source of indicator applet?

You know, that's a good question.  I've been looking for the source code for some of the standard packages, and I can't find them, either. :-k

---

### Post by jesuisbenjamin on 2010-06-24
Hello forum,

I just moved to 10.04 and it runs fast and fine except for few things which relate to appearance.
The most disappointing part is the gnome-panel which is really customisation-unfriendly. I was warned by this thread a while ago, but i had hoped things would have been changed by now.
Besides volume control being inseparable from mail and user-menu being inseparable from the shut-down menu (which i feel is absurd), some icons behave strangely.

One instance is the Banshee icon, cf. screenshot. As you can see, the icon appears with a white background on panel while it should be transparent.

How come such a thing happens? How can i correct it?
This gnome-panel is the main instrument of the interface: it should be taken more seriously and allow more customisation. (But i hardly can program, so who am i to speak?)

Thanks for your help.

---

### Post by jesuisbenjamin on 2010-06-24
PS: i am noob in programming so i won't be much help on that level.
But if i can help with ideas i'd like to do so.

Let me know how i can help improving the panel experience for future releases. (i was thinking of starting with a proper survey to see what people in general really want).

---

### Post by tamashumi on 2010-06-25
> **temporos said:**
> You know, that's a good question.  I've been looking for the source code for some of the standard packages, and I can't find them, either. :-k

I found it here: [https://launchpad.net/indicator-applet](https://launchpad.net/indicator-applet)
Big green button on the right to download source.

However I even can't compile it \\:D/

I'm pretty skillful with JAVA and some other languages but with C not really.

Anyone willing help how to start? I tried creating project with Netbeans (existing C/C++ sources). Well, it creates but doesn't compile (some build config issues).

> **jesuisbenjamin said:**
> 
Let me know how i can help improving the panel experience for future releases. (i was thinking of starting with a proper survey to see what people in general really want).

Check the [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com) There is a lot of indicator applet surveys already. Just find proper ones and vote. You can post links to them here so other could vote too. Somehow search feature on the brainstorm site doesn't work very well.

---

### Post by jesuisbenjamin on 2010-06-25
Thanks i reacted on Brainstorm [http://brainstorm.ubuntu.com/idea/24984/](http://brainstorm.ubuntu.com/idea/24984/)
please help promoting improvement of the gnome-panel functionality.

---

### Post by jesuisbenjamin on 2010-06-26
> **tamashumi said:**
> I found it here: [https://launchpad.net/indicator-applet](https://launchpad.net/indicator-applet)
Big green button on the right to download source.

However I even can't compile it \\:D/

I'm pretty skillful with JAVA and some other languages but with C not really.

Anyone willing help how to start? I tried creating project with Netbeans (existing C/C++ sources). Well, it creates but doesn't compile (some build config issues).


You may find help here: [http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

---

### Post by Tasc0 on 2010-06-26
So, there's currently no solution to the hide/show Transmission with on left-click?

---

### Post by jesuisbenjamin on 2010-06-26
Hi there,

Here are my thoughts on the indicator-applet situation:

[LIST=1]
[*]We should be looking at participating in the [Indicator Applet project]("https://launchpad.net/indicator-applet"), which itself i part of [a larger project called Ayatana ]("https://launchpad.net/ayatana")that houses user interface, design and interaction projects started by Canonical and--so have i read somewhere--should aim at consistent desktop environment.

[*]Or we should try to rethink this and do it the way we like it, either offering an alternative solution in cooperation with the Ubuntu project or alone and leave it to users to chose for our alternative.
[/LIST]

Now i think the current mess-up experienced in the Indicator Applet is also affecting the Notification Area applet. In fact they both are inconsistent: some applications appear in the former, others in the latter. What determines which is where is unclear at best.

_What i propose instead:_

[LIST=1]
[*]**A Process Indicator Applet (PIA)**, i.e. a small, consistent and customisable applet for Gnome-Panel to display the various processes running on Ubuntu. The function of PIA should be to draw a list of current processes from the Gnome-System-Monitor (or the application the latter draws information from). For each process in the list should be displayed an icon in PIA. 
[LIST]
[*]The process-icons displayed by PIA can be filtered by:root/user (this is not available in Gnome-System-Monitor in Ubuntu 10.04 is the information available somewhere?), status or process name.Process names listed in the PIA filter preferences should be drawn from a process history since PIA first was added to the panel. 
[*]Icon displayed should be drawn from current theme in Ubuntu. If the icon of a specific program is not available it should find it online on a library where icons designed by or submitted to the PIA team are archived. If no icon is found in the online archive, PIA displays a default icon and signals (in Notification Area?) the icon is missing and should be submitted to the PIA team (automatic message to the team to update icon archive?) 
[*]A left-click on a process icon displayed on PIA should hide/show the GUI of the process is there is any. 
[*]A right click on a process icon should display a list of options. Default options can be drawn from a library for common programs (eg. rythmbox play/pause, Transmission pause etc.) other options can be added/removed by adding a command line.
[/LIST]

[*]**A Notification Applet (NA)**: i.e. a proper notification area which does just that i.e. notifying. I have less ideas on that, except that it should be fully filtered (which application/process is allowed to notify me) and customisable (where, how and when do i want my notifications).
[/LIST]

**Conclusions:**
To sum up the above ideas are not revolutionary, but they are clear as to what applet should do what. It could be just a matter of discussing these ideas with the current Ubuntu members who are working on these applets. 
I'd be glad to hear your thoughts on the above.

Also i have little knowledge of how one is supposed to get involved in any Ubuntu project nor how one goes about organising the collective development of a program. So if you feel you have any insights on the matter, please share.

In any case, this thread is a first step.

B.

**PS:** here is [some lecture from the Ayatana project]("http://design.canonical.com/2010/04/notification-area/"). It seems clear that Ubuntu us moving towards phasing out the notification area and implementing custom status menus. In shorts apps should not use the system tray anymore and will be integrated in a menus like the messaging menu.

I personally think this whole move towards consistency is well intended, but the ideas they provide suck. They have apparently no idea so far on how apps usually moved into a systray (eg. Transmission, Museeq) will be dealt with. Some vague reference to the window switcher is made in this document but that's all.

---

### Post by Tasc0 on 2010-06-27
Why not just fix the problem?

---

### Post by lunatico on 2010-07-21
Yes very annoying and ugly and all that... but I'm trying to get used to it...
I hate how it takes over my Super+M shortcut... I'm used to map Super+M to open my *M*usic. But now that opens my sound indicator.
That would be fine if there was an easy way to disable/change this shortcuts. From System -> Preferences -> Keyboard Shortcuts for example, but no, there isn't.

If found an awful and partial workaround. Remove the indicator-sound package, logout and back in, the sound icon is gone and compiz shortcuts has regained the shortcut. Reinstall indicator-sound and logout and in again and the shortcut will work for a while but at some stage the sound applet steals it again.
I know I could stop using the indicator-applet and use the old gnome-volume-control-applet, but as I said I'm trying the "embrace the change"...

Anyone knows how to disable the Super+M shortcut? From gconf-editor maybe?

Thanks!

---

### Post by OzzyFrank on 2010-07-21
Hey lunatico, I'v probably got the answer, but no time in the next few days to draft a guide specific to you, so check out my guide on how to get Ctrl+ALt+Del to stick for opening the System Monitor:

[http://ubuntugenius.wordpress.com/2010/06/04/ubuntu-keyboard-shortcuts-what-to-do-if-ctrlaltdelete-does-not-open-system-monitor/](http://ubuntugenius.wordpress.com/2010/06/04/ubuntu-keyboard-shortcuts-what-to-do-if-ctrlaltdelete-does-not-open-system-monitor/)

It shows you what to if using the GUI of Config Editor, but you can alter these commands and use the terminal instead:

[B]gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 ‘<Ctrl><Alt>Delete’

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 ‘gnome-system-monitor’
[/B]
I guess you would want something like:

[B]gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 ‘[COLOR="Red"]<Super>m[/COLOR]’

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 ‘[COLOR="Red"]nautilus ~/Music[/COLOR]’[/B]

The guide explains the command number; I just picked "command_9" because it is likely to be unused (I use command_1 but it may be taken on other systems).

Actually, I suppose this was specific enough, but read the guide for the rest on how to ensure this works. Cheers.

---

### Post by lunatico on 2010-07-22
Hey OzzyFrank!

Thanks for taking the time to reply. I had actually tried what you suggested, in gconf-editor I had:
/apps/metacity/global_keybindings/run_command_5 = <super>m
/apps/metacity/keybinding_commands/command_5 = rhythmbox

And as I said it sort of works for a while but then the indicator-sound applet steals the shortcut.

Anyway, your guide gave me an idea that might be a solution. Why was I wasting on of the limited run_command_x if I could use the already available Keyboard Shortcut to map it to Super+M. So I opened System -> Preferences -> Keyboard Shortcuts and assigned Super+M to 'Launch Media Player' which opens Rhythmbox anyway.
I confirmed this by looking at /apps/gnome_settings_daemon/keybindings/media in gconf-editor.

Hopefully this will work and indicator-sound wont steal my shortcut anymore.

---

### Post by dbarto on 2010-08-10
> **tamashumi said:**
> I found it here: [https://launchpad.net/indicator-applet](https://launchpad.net/indicator-applet)
Big green button on the right to download source.

However I even can't compile it \\:D/

I'm pretty skillful with JAVA and some other languages but with C not really.

Anyone willing help how to start? I tried creating project with Netbeans (existing C/C++ sources). Well, it creates but doesn't compile (some build config issues).


I found if I downloaded ALL the development tools I could recompile the program. I finally gave up because Linux development appears to be pretty scattered, unlike for the Mac (where I am more familiar). So if you want to develop, select ALL developer tools, download them, then try to compile this code. I could then remap the <super>M and <super>S keys to something I don't use.

Sad that this app grabs the keys in a way that the user can't change them without recompiling the code and recompiling the code is very very very hard.

<rant>As a Unix user for over 30 years, Linux seems too fragmented to ever make it to the big leagues.</rant>

---

### Post by tamashumi on 2010-08-20
Guys, after removing indicator applet and reboot all necessary icons (for me: rhytmbox, volume control, update indicator, pidgin, wifi, bluetooth) just got back to the notification applet :D

I don't think did anything special. I mean I was trying to add volume icon before reboot (posted in previous post) but probably even this one isn't necessary (as I didn't added this to run-at-start programs).

Check this out:
[IMG]http://img186.imageshack.us/img186/6250/screenshot4ay.png[/IMG]

Ubuntu 10.04 with correct looking notification area. Functionality still lacks a bit though (like middle mouse button mute etc...)

---

### Post by jesuisbenjamin on 2010-08-20
> **tamashumi said:**
> Guys, after removing indicator applet and reboot all necessary icons (for me: rhytmbox, volume control, update indicator, pidgin, wifi, bluetooth) just got back to the notification applet 

Hey Tamashumi,

Do you mean you simply removed the indicator applet as in "uninstalled" the indicator applet?
Because i simply removed the indicator applet and rebooted and the notification applet is still messy (doesn't display transparency properly) whilst it seems to be fine on your screenshot.
Also the volume-control applet is not available by default on 10.4, do you mean you didn't do any install nor created a custom launcher applet to get your volume control to show on the panel?

Thanks for clearing up!
B.

---

### Post by lunatico on 2010-08-21
> **jesuisbenjamin said:**
> Hey Tamashumi,
Because i simply removed the indicator applet and rebooted and the notification applet is still messy (doesn't display transparency properly) whilst it seems to be fine on your screenshot.


He doesn't seem to have any of the icons affected by the transparency bug.

---

### Post by jesuisbenjamin on 2010-08-21
Is it icon-specific then?
I was wondering about this the other day ans suspected the issue could be due to the use of either png or svg icons. I just don't know how to trace which program uses which icon and whether it is the notification applet or the main application which imposes the icon.

B.

---

### Post by lunatico on 2010-08-21
> **jesuisbenjamin said:**
> Is it icon-specific then?


I think so anyway... afaik it's gnome-panel no been able to handle the icons transparency. Not all icons are affected, for me for example it's for the mail-notification icon...

---

### Post by Elcid247 on 2010-12-07
> **EtherBunny said:**
> Here's my thought process as I configured my new 10.04 install.

1. [IMG]http://i848.photobucket.com/albums/ab44/etherbunnys/ubuntu/one-1.png[/IMG]

Gee, that message icon is spaced awkwardly. Why is it so far from the volume control?
  I'll just move it closer *right-clicks* oh.. can't do that
  Fine, I'll delete it then *right-click - remove from panel*
     poof, message *and* volume icons disappear

Sorry if I can't express this in a more eloquent or useful way at the moment, but the fact that these two completely unrelated functions are tied into the same tray applet strikes me as so utterly STUPID, that I had to come here and complain.

WHY? Who makes these design decisions? (don't answer that, I already saw the post about UI consistency in the panel, but I disagree vehemently.) 
It was fine the way it was.

So, after waaaay too much reading, I learned that you can remove the message part of the applet by **uninstalling a package**. That's right, you have to apt-get remove indicator-messages if you want to get rid of it. I don't know about you, but back in my day panels were configurable. If you didn't like something, you right clicked on it, and hit "remove from panel", or failing that, went into some menu and unchecked the "display annoying icon" box. You don't uninstall a freaking package! This is such a hack it's not funny, and I expect better from a distro like Ubuntu.

2. [IMG]http://i848.photobucket.com/albums/ab44/etherbunnys/ubuntu/two-1.png[/IMG]

Next, I tried learning to live with the new applet. Like its predecessor, you can scroll the mouse wheel over it to raise and lower the volume. Great. I like this feature, and use it often. *Unlike* its predecessor, when you click on the icon to see the volume bar, the scrolling stops working. So, you can scroll to change the volume, but you can't see what you're changing while you change it. Ridiculous.

Try it yourself if you want - run gnome-volume-control-applet to start up the old one.


At this point, I've had it with the entire indicator-applet system. I want it gone now. I was just about to remove it from the panel when my power cord came unplugged and .. guess what else is part of indicator-applet...

3. [IMG]http://i848.photobucket.com/albums/ab44/etherbunnys/ubuntu/three-1.png[/IMG]


All I ask is that it's possible to configure it the way it was in the last release without too much of a hassle. This was frustrating and not at all intuitive.

I LOVE U! i just removed the applet completely from my panel in maverick, the old battery applet showed up and i used the gnome-volume-control-applet for sound control.

---

### Post by Mycen on 2012-09-08
I hate the way the panel is handled in recent releases (12.04 currently).

Before, the panel was an icon handling gizmo, where you could add and remove applications' icon in a slick menu, and remove and add panels all over your desktop if you so desired. Now I had to browse forums to discover the name of the app that magically appeared when I installed Ubuntu to get rid of it(I don't care about MSN, pidgin, icq, the whole lot).
The same applies to adding an icon to the list (I just like to know if my dropbox is up to date, connected, etc). I had a hard time getting it to show up there, and had to search for and edit a config file.

As we are all different, we all want to see different icons up there. Why has this option, which was nice and adjustable before, been fixed in stone? For a **human-oriented** operating system, this is a step back. I seriously don't care if I have to dig through forums and config files for stuff that isn't finished yet, not correctly supported, or can still be improved, but leaving perfectly polished and user-friendly stuff behind and getting people back into their terminal is certainly not the way.

Reading this thread I understand I'm not the only one with discomfort around the 'panel' zone, and that gives me some comfort at least.
I hope this post counts as a vote for adjustability in next distros.

---

