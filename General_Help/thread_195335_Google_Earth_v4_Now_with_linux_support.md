---
title: "Google Earth v4: Now with linux support"
date: 2006-06-12
forum: General Help
---

### Post by cooldudejz on 2006-06-12
[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

can anyone help me get the .bin to run because i really would like to run google earth thanx. when i try to run it it says something about encoding.

---

### Post by RotoGrip on 2006-06-12
sudo sh GoogleEarthLinux.bin

---

### Post by taurus on 2006-06-12
Try something like
```

cd ~/Desktop (assuming you downloaded it to ~/Desktop directory...)
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin (for yourself)
-or
sudo ./GoogleEarthLinux.bin (for system wild)

```

---

### Post by mqy on 2006-06-12
Testing it right now, it is very sweeeeet!

However I get a message at startup saying that I do not have the Bitstream Vera Sans font installed. I am sure it is installed.

Does anybody know how to make Google Earth find it?

---

### Post by Mitush on 2006-06-12
Doesn't work for me (Breezy x86):

```
root@MITUSH:~/Desktop
./GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1563..................................................................

(setup.gtk2:15349): Gdk-WARNING **: locale not supported by Xlib

(setup.gtk2:15349): Gdk-WARNING **: cannot set locale modifiers

(setup.gtk2:15349): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO
-8859-1' is not supported

(setup.gtk2:15349): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO
-8859-1' is not supported

(setup.gtk2:15349): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No 
such file or directory

(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
./setup.sh: line 158: 15349 Aborted                 (core dumped) "$setup" "$@"

root@MITUSH:~/Desktop
ls -lart /usr/lib/pango/1.4.0/modules/pango-basic-fc.so
-rw-r--r--  1 root root 9240 2005-10-03 16:45 /usr/lib/pango/1.4.0/modules/pango-basic-fc.so
root@MITUSH:~/Desktop

```

Bummer!!!

---

### Post by nugglets on 2006-06-12
Not only does it work, but I have had it only 5 minutes and it already seems at least 5x more intuitive than the previous version I have installed on XP.

---

### Post by mgmiller on 2006-06-12
I have it crashing sometimes when I move my mouse to the upper right corner to the navigation controls.  I am suddenly on my desktop.  It starts right back up though.  It does seem smoother than my XP install.  Has anyone else notice if you turn on 3D buildings and go to New York City, that the buildings look like cardboard cutouts instead of real buildings?  It does this on my XP install also.

---

### Post by Elrohir on 2006-06-12
it still has some problems...

or its just my laptop... here the specs: Pentium M 2.00, 1GB RAM, 256 MB video

take a look at the screenshot...

---

### Post by dudus on 2006-06-12
It works very nice for me on dapper, altough it's damn slow as I'm using Mesa... but it's ati - I don't support most chips - driver fault

---

### Post by blackjack6.21.91 on 2006-06-12
Is this just another google app that is wrapped with WINE or is this a native linux application?

---

### Post by Fedup on 2006-06-12
[QUOTE=blackjack6.21.91]Is this just another google app that is wrapped with WINE or is this a native linux application?[/QUOTE]

Native apparently.

---

### Post by Elrohir on 2006-06-12
at least Google Earth says its native...

---

### Post by jecos on 2006-06-12
Its native. Runs great here, No problems at all (settings all set to high quality).  9800pro(FGLRX) for you downers about ATI.

---

### Post by beuno on 2006-06-12
It has .so and not .dll
plus:
~/google-earth$ ldd googleearth-bin
libqt-mt.so.3 => /usr/lib/libqt-mt.so.3 (0xb6dc2000)

so it seems to be using qt

---

### Post by nixon on 2006-06-12
anyone else getting this?

symlink: Permission denied

finding that i have to run it.. sudo Googleearth.. seems to be pretty unstable for me too, atix600 using fglrx

---

### Post by jecos on 2006-06-12
Try installing in regular user mode.

sh GoogleEarthLinux.bin

---

### Post by JoWilly on 2006-06-12
W00000T !!

What a beauty ! Native Google Earth working perfectly on dapper 64bit :D

---

### Post by nixon on 2006-06-12
[QUOTE=jecos]Try installing in regular user mode.

sh GoogleEarthLinux.bin[/QUOTE]

have done.. made the bin file executable and then sh.. still get symlink permission error.. tried uninstalling and re-installing.. still nothing.. ? :/

---

### Post by Fred Doolie on 2006-06-13
[Runs around the room singing the "Happy Happy Joy Joy Song]
 
My Windblows partition just moved one more *HUGE* step towards Death Row.  Now all that's left is the games I play. If VMWare could use my native hardware (graphics card and sound) instead of the lame hardware it emulates I wouldn't need that freaking Winpoop partition at all!

---

### Post by tsb on 2006-06-13
Awesome. Now I know what all the fuss was about.  I hope they start to get more details and addresses for international cities.

---

### Post by Torstein_V on 2006-06-13
I got it to work as well by doing the following:

I assume googleEarthLinux.bin is the only .bin file on your desktop:

```
cd Desktop

sudo chmod 777 *.bin

./*.bin
```

Up and running! :)

Just a pitty it has to be run from Terminal, typing "googleearth" every time, but it's still in beta, so I forgive it ;)

Has anyone else noticed that the performance has gotten a major upgrade? With the previous version, made for Windows XP, my fans were working so hard the computer almost took off into the air, but now, on the contrary, all I hear is a little calm buzz. :p 

I'm using Pentium 2.8 GHz, 1024 mb ram, Ati Radeon 9600 256mb.

Anyone else's noticed this?

---

### Post by _simon_ on 2006-06-13
^ maybe it's the way you installed it.

I used ```
 sh GoogleEarthLinux.bin
```

I have a menu item under Applications -> Internet

---

### Post by Torstein_V on 2006-06-13
Thanks, I'll try that after I've reformatted my Ubuntu-desktop (some XGL issues), but why would that method be any different from mine? Both will start the GoogleEarth installation interface, so I guess, technically, there shouldn't be any difference, since it's not sh *.bin or ./*.bin that installs the application.

---

### Post by _simon_ on 2006-06-13
I dunno, I was just guessing lol

You could make your own launcher or menu item to it....

Mine looks like this: /home/simon/google-earth//googleearth %f

---

### Post by alingatong on 2006-06-13
[QUOTE=_simon_]^ maybe it's the way you installed it.

I used ```
 sh GoogleEarthLinux.bin
```

I have a menu item under Applications -> Internet[/QUOTE]

I used this and still I don't get an entry in the applications-internet menu. what version are you saying? the stable or the beta version 4?

---

### Post by _simon_ on 2006-06-13
Beta 4, the stable one doesn't work with linux

---

### Post by purdy hate machine on 2006-06-13
I’m loving this, it runs so smoothly and I have not encountered any problems so far *touch wood* Nice work Google.

---

### Post by dapperjohndoe on 2006-06-13
Google Earth does not run on my system, there is probably an issue with my graphics card. How can I remove Google Earth from my system?

John

---

### Post by phido on 2006-06-13
There is an uninstaller in the gEarth directory.
Here it is under */usr/local/google-earth*, installed as root.
Then go there and do *sudo uninstall*.

I didn't try this out.

---

### Post by olsen on 2006-06-13
Works great for me, mostly. The text in the "earth"window dosn't seem to work.  Instead of text it is a square. I have the same problem in Armagetron. Any one know what to do?

---

### Post by Fred Doolie on 2006-06-13
It works but it's SLOOOOOOOOOOOOOOW if you resize the window.

---

### Post by master5o1 on 2006-06-13
what is the command once it's installed? ...because it installed, and it actually showed...but then i closed it :D...and i can't find the program :(

---

### Post by Torstein_V on 2006-06-13
Master501, the command for starting Googleearth is:

```
sudo googleearth
```

;)

---

### Post by aussiedini on 2006-06-13
[QUOTE=JoWilly]W00000T !!

What a beauty ! Native Google Earth working perfectly on dapper 64bit :D[/QUOTE]


Excellent. I installed with no problems, runs well. I was so excited about getting a linux version my wife's comment was "linux users need to get laid more often" lol.
Anyway this should help legitimize the linux movement with the doubters.

---

### Post by phido on 2006-06-13
googleearth should work, if not change permissions for ~/.googleearth or delete it

---

### Post by alingatong on 2006-06-13
I was able to run it in my dapper. But it crashes after about 4-5 minutes. Looking at the terminal window where I launched it, it says that its a bug and a bug report was generated and will be sent to google developers when the google earth will be started again. anybody here having the same problem? is this really a bug or this has something to do with my system?

I have nvidia geforce4 32mb VRAM in a dell laptop.

---

### Post by bunty on 2006-06-13
Erm , had nobody stopped to ask themselves why this prog requires to be run as ROOT?! and whether this is really a good idea.

GoogleEarth is a nice little tool but it is strickly userland on the face of it. Why does it need root privileges ? What is it doing that it does not tell you about?

I'd trust Google about as far as I could throw them and Microsoft tied together.

Cheerfully opening up your system like this is EXIACTLY what created the Sony rootkit problems on XP last year. You are invited to change to admin to run an "audio CD". Duh, why? So that Sony can hijack every write operation performed by your PC. 

If you guys cant wise up please go back to windows before Linux becomes the same virus/trojan infested mess.

No offence but please use common sense here. You just DONT run userland stuff as root. ABOVE ALL when it's **closed source**, 3rd party stuff from a big corp. with a dodgy record.

And by the way did I mention : **dont run userland progs with root privs!**

Desktop linux will be the death of Linux. :-(

---

### Post by shinygerbil on 2006-06-13
I only ran the installer as root so I could install the binaries system-wide. I run the program as a reguar user, of course.

Desktop linux may be the death of linux as we know. So? Welcome to a new linux. Before long we'll have more and more users learning to separate users from root (learning the hard way maybe, but still learning). This can only be a good thing, surely? There are always people who are new to anything. I find it better to give them a few helpful words. Sure, it gets repetetive; I see it as altruism. Did your school teachers get annoyed after teaching their second class?

This is just me speaking my mind; I'm not trying to be argumentative.

Steve

EDIT: As far as I know the program doesn't **require** to be run as root at all. It's just an option, as it is with any program, to give you, as a user, temporary access to system-wide directories.

---

### Post by _simon_ on 2006-06-13
I'm not running it as root....

---

### Post by Half-Left on 2006-06-13
[QUOTE=bunty]Erm , had nobody stopped to ask themselves why this prog requires to be run as ROOT?! and whether this is really a good idea.

GoogleEarth is a nice little tool but it is strickly userland on the face of it. Why does it need root privileges ? What is it doing that it does not tell you about?

I'd trust Google about as far as I could throw them and Microsoft tied together.

Cheerfully opening up your system like this is EXIACTLY what created the Sony rootkit problems on XP last year. You are invited to change to admin to run an "audio CD". Duh, why? So that Sony can hijack every write operation performed by your PC. 

If you guys cant wise up please go back to windows before Linux becomes the same virus/trojan infested mess.

No offence but please use common sense here. You just DONT run userland stuff as root. ABOVE ALL when it's **closed source**, 3rd party stuff from a big corp. with a dodgy record.

And by the way did I mention : **dont run userland progs with root privs!**

Desktop linux will be the death of Linux. :-([/QUOTE]


It does not need to be run as root, it's works like any other application. Stop being such a alarmist.

---

### Post by aussiedini on 2006-06-13
[QUOTE=_simon_]I'm not running it as root....[/QUOTE]


ditto

---

### Post by matthew on 2006-06-13
Stunning...and BTW, I'm not running it as root either.

---

### Post by MKR. on 2006-06-13
It's a bit laggy on my Radeon 9250, but it works well enough.

---

### Post by hanzomon4 on 2006-06-13
I keep getting this message, unless I run it as root>  symlink: Permission denied

I installed with sudo googlearth.bin I even chmod the symlink and the file its pointing to, 
                                                         

                                                    ?????

---

### Post by CAFH on 2006-06-13
It run great with my ATI Radeon 9100

---

### Post by Torstein_V on 2006-06-13
Did you sudo chmod **777** it? That solved it for me.

---

### Post by eqisow on 2006-06-13
OK, for those of you having the "symlink: Permission denied" issue, it's because of an bug in the Google Earth installer.

Here's the deal. You run the installer with sudo to get a systemwide install, then when the installer is done it ask you if you want to run Google Earth. If you choose yes, it runs Google Earth as root and creates configuration files in your home directory that are owned by root. After that, when you try to run Google Earth as a user, it tries to access these files, but can't. The solution to this is to change the ownership of your ~/.googlearth directory with the following command:

```
sudo chown -R username ~/.googleearth
```

Be sure to replace your *username* with your user name.

Cheers :)

---

### Post by kyldere on 2006-06-13
Has anyone else experienced issues with running GoogleEarth and Compiz? When I have both running, GE only displays white text fields where the name lables should be. If I turn Compiz off, GE displays properly.

---

### Post by eqisow on 2006-06-13
Yeah, XGL/Compiz pretty much screwes up all 3D apps. There is a work-around though, hold on and I'll see if I can find it.

Edit: [http://www.ubuntuforums.org/showthread.php?t=176636]("http://www.ubuntuforums.org/showthread.php?t=176636")

See if that helps.

Edit again: It appears that this solution doesn't work for people with ATI cards, be warned!

Last edit: (I promise) I believe you can also have it set up to be able to choose a normal GNOME session when you login, but having to log out to run Google Earth seems silly.

---

### Post by PapaWiskas on 2006-06-13
[QUOTE=eqisow]OK, for those of you having the "symlink: Permission denied" issue, it's because of an bug in the Google Earth installer.

Here's the deal. You run the installer with sudo to get a systemwide install, then when the installer is done it ask you if you want to run Google Earth. If you choose yes, it runs Google Earth as root and creates configuration files in your home directory that are owned by root. After that, when you try to run Google Earth as a user, it tries to access these files, but can't. The solution to this is to change the ownership of your ~/.googlearth directory with the following command:

```
sudo chown -R username ~/.googleearth
```

Be sure to replace your *username* with your user name.

Cheers :)[/QUOTE]

Thank you, I have been hitting my head on my desk for the last hour, the bruise is quite nasty I assure you.

Again, my thanks!!!

---

### Post by kyldere on 2006-06-13
Thanks eqisow ... not only did that fix the GE problem, but also the lesser problem of IE6 starting up and disappearing.

---

### Post by bunty on 2006-06-13
*OK, for those of you having the "symlink: Permission denied" issue, it's because of an bug in the Google Earth installer.*

the bug is the user saying yes when still in a sudo command. The permissions the program creates seems correct for that situation.

*Thanks eqisow ... not only did that fix the GE problem, but also the lesser problem of IE6 starting up and disappearing.*

what's the percieved problem ? That it disappears , or that is starts in the first place. If your kernel is prepared to run .exe like native you should wonder why.

It is possible to configure it that way but I certainly would not recommend it.

Wine's declared aim is to reproduce windows API "bug for bug". This has been a resounding success: there are thousands more bugs in wine than in windows API, plus the correctly emulated ones. Wine like GE should only be run in a very well controlled environment.

I suggest a specific user with very restricted rights for this sort of application.

Thanks for all those who replied confirming that GE does not need to be run as root.
:D

bash-3.1#grep MISC /boot/config*
/boot/config-2.6.15:CONFIG_BINFMT_MISC=m

Hmmm.

---

### Post by eqisow on 2006-06-13
> the bug is the user saying yes when still in a sudo command. The permissions the program creates seems correct for that situation.

The bug is a usablity issue. Yes, technically that's what the installer "should" do, but to me that "it's not a bug, it's a feature" attitude just doesn't fly. Google knows applications don't need to be run as root, especially applications that interface to the internet. It would have been simple to change the behavior of the installer.

> Wine's declared aim is to reproduce windows API "bug for bug". This has been a resounding success: there are thousands more bugs in wine than in windows API, plus the correctly emulated ones.


What are you talking about? Google Earth runs native, not in Wine. No need to bring Wine into this.

> Wine like GE should only be run in a very well controlled environment. I suggest a specific user with very restricted rights for this sort of application.

Err, paranoid much?

---

### Post by reyfer on 2006-06-13
Hi.
I think it's great that we finally have Google Earth in Linux. I installed it, but can't use it. It starts and then it crashes, this is what I get from terminal:

> Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x212) [0x804ab32]
  ./googleearth-bin [0x804b133]
  [0xffffe420]
  /home/reyfer/google-earth/libevll.so(_ZN5earth4evll9CacheNode8populateEPNS0_5C
acheEPNS_10HeapBufferEPNS0_13CacheNodeTypeE+0x33) [0xb32de893]
  /home/reyfer/google-earth/libevll.so(_ZN5earth4evll5Cache18loaderNodePopulateE
PNS0_9CacheNodeEPNS_10HeapBufferE+0x50) [0xb32de950]
  /home/reyfer/google-earth/libevll.so(_ZN5earth4evll9NetLoader17finishHttpReque
stEPNS0_11NLQueueElemEmPNS_10HeapBufferE+0x1a2) [0xb33a92e2]
  /home/reyfer/google-earth/libevll.so(_ZN5earth4evll9NetLoader12asyncHandlerEv+
0x2ef) [0xb33b04df]
  ./libbase.so(_ZN5earth11AsyncThread12asyncHandlerEPNS0_10ThreadInfoE+0x53) [0x                  b79d1f13]
  ./libbase.so(_ZN5earth11AsyncThread9asyncFuncEPv+0x28) [0xb79d1fd8]
  /lib/tls/i686/cmov/libpthread.so.0 [0xb62f0341]
  /lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb63c64ee]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/reyfer/.googleearth/crashlogs/crashlog-FB47706F.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

