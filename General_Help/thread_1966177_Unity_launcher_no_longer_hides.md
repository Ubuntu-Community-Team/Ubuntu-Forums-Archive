---
title: "Unity launcher no longer hides"
date: 2012-04-26
forum: General Help
---

### Post by cogadh on 2012-04-26
Prior to the 12.04 upgrade, the Unity launcher would automatically hide itself when I maximized an application and only re-appear when I minimized the app or moved the mouse over to the left edge of the screen. After the upgrade, applications maximize up to the launcher edge and it does not hide at all. I tried setting the the auto-hide option in CompizConfig, but all that seems to do is hide launcher all the time and moving the mouse to the left won't even bring it back. Did I miss something? Is this the way Unity is supposed to behave now?

---

### Post by NoNameWill on 2012-04-26
Try System Settings>Appearances>Behavior 

Set the sensitivity scale.

Also just to make sure what graphics card do you have?

---

### Post by cogadh on 2012-04-26
Sensitivity doesn't change anything, the launcher stays hidden (when autohide is enabled). When I do set the autohide option I can see a slight color change when the mouse hits the left side of the screen, like a shadow of the launcher appearing, but the launcher itself stays hidden (the only way to make it come back is to hit the "super" button). However, the problem is autohiding is not what I want it to do anyway. I only want the launcher to hide when I maximize applications, the way it has worked since I first used Unity (what is it, 2 or 3 Ubuntu versions with it now?). Autohide hides the launcher all the time, whether or not I have anything open at the moment.

This is an older laptop with a Radeon Xpress 200M running the free drivers. The Catalyst drivers are not an option for this model, it is no longer supported, but the free driver has been good enough up until now, I can't imagine it could suddenly be a factor now.

---

### Post by mace2 on 2012-04-26
I'm having the same problem, when I set the launcher to auto-hide half of the time it won't appear when I mouse over the left side of the screen.

Instead, it will just show a tiny drop shadow half the time. Really really annoying, needs to be fixed.

---

### Post by DaveDeviant on 2012-04-26
HP G62 with a Radeon HD 5470, auto-hide option working perfectly from settings-behavior.

---

