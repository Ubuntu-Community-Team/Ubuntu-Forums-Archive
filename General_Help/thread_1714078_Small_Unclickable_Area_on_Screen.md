---
title: "Small Unclickable Area on Screen"
date: 2011-03-24
forum: General Help
---

### Post by PWill on 2011-03-24
There is a small area on my screen that I cannot click on or highlight, regardless of the application that I am using.  I know this sounds so weird, but it's like a 300 pixel long by 50 pixel high invisible box, horizontally centered and vertically offset just below the center of the screen. It is covering a part of this text box right now.

I can move my cursor all around the text box, and I mostly see the I-beam cursor, and can select text, etc. However, when I move my cursor over this invisible box (do I sound crazy yet?) it turns into the standard cursor shape, and I can no longer right click, select, etc.

I figured there was some application window not showing up that was in the way, but I've closed everything and can't think of what could be running that could cause this. Has anyone experienced anything like this before?

---

### Post by flipper T on 2011-03-24
look in system monitor

identify what it might be (sort by cpu usage)

kill it

---

### Post by ~Plue on 2011-03-24
enter *xkill* in a terminal/run dialog and then click on that area. if its a crashed application, that should terminate it

---

### Post by sakishrist on 2011-04-30
I have the same problem. I still can't identify the application that creates that window. When I restart it's ok but after a while it appears there just as described.

@~Plue could you please tell me if there is a program like the one you mentioned but that will actually identify the program? I mean pointing a window and showing me something like PID. Thanks

---

### Post by ~Plue on 2011-04-30
> **sakishrist said:**
> 
@~Plue could you please tell me if there is a program like the one you mentioned but that will actually identify the program? I mean pointing a window and showing me something like PID. Thanks
you can use xprop
```
xprop  _NET_WM_PID
```(run it without any specific property name to get all the info)

good luck

---

### Post by sakishrist on 2011-05-01
Thanks!!!

---

### Post by sakishrist on 2011-05-01
This area just reappeared. I used the command you provided but the result is:
```
~$ xprop
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
```And:
```
~$ xprop  _NET_WM_PID
_NET_WM_PID:  not found.
```Weird. 

PS: If I use the command on other windows it works fine.
PS2: xkill does not work on that area.

---

### Post by ~Plue on 2011-05-01
I can only guess whats wrong here.. 
Which graphics card are you using? And which version of drivers is currently installed?  see if changing the resolution and then reverting the changes removes the box, and also check if the issue persists in the gnome fail safe mode (logout > select user > before entering the password, select 'ubuntu classic/gnome (failsafe)' from the session: drop down box)

---

### Post by mc4man on 2011-05-01
A bit of a longshot - did you make any changes in ccsm > workarounds, specifically -  enabling "Keep previews of minimized windows"

If so then disable - should not be used

---

### Post by MasterProg on 2011-05-02
So far that's the weirdest bug I've ran into. Everything is exactly the same for me as it's been explained in the first post.

> **mc4man said:**
> A bit of a longshot - did you make any changes in ccsm > workarounds, specifically -  enabling "Keep previews of minimized windows"

If so then disable - should not be used

I had it disabled, but the invisible window is still there.

EDIT: The window disappeared after logging out and logging in again.

---

### Post by mc4man on 2011-05-02
While I haven't had these 'unseen', invisible' windows in quite some time, it may be reoccurring for some in 'some' situations

During dev it was quite an issue at times with the bug 'evolving' over time
Maybe keep an eye here - orig I filed that has just recently be re-opened yet again
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/709461](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/709461)

---

### Post by sakishrist on 2011-05-02
@~Plue I use the nVidia GeForce 9600M. I use the drivers from Administration -> Additional Driver and the version is 270.41.06. The box has not appeared in a while now but when it does I will try what you suggested. By the way, I use gnome classic and not natty's unity.

@mc4man No, I actually installed ubuntu natty from scratch (not by upgrade) a few days back and have not changed any of these settings (and I do not plan on that, at least not for now). 

I have to say that I think the actual shape of that area is not just a rectangle on the bottom of the screen. I have also noticed some lines going up from the edges of the rectangle. Very thin lines. I would bet they are 1-3 pixels.

Thanks a lot for the help so far :)

---

### Post by UbuNoob001 on 2011-05-02
> **sakishrist said:**
> @~Plue I use the nVidia GeForce 9600M. I use the drivers from Administration -> Additional Driver and the version is 270.41.06. The box has not appeared in a while now but when it does I will try what you suggested. By the way, I use gnome classic and not natty's unity.

