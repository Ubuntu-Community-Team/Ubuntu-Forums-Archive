---
title: "Unity and most GUI controls gone after running Computer Janitor"
date: 2012-03-20
forum: General Help
---

### Post by ShokTHX on 2012-03-20
Help! I've done something stupid.
I ran Computer Janitor in Ubuntu Tweak - I should have known better.
Now, all the Unity (and maybe Gnome) GUI features are gone from my desktop. All I have is an apparent file manager file menu in where the upper bar used to be once I log in. Not even a way to shutdown or restart.
Oddly, file icons are still on the desktop and all my data is still there. F2 does not even work to start Terminal (Control+Alt+T does now).
How do I get my desktop working again?
Ubuntu 11.10.

---

### Post by 0011235813 on 2012-03-20
> **ShokTHX said:**
> Help! I've done something stupid.
I ran Computer Janitor in Ubuntu Tweak - I should have known better.
Now, all the Unity (and maybe Gnome) GUI features are gone from my desktop. All I have is an apparent file manager file menu in where the upper bar used to be once I log in. Not even a way to shutdown or restart.
Oddly, file icons are still on the desktop and all my data is still there. F2 does not even work to start Terminal (Control+Alt+T does now).
How do I get my desktop working again?
Ubuntu 11.10.

Hmmm... OK. The terminal in 11.10 is invoked with Ctrl+Alt+T by default, so that is not the problem.

I think you should install KDE and use that for a while, or some other interface.

For KDE, type in terminal (KDE is more full featured than LXDE, but is much more bloated and has some {minor} compatibility issues with Gnome) :
```
sudo apt-get install kubuntu-desktop
```
WARNING! Large download size.
for lxde:
```
sudo apt-get install lxde 
```
Now turn off the computer. When you get to the logon screen, click on the spanner near the password bar, and there you can choose the interface. Set it to either lxde or kde, which ever one you installed.

---

### Post by ShokTHX on 2012-03-20
It looks like I just need to rebuild the GUI elements:
Unity bar and notification bar and menus.
Anyway to initiate this?

---

### Post by philinux on 2012-03-20
> **ShokTHX said:**
> It looks like I just need to rebuild the GUI elements:
Unity bar and notification bar and menus.
Anyway to initiate this?

Open a terminal.

If you were running the default install then.

sudo apt-get install --reinstall ubuntu-desktop

Then you might need

unity --reset

No need for kde or lxde

---

### Post by 0011235813 on 2012-03-20
> **philinux said:**
> Open a terminal.

If you were running the default install then.

sudo apt-get install --reinstall ubuntu-desktop

Then you might need

unity --reset

No need for kde or lxde

Sorry I wasn't aware of that. But one should still give the other DEs a go- they are excellent, especially LXDE.

---

### Post by ShokTHX on 2012-03-20
I'e gotten as far as the "unity --reset" but it seems to have hung at:
Setting update "run_key"

The --reinistall ubuntu-desktop actually seemed to do something I had tried uninstall and install before.

Any idea on the run_key hang?

James

---

### Post by philinux on 2012-03-20
> **ShokTHX said:**
> I'e gotten as far as the "unity --reset" but it seems to have hung at:
Setting update "run_key"

The --reinistall ubuntu-desktop actually seemed to do something I had tried uninstall and install before.

Any idea on the run_key hang?

James

Computer janitor should be made redundant.

From terminal run this.

gsettings reset com.canonical.Unity.Launcher favorites

Then again

unity --reset

Use copy and paste to avoid typos

From here for future peeps.

 [http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration)

See links in Sig.

---

### Post by ShokTHX on 2012-03-20
It still not working. It looks like there are a bunch of compiz errors at the start of unity --reset.
I've tried most of the suggestions on the link but nope. Here is what I get from the unity --reset command:

james@UmbrellaCorp:~$ unity --reset
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing mousepoll options...done
Initializing vpswitch options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
Initializing snap options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
Initializing session options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Initializing addhelper options...done
Initializing animation options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing debugspew options...done
Initializing decor options...done
Initializing expo options...done
Initializing extrawm options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing grid options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"

I'm sure there there were packages deleted by Janitor. Is that that cause? If I knew which ones couldn't I just just add them with Synaptic?

James

---

### Post by rg4w on 2012-03-20
Has anyone ever had a non-destructive experience with Janitor?

---

### Post by Mark Phelps on 2012-03-21
> **rg4w said:**
> Has anyone ever had a non-destructive experience with Janitor?

Not ME.  I tried that years ago and it trashed my setup so bad I had to reinstall from scratch to get it working again.

Given the HUGE size of hard drives these days, don't understand the compulsion some folks have to run stuff like Computer Janitor.  It's not like we're back in the days of 10GB hard drives and space is at a real premium!

---

### Post by 0011235813 on 2012-03-21
> **Mark Phelps said:**
> Not ME.  I tried that years ago and it trashed my setup so bad I had to reinstall from scratch to get it working again.

