---
title: "Ubuntu Classic unusable in 11.04"
date: 2011-05-01
forum: General Help
---

### Post by timgood on 2011-05-01
So if we don't like Unity or the way it crashes with alarming regularity, the fact that it requires multiple mouse clicks to do things we used to do with a couple and the fact that the launcher is not configurable in any meaningful way, we can always go back to Ubuntu Classic, right? Wrong!

Trying to enable desktop effects in Classic under amd64 and NVidia proves something of a nightmare. 

1. There is no 'Desktop Effects' tab anymore. We are told that this is no longer necessary as Compiz is running by default. 

2. Jockey reports that the NVidia driver is installed and that the driver is activated but 'not currently in use'. This is a bug and has been reported. However, this could tempt people to uninstall and re-install the driver (I am one of these) with disastrous results.

3. Trying to enable things like the Cube and Cube rotation break Compiz and remove *all* the settings in CCSM. Window menus and borders disappear and have to be restored by resetting the Window Manager to Metacity.

4. Getting applications like Radio Tray or Shutter to show in the System Tray involves circuitous circumventing of a 'Whitelist' (which is there for our protection because we shouldn't really want to use applications which put icons in the tray!) is really going to put off people installing applications which then apparently don't work. (They do work, they just become unusable because you cant see them or do anything with them!)

5. Skype will sometimes load and sometimes won't. Sometimes the sound is corrupted and sometimes not. Despite the fact that Skype is proprietary software, many people need to use it. If it becomes unreliable many people will look elsewhere or go back to Wingedows.

6. In both Unity and Classic the task bar will randomly freeze and become unresponsive, requiring a reboot.

Natty Narwhal? More like Natty Dread at the moment. I dread turning it on and it is dreadful. I'll try Gnome 3 or go back to 10.10. I can no longer recommend Ubuntu as a viable alternative to Windows to my customers.

---

### Post by marl30 on 2011-05-01
[B]I can no longer recommend Ubuntu as a viable alternative to Windows to my customers.
[/B]
This statement is rather unfair. There are still two other versions of Ubuntu that is still supported (10.04 and 10.10). Plus there are several other versions of Ubuntu with different desktop environments. 

Natty for Ubuntu (flagship desktop not the others) still has a way to go. It should see some bug fixes in updates in a few more weeks. So just give it some more time.

---

### Post by vanadium on 2011-05-01
There is no "Desktop effects" tab no more. The way you decide to run compiz (desktop effects) or metacity (2D environment) is now by choosing the appropriate session. You can choose to use the classic Gnome interface with or without desktop effects.

---

### Post by timgood on 2011-05-01
> **vanadium said:**
> There is no "Desktop effects" tab no more. The way you decide to run compiz (desktop effects) or metacity (2D environment) is now by choosing the appropriate session. You can choose to use the classic Gnome interface with or without desktop effects.

Indeed you can. But it still doesn't bloody work. If you had taken the trouble to read my original post, it is about Classic being broken. If using compiz as window manager I lose my window menus and borders. If I use metacity I can't enable any effects. In 10.10 I was able to enable desktop effects while still using metacity. Well and truly Bjorked.

The reason I cannot recommend Ubuntu to business users anymore is not because 10.10 doesn't work (it does and it is fantastic) it is that users will be tempted to upgrade and bugger their systems. You know users. They will.

---

### Post by bhaskar on 2011-05-02
[http://fossplanet.com/f10/%5Bbug-771847%5D-%5Bnew%5D-%5Bregression-%5D-no-way-enable-desktop-effects-inclassic-session-138948/]("http://fossplanet.com/f10/%5Bbug-771847%5D-%5Bnew%5D-%5Bregression-%5D-no-way-enable-desktop-effects-inclassic-session-138948/") suggested installing compizconfig-settings-manager.  I did and I now have visual effects in Ubuntu classic on 11.04.

---

### Post by madjr on 2011-05-02
> **timgood said:**
> 

4. Getting applications like Radio Tray or Shutter to show in the System Tray involves circuitous circumventing of a 'Whitelist' (which is there for our protection because we shouldn't really want to use applications which put icons in the tray!) is really going to put off people installing applications which then apparently don't work. (They do work, they just become unusable because you cant see them or do anything with them!)


6. In both Unity and Classic the task bar will randomly freeze and become unresponsive, requiring a reboot.

Natty Narwhal? More like Natty Dread at the moment. I dread turning it on and it is dreadful. I'll try Gnome 3 or go back to 10.10. I can no longer recommend Ubuntu as a viable alternative to Windows to my customers.

radiotray already has an app indicator (check online how to enable it) and shutter should be getting one soon.


you can also whitelist the tray completely:
as for your [http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

as for your customers, they should decide if they like it or not. You and your customers are not the same being. Some of them will even love unity.

recently, thx to unity, everyone asks me what OS am running or how i get my OS like that. I've never had that much response before. :)

the classic desktop is going away, so we must be supportive of the alternatives. We must help them mature.

if they dont like ubuntu, there's always xubuntu or kubuntu. and there's always the lts.

This is normal for a transition (actually its going smoother than expected) and by the next lts everything will be much better and we'll just laugh at how we had X issue, just like i laugh at issues we had back some time ago. :)

---

### Post by timgood on 2011-05-02
> **bhaskar said:**
> [http://fossplanet.com/f10/%5Bbug-771847%5D-%5Bnew%5D-%5Bregression-%5D-no-way-enable-desktop-effects-inclassic-session-138948/]("http://fossplanet.com/f10/%5Bbug-771847%5D-%5Bnew%5D-%5Bregression-%5D-no-way-enable-desktop-effects-inclassic-session-138948/") suggested installing compizconfig-settings-manager.  I did and I now have visual effects in Ubuntu classic on 11.04.

I did and I don't. See [http://teknolegy.blogspot.com/](http://teknolegy.blogspot.com/) for my experiences.

---

### Post by KVZTA on 2011-05-04
> **madjr said:**
> 
recently, thx to unity, everyone asks me what OS am running or how i get my OS like that. I've never had that much response before. :)


So you just like the recognition? Anyway, more importantly, I bounced up on this thread because I have the same issue, and it's seriously annoying me. But since I had to install 11.04 three times to 'get it right' only for it to break after an update [because Unity was initially working fine till I updated with the Update Manager then things went wrong after restart] I don't want to have to backup then downgrade... Long process AGAIN. 

Only reason why I'm waiting to see if they fix this issue, is because I'm too lazy to downgrade right now. But this is SERIOUSLY annoying

---

### Post by timgood on 2011-05-04
> **madjr said:**
> radiotray already has an app indicator (check online how to enable it) and shutter should be getting one soon.


you can also whitelist the tray completely:
as for your [http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

as for your customers, they should decide if they like it or not. You and your customers are not the same being. Some of them will even love unity

Why should some faceless **** decide for me which of the applications I choose to install on my computer should show up in my tray? Linux is about choice. Natty takes choice away. 

My customers are my customers because they find my advice on operating systems valuable. They come to me for advice. I won't advise them to use Natty until they have the same amount of choice and freedom that they have in 10.10

Linux is about freedom. Natty takes freedom away.

---

### Post by drseuk on 2011-05-04
Hi,

Clearly there are some issues that need urgent attention. On upgrading my T42 IBM Thinkpad from 10.10 to 11.04, Ubuntu informed me that my hardware was not good enough to run Unity (or words to that effect) so I had to use the Classic interface - that's fine by me.

After upgrading, the left mouse button on the laptop wasn't working which made things rather challenging - though it was amusing for a few minutes as as a web developer it opened my eyes to the real challenges faced by people with impairments who are unable to use mouses (trying to open the help to find out the keyboard shortcuts to use instead of the mouse was difficult enough!). 

Admittedly, my ***** had stomped over the keyboard during the upgrade and also managed to puke all over it. After I'd cleaned the ***** puke off it and recycled the ***** at the pet shop (cheaper than a new laptop), figuring that "It was the ***** what did it", I bought an external USB mouse at the computer shop.

To my surprise, the left button on this mouse didn't work either on my machine!

Fortunately, a friend of mine also has a T42 IBM Thinkpad which has also just been upgraded from 10.10 to 11.04 - the external mouse works perfectly on their (virtually identically configured) machine.

What gives? Any ideas?

> **timgood said:**
> Indeed you can. But it still doesn't bloody work. If you had taken the trouble to read my original post, it is about Classic being broken. If using compiz as window manager I lose my window menus and borders. If I use metacity I can't enable any effects. In 10.10 I was able to enable desktop effects while still using metacity. Well and truly Bjorked.

The reason I cannot recommend Ubuntu to business users anymore is not because 10.10 doesn't work (it does and it is fantastic) it is that users will be tempted to upgrade and bugger their systems. You know users. They will.

---

### Post by GreatKeyHunter on 2011-05-04
Have you given kubuntu a shot?  i never been a big fan of kubuntu since i had issues with it in the past. However, all i can say is that it is extremely well polished. it meets all my window management requirements that i need. Just like classic gnome did.

---

### Post by timgood on 2011-05-04
Finally got compiz working properly in classic by following instructions on this post: [http://ubuntuforums.org/showthread.php?p=10767302#post10767302](http://ubuntuforums.org/showthread.php?p=10767302#post10767302)

Hope this helps others.

---

### Post by drseuk on 2011-05-04
In case anyone's wondering, the censored, presumably black-listed, five letter word I used was "yssup" only reversed - common UK slang for a cat.

---

### Post by 3rdalbum on 2011-05-04
> **timgood said:**
> Why should some faceless **** decide for me which of the applications I choose to install on my computer should show up in my tray? Linux is about choice. Natty takes choice away.

The notification area is depreciated; it's been depreciated for two years and still program developers are yet to update their programs to follow. The whitelist exists to give you the choice. All indicator-aware programs appear in your "tray" (indicator area) and the non-indicator-aware programs that are whitelisted also appear in your "tray" (notification area).

If we don't depreciate old systems that don't provide a good desktop experience, nobody will ever change over to the new technology.

Natty adds choice. You can use Gnome Classic, you can use KDE, you can use XFCE or E17 or Window Maker; or you can use Unity. Unity is an additional choice on top of all the others. Your "customers" should probably be using an LTS version such as 10.04, and you should make sure it's set to notify on Long Term Service Releases, not Normal Releases. Having said that, if they updated to 11.04 there would probably not be any technical issues.

For most people, Unity is fine. Takes a little bit of getting used to, but then if you couldn't adapt to change then you wouldn't be a Linux user.

---

### Post by antiemptyv on 2011-05-04
i had that problem, too. this is what repaired it for me: in ccsm, toggle on window decoration and move window.

---

### Post by a2j on 2011-05-04
just because it doesn't work for timgood, doesn't mean 11.04 doesn't work at all. it works for me just fine, with gnome, without Unity.

---

### Post by timgood on 2011-05-04
> **3rdalbum said:**
> The notification area is depreciated; it's been depreciated for two years and still program developers are yet to update their programs to follow. The whitelist exists to give you the choice. All indicator-aware programs appear in your "tray" (indicator area) and the non-indicator-aware programs that are whitelisted also appear in your "tray" (notification area).

If we don't depreciate old systems that don't provide a good desktop experience, nobody will ever change over to the new technology.

Natty adds choice. You can use Gnome Classic, you can use KDE, you can use XFCE or E17 or Window Maker; or you can use Unity. Unity is an additional choice on top of all the others. Your "customers" should probably be using an LTS version such as 10.04, and you should make sure it's set to notify on Long Term Service Releases, not Normal Releases. Having said that, if they updated to 11.04 there would probably not be any technical issues.

For most people, Unity is fine. Takes a little bit of getting used to, but then if you couldn't adapt to change then you wouldn't be a Linux user.

Firstly, I think you must mean 'deprecated' rather than depreciated. Secondly, what is it about apps like Shutter and RadioTray that don't add to the desktop experience? Thirdly, Unity is the default desktop in Natty. Many people will have their only experience of Ubuntu or Linux through this interface. Fourthly, my customers are never put in inverted commas.

My gripe is not that it is impossible to get Unity or Classic to work - but that in order to do so you have to jump through hoops which the average user will find puts them off Linux in general and Ubuntu in particular.

I've been promoting the use of Linux and Ubuntu in home and small business environments for the past 5 years. This is the only version of Ubuntu I have not felt able to recommend as an alternative to Windows. I know it's early days, and I know that things will improve. I do not think that Natty should have been released in its present state. I'm sticking with 11.04 in the hope that over the coming weeks, things improve. Your knee-jerk response to legitimate criticism does not really help matters.

---

### Post by haudace on 2011-05-04
1) I like the new Unity interface, it is buggy but I've been an avid Ubuntu/Linux user for 3 years now, I can handle it... But I was not pleased when I learned I couldn't enable the cube while the Unity plugin remained active :(. I thought about switching to other distros, although I seem to have developed a liking to Ubuntu, my past experience with this distro has been nothing but excellent.

2) Desktop effects crashed completely in Ubuntu Classic. I'm using default environment in Natty (Unity). I thought about downgrading, but I'll wait and see if all these bugs will be fixed.

3) Unity is quasi (emphasis on quasi) stable for me now, it was not at the beginning (right after upgrade). The window borders had disappeared on me and I couldn't move any windows. In my case, this was fixed easily by enabling a few plugins in compiz (windows decorations, moving in WM etc...) and juggling with code in the terminal. The problem occurred when I started modifying settings in appearances.

4) I think the software is okay, the problem probably lies with the hardware. The question is, is that the user's fault or Canonical that didn't test their distro's compatibility with the PCs out there?


My opinion as a ubuntu power user.

---

### Post by robertj20112 on 2011-05-05
> **timgood said:**
> Finally got compiz working properly in classic by following instructions on this post: [http://ubuntuforums.org/showthread.php?p=10767302#post10767302](http://ubuntuforums.org/showthread.php?p=10767302#post10767302)

Hope this helps others.

Thanks.  It worked for me, too.

---

### Post by Dekenizer on 2011-05-05
I can see what TIMs point is.  This was release too quick, and just to make a deadline I guess.

M$ have that huge issue... it's not finish... we'll release it anyway, worry about it later. And that is when we all discover the word SERVICE PACK.  Sorry to say this to you guys but I think that Natty might be the Vista of Linux.  I know you have good intentions but it just doesn't work right yet.  

My personal opinion is that you should of made sure that even if Unity is not 100%, well that Ubuntu Classic was as ROCK SOLID (or at least normal regular areas are)  as it's predecessors.  The systray issue that icons just disappear in Ubuntu classic and you have to reboot to fix it... it drive me nuts.  

reboot to fix it... reboot to fix it... where have I heard that.... yeah that's how you fix 80% of M$ issues :confused:

I've tried Unity I see potential in it.  But having to actually TYPE urban in the app search to get Urban Terror,  well it's a nag compare to just 2 clicks I had to do before.  And if I try to pin it into the apps bar, well it won't work... it will just blink black and blue...  same thing for my Team Speak 3 App.  Like using Start->RUN in M$ to start most apps... nonsence.

I see Unity as a touch screen interface for a tablet or something like that.  For precise mouse click desktop environment, I can't see how we will ever get rid of the drop down menu click, which is the fastest way and no LONG mouse movement.  It just makes sense, click click you are there.  honestly I wouldn't have the iPad desktop interface on my PC.... it doesn't make much sense in the way it reacts, my wrist would hurt just from sliding thru the apps with my mouse.

We all make this mistake at some point, we assume that what know... others know.  That is said,  if you had the choice for your 70 years old grandmother, what would you give her to used.  A desktop that just work all around or the cool stuff that you have to tweak to make it work... you don't want to give your grandma troubles and headaches don't you... so before you release anything...  as yourself if you would give this to your grandma.

Isn't this the Human Desktop after all

Well it's my 2 cents... I try to make it more constructive... feel free to critic... that is how we evolve to something.

---

### Post by VanR on 2011-05-06
> **Dekenizer said:**
> I can see what TIMs point is.  This was release too quick, and just to make a deadline I guess.

M$ have that huge issue... it's not finish... we'll release it anyway, worry about it later. And that is when we all discover the word SERVICE PACK.  Sorry to say this to you guys but I think that Natty might be the Vista of Linux.  I know you have good intentions but it just doesn't work right yet.  

My personal opinion is that you should of made sure that even if Unity is not 100%, well that Ubuntu Classic was as ROCK SOLID (or at least normal regular areas are)  as it's predecessors.  The systray issue that icons just disappear in Ubuntu classic and you have to reboot to fix it... it drive me nuts.  

reboot to fix it... reboot to fix it... where have I heard that.... yeah that's how you fix 80% of M$ issues :confused:

I've tried Unity I see potential in it.  But having to actually TYPE urban in the app search to get Urban Terror,  well it's a nag compare to just 2 clicks I had to do before.  And if I try to pin it into the apps bar, well it won't work... it will just blink black and blue...  same thing for my Team Speak 3 App.  Like using Start->RUN in M$ to start most apps... nonsence.

I see Unity as a touch screen interface for a tablet or something like that.  For precise mouse click desktop environment, I can't see how we will ever get rid of the drop down menu click, which is the fastest way and no LONG mouse movement.  It just makes sense, click click you are there.  honestly I wouldn't have the iPad desktop interface on my PC.... it doesn't make much sense in the way it reacts, my wrist would hurt just from sliding thru the apps with my mouse.

We all make this mistake at some point, we assume that what know... others know.  That is said,  if you had the choice for your 70 years old grandmother, what would you give her to used.  A desktop that just work all around or the cool stuff that you have to tweak to make it work... you don't want to give your grandma troubles and headaches don't you... so before you release anything...  as yourself if you would give this to your grandma.

Isn't this the Human Desktop after all

Well it's my 2 cents... I try to make it more constructive... feel free to critic... that is how we evolve to something.

Yeah I have to say I agree with most of what you said. So much that I have left Natty for now after using it since Beta 1 and am using Zorin OS 4 (10.10 Maverick derivative) and really enjoying it. I'll probably come back to Ubuntu proper when the kinks are worked out some. I really think Unity should be dumped.

---

### Post by demilord on 2011-05-06
I switched back to 10.10 for some reasons also when you right click in the classic gnome on the bottom panel the submenu's are corrupted and ugly... And my cpu fan keeps blowing like crazy when doing nothing and being idle.. there are loads of bugs which means it NEVER deserved a status STABLE

---

### Post by GuiGuy on 2011-05-12
> **marl30 said:**
> 
This statement is rather unfair. There are still two other versions of Ubuntu that is still supported (10.04 and 10.10). Plus there are several other versions of Ubuntu with different desktop environments. 


The statement is fair, simply because once the user has upgraded, or maybe that should be "downgraded", there is no going back unless they do a complete clean install.

---

