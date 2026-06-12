---
title: "How do I enable compiz in Ubuntu 11,04?"
date: 2011-04-29
forum: General Help
---

### Post by colobix on 2011-04-29
Hey. I just upgraded ubuntu, and now I can't find visual effects.
For some reason it's gone. 
So how do I enable compiz?
I don't use unity, I use the normal classic gnome.
Please help.

---

### Post by jerome1232 on 2011-04-29
check that ccsm is installed, that's the program that configures compiz effects.

---

### Post by colobix on 2011-04-29
that's just the compiz config manager.
But how do I enable comiz now?

---

### Post by jerome1232 on 2011-04-29
Assuming you have a proper video card and the drivers are installed for it, compiz should be on by default, it is for me. Just start enabling the plugins you want in ccsm.

---

### Post by 3Miro on 2011-04-29
Are you using Unity? If you have the dock on the side, you are already using Compiz. You can use CCSM to adjust the individual effects.

---

### Post by Spc 4 on 2011-04-29
How do I get rid of the dock on the side and get my old desktop back?

---

### Post by colobix on 2011-04-29
As I said, no I am not using unity. I use the classic gnome.
And yes I have a proper graphic card. I said, this happened after I upgraded. Seriously, I already told you this.
The Visual Effects tab is gone.

---

### Post by WorMzy on 2011-04-29
Try running ```
compiz --replace
``` Anything happen?

---

### Post by colobix on 2011-04-29
That command didn't help much. 
It tried to restart compiz. The icons and the panels were gone for like a second and came back.
COmpiz is obvioiusly running but can't "read" the effects.
And no, I'm not logged in to the "no effects" session, but the normal gnome 2.

---

### Post by EarlsFurniture on 2011-04-29
I have the same problem but want to solve it for opposite reasons.  I have the capability to run Unity and want to, but there is no Visual Effects tab and Natty tells me I don't have sufficient hardware to run Unity.  Except that I DO have sufficient hardware...  And no way to turn on advanced effects...

---

### Post by caelum on 2011-04-29
I have the exactly the same problem and I am asking the same question, 'How do I enable compiz in Ubuntu 11,04?'.

I cannot find it anywhere in the new desktop. Anyone know?

---

### Post by SecretCode on 2011-04-29
Do you have **fusion-icon** running and showing in the notification area? Highly recommended if using compiz.

If you have, right-click > select window manager and check compiz is running. Also try "Reload Window Manager".

(eta: applicable if running classic desktop. May not work or be needed for those running Unity.)

---

### Post by caelum on 2011-04-29
Thanks for your reply SecretCode. I just installed fusion-icon, but it's not showing in the notification area.

How do I put new stuff in the notification area?

---

### Post by colobix on 2011-04-29
You don't understand. As I said, Compiz is obviously running, but the effects can't be enabled even though they are enabled in ccsm.

---

### Post by jerome1232 on 2011-04-29
Double post, could have sworn I clicked edit...

---

### Post by jerome1232 on 2011-04-29
What video card are you using, are you sure you have the proper video driver for it installed?

As an after thought did you do a network upgrade, upgrade from a cd, or fresh install.


I did a network upgrade (ie through apt-get) and unity was crashing on log in. Did a fresh install and all issues are cleared up.

---

### Post by SecretCode on 2011-04-29
> **caelum said:**
> Thanks for your reply SecretCode. I just installed fusion-icon, but it's not showing in the notification area.

How do I put new stuff in the notification area?

Are you running the Unity desktop? If so, compiz is already running.

To get notifications icons to appear in the Unity top bar you may need to "whitelist" them. You'll have to search the forum / the web for that as I haven't done it ...

---

### Post by EddieGal on 2011-04-29
> **colobix said:**
> You don't understand. As I said, Compiz is obviously running, but the effects can't be enabled even though they are enabled in ccsm.

Having the same problem as you, I have unity installed, compiz effects marked, but they are not working. My card is an Nvidia 7400Go, which run prefectly fine compiz on 10.10.

