---
title: "Current theme defaults to silver theme for no reason randomly on login"
date: 2011-05-04
forum: General Help
---

### Post by inameiname on 2011-05-04
For some reason, from time to time on login, as my normal theme starts to load, it changes to some sort of silver theme (a very basic one), and I am unable to change it over to any other theme.

Checking the theme being used, it still says my desired one is set, but it is not. Also, no matter what theme I change it to, that basic silver theme is the one being used. This includes a default icon theme, not the one I prefer. 

The only option that seems to fix things is a restart, and the hope that on this login it won't mess up like before.

I am using Natty, from a fresh install, with Ubuntu Classic as my desktop, and have reinstalled things more than once to try and fix a few of the Natty-related issues, but this one keeps coming back. 

Any help would be greatly appreciated.

---

### Post by inameiname on 2011-05-05
Bump.



UPDATE:

I managed to find a couple of similar threads, and one potential 'temporary fix':

```

sudo gnome-settings-deamon

```Unfortunately, this does not solve the issue, but if it works, will refresh things to allow for my default theme to work and not that silvery basic one, much like restarting does.


UPDATE2:

That potential 'temporary fix' does not work for me. While it does change the windows to the correct default theme, for some reason, it doesn't change the taskbar to the correct theme. It does, oddly, change the taskbar from that silver basic theme to what I think is the New Wave default taskbar theme. That makes no sense.

---

### Post by kenfeyl on 2011-05-07
I am having the exact same issue.

What are the specs of your machine? I'm on a T5750 Core 2 Duo Gateway M 6822 notebook with amd64 natty. This just started with natty. I have tried just about everything I could think of, but have not yet found out what's causing this behavior.

I too discovered the "sudo gnome-settings-daemon" fix, but like you found that it seems to affect only the bar at the top -- nothing else.

Have you made any progress?

---

### Post by inameiname on 2011-05-07
Sadly no, no fix yet. Since it continued to happen more often than not, I decided to try one potential solution and see if that fixes things. It is simply starting the desktop setting it to "Ubuntu Classic (No Effects)". I do not like this as a long-term solution, as I miss the effects, such as the genie effect with minimizing and maximizing windows and such, but I have not had the issue yet. We will see if I do over the next few days.

Mine is a Gateway as well, an MT6916, so very similar I suspect. And yes, it only started with me after a fresh Natty installation. It has to be something with Compiz, or something that is related to Unity and/or Ubuntu's concern for its stability over the Classic. At least my guess.

Regardless, I am glad I am not the only one who is finding this issue. Maybe if others come forward and see this posting, something might look further into it than what we might be able to do. 

Oh, and I am curious, with your Natty installation, are you also getting the following two problems as well.....1. the occasional complete freezing of the desktop and the screen and only holding the power button to reset fixes things.........2. drag/drop of files/folders from one taskbar item to another does not work without first having to refresh Compiz by 'compriz --replace'? I ask this because I ran across two folks saying Compiz was the culprit for both #2 and this issue, and the "Ubuntu Classic (No Effects)" is the only way to fix those. We will see if this solution really does. So far, though, I am not happy with the number of Natty issues I have, far more than ever with past Ubuntu releases. I am actually thinking of seeing if Linux Mint might be better when it gets released at the end of the month.

---

### Post by kenfeyl on 2011-05-09
Interesting. Definitely a Gateway issue, or at least an issue in a common Gateway notebook component circa 2008. BTW are you amd64 as well?

I agree that Compiz is the likely culprit for a regression, as I too work perfectly in Ubuntu Classic (No Effects).

I haven't had a complete desktop freeze like the one you described, at least since upgrading last Friday. The only exception was when it refused to wake up after a suspend and I had to hard-reset it.

I do not use drag-drop frequently, so I don't have enough data to confirm or deny. I just tried it now with a few different apps without problem.