@mc4man No, I actually installed ubuntu natty from scratch (not by upgrade) a few days back and have not changed any of these settings (and I do not plan on that, at least not for now). 

I have to say that I think the actual shape of that area is not just a rectangle on the bottom of the screen. I have also noticed some lines going up from the edges of the rectangle. Very thin lines. I would bet they are 1-3 pixels.

Thanks a lot for the help so far :)

same problem,  though my box is thinner and wider. Unity, 11.04

---

### Post by jqp on 2011-05-06
This is happening to me as well. Natty in Classic mode.

Yes, it does appear to be more than just a long rectangle.

it's a hollow square like this:

```

##############################
#                            #
#                            #
#                            #
#                            #
##############################
##############################
##############################

```

After rebooting, it goes away, but then comes back after a while. I don't know what program I'm opening in between that causes this. Same results with xkill and xprop as mentioned earlier.

Also using Nvidia with 270.41.06 driver.

This is driving me insane. Lots of dialogs tend to pop up with their buttons right inside that unclickable area.

I use my monitor in 'left' orientation if that makes a difference. It doesn't appear to based on others' comments.

---

### Post by sakishrist on 2011-05-06
> **jqp said:**
> 

```

##############################
#                            #
#                            #
#                            #
#                            #
##############################
##############################
##############################

```That is exactly it!

---

### Post by phonicboom on 2011-05-07
This affects me too. Seems to be a new 'feature' in the nautilus desktop. 

I'm subscribed to this post and awaiting a fix, so if you work it out please post back. 

Thanks!

---

### Post by phonicboom on 2011-05-07
Note that xkill may not appear to work as there could be hundreds or thousands of this invisible window on top of one another so that killing it kills one and the rest remain. 

Also the invisible could be owned by root so only sudo xkill would kill it (though there could still me multiples of it) 

For me it is on all desktops and quite low on the screen (my resolution is low 1280x768 and I'm using intel drivers. 

I suggest this: 

1) open one terminal and run top (press q when you want to quit top)

2) open another terminal and enter this

while [ 1 ];do sudo xkill;done

3) then click repeatedly in the dead spot looking to see in 'top' if anything goes away. 

4) To quit the infinite while loop press CTRL+Z CTRL+D CTRL+D then click one more time in the dead spot.

---

### Post by ~Plue on 2011-05-08
Another user seems to have had the exact problem in natty and found a solution.
Edit: Forum post> [http://ubuntuforums.org/showthread.php?t=1752249](http://ubuntuforums.org/showthread.php?t=1752249)[]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/777669")

---

### Post by phonicboom on 2011-05-08
> **~Plue said:**
> Another user seems to have had the exact problem in natty and found a solution.
Edit: Forum post> [http://ubuntuforums.org/showthread.php?t=1752249](http://ubuntuforums.org/showthread.php?t=1752249)[]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/777669")

Thanks but I'd say that is the same problem and *no fix* as restarting X is not a fix. 

It is likely this is a Compiz issue though.

---

### Post by ~Plue on 2011-05-08
> **phonicboom said:**
> Thanks but I'd say that is the same problem and *no fix* as restarting X is not a fix. 

It is likely this is a Compiz issue though.
His fix wasn't only restarting X, it was resetting the compiz settings to the default and re-enabling/disabling what he previously had..

---

### Post by phonicboom on 2011-05-09
> **~Plue said:**
> His fix wasn't only restarting X, it was resetting the compiz settings to the default and re-enabling/disabling what he previously had..

true :) I feel this problem is in Compiz - are all users with this problem using Unity 3D?

---

### Post by sakishrist on 2011-05-11
> **phonicboom said:**
> true :) I feel this problem is in Compiz - are all users with this problem using Unity 3D?I use ubuntu classic (with all the visual settings to default) and I have not installed anything that has to do with compiz. I mean ... there have to be some compiz* packages installed on my system but they are the pre-installed ones, the ones that came with the installation of natty.

So if the problem is with compiz then it's with one of the essential packages.

PS: I have a hunch though, that the problem comes from wine. It is usually then when the window appears. But, I am not sure.

---

