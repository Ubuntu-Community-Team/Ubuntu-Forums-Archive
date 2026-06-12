---
title: "Can't launch applications"
date: 2010-04-12
forum: General Help
---

### Post by Astarta on 2010-04-12
Hello, I upgraded from 9.04 to karmic, and then I found out that I can't launch applications some time after booting the os. I mean when I launch them from the panel or menu or if I just try to switch off the computer with a standard applet it won't work or when I try to open a folder on desktop or open some file on it. I need to reboot with a button on the case and then after boot I can launch applications for a while... tried reinstalling all packages concerning nautilus but it didn't help.
I searched the forum and googled and found nothing, what can it be?

---

### Post by 98cwitr on 2010-04-12
i had the same problem...can you run them from terminal though (i could and just had to re add the icons to the menus)?

---

### Post by Astarta on 2010-04-12
I can't launch terminal :D

---

### Post by jdackle on 2010-04-12
Try pressing Ctrl+Alt+F2. This will bring you to a text console. Ctrl+Alt+F7 will get you back to the GUI. ;)

---

### Post by Astarta on 2010-04-12
Okay, i tried to run several programs from tty using ctrl alt f1
opera: cannot connect to X server
opera: fatal error on creating Qt application object
evolution — cannot open display or something like that (I have russian localization)

---

### Post by sdibaja on 2010-04-12
Firefox flash player won't load... I want my Youtube!

---

### Post by wojox on 2010-04-12
> **Astarta said:**
> Okay, i tried to run several programs from tty using ctrl alt f1
opera: cannot connect to X server
opera: fatal error on creating Qt application object
evolution — cannot open display or something like that (I have russian localization)

Just try Alt+F2 and type in an application. You need X to run GUI's

---

### Post by Astarta on 2010-04-12
It doesn't launch this way too(

---

### Post by 98cwitr on 2010-04-12
From GUI:

Alt+F2 
xterm

Should still have X server loaded and load terminal.

If this doesn't work, try going back into tty and running:

sudo apt-get autoremove
asuo apt-get purge *whateverAutoremoveListedBeforeRemovalConfirmation*
sudo apt-get update
sudo apt-get upgrade

---

### Post by Astarta on 2010-04-12
xterm from Alt+F2 doesn't load too

---

### Post by 98cwitr on 2010-04-12
see edit

---

### Post by Astarta on 2010-04-12
> **98cwitr said:**
> From GUI:
sudo apt-get autoremove
asuo apt-get purge *whateverAutoremoveListedBeforeRemovalConfirmation*
sudo apt-get update
sudo apt-get upgrade
Found nothing to autoremove, nothing to upgrade, updated about 2 packages i think it was chrome.

---

### Post by 98cwitr on 2010-04-12
so you said it will work for a little while right after a hard reboot...how long is a little while?

---

### Post by Astarta on 2010-04-12
About half an hour I think, maybe an hour, I tried to measure but it's all approximate

---

### Post by 98cwitr on 2010-04-12
something else i'd measure is your processes. You be opening something and a process is conflicting with X. Keep your system monitor open and the process tab viewable.

---

### Post by Astarta on 2010-04-12
I did this, I booted and launched my usual applications one by one, not closing them after that, and then I launched Open Office, but closed the new document almost at once, and then when i tried to open my home folder it failed. And no applications launched after that. Then I closed almost all applications except firefox and pidgin and nothing still wants to launch now.

Now I go home, I can test further only tomorrow, I hope this thread won't be down too much, I have ubuntu here on work

---