And also cannot unistall it. Anyone? My specs: Sempron 2800+, 512 MB RAM, Nvidia Gforce 5500 128MB

---

### Post by eqisow on 2006-06-13
Not sure what to tell you reyfer, except that it's quite new beta software. It does run fine for me, however.

Why can't you unistall it? Do you get a similiar error?

---

### Post by reyfer on 2006-06-13
No matter how I try, it just says that the uninstall command does not exist. I tried with su, sudo, everything, and it's still there.

---

### Post by bunty on 2006-06-13
*It would have been simple to change the behavior of the installer.*

yes I agree, it's a bit of clumbsy port of the windows 'run it now' which probably also ran as admin.:rolleyes: 

*What are you talking about? *

If you reread my post you'll see I was commenting on kyldere saying IE6 popped up. I assumed he was not referering to a native linux port of IE6, tho' I guess it's only a question of time!

*Err, paranoid much?*

since when has excersizing proper system admin been regarded as a mental disorder?

If a closed source "native" linux program fires up IE6 I think some questions should be asked about whether this was intended / accidental / desirable.

IE6 is visible , if GE (or any other native or exe software) contains some other malware , dont count on it popping up a nice little window to warn you. :-$

---

### Post by cyB3r4rd on 2006-06-13
is there a way to make google earth run with shared libraries instead of it's own qt and stuff?