---

### Post by Blasphemist on 2011-04-29
ccsm can be installed from the software center. At the login screen. you can choose ubuntu classic for those that don't want unity. For the nvidia question, there has been much about that in these forums and I recommend you search on your particular version.

---

### Post by EddieGal on 2011-04-29
In my case I have ccsm already installed. Did a search on my graphics card and haven't found a solution.

It seems those problems come from updating through the manager, fresh installations work fine.

---

### Post by colobix on 2011-04-30
THere is nothing wrong with my graphics card. I know cuz everything worked before I upgraded.
And I think I Have the proper driver too. I have shadow effects around the windows but nothing when I check the "no graphic" mode.
And for the 3rd time, I have ccsm installed but it doesn't recomgnize the effects when I switch them on or off.
Maybe this will get solved if its possible to get the Visual Effects tab back?
Btw when I go to the nvidia configuration settings, everything seems to work fine. I mean no warnings or anything that indicates my driver isn't working. 
And games are working just fine too.

---

### Post by jerome1232 on 2011-04-30
If I recall correctly installing simple-ccsm will get that visual effects tab back, although I don't feel that is the issue.

I've seen one post where after doing a network upgrade, 3d was messed up. The op downloaded the cd, booted from it and had the option to upgrade from 11.04 to 11.04, it repaired his packages and everything was working.

Perhaps give that a try.

---

### Post by colobix on 2011-04-30
Thanks. So what did he do to upgrade from 11.04 to 11.04? Do you have the post link or title so I can find it?
Or will the cd basically ask if I want to upgrade from 11,4 to 11,4?

---