I have also experienced increased instability with particular apps. Flash is now riddled with white boxes. Getting 64-bit Flash fixed that, but also introduced dramatic slowdowns in more complex Flash apps (e.g., Meet the Press). Pidgin now crashes whenever attempting to close a video chat. The Internet now disconnects whenever the laptop goes into suspend. I am disappointed with Natty since there are more regressions than any previous update and no real improvements (except that, maybe, Unity feels a bit faster than GNOME).

---

### Post by inameiname on 2011-05-09
Perhaps. I don't think it is necessarily a Gateway issue; that is probably just a coincidence. Oh, and it is not an AMD64.

That's good that you are not having any issues since changing things to Ubuntu Classic (No Effects). So far so good for me as well. I have not had any issues with freezing, dragging/dropping, or funky silvery theme at startup.

Actually, I take that back. I noticed once small issue that was a bit strange, but it might not be related. Yesterday I noticed at random times, whether I was doing anything on the computer or not (fyi, it was still on and not in suspend/hibernate modes), it beeped. Just a random single beep, the kind of sound you would get if you clicked on something and an error box popped up. Weird, but doesn't hurt. Again, probably nothing, but figured I should mention it.

Hmmm, dragging and dropping is a big thing for me. I tend to overuse that function transferring stuff between external flash drives and whatnot.

That is strange. I would have to say that is an AMD64 issue, specifically in regards to Flash, as I'm sure you know. If you think about it, it is funny how many issues there are with those 64-bit processors, even though you would think they are the future.

Regardless, I really do hope Natty improves. Personally, I would love to figure out the least amount of stuff in a Debian-based OS I need before I can just make my own distribution. I do that already to a great extent once I install Ubuntu, but I think if I could figure out the minimum, I wouldn't need to worry so much about the issues that can occur, such as those found so far in Natty.

---

### Post by marcio_mi on 2011-05-09
I always had the same problem with previous editions (since Karmic), and I always "solved" it by logging out and in again. It didn't happen very often though, I would say once every 20 logins on average. Never thought of finding a solution since I thought it was something purely random that might depend on how elements load on boot. However since I upgraded to Natty, the issue didn't represent itself (so far).

As I said, I don't think it's something related to specific hardware, for me it was happening both on my sony vaio and on my samsung netbook.

---

### Post by kenfeyl on 2011-05-10
Today's updates to gnome-panel appear to have fixed it for me. Try it and let me know if it's the same for you.

---

### Post by inameiname on 2011-05-10
marcio_mi:

So you are saying the frequency of this issue for you has decreased since Natty? That's interesting. 

kenfeyl:

Gnome-panel was updated today? I looked in my history and did not see that package getting an update recently.

What is your current version of it? If you do not know how to get that, it's easy. Just type in the terminal: sudo apt-cache policy gnome-panel.

My current version of gnome-panel is:

```

gnome-panel:
  Installed: 1:2.32.1-0ubuntu6.5
  Candidate: 1:2.32.1-0ubuntu6.5
  Version table:
 *** 1:2.32.1-0ubuntu6.5 0
        500 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main i386 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ natty-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     1:2.32.1-0ubuntu6.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ natty/main i386 Packages

```Nonetheless, that is great if it solved things. If I do have the latest version, I just may have to get off of (Ubuntu Classic (No Effects) to see if it does indeed fix the problem.

---

### Post by marcio_mi on 2011-05-10
inameiname:
more than that, the issue didn't come up at all in natty (I've been using it since beta 1, hence already for more than a month, always using unity, never once logged in gnome classic). My opinion is that the way the machine boots with unity is somehow different than the way it does it with gnome classic, and this prevents the random "silver" graphical interface to replace my normal theme

Do you guys use gnome classic or unity?

---

### Post by marcio_mi on 2011-05-11
guess my theory was wrong... :rolleyes:

today it happened again, with natty, and also after the gnome-panel upgrade kenfeyl was talking about. clearly I spoke too soon... :)