i'd be impressed if it could use my tweaked qtcurve and the nuvola iconset where possible.

---

### Post by eqisow on 2006-06-13
Try the following to uninstallif you used sudo to install:

```
cd /usr/local/google-earth
sudo uninstall
```

If you installed a normal user run the following:

```
cd google-earth
uninstall
```

bunty:

Hmm, I didn't see see that post. Very odd thing to happen though. I didn't experience that on my computer, but I don't have IE installed either. I'd hardly say malware is a likely cause though, there would be much better ways to do that than depending on a Linux user to ahve IE6 installed. Then again, it probably isn't leftover Windows code either, as it would have to call Wine explicitly. Very odd indeed...

---

### Post by bunty on 2006-06-13
*Then again, it probably isn't leftover Windows code either, as it would have to call Wine explicitly. Very odd indeed...*

Like I said I dont let this sort of thing happen but AFAIK having misc binaries enabled in the kernel (even as modules) allows command line iexplore.exe to run and other progs , like here, to fire up an exe .

misc binaries requires a wrapper to know what to do, wine provides such a wrapper , as does dosemu and a number of other things.

I dont imagine malware would choose to run IE6 full screen but it points out that this is possible. It may just use part of IE or fish for another vector.


I dont have a std Ubuntu kernel here just now , would you like to run 

bash-3.1#grep MISC /boot/config*
and see what CONFIG_BINFMT_MISC is set to ?

Thanks.


from the misc binaries help page in make menuconfig:
* Once you have registered such a binary class with the kernel, you can start one of those programs simply by typing in its name at a shell prompt; Linux will automatically feed it to the correct interpreter. *

---

### Post by eightysix on 2006-06-13
Anyone else getting a segmentation fault error?

---

### Post by bollix47 on 2006-06-13
Yes.

Installation went fine and entry appeared in the menu.

Clicked on menu and splash screen appeared and immediately shut down.

Tried using terminal to start and again the splash screen appeared and closed.

The only error message was "Segmentation Fault".

Using an old ATI Radeon 9200 so perhaps it's not supported in the linux version of GE, but I do know it works in the windows version.

---

### Post by clandestino81 on 2006-06-13
[QUOTE=eightysix]Anyone else getting a segmentation fault error?[/QUOTE]
I get the same error. I have ATI RADEON 9200 se and ati proprietary driver.

---

### Post by Fred Doolie on 2006-06-13
GE puts an icon in the Internet menu and runs with a mouseclick within my normal user account. No "Root-Running" needed.

---

### Post by eightysix on 2006-06-13
[QUOTE=clandestino81]I get the same error. I have ATI RADEON 9200 se and ati proprietary driver.[/QUOTE]

I'm using an 8500 with the 8.23.7 ATI fglrx driver. ATI driver problems strike again. :(

---

### Post by tmastran on 2006-06-13
Before we all forget, Thanks Google! Runs great. Good job!

---

### Post by OrganicPanda on 2006-06-13
im am very impressed, i wasn't expecting this... lets hope its the start of a good trend, well done google

---

### Post by MartinJ on 2006-06-13
YES! Very impressive.

Works perfectly on my 5 year old laptop, with a mobility radeon 7000 and the out-of-the box video driver!!

---

### Post by OffHand on 2006-06-13
Works flawless on my celeron 1300, fx5200, 512mb sdram. Great job by google.
Imagine this with live video feeds.... hmmmm maybe not :rolleyes:

---

### Post by kyldere on 2006-06-13
Ok ... here's the scoop. I my wine'd version of IE6 would pop up and then disappear, although the process manager would still report it running if Compiz was active. I only used IE6 for intranetwork use, as the pages have been written expressly for IE6 and do not render correctly otherwise, so my workaround consisted of dual booting for that purpose only. eqisow's fix for the GE problem also fixed my IE6 problem, like two birds with one stone. Thanks again for the help.

---

### Post by whatever on 2006-06-13
works fine with radeon 9700 + fglrx 8.25.18

---

### Post by bunty on 2006-06-13
Yes , I've just installed it on my Gentoo partition. It's a pretty impressive piece of software although the detail that you can see in some areas is enough to stop you stripping off in your backyard ever again.

In the Southend area of UK you can clearly see mooring ropes and TV ariels!

It did crash after about an hour of scanning around all over the place but that's pretty good for a beta and no collateral damage. :D 

Well I suppose it's adware basically just to give us a taster of what is availble on subscription but it not to be sniffed at. Thanks for the freebee.