### Post by jerome1232 on 2011-04-30
[http://ubuntuforums.org/showthread.php?t=1741759&page=2](http://ubuntuforums.org/showthread.php?t=1741759&page=2)

Based on the thread it asked the op to upgrade as one of the options.

It also may not have worked as well as I had hoped. If it does not work, do you have a little extra room you can try a fresh install out in to determine if the problem is caused by doing an upgrade??

---

### Post by Blasphemist on 2011-04-30
> **colobix said:**
> Thanks. So what did he do to upgrade from 11.04 to 11.04? Do you have the post link or title so I can find it?
Or will the cd basically ask if I want to upgrade from 11,4 to 11,4?

Upgrading to release from beta is automatic from the daily updates. You don't have to do anything else.

---

### Post by jerome1232 on 2011-04-30
That's not what we are attempting to do.

---

### Post by filster on 2011-04-30
I have the same problem. For me, it's driver related, for sure. I have a Nvidia graphic card and can't use the proprietary driver (for ex. nvidia current). It's says that the driver is enabled but not in use. So I can't see the visuall effects tab, can't run Unity etc.. For me, it's related to this issue - [http://ubuntuforums.org/showthread.php?t=1739269](http://ubuntuforums.org/showthread.php?t=1739269) . The driver version that is shown in nvidia-settings is 270.41.06 , I run a 64bit Ubuntu (I upgraded from 10.10 just yesterday).

---

### Post by colobix on 2011-04-30
PRoblem is. I have the final version, not beta.
So I can understand why the upgrade was possible.
Also, I tried the cd version in virtual box but even there I have no visual effects tab. This means that the cd AND the network download are having the same annoying problem.
Is there a repository with an older compiz version available?
I thought that maybe if I uninstall all the compiz packages and force install an older version would work.
Also, I don't think this is a broken package or a glitch, but obviously something that makes unity work.
As you know, unity 3d does not work without compiz.

---

### Post by filster on 2011-04-30
It's not only a compiz thing, I think it's a general 3D support thing. The graphic driver doesn't work, so you only get 2D and that way you can't start Unity 3D or any other eye candy stuff, that requires 3D (as some fancy docks etc.).
I have the "final" Natty version too and all of those guys having Nvidia trouble have it too.

---

### Post by colobix on 2011-05-01
Nope. As I said in my first post.
I don't use unity. I use the old one.
So that's why I Think this is a compiz thing./

---

### Post by cottfcfan on 2011-05-01
Colobix, Ive read somewhere that this is a bug, but can't find it now.
Ive got the same problem, but installing fusion-icon, means i can adjust the effects from there.
Otherwise patience and a fix will probably appear in an update.

---

### Post by josephku on 2011-05-01
Sorry for your frustration.  If you have not already done so, look for "Hardware Drivers" in your "Applications" menu to see if you have "proprietary" drivers that need to be loaded (e.g Nvidia). Normally you have to install these drivers to enable high performance graphics (used by compiz).

---

### Post by filster on 2011-05-01
> **colobix said:**
> Nope. As I said in my first post.
I don't use unity. I use the old one.
So that's why I Think this is a compiz thing./

You didn't understand me. Look in additional drivers, if you have any proprietary drivers checked (installed). If it says enabled (or active) but not in use, you have the same problem as we all have. In my oppinion also in your case it's a driver problem, not a compiz/unity problem.

---

### Post by colobix on 2011-05-01
> **filster said:**
> You didn't understand me. Look in additional drivers, if you have any proprietary drivers checked (installed). If it says enabled (or active) but not in use, you have the same problem as we all have. In my oppinion also in your case it's a driver problem, not a compiz/unity problem.
Ok so if that's the case. HOw do I fix it?

---

### Post by timgood on 2011-05-01
> **filster said:**
> You didn't understand me. Look in additional drivers, if you have any proprietary drivers checked (installed). If it says enabled (or active) but not in use, you have the same problem as we all have. In my oppinion also in your case it's a driver problem, not a compiz/unity problem.

Got Nvidia card? Boot into Unity. Check proprietary drivers. It will tell you that the Nvidia driver is installed, activated but not in use! Then check the Window Manager using Fusion Icon. It will tell you that compiz is the window manager! It's *not* a driver problem, it's an 11.04 problem.

Now do the same for classic. Same problem. For me, trying to enable compiz in classic results in the loss of menu items and window borders. It is not a driver problem. It's Natty Dread!

---

### Post by colobix on 2011-05-01
Thanks. It works now. I have no idea how but after I uninstalled compiz and unity, and force installed an older version it works.
But I Think I wanna go back to the old version. There are too many glitches on this version in my opinion. Maybe cuz it's new and not fixed yet, but still.

Thanks for your help, everybody:)

---

### Post by hoopotus2 on 2011-05-02
Could I know as well, how I should run apt-get to install the version of compiz that makes the "visual effects" tab back visible? What version is it? Thank you in advance.

---

### Post by diaco on 2011-05-14
I've this problem too. Nvidia driver is not working in 11.04 (final ver.) could use compiz effects in previous versions of ubuntu. Jokey says "driver is activated but not in use...". I've tryed Nvidia-current, Nvidia 173 from repos and also the driver available on nvidia's website. Aftter 2 weeks trying finally gave up.  Long live windows 7! I'll be back to linux as soon as I can use my vga (GeForce go 7400) like older distros.

---

### Post by caelum on 2011-05-14
I could not figure this out, so I have reverted back to 10.10.

---

### Post by dugh on 2011-05-21
I see this issue, too, I don't see any option anymore to enable compiz.

I just installed bumblebee which allows nvidia optimus cards to work again:
[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

(didn't fix this issue though)

---

### Post by dugh on 2011-05-21
And I can't even report this bug, since the new command line tool we are forced to use to report bugs won't accept the bug report.  That pisses me off more than the actual bugs, and also the fact that it's buried under a lot of other text on some obscure wiki page.  It's no wonder there are so many regressions in this release compared to 10.10 when most people aren't even able to report bugs.

---

### Post by Gstrazds on 2011-05-24
Hi Folks.. your compiz is enabled.. with very limited function..

You have to install Compiz Config settings Manager - from Synaptic package manager.

That will give you access to all the settings.. 

Enabling incompatible settings will make all the menus/control features disappear leaving just the desktop.. 

Installing a Compiz Config settings Manager. icon on the classic desktop shows up on the Unity desktop; clicking it; reset to default, fixes everything - then enabling compatible features gives you some great effects... installing a control settings icon also gets you there...

Well done Ubuntu Development team :)

Having Compiz Config settings Manager. installed in Unity which is still Alien to me also lets you play with the compiz settings in Classic.. as well, works great!

I noticed two compiz settings devices; simple and the above - simple might have to go... although it's not gone on my system and not interfering..

My nividia proprietary driver saying - not in use; is false; It actually is in use..

You might run into my problem; where if you open a bunch of windows - they start going blank.. now guessing address space is being exceeded..
 
I'd say this thread is now solved

---

### Post by Tombigel on 2011-06-01
@Gstrazds: I couldn't understand this step:
> **Gstrazds said:**
> 
Installing a Compiz Config settings Manager. icon on the classic desktop shows up on the Unity desktop; clicking it; reset to default, fixes everything - then enabling compatible features gives you some great effects... installing a control settings icon also gets you there...


What appears where and where is a "Reset to default" button?
I just don't get what am I supposed to do.

Thanks

---

### Post by Blasphemist on 2011-06-01
You can search for ccsm in the software center, see first screen shot.

You will now have CompizConfig Settings Manager that you can run to make changes. Click the Preferences on the left side. See second screen shot. Then click the Reset to defaults button.

---

### Post by Tombigel on 2011-06-02
ok, thanks. just didn't find the reset button.

but

it does nothing in my case. I guess i'll have to wait for Nvidia to fix their drivers...

---

### Post by Blasphemist on 2011-06-02
> **Tombigel said:**
> ok, thanks. just didn't find the reset button.

but

it does nothing in my case. I guess i'll have to wait for Nvidia to fix their drivers...

I have a feeling. Please run this
```
lspci | grep VGA
```
My feeling is that you will have both an integrated Intel gpu and the nvidia. If so, look at the debumblebee project.
[https://github.com/z0rc/debumblebee#readme](https://github.com/z0rc/debumblebee#readme)
> This project allows you to utilize nVidia graphics card with proprietary driver
while running main desktop on Intel card. This service is only for Intel/nVidia
combination, it won't work with Intel/ATI or any other combination.

debumblebee is combination of additional X server for nVidia graphics card and
VirtualGL package which allows to access nVidia X server screen from Intel X
server screen with full OpenGL support.

---

### Post by Gstrazds on 2011-06-03
> **Tombigel said:**
> @Gstrazds: I couldn't understand this step:


What appears where and where is a "Reset to default" button?
I just don't get what am I supposed to do.

Thanks

Well Open CompizConfig Settings Manager; Left side of the window says Preferences..

Click on that... 

Profie & Backend tab

Under Profile import; import as; export; Reset to defaults; click this one - then your good to go..

an additional contribution..

enable the wiggly feature.. to see if your invidia drivers are working

---

### Post by bcollignon on 2011-06-10
Using Startup Applications, I've attached the commands compiz --replace and emerald --replace, which seem to obviate any problems with Compiz and Emerald starting and running properly for the time being.  I don't know why these commands seem to work, but they do for now.  Bear in mind, I have a somewhat unusual installation, ridding myself of Unity, then reinstalling post-crash.  I tried to revert to 11.04 w/o Unity (older version of Compiz) and Gnome.  It worked for a while, but seemed to have other issues.  I did a fresh install w/o formatting the drive (hold Home and other folders), and have used the above startup commands to resolve Compiz running issues with Unity.  I'm definitely not sold on the Unity desktop, but I want to work with it to see what happens in subsequent releases.

---

### Post by bcollignon on 2011-06-10
Incidentally, I had to install my Nvidia graphics driver from Nvidia (latest version) to get Unity to work at all.

---