Given the HUGE size of hard drives these days, don't understand the compulsion some folks have to run stuff like Computer Janitor.  It's not like we're back in the days of 10GB hard drives and space is at a real premium!

Unless maybe they could only afford the 40GB SSDs...
But I agree, with 1TB 7200rpm drives selling for under a hundred quid, it's really quite silly to obsess over disk usage, especially since Ubuntu uses a lot less than... You know who. 

But if one must clean up drives, have you tried Bleachbit?

---

### Post by HiImTye on 2012-03-21
> **rg4w said:**
> Has anyone ever had a non-destructive experience with Janitor?
I did, years ago, but I never actually did anything with it

---

### Post by wildmanne39 on 2012-03-21
Hi, the thing about unity --reset it never really gets done if you will let it run for about 3 minutes then tap the power button gently once then select restart and it should boot to unity.
thanks

---

### Post by TiloBunt on 2012-09-24
same issue here after using Janitor (Ubuntu Tweak)
looks like I'm back.(at least 2D)
first tried to unity reset and reinstall

but didn't help

After running:
[http://forum.parallels.com/printthread.php?t=259137](http://forum.parallels.com/printthread.php?t=259137)
Quote:
sudo apt-get install fglrx-updates
and rebooted.

I'm back at least 2D, will update the other post/questions I found.
Cheers
note I use a ASUS notebook with ATI 58xx mobile.

---

### Post by TiloBunt on 2012-09-24
after try to reinstall Unity
[http://askubuntu.com/questions/13101...-install-unity](http://askubuntu.com/questions/13101...-install-unity)

still didn't work but a new user I created was working.
check 2d vs 3d via

```
echo $DESKTOP_SESSION
```

so after login back to my account it also worked again.
check this thread for more ideas.
[http://ubuntuforums.org/showthread.php?t=1856053](http://ubuntuforums.org/showthread.php?t=1856053)
[http://ubuntuforums.org/showthread.php?t=2055955&page=3](http://ubuntuforums.org/showthread.php?t=2055955&page=3)

cheers

---

### Post by alwaysalicia on 2013-04-03
> **ShokTHX said:**
> Help! I've done something stupid.
I ran Computer Janitor in Ubuntu Tweak - I should have known better.
Now, all the Unity (and maybe Gnome) GUI features are gone from my desktop. All I have is an apparent file manager file menu in where the upper bar used to be once I log in. Not even a way to shutdown or restart.
Oddly, file icons are still on the desktop and all my data is still there. F2 does not even work to start Terminal (Control+Alt+T does now).
How do I get my desktop working again?
Ubuntu 11.10.


I've just fixed this issue with some poking around.  Go into synaptic package manager, status, residual config and reinstall everything in there except the kernals, next go into custom filters, missing recommendations and install everything in there.


That saved me from doing a complete reinstallation.  Hope this helps!

---

### Post by rsbrux on 2013-12-11
> **ShokTHX said:**
> It still not working. It looks like there are a bunch of compiz errors at the start of unity --reset.
I've tried most of the suggestions on the link but nope. Here is what I get from the unity --reset command:
...
James

Hi James,
I do not use Computer Janitor, but ran across this thread after my Unity 2d  desktop suddenly refused to display launchpad and title bar (for all  users), for no apparent reason. 

When I tried to run:
```
unity --reset 
```
I got results similar to yours; it would always hang at:
  ```
Setting Update "run_key" 
```  as also shown in [the log posted in the thread titled "unity has vanished"]("http://ubuntuforums.org/showthread.php?t=1974219&p=11910660#post11910660") for unity run with no arguments.

  I noticed that the error message delivered by:
  ```
/usr/lib/nux/unity_support_test -p
``` 
 was similar to some of the errors reported by unity --reset:
```
error while loading shared libraries: libGL.so.1: 
cannot open shared object file: No such file or directory.
```
Autohide was disabled. Reenabling Unity in CCSM as sugggested in other threads was part of the solution, but none of the other measures suggested in this and several other related threads, including, but not limited to:

[LIST]
[*]Reinstalling unity 
[*]Reinstalling ubuntu desktop 
[*]Removing all relevant (e.g. compiz, gconf, etc.) configuration information 
[/LIST]
 helped me to completely resolve these symptoms.

After extensive searching, I found the [following solution (courtesy of J.D. Bartlett]("http://sqizit.bartletts.id.au/2011/11/07/unity-launchersidebar-missing-on-ubuntu-11-10/")):
  
[LIST=1]
[*]Get the path of libGL.so.1 by using the command locate libGL.so.1. 
[*]Add a link to the library in /usr/lib/ as shown in the following example: 
[*]sudo ln -s /usr/lib/i386/mesa/libGL.so.1 /usr/lib 
[*]Restart the computer. 
[/LIST]
  
 This not only allowed both unity_support_test-p and unity --reset to  run, it also allowed Unity 2d to start. Like the author of the  above-mentioned post, I have no idea what caused my problems. I am also  still not sure whether the link is a complete solution, or whether I  should reinstall the graphics libraries completely, but since creating  the link, everything has worked fine for a few weeks now.

---