Now everyone can see how many chairs I have in my backgarden :(

---

### Post by Neo Ex on 2006-06-13
I have an ATI Radeon 9600XT and after about a minute I've opened Google Earth the system freezes. I have had this problem also with the Windows version of Google Earth used with WINE.
I have installed the lastest fglrx driver... what I can do?

---

### Post by jecos on 2006-06-13
[QUOTE=Neo Ex]I have an ATI Radeon 9600XT and after about a minute I've opened Google Earth the system freezes. I have had this problem also with the Windows version of Google Earth used with WINE.
I have installed the lastest fglrx driver... what I can do?[/QUOTE]

Make sure your not running it as root.

---

### Post by bunty on 2006-06-13
kildere > Ok ... here's the scoop. I my wine'd version of IE6 would pop up and then disappear, although the process manager would still report it running if Compiz was active. I only used IE6 for intranetwork use, as the pages have been written expressly for IE6 and do not render correctly otherwise,


that's pretty much what I guessed.

maybe GE picked up some error and tried to display and html help page. A probable relic of the windows version tried to run iexplore.exe and your kernel obliged.

I am sure you can see the potential security risk in this setup.

I have IE installed for my wine user since NaturallySpeaking voice rec needed some of the API to install correctly.

However there's no way it's going to pop up unless I run wine iexplore.exe

I think the misc binary option is a BAD idea, especially as a default setup on a distro where most user are not even aware of that it exists.

you may want to read up on make-kpkg , look at turning it off and rebuilding your kernel.  It's pretty straight forward once you've found some doc:

[http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation)


HTH

---

### Post by hanzomon4 on 2006-06-13
[QUOTE=eqisow]OK, for those of you having the "symlink: Permission denied" issue, it's because of an bug in the Google Earth installer.

Here's the deal. You run the installer with sudo to get a systemwide install, then when the installer is done it ask you if you want to run Google Earth. If you choose yes, it runs Google Earth as root and creates configuration files in your home directory that are owned by root. After that, when you try to run Google Earth as a user, it tries to access these files, but can't. The solution to this is to change the ownership of your ~/.googlearth directory with the following command:

```
sudo chown -R username ~/.googleearth
```

Be sure to replace your *username* with your user name.

Cheers :)[/QUOTE]

That did it Thanks :D

---

### Post by jejones3141 on 2006-06-13
[Message showing that I didn't read the thread clear to the end, which would've answered my question, edited.]

I promise I'll come back and delete this message, which I can supposedly do via "edit/delete" but found no way to do, once I learn how.

---

### Post by bunty on 2006-06-13
Did you do the fix quoted above? > sudo chown -R username ~/.googleearth

---

### Post by MKR. on 2006-06-13
It turns out the reason it didn't work well for me is because I had to use the OSS driver for my ATI card since ATI's latest driver breaks a lot of older cards.

I guess I'll have to live with the lag of 3D accelerated applications until ATI gets their act together.

---

### Post by reuben on 2006-06-13
When I start it, I get the message about bitstream vera fonts being missing. Is there a package I can install w/ apt-get, or do I have to install from gnome.org/fonts like they suggest? (I'm on kubuntu, so I don't have all the gnome stuff installed.)

---

### Post by _Zardoz_ on 2006-06-13
It works great! No sudo installation and no sudo running. Menu entry, Applications->Internet. I can start GE under Xgl+Compiz without problems. Ati mobility x600, driver 8.25.18.

---

### Post by arch stanton on 2006-06-13
Ati 9600 user experiencing complete lock up here within a minute off starting google earth, which is really breaking my heart because this thing is pretty neat.

---

### Post by mannheim on 2006-06-13
[QUOTE=eqisow]OK, for those of you having the "symlink: Permission denied" issue, it's because of an bug in the Google Earth installer. [snip]
```
sudo chown -R username ~/.googleearth
```

Be sure to replace your *username* with your user name.
[/QUOTE]

There is a similar issue that prevents Google Earth from appearing in the gnome menus (at least in my case). I installed googleearth using sudo, and it created ~/.local/share/applications/googleearth.desktop owned by root and unreadable by anyone else.  If this is your situation also, do

```
sudo chown *<username>*  ~/.local/share/applications/googleearth.desktop
```

then either "killall gnome-panel" or log out and in again. (There is surely a better way to do the last step.) Anyway, after this, I did have "Google Earth" with its nice icon in Applications-->Internet.

---

