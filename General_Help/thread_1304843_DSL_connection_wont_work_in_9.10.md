---
title: "DSL connection wont work in 9.10"
date: 2009-10-29
forum: General Help
---

### Post by Hornless_Unicorn on 2009-10-29
Hi everyone!
 
I've just installed Karmic Koala (Ubuntu 9.10) but can't get online - the DSL connection to my DSL-modem just won't work. 
 
I've done everything just like on Jaunty (which worked absolutely fine) and I don't have problems getting online on XP (writing this there right now). Seems like this is something specific to Karmic. 
 
You can imagine that I'm beginning to get frustrated - things like that should work right out of the box (after entering the connection data).
 
Karmic looks great - but I can't even get online :( Any help would be appreciated.
 
Thanks a lot in advance!


Hornless.

P.S. I use the 64 bit version of Karmic Koala (and 64bit Jaunty before that)

---

### Post by BarisBlaq on 2009-10-29
Maybe try this
[http://ubuntuforums.org/showthread.php?t=1304900](http://ubuntuforums.org/showthread.php?t=1304900)

---

### Post by VMC on 2009-10-29
What's the output of 'ifconfig'?

---

### Post by Hornless_Unicorn on 2009-10-29
Thanks for your help,

but after searching a lot in different forums I learned about pppoeconf (Shell) and used that to get online configured it and made it run on start up. It's not a permanent solution - since it should work from the GUI in my opinion. Seems like there's a lot to learn about Karmic. It's a bit sad that it doesn't run as smooth as it should...

Cheers,

Hornless.

---

### Post by Hornless_Unicorn on 2009-10-30
This is quite crazy! ha!

Well I decided to reinstall karmic - this time not going into live-cd mode. Still having the same problem with DSL and got it working through pppoeconf at the console. 

But! After I install the (proprietary) hardware driver for my Nvidia the pppoeconf connection wont work either! ha! This is insane... 

Well, I'll try to find a way to get this working, but so much for ease of use and creating a system that would attract people away from windows. I like ubuntu, but it's definately not "plug and play".

If these problems continue I might go back to Jaunty. To be honest I expected much more from Karmic, well, we'll see.

Cheers,

Hornless.

---

### Post by Hornless_Unicorn on 2009-10-30
> **BarisBlaq said:**
> Maybe try this
[http://ubuntuforums.org/showthread.php?t=1304900](http://ubuntuforums.org/showthread.php?t=1304900)

Thanks for the link - at first I thought it's only for wireless - I guess I have to try this - hope it works :)

---

### Post by blankego on 2009-10-31
I'm experiencing the some thing. And, I feel the booting time for karmic koala is much longer than jaunty.

---

### Post by Hornless_Unicorn on 2009-10-31
> **blankego said:**
> I'm experiencing the some thing. And, I feel the booting time for karmic koala is much longer than jaunty.

I went back to Jaunty after having numerable problems with Karmic. It's not really worth the trouble for me. And I don't want to mess with the kernel etc. It was quite a pleasure to see how Jaunty works and instantly recognizes the DSL connection etc. I think that for some system Karmic is just not ready - for me it felt more like a Beta. I also had kernel crash warnings.

I've decided to wait untill Karmic will be more stable and mature. It's a bit sad though...

Cheers,

Hornless.

---

### Post by 600WPMPO on 2009-11-01
I switched to Ubuntu when it was 8.04. I loved it and continued to 8.10 & 9.04. Those were the days of Windows Vista. Now, we have Windows 7 and Ubuntu 9.10. 

Quite simply put, for the first time in any Ubuntu release that I have tried, this one seems to lose to Windows. 

I cannot connect to the net via DSL (that's what I and a lot others use), and for the first time I thank myself that I am using WIndows 7 as a dual-boot. For the first time, I am posting on a Ubuntu forum through Windows. 

Tell me Ubuntu, what are Alphas, Betas and RCs worth when you have a bug (that's a bug with a capital B) that doesn't even allow net access ? Why should I use "sudo pppoeconf" when you have made a network manager that worked in all the previous releases but not now ?

I inspired a lot of my friends to switch to Ubuntu, and some were waiting for the Karmic release. Now they blame me for wasting their time with an OS that can not connect to the net. I say to them the usual "search in google and some ubuntu user will help you" or "update to to the latest build of network manager", and pat comes the reply "how do I do it without the net". Makes me remember the time where windows would give us stupid messages like "Keyboard not connected. Press F8 to continue".

I guess life has come full circle for me. Now using Windows 7 (and quite happy with it)while Ubuntu gathers dust on a separate partition, waiting for the day when someone would bring it to life.

Till then, Ubuntu Karmic: R.I.P.

---

### Post by Hornless_Unicorn on 2009-11-02
600WPMPO - I totally agree with you. Just after my debacle with Karmic it so happened that I've installed Windows 7 on my PC and it works like a charm, I love the idea of free software and a "naturaly evolving" OS and all that, but if one is honest and objective, one must say that Windows 7 works and Karmic doesn't even connect me to the Internet (left alone all the other problems I had with it). 

I just can't understand how and why Karmic could've been released in such a condition. This round certainly goes to W7.

Of course I'll still have Jaunty on my other PC and hopefully Karmic will get over it's problems too.

Cheers,

Hornless.

---

### Post by 600WPMPO on 2009-11-02
And Hornless, while we have not looked beyond DSL hassles in Karmic, there appear to be a lot of users experiencing further troubles. I even found a page titled [COLOR="DarkRed"]"Is Ubuntu 9.10 a Train Wreck?"[/COLOR] (search in google)

Now, this is something new...!! No one could have said a thing like this for ubuntu ever in the past. 

In my opinion, everything is pardonable. Everything, except an OS that is permanently offline (that too for an OS that relies heavily on the net for a lot of things). We have seen worse days, but for ubuntu, this is the first.

---

### Post by Hornless_Unicorn on 2009-11-02
> **600WPMPO said:**
> And Hornless, while we have not looked beyond DSL hassles in Karmic, there appear to be a lot of users experiencing further troubles. I even found a page titled [COLOR=DarkRed]"Is Ubuntu 9.10 a Train Wreck?"[/COLOR] (search in google)

Now, this is something new...!! No one could have said a thing like this for ubuntu ever in the past. 

In my opinion, everything is pardonable. Everything, except an OS that is permanently offline (that too for an OS that relies heavily on the net for a lot of things). We have seen worse days, but for ubuntu, this is the first.

Hi again!

Unfortunately it seems to be quite a "train wreck". I just tried karmic on my other (older PC) in LiveCD-Mode - I had the same crash-warnings (severy kernel crash or something the like) and guess what? The DSL-connection didn't work either. So on two very different computers Karmic Koala did not work properly! 

I really wanted it to work, because it seems to run faster and looks quite nice even if not dramaticaly different. But it's a total wreck! I wonder why they even released it - I think they should've waited untill it's a working OS. 

You just feel as if they don't really care or would never admit it. How can they promote this?! It's like promoting a car that doesn't drive...

Cheers,

Hornless.

---

### Post by 600WPMPO on 2009-11-02
> **Hornless_Unicorn said:**
> I really wanted it to work, because it seems to run faster and looks quite nice even if not dramaticaly different. But it's a total wreck! I wonder why they even released it - I think they should've waited until it's a working OS. 



Right Hornless, the very fact that we are still discussing Karmic means that we want it to work just like all the previous Ubuntu releases. 

By the way, here are files (for i386 only) we can install offline to make network manager work (probably).

I got these on another thread here courtesy rax0:

```
http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb

http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091031t155342.d08484c-0ubuntu2~nmt1_i386.deb
```

I am too tired for trying this out. You may try them if you still have the zeal for Karmic. Lets see if it works..

---

### Post by Hornless_Unicorn on 2009-11-02
> **600WPMPO said:**
> Right Hornless, the very fact that we are still discussing Karmic means that we want it to work just like all the previous Ubuntu releases. 

By the way, here are files (for i386 only) we can install offline to make network manager work (probably).

I got these on another thread here courtesy rax0:

```
http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb

http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091031t155342.d08484c-0ubuntu2~nmt1_i386.deb
```I am too tired for trying this out. You may try them if you still have the zeal for Karmic. Lets see if it works..

Thanks! 

I'll check it out, but I'm not sure if I want to mess with it anymore. The DSL-problem wasn't the only thing, so I'll stick with Jaunty for now and with Windows 7. I really hope that Koala will turn into something stable, reliable and productive and that canonical will provide a new ISO file for download accordingly. Then I'll try it out again.

Cheers,

Hornless.

---

### Post by Hornless_Unicorn on 2009-11-02
Interesting that according to this small poll - around 80% like Karmic - seems like it works on some machines (!?)

[http://ubuntuforums.org/showthread.php?t=1306097](http://ubuntuforums.org/showthread.php?t=1306097)

Jaunty was my fist ubuntu installation, so I don't know if it's allways like that when a new version comes out? Are they allways as shaky as Karmic? 

I really do like the overall feel and working environment of GNU/Linux, particularly the more "spartanic" Ubuntu, wich I find very ergonomic (didn't like Kubuntu or Mint) but after Karmic I begin to wonder if it's able to survive - I do hope so...

---

### Post by 600WPMPO on 2009-11-02
> **Hornless_Unicorn said:**
> Jaunty was my fist ubuntu installation, so I don't know if it's always like that when a new version comes out? Are they always as shaky as Karmic? 

See, what a bad impression Karmic has given you, that now you (and a lot of my friends whom I made to switch to ubuntu 9.10) are doubtful about all previous ubuntu distros..! 

All previous ones have been excellent, connecting to the net before I could blink my eyes, giving swift updates, almost flawless stability & security, and users sharing and ready to provide quick & correct solutions to our 'nooby' problems..

But this time, I feel the excitement has waned out. 

And Hornless, I really really doubt if they'll give a new ISO for download.. that's not like them. So, we'll wait till we get 6 months older... right ?!! 

Till then, here's some popcorn for us.. :popcorn:



p.s. i installed the 2 deb files i mentioned above, but they made no difference. I'm still offline on ubuntu. Windows 7 is loving it.

---

### Post by ea1387 on 2009-11-02
You must have DSL without a modem?

---

### Post by 600WPMPO on 2009-11-02
> **ea1387 said:**
> You must have DSL without a modem?

It has an external modem. Working fine in windows.

Earlier in intrepid & jaunty, I used to make  a new DSL connection, input my username & password, and it'd work strrightaway. Now they say something about IPv6 not working properly in Karmic. They were busy beautifying the notification system, but nobody cared to check the basics. :(

---

### Post by Hornless_Unicorn on 2009-11-03
> **ea1387 said:**
> You must have DSL without a modem?

I have an ordinary (external) DSL-Modem which has allways worked fine and works on Windows 7 and Jaunty (64) without a glitch.


[B]600WPMPO - thanks for the popcorn! It's really good ;) where did you get it? hehe...

Well maybe canonical just decided that releasing within the deadline is more important than providing a working OS? Not sure if that's wise. They probably didn't have enough time for everything. I just hope that in the end it'll be a better OS. 
But they've "shot themselves in the leg" - because on one hand they promote it like the great netx thing, but on the other many people attracted to it will be seriously dissapointed after trying it and might not decide to go anywhere near ubuntu in the future.

As you said - a working (DSL) internet connection is like a must nowadays - but the problem is that this is not the only trouble, there're lot's of other bugs in it. Ah well... it is how it is. Maybe I'll give it another try after a while.

Cheers!

Hornless.:D :popcorn: I'll eat my popcorn now...
[/B]

---

### Post by 600WPMPO on 2009-11-03
Well Hornless, just for the record: 

Rax0 says, try these new files to connect to the net with DSL:

you need to install all these files to fix the problem

```

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-glib2_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-glib2_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-util1_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-util1_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/m/modemmanager/modemmanager_0.2.git.20091031t001131.107f950-0ubuntu2~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/m/modemmanager/modemmanager_0.2.git.20091031t001131.107f950-0ubuntu2%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091102t055646.67067af-0ubuntu2~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8%7Ea%7Egit.20091102t055646.67067af-0ubuntu2%7Enmt1_i386.deb")


```those are for i386 only.

I tried but could not succeed. I think I have done so many interventions earlier that the system is screwed up. May be a fresh install will work.

Lets see if someone tries them out successfully. 

**My Koala is sleeping till then:**

[IMG]http://i34.tinypic.com/2i12geu.jpg[/IMG]

---

### Post by 600WPMPO on 2009-11-03
Yes..!!! Finally I'm able to connect to the net via DSL in Karmic..!!!!!!

The files in the post above (post #20) work fine & should be tried by anyone having similar troubles...

**Hornless, I guess you may give it another try** :lolflag: 


**Edit (5 Hours Later): **

My happiness was short lived.

Here's what happened:

When I posted last, I just installed the files in post #20 and restarted the system. It connected to the net. I opened firefox, posted here on ubuntuforums and happily shut down. 

Then, after 4-5 hours later, I turn on my computer and try to connect to the net, but again the "insufficient privileges" error messages comes. Then DSL authentication would ask again and again for my password. 

I'm again offline.

Now I'm getting real mad....... :mad:

What am I doing? Looking at network manger and playing a sad tune on my violin  :-({|=

---

### Post by Hornless_Unicorn on 2009-11-04
> **600WPMPO said:**
> Yes..!!! Finally I'm able to connect to the net via DSL in Karmic..!!!!!!

The files in the post above (post #20) work fine & should be tried by anyone having similar troubles...

**Hornless, I guess you may give it another try** :lolflag: 


**Edit (5 Hours Later): **

My happiness was short lived.

Here's what happened:

When I posted last, I just installed the files in post #20 and restarted the system. It connected to the net. I opened firefox, posted here on ubuntuforums and happily shut down. 

Then, after 4-5 hours later, I turn on my computer and try to connect to the net, but again the "insufficient privileges" error messages comes. Then DSL authentication would ask again and again for my password. 

I'm again offline.

Now I'm getting real mad....... :mad:

What am I doing? Looking at network manger and playing a sad tune on my violin  :-({|=

Oh - darn! I thought it finaly worked. I had the same trouble when using the shell, it only worked sporadically. By the way I just fried the BIOS on my older PC LOL, bad luck I guess (and a good portion of stupidity on my part). I found the same board - so I'm going to rebuild it - anyways - it'll be a while untill I can install Ubuntu again :(, but I'll install jaunty 64bit that's for sure ;) 

I know what's wrong with Koala - it doesn't get enough eucaliptus leaves around where I live ;) 

But the whole story shows that it can happen to anyone (i.e. releasing a crappy OS). Maybe people should stop bitching and blaming and concentrate on producing the best OS :D

---

### Post by Louigi Verona on 2009-11-04
I tried these fixes. Now all my old Network settings are gone and network manager doesn't even detect any network cards and if I create a network connection, as soon as I press ok and enter that keyring thing, the window disappears but no connection is created.

Overall, this is THE major bug which in my opinion should have been fixed immedeately. But so far I can only see open bugs everywhere and not a single person saying he found a solution other than using pppoeconf.

I do not understand how an OS could have been released with such a bug. Don't developers use DSL?

At this moment I feel ashamed that I have supported Ubuntu on so many occasions and yesterday all my friends could see that I upgraded to an OS that can't do such a basic thing as go to the Internet.

Ubuntu depends on Internet, being able to connect should be the top most priority.

At this moment there is no solution. I am afraid this is a major problem which is serious enough to denounce the whole pathos of the new Ubuntu. Bugs happen, but bugs like this one should be fixed asap.

---

### Post by Hornless_Unicorn on 2009-11-04
One could say that with Karmic Koala (as it is now) canonical commited nothing less than selfsabotage on a major scale, funny thing is that I read that they still denounce and belittle windows 7 - but what have they created this time round?

Don't get me wrong, but this whole affair is just ridiculous! Free or not free you should not unleash a system like that with big fanfares and than keep quiet about it's numerous shortcomings - what went wrong? 

If you wonder I'm not writing this because I'm against linux, but because I'm for Linux - I'm just dissapointed and puzzled...

---

### Post by P4man on 2009-11-04
I dont know if you guys are still looking for a solution, but if you do..
Im assuming when you say DSL that you mean an ethernet connection to a xDSL modem/router, right?

If network manager reports a disconnected cabel thing "no connection", then edit the settings for the auto ethernet and enable the "available to everyone" checkbox at the bottom. That seems to cure it for many.

On some network cards you also have to specify the MTU. Rather than automatic, set it to 1500.

Lastly if all else fails, remove network manager and install wicd instead.

---

### Post by 600WPMPO on 2009-11-04
> **P4man said:**
> I dont know if you guys are still looking for a solution, but if you do..
Im assuming when you say DSL that you mean an ethernet connection to a xDSL modem/router, right?

If network manager reports a disconnected cabel thing "no connection", then edit the settings for the auto ethernet and enable the "available to everyone" checkbox at the bottom. That seems to cure it for many.

On some network cards you also have to specify the MTU. Rather than automatic, set it to 1500.

Lastly if all else fails, remove network manager and install wicd instead.


I doubt that wicd will work in Karmic. There's already a bug posted: [Bug 388110] [NEW] wicd not recognizing wired connection in karmic

here [https://lists.ubuntu.com/archives/universe-bugs/2009-June/102127.html]("https://lists.ubuntu.com/archives/universe-bugs/2009-June/102127.html")

However, other 2 solutions look promising:

1) edit the settings for the auto ethernet and enable the "available to everyone" checkbox at the bottom

2)set MTU to 1500 ... Here I'd like to say that I've never required setting MTU to any value till Jaunty. I'll try it anyway

I'll post the results here soon..

Thanks for helping

---

### Post by P4man on 2009-11-04
> **600WPMPO said:**
> I doubt that wicd will work in Karmic. There's already a bug posted: [Bug 388110] [NEW] wicd not recognizing wired connection in karmic

wicd works (and is in the repo's) and switching to it solved wired connection problems for at least one person I suggested it to (using karmic) 

Of course YMMV.

---

### Post by Louigi Verona on 2009-11-04
Hornless: Yeah, I hear you. I am also for GNU/Linux and free software ideals. And it is disappointing that Karmic has been released with so many regressions.

After I couldn't launch a game in Wine (I could but it was VERY slow, I spend 2 minutes trying to get with my mouse to the Exit button), turn off my touchpad (I check Disable in Preferences-Mouse, but nothing changes) and when the sound once more disappeared without any warning, I decided that the decision to upgrade was bad. I trusted that Ubuntu releases should be stable thx to the community testing, but what I saw were bugs which people reported as early as alpha stage but nobody ever fixed them. I am also puzzled. I mean, this DSL thing is a blocker for a release, but nobody fixes it and actually nobody even mentions it. If you go to fsdaily, they only say how Karmic is perfect. Well, I am sorry - a computer that cannot connect normally to the Internet and has no sound is not a perfect OS to me.

P4man: I am interested, but unfortunately now Network Manager says Wired Networks are disabled or disconnected, so no matter what I do - all options are greyed out. I can create a connection, but it does not show up in the list and Network Manager is mute. It may do smth with pppoeconf connecting at boot - I wish I could turn this option off to see if this is teh reason, but I don't know how and I have not much time (and desire) to go spend hours reading it out on the Internet.

All in all, today I really need to do some work which requires no sound, but tomorrow I am deleting the system and installing 9.04 back. Unfortunately, Karmic is Ubuntu's Vista.

---

### Post by Hornless_Unicorn on 2009-11-04
> **P4man said:**
> I dont know if you guys are still looking for a solution, but if you do..
Im assuming when you say DSL that you mean an ethernet connection to a xDSL modem/router, right?

If network manager reports a disconnected cabel thing "no connection", then edit the settings for the auto ethernet and enable the "available to everyone" checkbox at the bottom. That seems to cure it for many.

On some network cards you also have to specify the MTU. Rather than automatic, set it to 1500.

Lastly if all else fails, remove network manager and install wicd instead.

Thanks for the tip, but as I said earlier, I can't try it out, have to get my PC back together first and I will not install Karmic on my main PC.

Cheers,

Hornless.

---

### Post by 600WPMPO on 2009-11-04
> **Louigi Verona said:**
> P4man: I am interested, but unfortunately now Network Manager says Wired Networks are disabled or disconnected, so no matter what I do - all options are greyed out. I can create a connection, but it does not show up in the list and Network Manager is mute. It may do smth with pppoeconf connecting at boot - I wish I could turn this option off to see if this is teh reason, but I don't know how and I have not much time (and desire) to go spend hours reading it out on the Internet.

All in all, today I really need to do some work which requires no sound, but tomorrow I am deleting the system and installing 9.04 back. Unfortunately, Karmic is Ubuntu's Vista.

the same happened to me What I did was (courtesy rax0):

[B]open /etc/NetworkManager/nm-system-settings.conf as root 

edit "managed=false" to "true" then save and restart,[/B] 

I think it'll work... tell me the results

-------------------------------------------------------

**Edit (1 hour later): **

> **P4man said:**
> I dont know if you guys are still looking for a solution, but if you do..
Im assuming when you say DSL that you mean an ethernet connection to a xDSL modem/router, right?

If network manager reports a disconnected cabel thing "no connection", then edit the settings for the auto ethernet and enable the "available to everyone" checkbox at the bottom. That seems to cure it for many.

On some network cards you also have to specify the MTU. Rather than automatic, set it to 1500.

Lastly if all else fails, remove network manager and install wicd instead.

[COLOR="DarkRed"]**Yessir P4man !!! It works again..!! I'm online.**[/COLOR]

I edited the settings for the auto ethernet and enabled the "available to everyone" checkbox. I then set MCU to 1500. But, I was confused whether I had to change MCU for auto ethernet or for DSL. So, I didn't change it for auto ethernet, but rather for DSL connection.

Anyway, I'm able to connect to net for the time being. Still, I have to click 2-3 times at NM icon at startup to connect. I fear it won't last long.


-------------------------------------------

**Edit (10 Hours Later)**:

Still Online, everything working fine..!!

I guess its now okay to put a "[Solved]" box before the thread title..

---

### Post by Hornless_Unicorn on 2009-11-05
> **600WPMPO said:**
> 


[COLOR=DarkRed]**Yessir P4man !!! It works again..!! I'm online.**[/COLOR]

I edited the settings for the auto ethernet and enabled the "available to everyone" checkbox. I then set MCU to 1500. But, I was confused whether I had to change MCU for auto ethernet or for DSL. So, I didn't change it for auto ethernet, but rather for DSL connection.

Anyway, I'm able to connect to net for the time being. Still, I have to click 2-3 times at NM icon at startup to connect. I fear it won't last long.


-------------------------------------------

**Edit (10 Hours Later)**:

Still Online, everything working fine..!!

I guess its now okay to put a "[Solved]" box before the thread title..

That's great news! Thanks P4man,  600WPMPO and everybody else who took part and as soon as I can I'll try it out. Of course it's only a workaround (is it?), ideally Karmic should do it out of the box, hopefully the bug will be fixed by an update sometime in the future, but I put "solved" before the title. 

Later,

Hornless.

---

### Post by P4man on 2009-11-05
> **600WPMPO said:**
> the same happened to me What I did was (courtesy rax0):

[B]open /etc/NetworkManager/nm-system-settings.conf as root 

edit "managed=false" to "true" then save and restart,[/B] 

I think it'll work... tell me the results

-------------------------------------------------------

**Edit (1 hour later): **



[COLOR="DarkRed"]**Yessir P4man !!! It works again..!! I'm online.**[/COLOR]

I edited the settings for the auto ethernet and enabled the "available to everyone" checkbox. I then set MCU to 1500. But, I was confused whether I had to change MCU for auto ethernet or for DSL. So, I didn't change it for auto ethernet, but rather for DSL connection.

Anyway, I'm able to connect to net for the time being. Still, I have to click 2-3 times at NM icon at startup to connect. I fear it won't last long.



You obviously have to set those settings for the connection you are using. I just use "auto ethernet" but that is just a name, so if you made another new connection called DSL then set it there and check the "connect automatically" for that "DSL" connection. Each connection is just a set of settings. You probably only need 1. At least make sure you apply all settings to that 1 and select that one to connect automatically and you should normnally not have to click anything at bootup.

BTW can you experiment a bit by disabling some of my suggestions again and seeing which one actually solved it? If its the MTU setting id like to see what network card you have (lspci). You may also want to file a bug report so its fixed eventually.

---

### Post by Hornless_Unicorn on 2009-11-05
> **P4man said:**
>  You may also want to file a bug report so its fixed eventually.

P4man: As far as I know this bug was allready present in testing versions of Karmic and is reported since then: [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933)

I might be wrong but it seems to be the same old bug(?)

This might also be of interest (not about DSL) but it's another bug that I've also encountered while I tried Karmic:

[http://ubuntuforums.org/showthread.php?t=1313536](http://ubuntuforums.org/showthread.php?t=1313536)

Seems like the new kernel causes problems! All in all I'll probably install Jaunty and maybe make a partition for Karmic (Test-Laboratory). But before that I'll have to put some hardware together :)

---

### Post by P4man on 2009-11-05
> **Hornless_Unicorn said:**
> P4man: As far as I know this bug was allready present in testing versions of Karmic and is reported since then: [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933)

I might be wrong but it seems to be the same old bug(?)



It looks entirely different to me? Both the symptoms and the solution (and therefore the cause)

---

### Post by 600WPMPO on 2009-11-05
> **P4man said:**
> BTW can you experiment a bit by disabling some of my suggestions again and seeing which one actually solved it? If its the MTU setting id like to see what network card you have (lspci). You may also want to file a bug report so its fixed eventually.

Actually P4man, it is not as smooth as you say or Karmic promises.

What happens is that a connection named "Autoeth0" is present as I make a fresh install of Karmic (or any Ubuntu distribution). It does not require any username/password. It does not serve any direct purpose to me. When I boot into the system, it is connected automatically. To connect to the net, I have to make a DSL connection fron the DSL tab of NM. I input my username/password, and now I also set MTU to 1500. I check "connect automatically", but I do not check "available to all users"

Now, any difference in this combination of events, breaks the connection (even now). Any difference, like e.g. unchecking "connect automatically" from Autoeth0 connection.

So, its like.. hanging from a thread, you see..

The net is working fine.. but any experimentation leads to the same error messages "insufficient privileges", "disconnected" etc.

P4man, can you help..?!

---

### Post by P4man on 2009-11-05
> **600WPMPO said:**
> 
P4man, can you help..?!

I can try but I have no experience with the DSL connection as thankfully, I have a (A)DSL router, not a modem as you seem to have. I configure password and stuf in the router interface and any machine can connect to the router be it wired or wirelessly using just "auto" DHCP settings.

Anyway, just to say that Im not 100% certain of what Im about to write, but it looks like if you need to use the DSL tab, you do not need (and should not use) the "wired" tab, The connection in wired I would guess can even be removed. You should apply all the mentioned settings in the connection you configured under DSL, the auto connect, available to all users, and possibly the MTU size if you have one of those semi-broken onboard gigabit ethernet controllers.

---

### Post by 600WPMPO on 2009-11-05
> **P4man said:**
> Anyway, just to say that Im not 100% certain of what Im about to write, but it looks like if you need to use the DSL tab, you do not need (and should not use) the "wired" tab, The connection in wired I would guess can even be removed. You should apply all the mentioned settings in the connection you configured under DSL, the auto connect, available to all users, and possibly the MTU size if you have one of those semi-broken onboard gigabit ethernet controllers.

Ok, I'll try that today and post the results here..

Thanks anyway P4man, you have been very helpful..:D

p.s. Hope someone would convince my friend Hornless_Unicorn to try out Karmic... (so that I'd have another head to bang with !!) ;)

---

### Post by Hornless_Unicorn on 2009-11-05
> **600WPMPO said:**
> Ok, I'll try that today and post the results here..

Thanks anyway P4man, you have been very helpful..:D

p.s. Hope someone would convince my friend Hornless_Unicorn to try out Karmic... (so that I'd have another head to bang with !!) ;)

LOL :)

I will try it :) But right now my old PC lies in ruins (I tried to update the bios) I'm waiting for the identical board (found one on ebay) and will restore my system. That'll be my Linux machine and I'll probably install Jaunty and Karmic side by side - so I can experiment with Karmic. 

So how's your experience with it so far? I've had other freezes and the kernel crash warning all the time (back when I still had it on my PC). Did you or do you get the crash warning?

By the way is there some nick you have other than 600WPMPO? Cause it's kinda clumsy to write "hey 600WPMPO how have you been?" hehe ;)

P4man: Thanks for your help :)

---

### Post by 600WPMPO on 2009-11-05
> **Hornless_Unicorn said:**
> LOL :)
So how's your experience with it so far? I've had other freezes and the kernel crash warning all the time (back when I still had it on my PC). Did you or do you get the crash warning?

So far, it has been absolutely fine.. quite like I expect from ubuntu (that is, except the DSL disaster)

I have updated the system, enabled medibuntu and restricted extras, installed a few softwares I use. Installed Nvidia graphics v190. System is stable, no crash warnings till yet. Its fast and looks good. 

Currently I'm busy modifying Grub2 appearance. People here are helping me out. Eventually, I'll learn everything about Grub and change it to my liking.

> **Hornless_Unicorn said:**
> By the way is there some nick you have other than 600WPMPO? Cause it's kinda clumsy to write "hey 600WPMPO how have you been?" hehe ;)

You can call me "Salvatore"...!! Can't change the ugly nickname as its too late now.... :lolflag:

keep in touch..

-----------------------------------

**Edit:**

> **P4man said:**
> Anyway, just to say that Im not 100% certain of what Im about to write, but it looks like if you need to use the DSL tab, you do not need (and should not use) the "wired" tab, The connection in wired I would guess can even be removed. You should apply all the mentioned settings in the connection you configured under DSL, the auto connect, available to all users, and possibly the MTU size if you have one of those semi-broken onboard gigabit ethernet controllers.

Well P4man, I tried what you said, but found 2 things:

1. I cannot permanently delete Autoeth0, as it reappears everytime system reboots. But when I delete it during a session , DSL connects automatically

2. DSL doesn't connect if I check "make available to all users" in the DSL tab. Incidentally, if you remember, I was not able to connect if I didn't check "make available to all users" in the Wired tab. Though I have no problem with that, it is still a wide open bug..

---

### Post by bbqsauced on 2009-11-05
I've tried the fixes you've listed on this thread, and it doesn't seem to be working for me.  Same situation and everything too.

Is it because I don't have the files?  All of the links pull up 404 not found pages now.

---

### Post by SawyerLX on 2009-11-05
9.10 Network manager is buggy! Would not connect, went through pppoeconf. Both beta RC and Final have same bug.  after, change-> goes broke TO ifupdown (eth0) under gui network manager and no dsl connection!?

---

### Post by 600WPMPO on 2009-11-05
> **bbqsauced said:**
> I've tried the fixes you've listed on this thread, and it doesn't seem to be working for me.  Same situation and everything too.

Is it because I don't have the files?  All of the links pull up 404 not found pages now.

Here, for you only dear, I have attached 4 files below and uploaded the 5th one to mediafire (cannot attach because of size restriction):

```
http://www.mediafire.com/download.php?5zmnxjqnmht
```

Download all the 5 files & install..

However, newer files may be available at launchpad, but I have these only (see post #20) and these work for me..

tell me the result..

---

### Post by bbqsauced on 2009-11-06
Thanks man, that did the trick.  I'm using XFCE so one of the files had an error, but hey I'm now posting this from my 9.10 install so I can't complain.  Props.

---

### Post by Louigi Verona on 2009-11-10
This worked for me too, however I had to connect a connection from scratch.

---

### Post by p1977p on 2009-11-27
The problem is solved by installing the [Network Manage]("https://launchpad.net/%7Enetwork-manager/+archive/trunk")r trunk on lunchpad

---

### Post by 600WPMPO on 2009-11-30
Here is a post from [How to setup NetworkManager work with pppoe connection on Ubuntu 9.10]("http://blogs.gnome.org/happyaron/2009/11/27/getting-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10/"), which is relevant to this thread & may prove helpful:

> In Ubuntu 9.10, pppoe connection via NetworkManager is impossible because of some bug in it so to fix this we will install network manager from daily network manager trunk ppa:
Install network manager from Daily trunk PPA

First you need to edit the /etc/apt/sources.list file

    ```
gksudo gedit /etc/apt/sources.list
```

Add the following two lines

    ```
deb http://ppa.launchpad.net/network-manager/trunk/ubuntu karmic main
deb-src http://ppa.launchpad.net/network-manager/trunk/ubuntu karmic main
```

Save and exit the file

Update the source list

    ```
sudo apt-get update

```
Install network manager

    ```
sudo apt-get install network-manager
```

Configure pppoe

Disable your previous &#8220;pppoe on boot&#8221; setting which is configured by pppoeconf.

Edit /etc/ppp/pppoe_on_boot file

    ```
gksudo gedit /etc/ppp/pppoe_on_boot
```

change

    ```
exec pppd call dsl-provider
```

to

    ```
#exec pppd call dsl-provider
```

Now you need to rename /etc/network/interfaces to backup file. NetworkManager will only handle connections which haven&#8217;t declared in interfaces.

$cp /etc/network/interfaces /etc/network/interfaces.back

Also edit /usr/share/polkit-1/actions/org.freedesktop.network-manager-settings.system.policy , find out the line contains &#8220;System policy prevents modification of system settings&#8221;, and below it there is a &#8220;auth_admin_keep&#8220;, change it to &#8220;yes&#8220;. This will enable you to edit a system wide connection. If you consider this will do harm to your security, then revert the change once you have set up your connection correctly.

Finally reboot your system

---

### Post by wm_brant on 2009-12-08
The above solution probably works, but since it requires a working DSL connection in order to get a working DSL connection, at some level it's wrong, not to mention being a paradox.

I've tried upgrading from 9.04 to 9.10 twice now.  In both cases, everything looked good after the upgrade, except I cannot connect to the Internet through my DSL connection.  Since I have only one computer at home, when it can't connect to the Internet, I'm stuck.

The last time I tried, I even had information about using pppoe.  However, that was some time ago, and 'back then' there was a lot of conflicting advise about which suggested fixes worked, and which did not.  To make a long story short, I was unsuccessful in making things work.  Both times I tried going to 9.10 I had to revert back to 9.04 and re-load all my data, and re-install my programs.

I'm not willing to try the upgrade to 9.10 again until I believe that the normal upgrade process will result in a working DSL connection - is this too much to ask?

---

### Post by rahilm on 2009-12-08
open firefox and enter 74.125.65.105 in the address bar and press enter.. Reply with what you see

---

### Post by wm_brant on 2009-12-08
A Google English page.

I'm currently running 9.04 AMD64.  Browser is Shiretoko.

---