### Post by jdackle on 2010-04-12
Sorry, my post was misleading but was unintentional...
It will give you a command-line to run programs but you must either specify the display to use (the one on Ctrl+Alt+F1/F2 is not the same as that of Ctrl+Alt+F7) if the program allows it (and I don't actually know how to specifu) or run a program that does not use the graphical interface.

So you can go to tty2 and run```
ps ux
```This will give you information similar to the graphical System Monitor application.
Why?
My hint is that you are might be running an application (you started or the system is configured to start after some time) that is blocking your mouse clicks (some programs claim access to the input devices  but usually only inside their own windows, you might be running a faulty app though, which somehow "managed" to claim more it's entitled).
With ps you can check what programs were on before you lost control of the mouse clicks and which ones are there after.
You can then try to kill the concerning process:```
kill -SIGKILL <pid>
```The pid (process identification) is the number listed by ps under PID for the respective process name. ;)

If that works, you'll at least know what process is causing the issue. How to solve it will be another issue...
But you can try this out and maybe we'll get some more useful info.

There are also some log files you might check but I don't really know much about that. Sorry. ;(

---

### Post by Astarta on 2010-04-13
I did what u said and looked through thi list but all the applications launched on start and after that I launched only remote desktop client manually, and then I launched Open Office from Gnome Panel and closed it at once just to check if it stops working after that and yes it did. I tried to check if it is a coincidence and killed one by one almost all applicatiions (starting with remote desktop and then killed those who launch on start until there were almost nothing left, including panels and I checked as I killed them but applications didn't want to launch and then I killed something important after that all icons disappeared and I couldn't check further)
Then I rebooted and at once after start I launched Open Office and closed it at once and after that nothing worked again. So I think it can be the cause maybe no proccesses are guilty but something else which happens when I start and close open office.

---

### Post by Astarta on 2010-04-13
Now I tried to test this openoffice issue further: I didn't run openoffice (I mean Writer) and everything worked for about hour and a half and then I ran it again, and closed it, and after that nothing launched again at once, I tried to connect to remote desktop with a client than was opened before the openoffice. And there was an error: 
Autoselected keyboard map ru
Xlib: Did not parse entire setup message: parsed:
3084, message 120252
ERROR: Failed to open display: :0.0

Maybe this helps you to see what's going on, I don't know what to do... reinstalled openoffice packages that didn't help.. don't want to reinstall the system because it has been almost two years as I work on it, from 8.04 to 9.10 and there are lot of configs to backup

---

### Post by Astarta on 2010-04-13
Now I didn't launch OpenOffice at all and everything's working... but I will have to use it every day... the problem is that reinstallation of its packages doesn't work and I think it's not openoffice that causes this but something that I trigger when I launch it, because when I run it and then close the document the programs stop to launch when no openoffice process is running... and no other processes that could have started alongside with it
Any ideas? Please help, tell me where to dig

---

### Post by jdackle on 2010-04-16
Sorry it took me so long to reply back... :(

If I understood correctly, when you said (in your first reply to my previous post):
> Then I rebooted and at once after start I launched Open Office and closed it at once and after that nothing worked again. If I understood correctly, you did NOT run your remote desktop client before openoffice and still the problem appeared again after you started and closed openoffice, right? If so... the remote desktop connection is NOT related to your problem.

I'm beting it's probably some OpenOffice ADD-ON. Did you add any extension to OpenOffice? Sometimes they are not so reliable as OpenOffice itself... Some buggy add-on may be messing with your mouse configuration (to my experience, such devices' configuration is very permeable to be messed up by other programs even outside the scope of the affecting program).
If you have openoffice addons installed, you could try and test them like you did with the processes.

---

### Post by Astarta on 2010-04-16
> **jdackle said:**
> 
 If I understood correctly, you did NOT run your remote desktop client before openoffice and still the problem appeared again after you started and closed openoffice, right? If so... the remote desktop connection is NOT related to your problem.

Yes I know, I just wanted to say that remote desktop was running anc connecting ok, then I disconnected and ran Open Office Writer (only Writer! not Calc or smth) and when I closed the document and tried to connect it didn't work, so applications not only cannot be launched but some don't work even if they are running, I hoped that this will give you some hints.
After your previous reply I tested the system for 2 days and can say that this is exclusively Writer that messes things up. Everything works fine until I run it.
I will check for addons, but as long as I remember I didn't install any, at least I know for sure that I didn't find and install them myself. Maybe they were installed automatically.
I will find out this only on Monday sorry. 
I burnt an install karmic cd for me and thought about reinstalling in a week but as long as you answer I still have hope :)

---

### Post by jdackle on 2010-04-17
Oh, don't get too many hopes from me!... :rolleyes:

Back ontopic, if it's not an addon messing up OpenOffice, I'll have two more ideas:

1. A script you're using to call openoffice. But I think you said you're running it from the Applications menu, right? In that case, even if you were calling OOo through some script you called from the menu... the menu link would be reset to the original when reinstalling. Still... nothing's impossible and somehow there might be a script being called to run OOo and that script may be running anything before or after.
The fact only Writer causes the problem might also be because of this: you might have one custom script to run Writer and the default ones for the other OOo applications.

2. You are NOT reinstalling the default Ubuntu Karmic OpenOffice.org but rather some other build of it, it would only depend on what repositories you added to your /etc/apt/sources.list (i.e. what you added in the "Third Party Sources" tab of your "Configurations -> Repositories" in Synaptic). In that case, anything can be (un)expected. :P
Also... other third party repositories that might change packages on which the openoffice ones depend (e.g. uno) might be the problem.

But the above is pretty obvious, that's why I'm betting on the addons... :rolleyes:

---

### Post by Astarta on 2010-04-19
Writer doesn't have any addons installed.. and it is also run with default script at least I didn't change anything, no custom scripts
About the uninstall — I may have added some repositories when installing some programs like converters but I uninstalled Writer from Synaptic Manager I don't think it took packages from third-party repositories
I'm stuck now

---

### Post by jdackle on 2010-04-19
Below is theoutput on running *dpkg -p openoffice.org* on my Ubuntu 9.10:
```
$ dpkg -p openoffice.org
*<snip for for forum post>*
Depends: openoffice.org-core (= 1:3.1.1-5ubuntu1.1), openoffice.org-writer, openoffice.org-calc, openoffice.org-impress, openoffice.org-draw, openoffice.org-math, openoffice.org-base, openoffice.org-report-builder-bin, ttf-dejavu, openoffice.org-officebean, openoffice.org-filter-mobiledev, openoffice.org-java-common (>> 2.2.0-4), debconf (>= 0.5) | debconf-2.0
Recommends: openoffice.org-filter-binfilter, ttf-liberation | ttf-mscorefonts-installer
Suggests: hunspell-dictionary, myspell-dictionary, openoffice.org-help-3.1, openoffice.org-l10n-3.1, menu, unixodbc, cups-bsd, libsane, openoffice.org-hyphenation, openoffice.org2-thesaurus, libxrender1, libgl1, openoffice.org-gnome | openoffice.org-kde, iceweasel | firefox | icedove | thunderbird | iceape-browser | mozilla-browser, default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre, openclipart-openoffice.org, pstoedit, graphicsmagick-imagemagick-compat | imagemagick, libpaper-utils, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad, gstreamer0.10-ffmpeg
*<snip for for forum post>*
```
As you can see, most _dependencies_ are directly related to openoffice.org itself. Hence, if your openoffice packages come from the official Ubuntu repositories, you should have no problem coming from there.
Your system may be configured to treat _recommendations_ just like they were dependencies, in which case they will be automatically installed too. I don't think text-fonts packages different from the official (had you installed them) would cause the behaviour you describe. But I'm mostly making a point here...
The _suggestions_ will only be installed if you specifically order their installation. Still, people often do install (at least some) suggestions and in this case, openoffice will use that software. Something might break in openoffice if one or more of those packages are not  official. Do note the gstreamer-plugins packages are often repackaged for several purposes: if you are using a custom gstreamer package (or gstreamer plugins), that may be the source of your problem - but I would look for bugs in launchpad relating to that package and the use of openoffice (specially look in the concerning PPA in case that's where you got your gstreamer from).

Now for the (maybe) more interesting part: *[I]dpkg -p openoffice.org-_writer_*[/I]
```
Depends: openoffice.org-core (= 1:3.1.1-5ubuntu1.1), openoffice.org-base-core (= 1:3.1.1-5ubuntu1.1), libc6 (>= 2.3.6-6~), libgcc1 (>= 1:4.1.1), libicu40 (>= 4.0-1), libstdc++6 (>= 4.1.1), libstlport4.6ldbl, libwpd8c2a, libwps-0.1-1, ure (>= 1.5.1), zlib1g (>= 1:1.1.4)
Recommends: openoffice.org-emailmerge, openoffice.org-math
Suggests: openoffice.org-gcj, openoffice.org-base, openoffice.org-filter-binfilter, default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre, openoffice.org-java-common (>> 2.2.0-4)
Conflicts: openoffice.org-debian-files, openoffice.org-java-common (<= 1:2.3.1), openoffice.org2-writer (<< 1:3.1.1-5ubuntu1.1)
```Now for the Writer package you can see some libraries you might have gotten from a different source. These could also potentially break Writer in particular.

So... I'm not telling you what package **may** be messing with your openoffice.org install but ... I think you got the hint. ;)
If you still need more help, please do say so, I'll help if I can.

Cheers!

---