---

### Post by inameiname on 2011-05-12
Doh!!!! 

I was hoping it was because we were using the classic gnome desktop instead of Unity, and that was why this issue was coming up. My thinking of it was the issue was a result of a bug in the gnome desktop, and was not looked into all the much or cared enough about to fix since Unity is now the default. However, since you found this issue using Unity, I guess that theory is not valid anymore.

Another observation of mine for those interested, is that sadly, logging in using Ubuntu Classic (No Effects) does not completely take this problem out of the equation. I have been logging is under that scheme for a few days now and while it seems to fix a few other 'bugs', that silver theme still does occasionally come up, and a restart/logout and login is required.

---

### Post by Flugz on 2011-05-13
This has happened to me as well, using both Unity and Gnome when logging in on 11.04. I have to admit it's quite annoying, especially since that silver theme looks rank.
 
Is this a x64 issue or does it happen to 32-bit users too?

---

### Post by inameiname on 2011-05-14
Good question. I wonder that too.

---

### Post by Salahare on 2011-05-14
I have this same issue. I'm not sure how to pinpoint the problem, but I was sure there must be some conflict between having both Unity and Gnome installed after the update to 11.04. And not only do I randomly get the bad silver theme, but often during boot up I get white blocks all over the screen, often needing a force quit so that I'd be able to actually read anything.

I'm running an old Gateway Media Center from 2005, with the original Intel Pentium D. Since then I've added an Nvidia GeForce 6200 TurboCache *and* I still have Ubuntu Studio installed (in case that might add extra issues). 

Still very new to Linux distributions in general having only started using Ubuntu in the late summer of 2010.

---

### Post by inameiname on 2011-05-16
It must be something like that. 

Besides this, I occasionally get a frozen screen, am always unable to drag and drop things to and from the taskbar items without a "compiz --replace" terminal command, and on occasion, my plymouth splash doesn't work at startup (might not be due to the new Unity troubles).

---

### Post by marcio_mi on 2011-05-17
just randomly run in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296)

it describes the same problem. Apparently we're not alone! :popcorn:

