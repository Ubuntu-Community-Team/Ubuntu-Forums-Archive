---
title: "Ubuntu 12.04 Login fails"
date: 2012-04-28
forum: General Help
---

### Post by leconte on 2012-04-28
I recently upgraded from Ubuntu 11.10 to 12.04 and everything was working fine.  I edited a few settings in compizconfig (set the launcher to autohide and changed the number of viewports to 6) and everything continued to work.  Finally I followed the steps here [http://askubuntu.com/questions/123759/how-do-i-disable-the-startup-sound-in-ubuntu-12-04-login-screen](http://askubuntu.com/questions/123759/how-do-i-disable-the-startup-sound-in-ubuntu-12-04-login-screen) to turn off the drum noise at the login screen.
    Now whenever I start boot into Ubuntu I can get into the login screen and type my password but when I hit enter it just says "logging in" and never actually logs in.  I can still turn caps lock on and off and my mouse still works.  I can even shutdown my computer from the menu in the upper right, but I can't actually get to the desktop.  Any ideas on how to fix this?  Thanks in advance for any tips

EDIT:
You can read the discussion below for more details but it seems that the problem is usually caused by using a wallpaper that isn't a default or changes periodically.  For instructions on how to fix that, see this post [http://ubuntuforums.org/showpost.php?p=11886394&postcount=3](http://ubuntuforums.org/showpost.php?p=11886394&postcount=3)

---

### Post by leconte on 2012-04-28
By the way, I can login to the terminal by pressing ctrl+alt+F1, so there is no issue with the account or password.  My guess is that either the command "sudo glib-compile-schemas /usr/share/glib-2.0/schemas/" messed something up, or more likely, that compizconfig messed something up. I managed to log into the 2d gui once or twice after this issue started, but most of the time that doesn't work either.  Perhaps there is a way to reinstall Unity 3d/2d from the terminal?  Or maybe I could install gnome from the terminal and see if I could log in to that?

---

### Post by anejo on 2012-04-29
Bump!

---

### Post by The Bright Side on 2012-04-29
Hey guys,

another affected guy here. Firstly, several people out there share our problem:
[http://ubuntuforums.org/showthread.php?p=11886627](http://ubuntuforums.org/showthread.php?p=11886627)
[http://ubuntuforums.org/showthread.php?p=11886599](http://ubuntuforums.org/showthread.php?p=11886599)

[http://askubuntu.com/questions/127282/after-upgrade-to-12-04-hanging-in-login-screen](http://askubuntu.com/questions/127282/after-upgrade-to-12-04-hanging-in-login-screen)
[http://askubuntu.com/questions/126275/cant-login-after-using-ubuntu-tweak](http://askubuntu.com/questions/126275/cant-login-after-using-ubuntu-tweak)

For me, the problem happened after using Ubuntu-Tweak to change some lightdm settings (I set a wallpaper for the login screen), like the guy in the second askubuntu thread above did. I get the exact same results that everybody here is describing, regardless of whether I try to go into Unity, Gnome Shell (my standard) or any other of the available UIs.

I think we can narrow the cause down to messing with lightdm. Currently, I am completely locked out of my system, though I managed to log in one time since it happened yesterday night (that's one out of ~30 attempts so far).

Now, the akubuntu thread above features two workarounds:

> 
It happened to me too. use gdm to replace lightdm

go to a text terminal using alt-ctrl-F1
Stop LightDM with sudo stop lightdm
Start GDM with sudo start gdm
Run sudo dpkg-reconfigure lightdm to set the default display manager for gdm
Edit /etc/X11/default-display-manager and set it to /usr/sbin/gdm if you can't run the above
Restart your computer and login.


I get stuck at "sudo start gdm". It says:

```

start: unknown job: gdm

```

Another suggestion from the same thread is:

> 
I found that when I set: Ubuntu Tweak, Login Settings, "Set the same background as the current desktop background" (I also have "Draw Grid" ON, but that was ON before), the login screen then actually does not show my current background but the purple default - however, when before it took me 2-4 cycles of shutdown/login to actually log in, with the changes I was able to login 5x in a row without problems.

Wonder whether this will work for you as well.


I'd love to do that, but I'm completely stuck on that login screen. Perhaps it helps some of you out there though.

One other thing I read in [http://ubuntuforums.org/showthread.php?p=11886599:](http://ubuntuforums.org/showthread.php?p=11886599:)

> 
Other thing, with the combination Ctrl+Alt+F1... I can login.


[B]With this, one can only log into the terminal, right? There's no way to get into the graphical UI after having logged in?

If there is, please let me know how.[/B]

Anyway, this is what I could gather so far. Perhaps we can keep working together in this thread to find a fix. I will not format my system yet, because I want to contribute to fixing this issue.

I have to run, but perhaps one of you guys could log a bug in launchpad?

Thanks.

---

### Post by Kaladze on 2012-04-29
so my problem: [http://ubuntuforums.org/showthread.php?p=11886539&posted=1](http://ubuntuforums.org/showthread.php?p=11886539&posted=1)
what I've seen common to both of us is that we have installed ubuntu tweak... so do you know how to uninstall this from the terminal ?

---

### Post by Kaladze on 2012-04-29
Now, I managed to login on Ubuntu after 2 reboots, in the process to login I've activated the voice thing by mistaken ( that repeats what keys are pushed). Now i'm afraid to reboot my pc :)

---

### Post by anejo on 2012-04-29
> **The Bright Side said:**
> Hey anejo ... Let's move there and try to work on a fix together.
Ok I am here... and not too happy!

After spending the whole day--after last nights fresh re-install--doing updates and logging in and off a whole bunch of times. I get home tonight and what happens... "Logging in..." but that's all that happens, there is no login actually happening!

Mmmm... what's next?
I have a launchpad account. Should I register this as a potential bug? Is this a greeter bug or something else?

---

### Post by anejo on 2012-04-29
> **Kaladze said:**
> what I've seen common to both of us is that we have installed ubuntu tweak... so do you know how to uninstall this from the terminal ?

```
sudo apt-get remove ubuntu-tweak
```Let us know if removing tweak works... I've been messing with it and I'd hate to think that this app is the problem!

---

### Post by bogan on 2012-04-29
Hi! **All**,
 I am running Ubuntu Tweak on 12.04 LTS release 3.2.0-24, without any problems.

But I thought I would point out that the correct commands for starting or stopping gdm/lightdm are as follows: ```
sudo service lightdm start
 # use this to start GUI after using Ctrl+Alt+F1 or F2, to open a tty text log-in prompt
 # and Terminal. Or after using the next to do the same from a GUI started Terminal,
 # to return to GUI - [wait a long time!!]
sudo service lightdm stop
```Chao!, **bogan**.

---

### Post by mendhak on 2012-04-29
If you can't start GDM, simply make it the default and reboot.

```
    sudo apt-get install gdm
    sudo dpkg-reconfigure gdm
    sudo reboot
```

The second command above will give you a colorful screen where you choose between lightdm and gdm.  Choose gdm, press enter.  Then use the last command to reboot. 

To find out what went wrong, have a look at your log files:

```
sudo less /var/log/lightdm/x-0-greeter.log
sudo less /var/log/lightdm/lightdm.log
```

---

### Post by whiskers751 on 2012-04-29
Try:
```
sudo **service** gdm start
```

By the way you can use the Report Abuse button to alert the moderators!

---

### Post by The Bright Side on 2012-04-29
Hey guys, I'm back.

I found 2 things:

[LIST=1]
[*]When I leave my PC off for a couple of hours (first time over last night, and again this afternoon while I was out with friends), the first login attempt after returning works. Reproduced in 2/2 cases so far.
[*]I attempted the workaround from the askubuntu thread I posted earlier, setting Ubuntu Tweak back to "use same wallpaper as user". It worked immediately after rebooting, but now it's stopped working again and I'm locked out again.
[/LIST]

Leaving my PC off for another 20-30 minutes now. Will keep you posted.

P.S.: spam post reported as abuse.

EDIT: oh, I also removed Ubuntu Tweak, but as I expected, removing it did not undo the changes it had made to my system. My situation is unchanged.

---

### Post by anejo on 2012-04-29
Okay... I'm back (from a fresh install and using 2D for now!)
Has anyone tried **mendhak** or **whiskers751**'s suggestions?

[I](And thanks for the RA button thingy... I don't what I was thinking!)
[/I]

---

### Post by Mike235 on 2012-04-29
My system has been off for the whole day, was fiddling around in the morning when the problem arouse, but gave up as many "solutions" were just not working. I turned it on about 5mins ago and still stuck on "logging in", so bright side you pretty lucky to at least get in some times! I'm also running ubuntu tweak so this may very well be the source of the problem?

---

### Post by Mike235 on 2012-04-29
I could stop lightdm and start it again, but that doesn't really change anything, gdm however, I do not have on the system and cannot install as I am not connected to the internet because I cannot log in to do so, even logging in through the tty1 doesn't connect me online, so I can't download any packages

---

### Post by The Bright Side on 2012-04-29
I looked at the two log files:

sudo less /var/log/lightdm/x-0-greeter.log
sudo less /var/log/lightdm/lightdm.log

I see some errors when it's trying to find and access the correct wallpapers (my login screen has no wallpaper as a result), but that's all still before I punch in my password.

The last thing I see in both files is a line saying that I have been authorized.

I'd love to post the contents here, but am not sure how.

EDIT: screenies attached!
EDIT 2: zip with higher-res screenies attached. They're easier to read.

---

### Post by Kaladze on 2012-04-29
I've installed gdm (instead of lightdm) and now works like a charm.
When you are on ubuntu go to Synaptic Package Manager => search gdm => install => choose as a default display...and thats all fox. 
For command line, I think another experienced user should write this correctly. 
Thanks guys!

---

### Post by The Bright Side on 2012-04-29
Hey guys,

I understand this fixes our problem, but isn't gdm the outdated technology that Ubuntu moved away from a couple releases ago? I'd prefer to stay with lightdm, but I will give it a shot the next time I can get in.

Is there an easy way to switch back and forth between the two?

---

### Post by Kaladze on 2012-04-29
Hey, 
I think that when you want to switch back to lightdm you can simple reinstall gdm and when you have to choose the default display you can choose lightdm...but until lightdm is functional I will stay with this one. 
Cheers!

---

### Post by The Bright Side on 2012-04-29
Yeah I hear you. Just installed it, works well! And as mendhak posted before, we can switch back and forth with sudo dpkg-reconfigure gdm1

Then I went into my user account settings and turned on automatic login. Now Ubuntu boots into a black screen. So what I did was switch back to lightdm. Now my system boots without a problem - because the login screen is gone.

However, after a minute or two, I get an error popup: "System program problem detected - Do you want to report the problem now?". When I try to report it, I get another message saying "Sorry, Ubuntu 12.04 has experienced an internal error."

Also, one more thing: when I log out, I go back to the same lightdm screen as usual and yep, the problem's still there.

**So: automatic login works, but leaves system unstable - manual login does not work, no matter if it's directly after boot or after logging out manually.**

---

### Post by leconte on 2012-04-29
Ooooh, I'll give gdm a try in a minute.  I just figured I'd post what I've tried so far to help along other people who end up in this mess.  Since it seems to be universally agreed that this is caused by Ubuntu Tweak or CompizConfig, I tried running "unity --reset" from the terminal to see if resetting the settings would fix it.  Unfortunately it just threw an error and couldn't run.  I also tried installing gnome from the command line with "sudo apt-get install gnome-shell", which installed successfully, but I still couldn't log in to it.  Maybe someone else might have better luck with that?

---

### Post by leconte on 2012-04-29
Ok, using gdm seems to have worked, thanks for the tip!  After installing it, I could login in to Gnome and Unity 2D.  When I tried logging into Unity 3D, the launcher never appeared and the top menu wasn't there.  However, after switching back to 2D and running "unity --reset" in the terminal, Unity 3D was back in order.  I tried switching back to lightdm once I had everything working again, but it did the same old "logging in..." thing.  Has anyone reported this bug?

---

### Post by anejo on 2012-04-30
Ok Its a new day on this side of the world and its bright and early in the morning. I'm gonna spend this morning working on this!
So I noted your posts and it comes down to **lightdm** and the **ubuntu-tweak** tool.
I have a fresh install--again--but this time I am only running in 2D.
I also installed tweak but for now I've only touched fonts and themes. If anything, I'll report back later...
In the meantime I shall log a bug at lightdm and point the team to this thread.
I see theres a blog at the tweak site... so I shall post something there and also point them to this thread.
Lets see what happens...

---

### Post by anejo on 2012-04-30
Bugs reported at
[https://bugs.launchpad.net/ubuntu-tweak/+bug/991684](https://bugs.launchpad.net/ubuntu-tweak/+bug/991684)
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/991695](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/991695)

---

### Post by leconte on 2012-04-30
I did a little more looking around and came across this thread on lightdm's launchpad that seems to be describing this same problem.  They don't mention Ubuntu Tweak specifically as a cause but all the symptoms are the same [https://bugs.launchpad.net/lightdm/+bug/986967](https://bugs.launchpad.net/lightdm/+bug/986967)

---

### Post by anejo on 2012-04-30
Yeah I saw that one too!
However deleting .Xauthority or logging in with XMonad didn't work for me.
It looks like for now the short-term solution is that gdm route...

---

### Post by anejo on 2012-04-30
Looks like **mendhak** is going with his problem being a non-standard wallpaper!
His solution:  [http://ubuntuforums.org/showpost.php?p=11886394&postcount=3](http://ubuntuforums.org/showpost.php?p=11886394&postcount=3)
If that is true... then there's a bug in whatever manages the DE wallpaper, say from 'Pictures Folder'.

I wonder what constitutes a non-standard wallpaper?
EDIT: this question is answered in 4th post (from the above link's parent)

---

### Post by anejo on 2012-04-30
After reading mendhak and Zukaro's posts ([http://ubuntuforums.org/showthread.php?p=11886394](http://ubuntuforums.org/showthread.php?p=11886394)) I'm thinking that maybe ubuntu-tweak is not the problem after all but the wallpaper permissions in the DE space.

My current settings--read solution--for now are logging into full Unity, set one of the usr/share/background images as a greeter wallpaper and see what happens...

---

### Post by Mike235 on 2012-04-30
It definitely has something to do with the wallpaper settings because my system was running perfectly before, with ubuntu tweaks being tweaked and some general settings changed, but until I messed around with the wallpapers, choosing from pictured folder etc its failed to log in. Can anyone post code of how to change the wallpaper through the terminal? To test if that'll work, tia.

---

### Post by anejo on 2012-04-30
> **Mike235 said:**
> Can anyone post code of how to change the wallpaper through the terminal? 
Start with... if that doesn't work, I'll post some other methods:
```

gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/warty-final-ubuntu.png

```This will reset the wallpaper to default. 
Restart and ensure for the time being that you do what I did in post #28...

---

### Post by sonicb00m on 2012-04-30
Also had this problem after install ubuntu-tweak and rebooting. FOr now the GDM solution works.

---

### Post by Mike235 on 2012-04-30
> **anejo said:**
> Start with... if that doesn't work, I'll post some other methods:
```

gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/warty-final-ubuntu.png

```

this is what came up after that command:

[B]** (process:2367): WARNING **Command line 'dbus-launch --autolaunch=be469003f494e5eef785fd2400000007 --binary-syntax --close-stderr' exited with non-zero exit status 1; 
Autolaunch[/B] [B]error: X11 initialization failed.\n
[/B]
Could anyone tell me how i could connect to a mobile broadband 3G dongle, through the tty1, because i am unable to install gdm packages because of no Internet connection

---

### Post by anejo on 2012-04-30
Bummer!
If you just run 'gsettings' or even 'gconftool-2' by themselves...?

---

### Post by Mike235 on 2012-04-30
if i run gconftool-2, it just says i should run --help to see commands, which then gives me options to install it or view test options, save/load etc 

when i run gsettings it gives me commands like get, set, reset for values of a key, and other commands like listing the keys in a schema, checking if a key is writable etc.

Do you have a command for gconftool-2? to change the walpaper

---

### Post by anejo on 2012-04-30
**@Mike235**
Perfect. That means the commands themselves are there.
Don't waste your time (via your 3G) trying to install a gdm environment.
Rather try and get this wallpaper fixed so that you can log in!
Having said that... the gsetting command I gave you should work (I did test it)
Try ```
gnome-session --version
```That will return the version of Gnome you're using.
The version number should start with 3... implies that those gsettings can be used
But ok... if it still is not working then try
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename /usr/share/backgrounds/warty-final-ubuntu.png    

```And restart. Let's see what that does!

---

### Post by Mike235 on 2012-04-30
Did a fresh install and all is good - keeping in mind to not mess around with background settings. Although this is not a proper solution, hopefully they'll fix the bug asap!

---

### Post by The Bright Side on 2012-04-30
Hey guys! I re-installed my system as well and opted to keep my paws off the login screen until further notice... Working fine for me now.

Anejo, reinstalling doesn't really cut it for you if I remember correctly, right? Perhaps give my screenshots from the log files another shot, there may be something helpful in there?

---

### Post by leconte on 2012-04-30
Woh, Mendhak's suggestion worked for me as well.  I was using one of the default Wallpapers that periodically changes automatically.  Once I set it to a defaul that doesn't change, I was immediately able to log in with lightdm.

Also, Anejo, it might be a good idea to update your bug reports on launchpad, especially if more people confirm that this fixes the issue for them

---

### Post by leconte on 2012-04-30
Woh, Mendhak's suggestion worked for me as well.  I was using one of the default Wallpapers that periodically changes automatically.  Once I set it to a defaul that doesn't change, I was immediately able to log in with lightdm.

Also, Anejo, it might be a good idea to update your bug reports on launchpad, especially if more people confirm that this fixes the issue for them

---

### Post by anejo on 2012-05-01
It's another new day... and yes, it starts with another fresh install!

The problem I have with mendhak's solution is simply that I don't have any internet connection at that point in time and so can't execute that instruction set. I need to learn how to connect to a SSID from the command line but until then... fresh installs it shall be!

[B]The problem definitely occurs  when one selects that default wallpaper that is set to periodically change!
[/B]
At least that is my case... and on Mike235, leconte and others.
I shall be updating the bug reports accordingly!

Thank you to **leconte** and **mendhak** for your efforts in getting us to this point...

---

### Post by aextance on 2012-05-01
I have a very similar "freeze on login" problem with lightdm and am reluctant to reinstall as my partitions are in a bit of a mess and I've got a lot of work I need to do. Choosing gdm wouldn't even get me to the login screen, oddly. However, I've been able to get into Ubuntu by keeping lightdm as the default display manager, then pressing ctrl+alt+F1 when getting to the frozen login. From there:

sudo stop lightdm
startx

Got me into Ubuntu. I had to log in to the keyring but it looks like I should be able to get some work done. Interestingly, changing my wallpaper hasn't fixed my problem, so perhaps this is slightly different, but maybe my workaround will be useful for some.

I may well reinstall once I get some breathing space - unless another obvious answer becomes clear!

---

### Post by pedrospeixoto on 2012-05-01
I am having the same login problem. I type me passwd and it just says "loging in ...".

To help figure out the reasons I will post my details:
- Ubuntu 12.04 fresh install dual boot with win7 on a Samsumg RF511 notebook
- Worked fine for a couple of days.
- I changed some things in Compiz
- I tried to set up Wine, but got lots of error messages so I removed it.

The problem happened when rebooted and tried to boot on LiveUSB ubuntu to do some partition changes. I put the pen drive, set bios to boot it, but it just didn't boot the pen drive and logged in ubuntu with the loging problem. After that the loging problem continued even after several reboots without the pen drive.

Since there other with the same problem I think it would nice to concentrate efforts on one thread (like this one).

Thanks,

Pedro.

---

### Post by pedrospeixoto on 2012-05-01
Sorry for my last post...I noticed that I hadn't read all the thread pages...

The wallpaper solution seems to work for me (disabling the cyclic/changing wallpaper). Hope it solves the problem.


Pedro.

---

### Post by leconte on 2012-05-01
That's a good point, I bet most people won't get that far into this thread.  I'll update the first post with a link to the solution

---

### Post by anejo on 2012-05-02
Mmm... seems that if you suspect that* logging in* is not gonna do it for you
instead of pressing the Enter key
select the character **>** rather at the end of the login button

---

### Post by brx75 on 2012-05-02
I've a similar problem with black screen after lightDM login.
I've found that I'm able to Ctrl-Alt-F1 and restart lightdm.
I've also found that if I kill '/usr/lib/gnome-desktop3/check_gl_texture_size' session would start fine.

So, my workaround is:
 - wait for lightdm login
 - enter you password to login
 - hit Ctrl-Alt-F1
 - login to tty (your username and password)
 - issue ```
 $ ps -ef | grep check_gl_texture | grep -v grep | awk '{print $2}' 
```
 - the command wull return the process PID
 - issue ```
 $ kill <pid_from_previous_command> 
```
 - hit Ctrl-Alt-F7

Let me know

---

### Post by bogan on 2012-05-02
Hi!,** anejo**,

You Posted:>  select the character **>** rather at the end of the login buttonPlease what does this mean?

In my 12.04 LTS 3.2.0-24 login widget, there are only the user names above and below, plus the Gear/Ubuntu/Gnome button top-right that gives the drop-down menu when clicked, and changes according to which choice is default.

Are you referring to the 10.04 and earlier login?

Chao!, **bogan**.

---

### Post by anejo on 2012-05-02
It means that on the greeter screen, after you enter your password, instead of using the Enter key to continue, you select that "greater than" symbol (that is to the right of your password input) with the mouse and click it instead (of using Enter).

I had occasion to use it just now... and it didn't work.
At least for me... but apparently it has for others. The only solution for now is to ensure that while the system works, install 'gdm' so that if the problem occurs, follow **mendhak's** methods posted earlier...

---

### Post by bogan on 2012-05-02
Hi!, **anejo,**

Thanks for that explanation. The "PASSWORD" text in the login-in widget in my 12.04 screen is off-white on white and virtually invisible; and I did not know there was a '>' symbol at the end of the text entry bar until after your last post, when I put the Mouse cursor over it, it changed colour and became visible.  - Theme problems!

Edit: I just tried it and it worked for me!

Thanks again, Chao!, **bogan**.

---

### Post by anejo on 2012-05-03
Further developments on my side...
**I have disabled the dynamic switching off!**
I don't mind the greeter wallpaper being different from the current desktop!
[On how to do that can be found here]("http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#answer-64002")

---

### Post by Wtower on 2012-05-03
I had the same issue here. Had been using the ati propriatary drivers which seem to have been causing the trouble. I removed them and now works like a charm. So maybe the whole issue is something about the graphics device. I hope this was helpful.

---

### Post by LinuxPS2 on 2012-05-04
> **Wtower said:**
> So maybe the whole issue is something about the graphics device.

I believe that is exactly what it is, quick test run
```
grep -e '(EE)' /var/log/Xorg.0.log
```

if it returns something along the lines of
```
[...](EE) No devices detected.
[...](EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

Then my solution should help you - [http://ubuntuforums.org/showthread.php?p=11904251&posted=1#post11904251]("http://ubuntuforums.org/showthread.php?p=11904251&posted=1#post11904251")

---