### Post by eqisow on 2006-06-13
Good catch mannheim! I hadn't noticed this problem since I'm running KDE. (It dind't make a KDE icon at all, I had to create my own)

---

### Post by reuben on 2006-06-13
Hm, I just noticed that I *do* have ttf-bitstream-vera (package) installed, and yet google earth still complains about it on startup. Anybody else?

---

### Post by Rory on 2006-06-13
I keep getting "segmentation fault."  Anyone know why?  I did the regular sh googleearth.bin install.  Seems to install correctly.  I start it, I see the opening Google Earth welcome screen and then... nothing.  

```
rory@ubuntu:~$ googleearth
Segmentation fault

```

Any ideas?

Rory

---

### Post by fnjordy on 2006-06-14
Dammit:
> Google Earth detected an error while trying to authenticate
Please check the following:
- your network connection (can you get to [www.google.com?](www.google.com?))
- your firewall settings
(are you blocking /usr/local/google-earth/google-earth-bin?)

Error code: 29
For more information, visit:

  [http://earth.google.com/support/bin/answer.py?answer=20717](http://earth.google.com/support/bin/answer.py?answer=20717)

(edit) Found the problem, what is it with Dappers messed up $http_proxy=http://:8080/ ?

---

### Post by purdy hate machine on 2006-06-14
I have installed this on both Ubuntu Breezy (Gnome) and Mepis 6 (KDE) using

```
 sh GoogleEarthLinux.bin
```

Installs and runs perfectly (without Root) and places a purdy icon in the relevant menu.

---

### Post by JoWilly on 2006-06-14
[quote=kyldere]Has anyone else experienced issues with running GoogleEarth and Compiz? When I have both running, GE only displays white text fields where the name lables should be. If I turn Compiz off, GE displays properly.[/quote]

Works perfectly here on dapper 64 with xgl/compiz (nvidia drivers).

---

### Post by JoWilly on 2006-06-14
For those with no icon/launcher in the menu, do this (it will then appear in the internet menu):

```

sudo cp /opt/google-earth/googleearth.desktop /usr/share/applications/

``` 
(you will eventually need to replace /opt with your location, if you installed it elsewhere; i.ex /usr/local ...)

---

### Post by myoldryn on 2006-06-14
I have problem installing google earth.....

It say´s

```

jaan@bloodrayne:~/Desktop$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1563..................................................................
You don't see to be running an X server (no DISPLAY set).
Google Earth and its installer both require X11.
Aborting...
jaan@bloodrayne:~/Desktop$ 

```

Where can I find this server......

---

### Post by janki on 2006-06-14
[QUOTE=Elrohir]it still has some problems...

or its just my laptop... here the specs: Pentium M 2.00, 1GB RAM, 256 MB video

take a look at the screenshot...[/QUOTE]

I'm running Google Earth on Dapper, installed on a brand new Dell laptop. I'm having the same problem as Elrohir. It's totally screwed up whenever I scroll or do any other action.

Strange, because it appears that most of you have it working just fine.

---

### Post by joshrobinson on 2006-06-14
works awesome here.. dapper 64bit

---

### Post by pabix on 2006-06-14
Oops... ATI Radeon 9200+ M9 Mobility... Segmentation fault!

But I'm not alone apparently!

Benoit

---

### Post by Lord Illidan on 2006-06-14
Astonishing. 2 days ago, I was at my granddad's, using his laptop with a cousin of mine. And my cousin had downloaded Google Earth for Windows and was playing with it. My uncle made several snide comments that in Linux, I did not have anything like it.

Now, I have it running on my own pc. Great work, Google.

Actually, I would have expected it to be native. The majority of the work is in streaming, the rest is just generic interface stuff. It would have been a major hassle for google to wine it.

Works just fine. A bit slow, but I guess that is my net connection. 3D anims work fine. Crashed once, but it is a beta, after all.

---

### Post by siriusnova on 2006-06-14
[QUOTE=janki]I'm running Google Earth on Dapper, installed on a brand new Dell laptop. I'm having the same problem as Elrohir. It's totally screwed up whenever I scroll or do any other action.

Strange, because it appears that most of you have it working just fine.[/QUOTE]

What video card are you using?
I have the same problems on my Thinkpad T30

[http://web.umr.edu/~taknnc/Screenshot.png](http://web.umr.edu/~taknnc/Screenshot.png)

the T30 has an ATI Radeon 7500 mobility and im using the x.org "radeon" driver :(

---

### Post by steve.horsley on 2006-06-14
[QUOTE=reuben]Hm, I just noticed that I *do* have ttf-bitstream-vera (package) installed, and yet google earth still complains about it on startup. Anybody else?[/QUOTE]
Yes, it says that on my laptop. Not my desktop though. Bizarre.

---

### Post by PriceChild on 2006-06-14
[quote=Mitush]Doesn't work for me (Breezy x86):
 
```
root@MITUSH:~/Desktop
./GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1563..................................................................
 
(setup.gtk2:15349): Gdk-WARNING **: locale not supported by Xlib
 
(setup.gtk2:15349): Gdk-WARNING **: cannot set locale modifiers
 
(setup.gtk2:15349): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO
-8859-1' is not supported
 
(setup.gtk2:15349): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO
-8859-1' is not supported
 
(setup.gtk2:15349): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No 
such file or directory
 
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(setup.gtk2:15349): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed
 
Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
./setup.sh: line 158: 15349 Aborted                 (core dumped) "$setup" "$@"
 
root@MITUSH:~/Desktop
ls -lart /usr/lib/pango/1.4.0/modules/pango-basic-fc.so
-rw-r--r--  1 root root 9240 2005-10-03 16:45 /usr/lib/pango/1.4.0/modules/pango-basic-fc.so
root@MITUSH:~/Desktop

```
 
Bummer!!![/quote]
 
The requirements for v4 beta state that a 2.6 version kernel is reccomended!
 
This may be your problem, Pricey

---

### Post by Hoffmann on 2006-06-14
See the mess I got when I run Google Earth. Any help?

---

### Post by bunty on 2006-06-14
> Where can I find this server......

this just means the X windowing system. Since you are posting I guess it's fair to assume that you have that running already.

your dont say anything about your setup so I cannot even hope to guess the problem but you could try this:

export DISPLAY=:0.0

it's the variable that GE installer seems to be requiring. This value means X-server 0, screen 0 .

then try again.
:cool:

---

### Post by Hoffmann on 2006-06-14
[QUOTE=bunty]this just means the X windowing system. Since you are posting I guess it's fair to assume that you have that running already.

your dont say anything about your setup so I cannot even hope to guess the problem but you could try this:

export DISPLAY=:0.0

it's the variable that GE installer seems to be requiring. This value means X-server 0, screen 0 .

then try again.
:cool:[/QUOTE]

DIDN'T WORK ALSO!
What am I missing?

---

### Post by bunty on 2006-06-14
you're failing to read (ignoring) the quote , my last post was a reply to myoldryn's question.

---

### Post by Hoffmann on 2006-06-14
[QUOTE=bunty]you're failing to read (ignoring) the quote , my last post was a reply to myoldryn's question.[/QUOTE]
OK...
It seems like you become nervous so soon....

---

### Post by linuxbz on 2006-06-14
GoogleEarth installed fine, but only runs a minute or two and crashes.

Kubuntu 6.06, AMD Athlon XP, nVidia video, 1GB ram, not running as root.

---

### Post by Hoffmann on 2006-06-15
[QUOTE=linuxbz]GoogleEarth installed fine, but only runs a minute or two and crashes.

Kubuntu 6.06, AMD Athlon XP, nVidia video, 1GB ram, not running as root.[/QUOTE]
It seems like Google Earh is too experimental on linux yet. This is the reason it is still a beta version.
I will give it one more try when they released the final version.

---

### Post by JoWilly on 2006-06-15
[quote=Hoffmann]It seems like Google Earh is too experimental on linux yet. This is the reason it is still a beta version.
I will give it one more try when they released the final version.[/quote] 
Why do you need to generalize ?

If it is not made to run properly on "your hardware" yet, it does not mean it is too experimental "on linux". It works perfectly here, as good as a finaly product; its also very fast on xgl, I'm impressed.

Furthermore, it **could** also be that the problems you are experience do not have anything to do with googlearth, but with 3D hadware supprot for your gfx card. Especially ATI and laptop 3D support, have been known to be a pain in the butt for a long time.

Give it time, and don't forget to report bugs.

---

### Post by bunty on 2006-06-15
> OK...
It seems like you become nervous so soon....:p 

nobody's getting nervous, you asked whay you were missing and I told you.;) 

It seems just about everyone having probs is having ATI probs, so if that's the case dont blame google. Half the time ATI cant even get their windows drivers to work properly. I would not buy a computer with an ATI card , or buy an ATI card for a computer,  end of story.

This software runs very fast and reliably here : Athlon XP, nvidia GeForce. NO glitches , perfect rendering. I am impressed.

It does sometimes crash after 10/15mins but I have not been able to tie it to anything specific. That seems pretty fair for beta release though.

Thanks you google.

---

### Post by cuhlik on 2006-06-15
[QUOTE=Mitush]Doesn't work for me (Breezy x86):
...
(setup.gtk2:15349): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No
 such file or directory

Bummer!!![/QUOTE]


I had the same problem on my Ubuntu AMD64x2 system
uname -a says
Linux cyber2 2.6.12-custom #1 SMP Sun Feb 19 12:49:35 PST 2006 x86_64 GNU/Linux

Here's how I worked around the problem.

Manually unpack the install binary like this

> dd if=GoogleEarthLinux.bin ibs=8876 skip=1 obs=1024 conv=sync | bzip2 -d | tar xvf -

Edit the setup.sh file and change this line

> try_run setup.gtk2 $args $*

to 

> try_run setup.gtk $args $*

There are two setup binary programs 
./setup.data/bin/Linux/x86/setup.gtk2  and
./setup.data/bin/Linux/x86/setup.gtk

I don't know what the difference is, but the gtk<not-2> one worked fine where the first one failed as you described.

Good luck,

Chris

---

### Post by Fred Doolie on 2006-06-16
[QUOTE=Fred Doolie]It works but it's SLOOOOOOOOOOOOOOW if you resize the window.[/QUOTE]

Correction: It's slow if you resize yhe window and then keep going.
If you exit and the restart it's just fine then.

---

### Post by flar on 2006-06-16
For those with symlink: permission denied problems, install it as root, not via sudo.

for example, 

sudo ./GoogleEarthLinux.bin 

does NOT work, but

su
./GoogleEarthLinux.bin

does work.


NOTE: you need to give your root account a password to do this:
sudo passwd root

---

### Post by koomapotilas on 2006-06-17
>>[QUOTE=nixon]anyone else getting this?

symlink: Permission denied

finding that i have to run it.. sudo Googleearth.. seems to be pretty unstable for me too, atix600 using fglrx[/QUOTE]

<<

I found the answer! If you run 'strace -f googleearth' it will report access denied for some files under ~/.googleearth . Just delete that directory with 'sudo rm -r ~/.googleearth'.

---

### Post by sha_man on 2006-06-17
it would be such a **dream** if Google could also release the *excellent* [[SIZE="4"]Google SketchUp[/SIZE]]("http://sketchup.google.com/") for Linux (native) too :D 
This would probably be the first good CAD/3D app for Linux!

---

### Post by sha_man on 2006-06-17
Screenshots of google earth 4 with models (which you can also create with Google SketUp, that means you can create your *own* domicile in 3D with textures and watch it in Google Earth) :D :

[IMG]http://earth.google.com/images/3dtexturedlarge.jpg[/IMG]

[[IMG]http://img148.imageshack.us/img148/5332/geesbcb3os.th.jpg[/IMG]](http://img148.imageshack.us/my.php?image=geesbcb3os.jpg)

---

### Post by ssmaxss on 2006-06-17
What about bitstream vera fonts? How can I fix it? I am using Dapper 64-bit.

---

### Post by dresnu on 2006-06-17
[QUOTE=siriusnova]What video card are you using?
I have the same problems on my Thinkpad T30

[http://web.umr.edu/~taknnc/Screenshot.png](http://web.umr.edu/~taknnc/Screenshot.png)

the T30 has an ATI Radeon 7500 mobility and im using the x.org "radeon" driver :([/QUOTE]

I confirm this. I have the same problem on my laptop on a 7500 mobility radeon using both the ati and radeon drivers.

---

### Post by Patrick-Ruff on 2006-06-17
[QUOTE=dudus]It works very nice for me on dapper, altough it's damn slow as I'm using Mesa... but it's ati - I don't support most chips - driver fault[/QUOTE]
simply use the fglrx driver. gives you pretty much just as good graphics accelleration as windows. 

good luck

---

### Post by franck.galbrun on 2006-06-17
Same problem here. SONY VAIO PCG-FR285E Laptop with nVidia GeForce4 420 Go. If I run Google earth without 3D accel, it displays ok, but slow, of course.

---

### Post by Corvillus on 2006-06-17
[QUOTE=Hoffmann]See the mess I got when I run Google Earth. Any help?[/QUOTE]
No idea, but I have the same issue with Google Earth. I'm running on a laptop with an Intel i855, using the open source i810 driver included with Ubuntu, if anyone has any tips on how to get it working properly with it.

---

### Post by marcog on 2006-06-17
[QUOTE=Corvillus]No idea, but I have the same issue with Google Earth. I'm running on a laptop with an Intel i855, using the open source i810 driver included with Ubuntu, if anyone has any tips on how to get it working properly with it.[/QUOTE]

In the options, try enable graphics safe mode. It worked for me.

---

### Post by bunty on 2006-06-17
[QUOTE=koomapotilas]>>

<<

I found the answer! If you run 'strace -f googleearth' it will report access denied for some files under ~/.googleearth . Just delete that directory with 'sudo rm -r ~/.googleearth'.[/QUOTE]


I thought this was resolved some pages back, tho' this is getting long and you  probably didnot bother ploughing through the whole thing.

The ~/.googleearth files get created when you first run , if you do this as root (effecively under sudo) you create this with perms that the user cannot alter when correctly run as user.

The setup script should not say "do you want to run it now" and you should not say "yes" when it does!

That is why every second post is saying "not running as root". Pls take note.

:D

---

### Post by Hoffmann on 2006-06-17
When I run Google Earth, I get:

>  "Unknown Graphics Card" error and
> Xlib:  extension "GLX" missing on display ":0.0".
Any hint?

---

### Post by grsing on 2006-06-17
[QUOTE=Hoffmann]When I run Google Earth, I get:

 and

Any hint?[/QUOTE]

Have you installed the drivers for your video card?

---

### Post by Hoffmann on 2006-06-17
[QUOTE=grsing]Have you installed the drivers for your video card?[/QUOTE]
My system was shipped with "Intel 915G chipset " and integrated video card. I mean, the video card is integrated on the motherboard.
Do you have any idea about which drivers should I install? Are they available on Synaptic? :confused:

---

### Post by the_guy1 on 2006-06-17
the only probelem I have is that It has a harder time streaming with the lack of bandwith that I have its still great thow

---

### Post by grsing on 2006-06-17
[QUOTE=Hoffmann]My system was shipped with "Intel 915G chipset " and integrated video card. I mean, the video card is integrated on the motherboard.
Do you have any idea about which drivers should I install? Are they available on Synaptic? :confused:[/QUOTE]

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

That's the guide I used to get mine running, worked very well.

---

### Post by grsing on 2006-06-17
[QUOTE=the_guy1]the only probelem I have is that It has a harder time streaming with the lack of bandwith that I have its still great thow[/QUOTE]

It definitely is a bandwidth hog, but that's the nature of the beast, I suppose.

---

### Post by ssmaxss on 2006-06-18
About sudo and su:
1) It is better to install like user.
2) you can use sudo su - so you don't need root password
It works ok for me (ATI Mobility Radeon 9200,fglrx,AMD64). The only problem is message about missing bitstream sans font...

---

### Post by Hoffmann on 2006-06-18
[QUOTE=grsing][http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

That's the guide I used to get mine running, worked very well.[/QUOTE]
I solved my problem with graphic cards. In my case, I should not to install nvdia-glx.
Regarding Google Earth, iI am still having problem, and I will wait for the final version.
Thanks!

---

### Post by jaymode on 2006-06-18
[QUOTE=Hoffmann]I solved my problem with graphic cards. In my case, I should not to install nvdia-glx.
Regarding Google Earth, iI am still having problem, and I will wait for the final version.
Thanks![/QUOTE]

Google stuff stays in beta for a while but most of their "betas" are other companies "final" versions. So it could be a while before it comes out of beta.

---

### Post by grsing on 2006-06-18
[QUOTE=Hoffmann]I solved my problem with graphic cards. In my case, I should not to install nvdia-glx.
Regarding Google Earth, iI am still having problem, and I will wait for the final version.
Thanks![/QUOTE]

Sorry, you're right, I wasn't thinking clearly, of course an integrated intel video isn't nvidia.  I don't know much about integrated graphics, but if there is a driver somewhere for your card, that's probably what you need to get Google Earth working properly (or at least part of it).  I wouldn't hold my breath for the final version; gmail is still in beta, so who knows how long Earth will be (though it might be worth waiting for the first updates).

---

### Post by Hoffmann on 2006-06-18
[QUOTE=grsing]Sorry, you're right, I wasn't thinking clearly, of course an integrated intel video isn't nvidia.  I don't know much about integrated graphics, but if there is a driver somewhere for your card, that's probably what you need to get Google Earth working properly (or at least part of it).  I wouldn't hold my breath for the final version; gmail is still in beta, so who knows how long Earth will be (though it might be worth waiting for the first updates).[/QUOTE]

The problem is that I messed up my system yesterday by installing nvidia (and I needed to re-install the system once again). So, am not sure if I will change/install any driver for my integrated graphic cards. In my opinion, Ubuntu is more important than Google Earth. So, since I have no idea about that driver, I won't install Google Earth. ;)

---

### Post by grsing on 2006-06-18
[QUOTE=Hoffmann]The problem is that I messed up my system yesterday by installing nvidia (and I needed to re-install the system once again). So, am not sure if I will change/install any driver for my integrated graphic cards. In my opinion, Ubuntu is more important than Google Earth. So, since I have no idea about that driver, I won't install Google Earth. ;)[/QUOTE]

Good point.

---

### Post by flyingbrass on 2006-06-19
It doesn't work with onboard 6150 (nor my 6100), but Nvidia says the problem will be fixed in the next driver.

[http://www.nvnews.net/vbulletin/showthread.php?t=71756](http://www.nvnews.net/vbulletin/showthread.php?t=71756)

---

### Post by moontide on 2006-06-22
[QUOTE=nixon]anyone else getting this?

symlink: Permission denied

finding that i have to run it.. sudo Googleearth.. seems to be pretty unstable for me too, atix600 using fglrx[/QUOTE]

Same problem, Google Earth will only run using sudo. funny thing is I cant see any difference between the permissions used by googleearth and my other applications.

---

### Post by berserker on 2006-06-22
Anyone had any luck e-mailing a view or image within GE?  I can get it to launch an e-mail but there's no attachment with it.

---

### Post by yusufk on 2006-06-23
[QUOTE=moontide]Same problem, Google Earth will only run using sudo. funny thing is I cant see any difference between the permissions used by googleearth and my other applications.[/QUOTE]


To fix, type the fol in your home folder:
```

sudo chmod -R yourusername:yourusername .googleearth

```

The settings folder is owned by root after installing google earth using root even though its in the users home folder.

---

### Post by moontide on 2006-06-23
[QUOTE=nixon]anyone else getting this?

symlink: Permission denied

finding that i have to run it.. sudo Googleearth.. seems to be pretty unstable for me too, atix600 using fglrx[/QUOTE]


I had the problem and fixed it finaly by deleting all google earth directories (sudo rm -r <name of directory>) including the hidden one in my home directory named ".googleearth". I looked inside this directory and noticed a file named something like "access lock file". Anyway as I had tried installing first as sudo then later as normal user, I had to remove directories from /usr/local and us/local/bin as well a my home directory.

After cleaning out google earth I re-installed without sudo (just ./GoogleEarthLinux.bin) and it installed and runs perfectly as normal user. It even placed a launch icon in Applications/Internet. 

I'm running dapper with an nvidia 6600 video card.

---

### Post by moontide on 2006-06-23
[QUOTE=yusufk]To fix, type the fol in your home folder:
```

sudo chmod -R yourusername:yourusername .googleearth

```

The settings folder is owned by root after installing google earth using root even though its in the users home folder.[/QUOTE]

This sounds better than my method of deleting everything and re-installing as normal user. Too late form me to try it as googleearth is working for me now.
Is the user name entered twice to cope the symlink?

---

### Post by Kobalt on 2006-07-14
Argh, I can't install it... It gives me this error message when I want to run the .bin file : 

```
(setup.gtk2:6950): Pango-WARNING **: No builtin or dynamically
loaded modules were found. Pango will not work correctly.
This probably means there was an error in the creation of:
  '/etc/pango32/pango.modules'
You should create this file by running pango-querymodules.

(setup.gtk2:6950): Pango-WARNING **: pango_shape called with bad font, expect ugly output

(setup.gtk2:6950): Pango-WARNING **: pango_font_get_glyph_extents called with bad font, expect ugly output

(setup.gtk2:6950): Pango-CRITICAL **: pango_cairo_show_glyph_string: assertion `PANGO_IS_CAIRO_FONT (font)' failed
./setup.sh: line 158:  6950 Erreur de segmentation  "$setup" "$@"
```

I've tried installing some other packages of the pango libraries, but it doesn't work... I'm on a 64bit version of ubuntu, if that matters.

Thanks for your help dudes.

Cheers !

---

### Post by flar on 2006-07-14
A very long thread, for reference:

> **flar said:**
> For those with symlink: permission denied problems, install it as root, not via sudo.

for example, 

sudo ./GoogleEarthLinux.bin 

does NOT work, but

su
./GoogleEarthLinux.bin

does work.


NOTE: you need to give your root account a password to do this:
sudo passwd root

---

### Post by mogliii on 2006-07-15
Hi,

works nice on my system (Pentium M 1.3 GHz and Radeon Mobility 7500)

But one question: How to set to metric system? When I say: show scale legend, he shows in feet.

And really, the last thing that I want to do is to measure in feet and miles :P

---

### Post by matthew on 2006-07-15
> **mogliii said:**
> But one question: How to set to metric system? When I say: show scale legend, he shows in feet.In Google Earth...
Tools->Options
In the dialog box, in the lower left area titled "Rendering," change the selection for "Elevation" from "Feet, Miles" to "Meters, Kilometers"

---

### Post by t-dome on 2006-07-16
Works perfectly. No problems with the installation or video drivers...

I have kubuntu dapper and use the latest ATi proprietary drivers 8.26.18 (Radeon X800 Pro AGP 256 MB).

---

### Post by OffHand on 2006-07-17
Too bad my new motherboard with intergrated graphics card has some issues on Linux (Asrock 939NF4G-SATA2).
Guild Wars under Cedega and Google Earth for instance have messed up graphics.

---

### Post by jaka on 2006-07-22
I have one problem i cant uninstall google earth.

---

### Post by Irony on 2006-07-22
Installing Googleearth is at;

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Google_Earth](http://ubuntuguide.org/wiki/Dapper#How_to_install_Google_Earth)

Mine crashed at first until I ran googleearth from terminal then it ran fine from the Internet toolbar.

---

### Post by cvmostert on 2006-08-31
> **phido said:**
> There is an uninstaller in the gEarth directory.
Here it is under */usr/local/google-earth*, installed as root.
Then go there and do *sudo uninstall*.

I didn't try this out.

Thank you, 

i used  *sudo sh uninstall*

---

### Post by llanitedave on 2006-09-01
My problem is a bit different.  I installed using "sh GoogleEarthLinux.bin".

It started the installation process, and at the very beginning gave me this error:

"setup.data/bin/Linux/amd64/setup.gtk2: error while loading shared libraries: lib gtk-x11-2.0.so.0: cannot open shared object file: No such file or directory"

It continued installing, placed the icon in my desktop menu, and attempted to start.  I dropped out with this error:

"./googleearth-bin: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory"

Stupid question, but is this a library I can and should download from the repositories?  Shouldn't I already have it?

If I install it, where should it go?

---

### Post by berserker on 2006-09-01
> **llanitedave said:**
> "setup.data/bin/Linux/amd64/setup.gtk2: error while loading shared libraries: lib gtk-x11-2.0.so.0: cannot open shared object file: No such file or directory"

"./googleearth-bin: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory"

Stupid question, but is this a library I can and should download from the repositories?  Shouldn't I already have it?

If I install it, where should it go?

Try installing libgtk2.0-0 and libxcursor1:

```
sudo apt-get install libgtk2.0-0 libxcursor1
```

To determine the package in which a file belongs install apt-file and do this:

```
sudo apt-file update
apt-file search libXcursor.so.1
```

Hope this helps.

---

### Post by llanitedave on 2006-09-02
> :~$ sudo apt-get install libgtk2.0-0 libxcursor1
Reading package lists... Done
Building dependency tree... Done
libgtk2.0-0 is already the newest version.
libxcursor1 is already the newest version.

So, I already seem to have the same libraries that Google Earth can't find when it's trying to open.  Could it be a directory problem?

This is getting confusing!

So I followed your other instructions:
> 
:~$ sudo apt-file update

And after a long scrolling set of returns got the following result:
> 
Server file no newer than local file `/var/cache/apt/Contents-amd64.gz' -- not retrieving.


I'm not sure what this means...

Then I put in the final command:
> 
:~$ apt-file search libXcursor.so.1


And this was the output:
> 
ia32-libs-gtk: usr/lib32/libXcursor.so.1
ia32-libs-gtk: usr/lib32/libXcursor.so.1.0.2
libxcursor1: usr/lib/libXcursor.so.1
libxcursor1: usr/lib/libXcursor.so.1.0.2
libxcursor1-dbg: usr/lib/debug/usr/lib/libXcursor.so.1.0.2


Will I need to change a GoogleEarth configuration file to set a path to one of these files?

---

### Post by dpicker on 2006-09-02
The new 1.0-8774 nvidia driver didn't fix the google earth problem that people experienced with 6100/6150 onboard graphics. Hopefully they will do what they originally said and fix it in the NEXT driver.

---

### Post by berserker on 2006-09-02
> **llanitedave said:**
> So, I already seem to have the same libraries that Google Earth can't find when it's trying to open.  Could it be a directory problem?

Both of those files are located in /usr/lib on my system.  Are yours located in /usr/lib32?

If so then you may have to link them like so:

```
sudo ln -s /usr/lib32/libXcursor.so.1 /usr/lib/libXcursor.so.1
```

---

### Post by llanitedave on 2006-09-08
Sorry this has taken so long. The file "libXcursor.so.1" seemed to be in both usr/lib AND usr/lib32.  I ran the link as you suggested:

**sudo ln -s /usr/lib32/libXcursor.so.1 /usr/lib/libXcursor.so.1**

Then I attempted to open google earth again from the command line.  THIS time I got a totally different error:

**./googleearth-bin: error while loading shared libraries: libfreeimage.so.3: cannot open shared object file: No such file or directory**

So there's another missing dependency, apparently.  So, not wanting to be a bother, I attempted to download the needed file from the repositories:

**$ sudo apt-get install libfreeimage.so.3**

But the file apparently doesn't exist:

[b]
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libfreeimage.so.3
[/b]

I'm pulling my hair out!  Why am I missing so many fundamental pieces on my system?

---

### Post by berserker on 2006-09-08
> **llanitedave said:**
> 

**./googleearth-bin: error while loading shared libraries: libfreeimage.so.3: cannot open shared object file: No such file or directory**

Interesting.  libfreeimage.so.3 is located in the google-earth directory.  Are you running googleearth-bin from the google-earth directory?  If not then try doing that.

---

### Post by llanitedave on 2006-09-09
Yep.  I'm definitely in the google-earth folder.  And I can see the file "libfreeimage.so.3" there as well.  It's just not loading.  I've downloaded Google Earth twice now, with the same result each time.  So, should I submit a bug report to Google?  Could it be a hardware issue on my AMD-64 system?

The OS X version downloaded and installed just fine on my iBook, but I'd really rather use it under Linux.

---

### Post by MintabiePete on 2006-09-09
I have  had this beta googleearth for a  while  now on my 32 bit  system , and it seems to work great , but I have never been able  to get  rid of the problem with  it  freezing at times  when I move the mouse curser to the   top right hand  in the  direction menu . Sometimes the mouse  curser  just  disappears , sometimes  it just freezes. A reboot seems  to  fix it , until the next time . Has  anyone   come up with a  fix  to this ? I havnt   seen anything , only  back in the thread  someone else  had a very similar problem with a laptop , but they were  able to  move it after a while , I cant , it  completely  disappears or freezes.

---

### Post by Treviño on 2006-09-18
New google-earth release is out... GoogleEarth 4.0.2091 is now available for linux....
If you want it, you can download it from my ubuntu repository: [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)

Bye

---

### Post by Blyzzard on 2006-09-19
Hey there Guys,

I've installed GoogleEarth and it works, however, the pane that displays the earth is only about 30% the width of the main window. 

The pane to the left of it is there, and on the right of the screen is dead window space that doesn't refresh (redraw). If a window opens above it, and you move that window away, it'll have an image of the window stay behind.



---------------------------------------------------
|......|..................|.......................|
|.P....|..................|.......................|
|.A....|...Working area...|....Dead Space.........|
|.N....|..................|.......................|
|.E....|..................|.......................|
|......|..................|.......................|
|......|..................|.......................|
---------------------------------------------------

This is basically what I have.

I hope the ascii art picture comes out properly. (if not - copy and paste into gedit or something... seems to work a bit better).

Blyzzard

---

### Post by hafsal on 2006-09-21
I'm having some troubles with Google-Earth, it won't start...
This is the error message im getting when after doing "googleearth" in terminal

> Google Earth has caught signal 8.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x21e) [0x804ab52]
  ./googleearth-bin [0x804b153]
  [0xffffe420]
  ./libqt-mt.so.3 [0xb6de921d]
  ./libqt-mt.so.3(_ZN12QPaintDevice10x11AppDpiYEi+0x20) [0xb6de9280]
  ./libqt-mt.so.3(_ZN12QPaintDevice10x11AppDpiYEv+0x1e) [0xb6de92ee]
  ./libqt-mt.so.3(_Z16qt_init_internalPiPPcP9_XDisplaymm+0xf30) [0xb6dc9230]
  ./libqt-mt.so.3(_Z7qt_initPiPPcN12QApplication4TypeE+0x36) [0xb6dca946]
  ./libqt-mt.so.3(_ZN12QApplication9constructERiPPcNS_4TypeE+0x7b) [0xb6e3b2cb]  ./libqt-mt.so.3(_ZN12QApplicationC1ERiPPc+0x6f) [0xb6e3b79f]
  ./libgoogleearth.so(_ZN5earth6client11ApplicationC1EiPPcb+0xde) [0xb78597ae]
  ./googleearth-bin [0x804c75d]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb6229ea2]
  ./googleearth-bin(__gxx_personality_v0+0x4d) [0x804a981]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/hafsal/.googleearth/crashlogs/crashlog-FA715A8B.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.


Can anyone help me? I really love this program!

---

### Post by stefangr1 on 2007-02-22
> **llanitedave said:**
> Sorry this has taken so long. The file "libXcursor.so.1" seemed to be in both usr/lib AND usr/lib32.  I ran the link as you suggested:

**sudo ln -s /usr/lib32/libXcursor.so.1 /usr/lib/libXcursor.so.1**

Then I attempted to open google earth again from the command line.  THIS time I got a totally different error:

**./googleearth-bin: error while loading shared libraries: libfreeimage.so.3: cannot open shared object file: No such file or directory**

So there's another missing dependency, apparently.  So, not wanting to be a bother, I attempted to download the needed file from the repositories:

**$ sudo apt-get install libfreeimage.so.3**

But the file apparently doesn't exist:

[b]
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libfreeimage.so.3
[/b]

I'm pulling my hair out!  Why am I missing so many fundamental pieces on my system?


I have an idea about what might have gone wrong. I experienced something similar when i attempted to install googleearth as a superuser via the commandline. You might want to try (after deinstalling it) to install the bin file using the "Run Command" thing that appears after pressing Alt-F2. You can just use a command like ./location/location/filename.bin . After installing it this way everything worked without errors on my machine. I'm using linux only since a few months, so i don't have a clue about the technical details behind this, I only found it out via trial and error.

---

### Post by SeaSky on 2007-05-18
[http://earth.google.com/](http://earth.google.com/)

download GoogleEarthLinux.bin

right click the .bin file and select properties

tick off allow executable under permissions tab

click apply

double click the bin file

:guitar:

---

### Post by SeaSky on 2007-05-19
"Feisty"

---

### Post by highcc on 2007-05-30
You still missing some 32bit libraries.
Install ia32-libs-gtk. This should work for you as worked for me.

---

### Post by carloslosgrande on 2007-08-14
[FONT="Comic Sans MS"]I had google earth working in XP and Dapper, but I've never had any success getting it working in Feisty. I've tried various methods including those I've read here.

I don't get any error messages, it just hangs at the splash screen and then proceeds to eat up almost all my cpu. The only way to stop it is thru the system monitor app. Force quit only clears the screen view, the bin file keeps on running.

Unfortunately, google maps just doesn't cut it for me.
It'd be nice to have this working.
I've got an ATI card but like I wrote, I've had this app working before with this card.

Got me tossed.[/FONT]:confused:

---

### Post by forestpixie on 2007-08-14
have you tried getting it from the repos

Medibuntu that is :)

---

### Post by walkerk on 2007-08-14
> **blackjack6.21.91 said:**
> Is this just another google app that is wrapped with WINE or is this a native linux application?

its native.

---

### Post by fluteflute on 2007-08-14
> **forestpixie said:**
> have you tried getting it from the repos
its not in the repos

---

### Post by forestpixie on 2007-08-14
Sorry - wrong I was -what I meant to say was that it's in the medibuntu repos :oops:

Forgot that bit

Is it still raining in soton? Here the other side of the forest it's chucking it down :(

---

### Post by carloslosgrande on 2007-08-14
[FONT="Comic Sans MS"]I've tried it thru Automatix, thru Medibuntu and direct from Google. Same problem each time, and I've tried multiple times for each over the last few months - hoping for updates to have remedied the problem.:(

Out of curiousity, where or what is soton?[/FONT]

---

### Post by Hampster on 2007-08-14
> **Neo Ex said:**
> I have an ATI Radeon 9600XT and after about a minute I've opened Google Earth the system freezes. I have had this problem also with the Windows version of Google Earth used with WINE.
I have installed the lastest fglrx driver... what I can do?

It appears that I have the same problem.  I have ATI Radeon 9600.  I am operating two screens.  Just adding that as it may be a clue. GE loads up but then freezes swallowing my cursor and locks the whole system necessitating a restart of computer.  Can anyone suggest a fix?  BTW I have an icon under applications> Internet> Google Earth but also have an icon on the desktop courtesy of the original install.  I have read thru the entire thread and it appears that others have had the same freezing problem but there doesn't appear to be any mention of a fix.  Any help appreciated...

---

### Post by forestpixie on 2007-08-15
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]..Out of curiousity, where or what is soton?[/FONT]

Southampton :D

---

### Post by Hampster on 2007-08-19
I have just up graded to feisty Fawn and was hoping that that would kick G/Earth into gear but still the same freezing up when I move the cursor ....

Any clues?????

---

### Post by markus_ö on 2007-09-14
This worked for me: [http://bbs.keyhole.com/ubb/showflat.php/Cat/0/Number/620003/page/0/fpart/2/vc/1](http://bbs.keyhole.com/ubb/showflat.php/Cat/0/Number/620003/page/0/fpart/2/vc/1)

Quote: "I put this file [http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2) in the google earth directory and renamed it libGL.so.1. GE is running again [...]"

[I am using Ubuntu 7.04, Google Earth 4.2.0180.1134 (beta), ATI Radeon X1600 with Catalyst driver 8.40.4.]

---