### Post by mc4man on 2012-04-26
Dodge is gone, both forms. The only options now are never hide & auto hide, (always hide

---

### Post by cogadh on 2012-04-26
Yeah, I was just reading a mail list post from Mark Shuttleworth about it. Unfortunately, the Ubuntu devs once again mis-judged their users preferences and completely removed the feature, rather than leaving it in as an option as they should have done. The default "never hide" is frankly ugly and obviously the "auto(always) hide" doesn't work correctly, plus for new users it starts them off with a desktop that has little to no obvious functionality (smart move there). It seems to me that Ubuntu is heading down the path that many open source projects that get "big" eventually go down: they lose touch with the majority of users and make decisions based solely on the feedback of a small group of "in" people.

---

### Post by grahammechanical on 2012-04-26
From what I read doge windows was removed as a response to user feed back.

It just goes to prove to me the truth of the saying: You can't please everyone, so you'd better please yourself.

The feature or the removal of it was thoroughly tested. I know I shared in testing it when Unity was upgraded to 5.2, 5.4, 5.6 and 5.10 before each of these revisions was brought into Precise.

Regards.

---

### Post by cogadh on 2012-04-26
I'm sure it was tested, but only tested by a small percentage of Ubuntu users who have an active interest in Ubuntu development. The rest of us who just *use* Ubuntu as our daily OS have plenty of "regular life" things to do that are far more important to us than making sure a simple feature of Ubuntu that just makes sense once you use it actually stays in the OS. Had I known that there was even a chance that something as basic as this might be changed, I might have taken the time to get involved, but it makes no sense to me that they would even consider changing something like that, and I'm sure I'm not alone in this. Not to mention, user feedback is always going to be biased to the negative. People who hate something are far more likely to tell you they hate it than people who are simply comfortable using it. Like I said, it's par for the course with projects like this that get way, *way* bigger than the small group of people actively participating in its development.

---

### Post by mortsemious on 2012-04-26
I have a bit of a work around to make it like 11.10.

There are two packages on this page: [http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html](http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html)

Download and install unity-dodge-maximized-windows. This will hide the launcher when maximized and when not maximized it will show the launcher. Unfortunately window dodge does not work with this package, I think it works with the other though. But, you can't have both of them at the same time.

To make the launcher activate when mouse contacts with left side, launch appearance and go to behaviors. Put sensitivity as high as possible. To make the launcher appear drag the mouse quickly to the left side, make sure you do it quickly or else the launcher won't appear.

I hope this helps

---

### Post by mc4man on 2012-04-26
I don't particularly miss on a 13" laptop where I find I always want the launcher - on a small screen I need access to it more than on my 22" in. screen where more windows can fit visibly. Anyway, so what.

It is ironic that an Option that many liked & found useful is not retained, based on not keeping code paths around ect. when they then add unity greeter options that No normal user could ever use. Kinda hypocritical really.

There is a script discussed & linked thru out this thread that to some extent returns part of dodge

last page, if interested also read back a bit 
[http://ubuntuforums.org/showthread.php?t=1937199&page=3](http://ubuntuforums.org/showthread.php?t=1937199&page=3)

---

### Post by cogadh on 2012-04-26
> **mortsemious said:**
> I have a bit of a work around to make it like 11.10.

There are two packages on this page: [http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html](http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html)

Download and install unity-dodge-maximized-windows. This will hide the launcher when maximized and when not maximized it will show the launcher. Unfortunately window dodge does not work with this package, I think it works with the other though. But, you can't have both of them at the same time.

To make the launcher activate when mouse contacts with left side, launch appearance and go to behaviors. Put sensitivity as high as possible. To make the launcher appear drag the mouse quickly to the left side, make sure you do it quickly or else the launcher won't appear.

I hope this helps
^^
And that just goes to prove my point. Ubuntu changes something, it surprises the "regular users" like me, and then someone else goes to the effort to create something to try to change it back.  Unfortunately, as is also often the case, the fix is not as good as the way it was. Ubuntu could have avoided all this by just leaving it as an option. I actually find it offensive that they removed it because they considered the concept of "dodge" to be too confusing to users. What kind of low opinion must they have of their user's intelligence if an autohiding "task bar" is too confusing for them? It's only been part of Windows as an option for at least 15 years now and no one has ever had a problem with it there. The only difference is the Unity launcher would unhide itself when no apps were running in full screen, which was *brilliant*. Yeah, *way* too confusing for us.

Thank you for that link, I will definitely try it out.

---

### Post by NoNameWill on 2012-04-26
Just got 12.04 installed on older 32 bit Dell laptop with a ati graphics card. Seems to work better than the nvidia card drivers. Auto-hide works and sensitivity is set to bring up the panel without lag or doing the side screen rub :P. 

On my main laptop I will not be upgrading to 12.04 on my main OS.

---

### Post by cogadh on 2012-04-26
Yeah, I found that if I set the sensitivity to its maximum (and only if it is set to maximum), then I can "rub" the launcher into coming out. I feel kind of dirty when I do it though. :oops:

EDIT - And now I find that if I set my trackpad sensitivity to ridiculous heights, the launcher appears like it used to, but trying to use my mouse is like driving a car drunk.

---

### Post by Gyokuro on 2012-04-27
Hi

I have an Intel HD3000 and auto-hide works out of the box.

---

### Post by cogadh on 2012-04-27
No offense intended to those that posted these things (really), but how in any way does it help me for you to tell me that it works fine for you? It's like a 5 year old taunting another kid on the playground "Nya, nya, mine works and yours doesn't!" I posted in the General ***Help*** forum because I wanted ***help***, not further confirmation that it is not working the way it is supposed to on my system, I already know that it is not working the way it is supposed to. Granted, we may have gotten a little off-topic with my rant about the direction Ubuntu is taking, but I am still having a problem here and I am still looking for solutions, which those kinds of posts are not. Thanks for your input, but can we try to keep it to actually productive input?

---

### Post by cogadh on 2012-04-28
For those interested, I found the perfect solution, a custom compiled Unity with dodge built back in. Full instructions here:
[https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior](https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior)

---

### Post by PayPaul on 2012-05-01
I have a similar problem. I have Oneiric still but can't find the functionality in System Settings/Appearance for hiding or customizing the Launcher. I don't mind Unity too much but I'm thinking of searching for a way to get the Classic Gnome interface instead. I can see a very crowded launcher in my future.

Where are the settings for customizing the Launcher in Oneiric Ocelot? Are there any at all in Pangolin?

---

### Post by PayPaul on 2012-05-01
> **cogadh said:**
> No offense intended to those that posted these things (really), but how in any way does it help me for you to tell me that it works fine for you? It's like a 5 year old taunting another kid on the playground "Nya, nya, mine works and yours doesn't!" I posted in the General ***Help*** forum because I wanted ***help***, not further confirmation that it is not working the way it is supposed to on my system, I already know that it is not working the way it is supposed to. Granted, we may have gotten a little off-topic with my rant about the direction Ubuntu is taking, but I am still having a problem here and I am still looking for solutions, which those kinds of posts are not. Thanks for your input, but can we try to keep it to actually productive input?

I have to agree with you. It does seem that from the posts of people for whom the "hide" function works that its functionality would be related to their different machines. That doesn't make too much sense. A function like this should be somewhat independent of the machine specifications. They provide or have no clue as to why it works. What could be different is the way they installed Ubuntu? I also don't get a sense that some here are using the same flavor ie: Ubuntu, Xubuntu or Lubuntu. Could each of these flavors have differences in functionality?

---

### Post by zander1013 on 2012-05-03
> **cogadh said:**
> For those interested, I found the perfect solution, a custom compiled Unity with dodge built back in. Full instructions here:
[https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior](https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior)

hi,

ty for the diligence to find this work around a share it.

i was having similar problems as you described on my dell mini 9 (9inch screen) because the screen is compact i need every bit of it.

i could not get the launcher to appear at all before applying your workaround only the drop shadow would appear.

i would note that after applying your workaround it requires a double tap with the sprite to cause the launcher to appear.

---

### Post by dzsobacsi on 2012-05-09
I had the same problem. I looked around for some solution including this thread. I decided not to install any kind of scripts or whatever but to give a chance to Gnome 3. 
Now, as I have been using it for some days and after installing some extensions to it I am veeeery satisfied with it and actually I like it much more than Unity ever before.

---