### Post by sakishrist on 2011-05-11
They seem to have identified the problem and found a way to reproduce it. I have not tested this. [Link]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/709461/comments/30").> [Doug McMahon]("https://launchpad.net/%7Emc3man")             wrote             on 2011-02-09:                                                             [ #30]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/709461/comments/30")                                                        Try this - fresh boot
Open synaptic, should open in a typical default or so window size.
Maximize and then close synaptic
Open synaptic again, should open maximized, then click restore, it should only restore to slightly less than maximized
Grab the r. bottom corner of synaptic and resize to 'normal' windowed size
Then close synaptic and click on the power button > log out. At least  here the confirmation box will not show (enter on keyboard will work  though
 If the above doesn't cause, then  a slight variation - on my desktop I  need to Alt+l.click and move synaptic up to be able to resize, then  after the resize pull down to close. So same as above but move up then  down
 I can repeat this at will, hope you see the same
 Also on unity opening update after synaptic (open/close) may also cause the same or crash the kuancher

        


---

### Post by jmblock2 on 2011-05-16
Same issue. I did the infite xkill thing with no luck. I created a screenshot of the area where it's affecting me. I am using an upgraded natty with ubuntu classic. I'll try out the compiz thing.

---

### Post by phonicboom on 2011-05-17
To reproduce this error of the "Small Unclickable Area" all I have to do is Open Synaptic and the invisible area appears.

---

### Post by jperelli on 2011-05-23
The same issue here on Natty, compiz on, some experimental plugins
here some info, maybe some of you could see something in all this data...

sudo xwininfo -all (and then click in the invisible window)
```

xwininfo: Please select the window about which you
          would like information by clicking the
          mouse in that window.

xwininfo: Window id: 0x1281f70 (has no name)

  Root window id: 0x14d (the root window) (has no name)
  Parent window id: 0x14d (the root window) (has no name)
     0 children.

  Absolute upper-left X:  143
  Absolute upper-left Y:  278
  Relative upper-left X:  143
  Relative upper-left Y:  278
  Width: 1092
  Height: 264
  Depth: 0
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOnly
  Colormap: 0x0 (not installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: yes
  Corners:  +143+278  -131+278  -131-226  +143-226
  -geometry 1092x264+143+278

  Bit gravity: ForgetGravity
  Window gravity: NorthWestGravity
  Backing-store hint: NotUseful
  Backing-planes to be preserved: 0xffffffff
  Backing pixel: 0
  Save-unders: No

  Someone wants these events:
      EnterWindow
      StructureNotify
      FocusChange
      PropertyChange
  Do not propagate these events:
  Override redirection?: Yes

  No window manager hints defined
  Window manager hints:
      Process id: (unknown)

  No normal window size hints defined
  No zoom window size hints defined

  No window shape defined
  No border shape defined

```It's really a phantom!!

sudo xprop (and then click on the phantom freaky window)
```
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
```almost nothing...

then I made a
ps -aux > ps1
sudo xkill
ps -aux > ps2
and the diff between the pss is this:
```
< root      1126 10.4  3.1 166064 57296 tty7     Ss+  May22  92:43 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-PP7AGq/database -nolisten tcp vt7
---
> root      1126 10.4  3.1 166064 57296 tty7     Ss+  May22  92:44 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-PP7AGq/database -nolisten tcp vt7
96c96
< jperelli  1747  0.1  2.3 699248 42088 ?        Sl   May22   1:08 nautilus
---
> jperelli  1747  0.1  2.3 699248 42092 ?        Sl   May22   1:08 nautilus
123c123
< jperelli  2125  3.2  0.2 315292  4628 ?        Sl   May22  29:02 conky
---
> jperelli  2125  3.2  0.2 315292  4628 ?        Sl   May22  29:03 conky
129,130c129,130
< jperelli  9446 13.2 17.3 1070768 310480 ?      Rl   04:04  10:48 /usr/lib/firefox-4.0.1/firefox-bin
< jperelli  9530 38.3  2.2 481928 40724 ?        Sl   04:08  29:53 /usr/lib/firefox-4.0.1/plugin-container /home/jperelli/.mozilla/plugins/libflashplayer.so -omnijar /usr/lib/firefox-4.0.1/omni.jar 9446 true plugin
---
> jperelli  9446 13.1 17.3 1070768 310744 ?      Rl   04:04  10:50 /usr/lib/firefox-4.0.1/firefox-bin
> jperelli  9530 38.2  2.2 481928 40724 ?        Sl   04:08  29:53 /usr/lib/firefox-4.0.1/plugin-container /home/jperelli/.mozilla/plugins/libflashplayer.so -omnijar /usr/lib/firefox-4.0.1/omni.jar 9446 true plugin
140c140
< jperelli 10201 10.6 10.0 646104 180556 ?       Sl   05:05   2:17 gimp-2.6
---
> jperelli 10201 10.4 10.0 646104 180556 ?       Sl   05:05   2:17 gimp-2.6
146c146
< root     10560  0.2  0.0      0     0 ?        S    05:22   0:00 [kworker/0:1]
---
> root     10560  0.1  0.0      0     0 ?        S    05:22   0:00 [kworker/0:1]
149c149
< jperelli 10642  0.5  0.3  27304  6232 pts/2    Ss   05:25   0:00 bash
---
> jperelli 10642  0.4  0.3  27304  6232 pts/2    Ss   05:25   0:00 bash
151c151
< jperelli 10709  0.0  0.0  20316  1356 pts/2    R+   05:26   0:00 ps -aux
---
> jperelli 10714  0.0  0.0  20316  1360 pts/2    R+   05:26   0:00 ps -aux

```there are no respawning processes... xkill just doesn't work...
Really no idea.
This is a major bug somewhere, really annoying!
But it makes me laugh a little, we seem all crazy with a phantom!!

---

### Post by djbacon on 2011-05-30
The same problem for me too. I never had it on 10.10, but since clean install of 11.04 i started having this, but after a while. Interesting is that that unclickable rectangle is not standing in one place. Today i noticed that it is lower that it was before. 
This is a really annoying thing, especially when i work with files and i cannot click them.

---

### Post by RasH on 2011-06-01
This is one of MANY problems with the compiz version used in natty, which is NOT a stable release. I've never seen ubuntu this unstable and I've been using it since 7.04... I even switched to Linux Mint because I just don't like what's becoming of Ubuntu.

I have downgraded to older compiz version (0.8.6) and everything works just fine. It's much faster and all the problems are gone.

Here's a very simple how-to that works both for Ubuntu and Mint:

[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

**NOTE: Compiz 0.8.6 DOES NOT work with unity.** This is only good for those who want to use the "classic desktop".

---

### Post by .psd on 2011-06-03
Same problem, started a thread about it [here]("http://ubuntuforums.org/showpost.php?p=10896481&postcount=1"). There's no excuse for this whatsoever on any level, especially after **months**!! Heads should roll.

What, did Activision buy Ubuntu now, too? They're famous for hyping terrible releases and ruining brands at the peak of their potential. 

Honestly, even with M$ epic acts of suck and ignorance, I've never experienced anything this dumb in Windows.

This is perfectly ludicrous. ***ing amateurs.

EDIT: omg raging.

---

### Post by onon_onon on 2011-06-05
xkill -frame does the trick and restarts unity.

```
$ xkill -frame
Select the window whose client you wish to kill with button 1....
xkill:  killing creator of resource 0x1000f46
```

---

### Post by cybrian.saurav on 2011-06-05
Please help me,
I upgraded my ubuntu 10.10 to 11.04. Then I wanted to give some graphical effects by using "compizConfig Setting Manager". But Suddenly I saw that my sreen blinked once and all my window borders has gone! :(
The ubuntu 11.04 launcher in the left screen side is also vanished! :( There is no close button or minimize button to close a window.


Please give me some Idea

---

### Post by ernz on 2011-06-07
Here's another screenshot with the problematic area outlined. Dead area appears to be 660px wide and 40px high.

---

### Post by olivertreend on 2011-06-08
Just thought I'd add to this by confirming that I, too, am experiencing this bug.
It's also worth noting that this bug appears to cover all 4 workspaces - i.e. no matter what workspace I'm using, the unclickable region is in the same place, which is contrary to [this reported bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/709461").

I'm using Intel graphics drivers (at least, I think I am - I have Intel integrated graphics), running at 1920x1080 with Unity 3D on 11.04.

This unclickable area is bugging me! It looks like running:
```
compiz --replace
```
relieves the problem. But why is it occurring in the first place!?

Just a side-thought, but possibly a related issue: is anybody else (especially those running Intel drivers) experiencing problems of the screen turning into a mangled 'checkerboard' for a few seconds before the computer cuts out & reboots? It happens once every couple of hours - there's no telling when it will happen, and I can't find anything that will reliably reproduce it. Everything is fine & dandy, and then the screen screws up, and when it does I lose all my work & the PC reboots.

It's puzzling me beyond belief! My computer is a fresh build, and I'm not sure whether it's a hardware or software issue, though I'm leaning towards software. It's interesting that 11.04 is using an unstable version of Compiz... sounds like this might be causing the problem - maybe an incompatibility with the Intel drivers.

It's such a shame. 11.04 is just unusable at the moment. I don't want to have to wait until 11.10 though just to get a stable system.. :(

---

### Post by teique on 2013-01-05
thx! xkill did the trick to me!
next time I will try xprop to identify what app it is..
but, when I used xkill, compiz (Unity) was restarted.. and AFAIK it only restarts when it crashes or is terminated, so the unclickable area was Unity?

---

### Post by oldos2er on 2013-01-05
Old thread closed. If you have a question please start a new thread.

---