there are some workarounds in the comments (see #20, for instance) or links to other bugs report that have workaround. I haven't tried them yet, also because with unity it has not happened as often as it used to, therefore I am not too keen to mess around.

---

### Post by inameiname on 2011-05-17
Thanks for that, [marcio_mi]("http://ubuntuforums.org/member.php?u=808567")! I will be sure to check that link out.

Here are the main solutions I found on that link:

1. Typing in the terminal: gnome-settings-daemon.

I can say that it does not work on mine. As mentioned earlier, it simply fixes the top panel, but not the taskbar or, I believe, the icon set. And my issue seems confirmed by other comments there as well.

2. Typing in the terminal: sudo /etc/init.d/gdm restart

I will try that the next time this issue comes up.

3. Edit /etc/xdg/autostart/gnome-settings-daemon.desktop and change line 4 to: Exec= bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon". 

I will try that too.

4. Do the following:

Step 1: Create a script (I called it gnome-settings-daemon-fix.sh) under /etc/xdg/autostart with the following:

#!/bin/bash
# gsettingsdaemonfix.sh

pid=$(pgrep gnome-settings-)

# if [ -n "$pid" ]
# then
# ps $pid &> /home/sanjeev/Desktop/gnomesettingsdebug1.txt
# else
# echo "No previous instance of gnome-settings-daemon running!" &> /home/sanjeev/Desktop/gnomesettingsdaemondebug.txt
# fi

while [ -n "$pid" ];
do
        pid=$(pgrep gnome-settings-)
        sleep 0
done

exit 0

----------------------------------------------------------------------------------------------------------------------------------
Turns out 'wait' only works for child processes. I wonder why.

Enabling the 'if' comments will output some useful information about previously running instance (be sure to change the path as according to your system). 


Step 2: Edit 'gnome-settings-daemon.desktop' under 'Exec=' entry and replace it with:

----------------------------------------------------------------------------------------------------------------------------------
[Desktop Entry]
Type=Application
Name=GNOME Settings Daemon
Exec=bash -c 'bash /etc/xdg/autostart/gnomesettingsdaemonfix.sh ;/usr/lib/gnome-settings-daemon/gnome-settings-daemon'
OnlyShowIn=GNOME;
NoDisplay=false
X-GNOME-Autostart-Phase=Initialization
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=gnome-settings-daemon

5. There is a PPA mentioned, but for now, it is empty. We will see if it gets updated and the 'fix' inside works.

 [https://launchpad.net/~rodrigo-moya/+archive/ppa]("https://launchpad.net/%7Erodrigo-moya/+archive/ppa")



To note, ever since I have been logging in using Ubuntu Classic (No Effects), this issue has happen much, much less frequently. It has happened, but maybe twice in the past week.

---

### Post by cbcoza on 2011-05-21
Still occurs upto and including updates as of 20th May 2011 on 11.04 Natty.
Its just happened to me on a Gigabyte M1022C Netbook.

It think it happened before, as well as on Maverick but at the time I was still messing around alot.

I have now settled down and stopped changing stuff after my last re-install.

Everything is running super smooth, this occurrence is minor and does not phase me, as it seemed to correct itself after a start up again after a full shutdown.

---

### Post by philinux on 2011-05-21
This is happening randomly here too. nvidia 8600gt.

Logging out then in fixes it though.

Seems to be a clearlooks type theme snaffling the gnome panels and menus.

---

### Post by inameiname on 2011-05-21
I too recall this issue having prior to Natty, but extremely rarely. Maybe just a few times ever, and the same solution (a restart) fixed it just fine. It is just in Natty it happens more often. Using Ubuntu Classic (No Effects) has lowered the frequency of the problem, but not entirely.

---

### Post by cbcoza on 2011-05-24
Just happened again, again randomly after several reboots.

For clarity for the post, I will presume these images are what is being seen.

In my case, this is what it should be - Normal:

[IMG]http://www.crackberry.co.za/forumimgs/Screenshot_Normal.png[/IMG]

And this is the Silver issue:

[IMG]http://www.crackberry.co.za/forumimgs/Screenshot_Silver.png[/IMG]

---

### Post by robert shearer on 2011-05-24
As already posted here...
[http://ubuntuforums.org/showpost.php?p=10828027&postcount=17](http://ubuntuforums.org/showpost.php?p=10828027&postcount=17)

Post #20 in the link given..
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296)

Contains a workaround.
Tested here and appears to work.

---

### Post by inameiname on 2011-05-24
Thanks for that Robert. I will test it and see if it completely fixes the problem.

For those interested, that workaround is this:

```

sudo gedit /etc/xdg/autostart/gnome-settings-daemon.desktop 

Change line 4 to:
Exec= bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

```

---

### Post by robert shearer on 2011-05-24
> **inameiname said:**
> Thanks for that Robert. I will test it and see if it completely fixes the problem.

For those interested, that workaround is this:

```

sudo gedit /etc/xdg/autostart/gnome-settings-daemon.desktop 

Change line 4 to:
Exec= bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

```

Just for clarity for **new users**, please use gksudo 
(graphical sudo for GUI applications, standard sudo for terminal)

so..
```
gksudo gedit /etc/xdg/autostart/gnome-settings-daemon.desktop
```
Then the line that reads...
```
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
```
can be commented thus...
```
#Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
```
and a new line added below it ....
```
Exec= bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"
```

save and close.

Now if you ever need to revert you can simply remove the last/new line shown above and remove the comment # from the line we commented out.

---

### Post by inameiname on 2011-05-24
Thanks Robert. 

So far so good for me after using this. Although, I have only restarted my computer twice, so more testing is needed to conclude the issue has been fixed.

---

### Post by scpatl4now on 2011-05-24
I just noticed this started happening with me 2 days ago.  I've never had it happen before.  I have an Nvidia 7600GS and other than the nonactivated driver thing, its been ok.  I'm using Unity on a amd64 system

---

### Post by inameiname on 2011-05-26
I think help is heading our way! Well, at least confirmation and acknowledgment of this bug.

I checked out Linux Mint's (which was released today) and saw this very bug as one of them on there. they even mention the same 'fix' we have here, and a link to the bug report specifically about this one.

Mint's showing of the bug:
[http://www.linuxmint.com/rel_katya.php](http://www.linuxmint.com/rel_katya.php)

> 
Gnome theme failing to load         Because of a race condition between the GDM and session calls to gnome-settings-daemon, Gnome can load without a theme.
         For more information you can follow [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809").
         As a workaround, you can modify  /etc/xdg/autostart/gnome-settings-daemon.desktop and replace  'Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon' with  'Exec=bash -c "sleep 20;  /usr/lib/gnome-settings-daemon/gnome-settings-daemon"'.
         Note that "20" is an arbitrary value. You might have to fine  tune this value and find the one that's right for you. If the session  call is too soon it will fail because the GDM one is still alive. If it  occurs too late it will only theme your panel but fail to theme your  desktop and nautilus. In Virtualbox we found "20" to work quite well. On  real hardware this value is likely to be smaller. The slower your  computer is, the higher this value is likely to be.


As such, I think this problem is almost solved! I just wonder if the original '2' or '20' is better or worse. As mentioned, fine tuning seems to be the thing.

---

### Post by robert shearer on 2011-05-26
Since I originally applied the workaround I have had the theme fail to load only once. (20 boots)
This is much improved as before it would fail 50% of the time

Thanks for the link.
I have changed the value from 2 to 5 and will monitor.

Cheers, Bob

---

### Post by inameiname on 2011-05-27
No problem, Robert. If I may ask, why 5? I am using 2, as that was what was mentioned previously in this thread, and looking at the link I just gave, they have 20. They mentioned slower computers requires more of a wait time, and faster ones can use a lower number. 

I guess let me know if you can if 5 is better for you than 2. Ooh, and maybe what are the specs to your computer.

---

### Post by robert shearer on 2011-05-27
5 because 2 works mostly but very occasionally does not.

If 5 doesn't give 100% cure then I will try 10. 
Experimenting seems to be the way to find the optimum value in light of the guide you linked.  :)

Old and slow-ish,  (but adequate for my needs) system....
Dell Optiplex GX270.
Celeron CPU 2.4 GHz.
896 MiB Ram.
Nvidia MX-440 64 MiB Graphics.

cheers, Bob.

---

### Post by inameiname on 2011-05-27
Sounds like a good experiment. I decided to leave it at '5' and see if I get the issue, and if so, how often.

---

### Post by inameiname on 2011-06-03
"5" has worked for me for several days now, so I think I will mark this thread as solved.

This issue can also be found in a posting on WebUpd8, a further sign we weren't the only ones: [http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html). And the same 'fix' was given.

---

### Post by Romulo Carlos on 2011-08-10
Sorry for using this post, but is the closer I found about my problem.

After a few days tunning my system, the same problem happened here: the theme is changed to a basic gray, and even if I try to set another theme, nothing happens.

So, I noticied the source of problem is (maybe) the LOGIN SCREEN CONFIGURATION (MENU->System->Administration->Login Screen).

If I set it to autologin, no problem: my theme works like a charm. But this is a problem for family-shared, multi-user computers.

But, if I set the login screen to show users, don't matter what desktop I set on login screen (Ubuntu, Classic, etc), my theme is gone.

Maybe this helps to solve this bug, but anyone knows how to solve this?

Thanks!!

EDIT: Tryed the solution on the link, but don't work. The only way is for now set my computer to autologin!

---

