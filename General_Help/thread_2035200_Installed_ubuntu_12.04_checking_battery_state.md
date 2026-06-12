---
title: "Installed ubuntu 12.04 checking battery state"
date: 2012-07-30
forum: General Help
---

### Post by anexation on 2012-07-30
i installed ubuntu 12.04 and it hangs on checking battery state. any help would be appriciated.

graphics card - intel 82q963/q965

edit: ubuntu is installed onto a 8 gb usb card. if that helps at all

Iv'e tried replacing quiet splash with nomodeset and safe graphics mode

---

### Post by anexation on 2012-07-30
bump

---

### Post by bogan on 2012-07-30
Hi!, **annexation,**

Welcome to the Forum. Please note the rules are that you should not bump a thread more often than once in 24 hours.; See Sticky on Forum code of conduct.

Hanging up with a 'Checking Memory state [OK]' message, usually indicates a Graphics driver problem.

Google shows lots of posts with problems with the ' intel 82q963/q965' graphics, though most of them are about Low Resolution problems, and all are old, 2011 or earlier.

Please Post```
 lspci -nnk | grep -iA3 VGA
```As far as I know recent Intel integrated graphics generally work well with the default 12.04 Intel driver. i915. Whether that applies to your card I do not know,

What computer make and model is it -  HP laptop ??

Try editing the linux line of the grub menu script by adding ' i915.modeset=0 ' [that's a zero, not a large 'o'] after the words " ro quiet splash " then press 'Ctrl+x' to boot.

[To edit the grub script, highlight the Ubuntu entry in the grub menu & Press 'e'; the script will show; use arrow keys to scroll cursor to the line that starts "Linux", and along to "ro"; edit and press 'Crtl+x' to boot. The change is not permanent & will have to be repeated if needed, or the /etc/default/grub file edited, and 'update-grub' run.]

Chao!, **bogan**.

---

### Post by anexation on 2012-07-30
i tried that and got a blank screen

Computer is an HP desktop
HP Device [103c:2817]
kernal driver in use: i915

---

### Post by Mr.Plex on 2012-07-30
> **bogan said:**
> Hi!, **annexation,**
...

(1)Please Post```
 lspci -nnk | grep -iA3 VGA
```As far as I know recent Intel integrated graphics generally work well with the default 12.04 Intel driver. i915. Whether that applies to your card I do not know,

(2)What computer make and model is it -  HP laptop ??


Chao!, **bogan**.


...

---

### Post by bogan on 2012-07-30
> **anexation said:**
> i tried that and got a blank screen

Computer is an HP desktop
HP Device [103c:2817]
kernal driver in use: i915Please try again and at the blank screen Press 'Crtl+Alt+F1' [or F2-F6].

Do you get a screen of messages - if so what are they ?? - if not and you get a tty login prompt, can you login and run the lspci command requested?

Also, try ```
sudo service lightdm start # or, instead:
startx
```What happens?

If the " 8 gb usb card" that does not work is a full install, does the computer boot and run OK from a LiveCD/USB, in 'Try Ubuntu' mode?

Chao!,** bogan.**

---

### Post by bogan on 2012-07-30
Hi!, **anexation**,

You edited your OP and Posted:> Iv'e tried replacing quiet splash with nomodeset and safe graphics mode"nomodset" will not work with an i915 driver,  you need: "  i915.modeset=0 ". Please try that.

Chao!,** bogan.**

---

### Post by louisJ on 2012-10-09
Same problem here (thinkpad t400 with graphic card: Intel GMA 4500MHD).
I upgraded to 12.04 and now display starts only if I launch startx in tty1.
i915.modeset=0 doesn't work for me.

Any idea?

---

### Post by bogan on 2012-10-09
Hi!,** louisJ**,

Please Post:```
 lspci -nnk | grep -iA3 VGA
```How far does the boot sequence get before you go to a tty ? [ I presume you get to one with 'Crtl+Alt+F1'.] and does it then [ after startx ] go to a normal ubuntu GUI login screen?

Will it also boot correctly from a tty if you run: ```
sudo service lightdm start
```? if not what messages do you get?

There are other boot system cmds that can be tried depending on the above requested info.

Chao!, **bogan**.

---

### Post by louisJ on 2012-10-11
thanks Bogan, here it is:
```
lspci -nnk | grep -iA3 VGA
00:02.0  VGA compatible controller [0300]: Intel Corporation Mobile 4 Series  Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Lenovo Device [17aa:20e4]
    Kernel driver in use: i915
    Kernel modules: i915
louisro@louisro-ThinkPad-T400:~/Documents/Business/LolaArtGallery/backup120928avantGuestCheckout$  ^Cdo apt-get update && sudo apt-get -y upgrade
louisro@louisro-ThinkPad-T400:~/Documents/Business/LolaArtGallery/backup120928avantGuestCheckout$ lspci -nnk | grep -iA3 VGA
00:02.0  VGA compatible controller [0300]: Intel Corporation Mobile 4 Series  Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Lenovo Device [17aa:20e4]
    Kernel driver in use: i915
    Kernel modules: i915

```> 
How far does the boot sequence get before you go to a tty ?

I see the Ubuntu loading screen, then black screen with logs and last is "checking battery state"
> 
 [ I presume you get to one with 'Crtl+Alt+F1'.] and does it then [ after startx ] go to a normal ubuntu GUI login screen?

Yes!
> 
Will it also boot correctly from a tty if you run: ```
sudo service lightdm start
```? if not what messages do you get?

yes, I get to the desktop, it boots fine.

---

### Post by bogan on 2012-10-11
Hi!, **louisJ**,

A hang-up at 'Checking battery state [OK]' is nearly always an indicator of video driver or xorgserver problems; but in your case, as the GUI works OK after using 'startx' or 'lightdm start', it seems to be more complex.

The obvious thing would be to check out the /var/log files, especially the /Xorg.0.log and dmesg files, and also /home/user/.xsession-errors file ['Crtl+h' to show hidden files].

If you Post or attach them here perhaps someone with more knowledge than I have will be able to spot the cause of the problem. Searching for 'EE' & 'WW' may help.

Another route is various possible boot command additions: try the following in turn:
 A.: Edit with ```
gksudo gedit /etc/default/grub
``` to:
 1.: Uncomment the "GRUB_GFXMODE="680x440" line, and alter it to the resolution you want, eg. "1920x1080x24".
 2,: Add the line: "GRUB_GFXPAYLOAD_LINUX=text" [no quotes]
After each, Save & exit gedit and run:```
 sudo update-grub
``` and reboot. If they do not work comment out the line and rerun 'update-grub'.

 B.: From the grub menu add the following to the boot line in turn and use 'Crtl_X' to boot:
```
acpi=off
acpi_backlight=vendor
acpi_osi=Linux
xforcevesa
i915.modeset=0 xforcevesa
vmalloc=192M
```If one of them has the desired effect use procedure A.: to add the cmd to the GRUB_CMDLINE_LINUX=" " line between the quotes, and run update-grub.

Chao!, **bogan**.

---

### Post by louisJ on 2012-10-19
ok trying

---

### Post by louisJ on 2012-10-25
thanks
here are the logs.

Solution A doesn't work: the bars still don't pop out on the desktop

Solution B: doesn't work either, idem, the bars don't pop out as they should on the desktop, and I cant close or resize open windows...

thank for trying...any more ideas?

---

### Post by louisJ on 2012-10-26
it seems like compiz and metacity are not working...

---

### Post by bogan on 2012-10-27
Hi!, **LouisJ,**

Have you checked whether it will boot correctly using 'Try Ubuntu' from a Live CD/USB?

EDit: Check out this Thread, also a problem with lightdm not starting: [http://ubuntuforums.org/showthread.php?t=1966005](http://ubuntuforums.org/showthread.php?t=1966005)

Chao!,** bogan.**

---

### Post by louisJ on 2012-11-28
very good idea Bogan thanks.
I just tried a 12.10 live usb and it works fine! unity works fine....
It is the proof that 12.10 should work on my machine and that it is a setting problem.

Can you help fix it?
Can I copy the config files from the live version?

thanks

---

### Post by bogan on 2012-11-29
Hi!, **louisJ**,

I dont know about copying the LiveCD compiz configs, which are complex, so I would not advise it. [ I am not saying do not do it; just that it is your risk.]

I would suggest you first try:```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```This should reset compiz to the defaults, then reboot.

'gconftool' is also available from a graphics screen: enter 'gconf' in the Dash search box and you get: "Configuration Editor". You could search through that to see if there are any obvious mis-settings, such as 'metacity not enabled'.

I have notes of more detailed comprehensive resetting code, but I am reluctant to advise them as I have never used them myself, and am not sure of your familiarity with using terminal codes.

Chao!, **bogan.**

---

### Post by louisJ on 2012-11-30
Thanks Bogan

I just tried the compiz commands and rebooted...
Now it is weird because, it shows the desktop background image, I see the firefox window opening (because firefox launches on start on my system) but there is no desktop environment, and no way to manage the window.

I can use term command, no problem.

Thanks

---

### Post by bogan on 2012-11-30
Hi!,** louisJ**,

Please clarify exactly how things now stand.

Do you now get the Greeter Login screen, without having to enter 'startx'?

Can you login successfully?

Logged in or not do you still get a Text Terminal Login prompt with 'Ctrl+Alt+F1'?

You Posted: "it shows the desktop background image"; does that mean a whole Desktop with Launchers & Panel Icons?, or just the background image?. And is the Mouse Cursor evident and/or usable?

Have you tried logging in to a different account, or to Gnome Classic or Gnome Classic [no-effects]?.

Chao!,** bogan**.

---

### Post by louisJ on 2012-12-04
Now I get the greeter without seeing the black screen with "checking battery state".
That's better!

I can login.

But only if I choose to login using "gnome classic no effect" I get the desktop toolbars.
If I login to unity or gnome, I have the mouse pointer moving, I see windows (but I can't close them or move them) and I have no toolbars on the desktop, only the background image.

I have not tried another account but all shells other than gnome classic no effects, do not work.

---

### Post by bogan on 2012-12-04
Hi!,** louisJ,**

Try, from a terminal:
```
sudo apt-get update
sudo apt-get upgrade
```To check if Unity is installed:
```
sudo dpkg -l | grep unity # should list more than 20 items installed
sudo apt-get install -f --fix-missing
sudo dpkg-reconfigure -a # this may take a long time, wait it out
# log out & check if other options are shown
sudo apt-get install --reinstall ubuntu-desktop
# log out & check if other options are shown
sudo unity --reset
sudo reboot
```At  log in check if other options are shown.

Post how you get on.
Chao!,** bogan.**

---

### Post by louisJ on 2012-12-06
Hi Bogan,

Just to be clear first, every "option" is shown on the greeter login screen, it is just that when I choose on of them (except gnome no effect) none of them leads to a working desktop.

I tried the commands you gave above, everything went ok until
```
sudo dpkg-reconfigure -a
```for which I get the response: 
```
/usr/sbin/dpkg-reconfigure: libcapi20-3 is broken or partially installed
```then I tried ```
sudo apt-get remove libcapi20-3
``` but it said that it was installed, so I installed it with ```
sudo apt-get install libcapi20-3
```now
```
sudo dpkg-reconfigure -a
```gave the same error for the package: libmikmod2, which I installed also.
Idem for libsdl-mixer1.2 and libssl0.9.8

loging out and back in.
I retried all the possibilities (system default, gnome, etc...) but only "gnome  no effects" works.
Although now when I reach the desktop with the "gnome  no effects" option, I see an error window saying that Compiz has closed unexpectedly...maybe a clue!

Now, trying : ```
sudo apt-get install --reinstall ubuntu-desktop
```still the same problem...

and finally I get the message that
sudo unity --reset
is a deprecated command.

thanks, any other ideas?

---

### Post by bogan on 2012-12-06
Hi!,** louisJ.**

With the "broken or partially installed" libraries, try again with: ```
sudo apt-get install --reinstall libcapi20-3 # same for the others
```I doubt that the: "Compiz has closed unexpectedly" message is any more than another example of the Apport bug.

With regard to "sudo unity --reset", that is what is shown in 'man unity' but try "unity --replace" [without the 'sudo'].

You will probably get a whole string of Errors and Warnings, and it may hang with a disrupted window display [ no menus etc]. If so, give it a minute or two, and if nothing happens, press 'Ctrl+c'. You may get another string of errors and another hang-up that does not respond to keystrokes.

In any case reboot, if necessary with the Power button.

Another thing you could try is CCSM [compiz config settings manager, you can install it from the Software Center], it will show in Dash.

You will get a warning to be careful when it runs.

The main thing is to check that the Ubuntu Unity Plug-in is enabled [ ie 'ticked'] you will find it in 'Profile' or 'Desktop',  select it and a second window will open with an enable option on the left. Tick it, if it is not already, and close CCSM.

There are other things to try, but let's see how it goes this far first.

**Edit**: 2nd thoughts: when you Posted:> Just to be clear first, every "option" is shown on the greeter login  screen, it is just that when I choose on of them (except gnome no  effect) none of them leads to a working desktop.Can you get a TTY with the other options [Press 'Ctrl+Alt+F1'] if so what does " echo $DESKTOP_SESSION" show for each.??

Chao!, **bogan**.

---

### Post by louisJ on 2012-12-07
> **bogan said:**
> 
With the "broken or partially installed" libraries, try again with: ```
sudo apt-get install --reinstall libcapi20-3 # same for the others
```
Actually, I reinstalled them already.

> **bogan said:**
> 
With regard to "sudo unity --reset", that is what is shown in 'man unity' but try "unity --replace" [without the 'sudo'].
 when I choose the "system default" desktop at the greeter screen, I get windows (see screen capture below) but I can't type in commands in the term...so I can't do this. I can only do it within "gnome no effect" which has no use because unity is not launched in this case, but gnome.
[IMG]http://imageshack.us/photo/my-images/716/capturedu20121207101648.png[/IMG][[IMG]http://img707.imageshack.us/img707/561/capturedu20121207101648.png[/IMG]](http://imageshack.us/photo/my-images/707/capturedu20121207101648.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Uploaded with [ImageShack.us]("http://imageshack.us")

> **bogan said:**
> 
Another thing you could try is CCSM [compiz config settings manager, you can install it from the Software Center]
Ubuntu Unity plugin was disabled indeed, I just reenabled it.;..but as I have also gnome shell installed...I hope it is ok.

> **bogan said:**
> 
**Edit**: 2nd thoughts: when you Posted:Can you get a TTY with the other options [Press 'Ctrl+Alt+F1'] if so what does " echo $DESKTOP_SESSION" show for each.??

the results is nothing... it's blank (actually black!).

Thank you Bogan for helping like this!! so kind of you.

---

### Post by bogan on 2012-12-07
Hi!, **louisJ,**

I do not see any 'attached Screenshot'. Edit: Whoops!, now I do!! BUT! unfortunately, it is not legible.

Did enabling 'Unity Plugin' have any effect ?

I ran 'unity --replace' from Gnome Classic [no-effects] with the result I indicated, and running:```
sudo dpkg -l | grep unity # should list more than 20 items installed
``` was also from that log-in.

Chao!, **bogan.**

---

### Post by louisJ on 2012-12-07
I edited to post a better image, sorry!

enabling the unity plugin did not do anything noticeable.

OK I understand, I just run unity --replace from wihtin gnome no effect, and the effect is that I loose all menu bars, top bars, and windows management bars (to close or reduce windows). I still can move the windows though using the mouse:
[[IMG]http://img141.imageshack.us/img141/8168/capturedu20121207110013.png[/IMG]](http://imageshack.us/photo/my-images/141/capturedu20121207110013.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

```
ThinkPad-T400:~$ sudo dpkg -l | grep unity # should list more than 20 items installed
[sudo] password for louisro: 
ii  gir1.2-unity-5.0:amd64                      6.10.0-0ubuntu1                                                             amd64        GObject introspection data for the Unity library
ii  gnome-themes-ubuntu                         0.6.1                                                                       all          Ubuntu community themes
ii  libmeanwhile1                               1.0.2-4ubuntu2                                                              amd64        open implementation of the Lotus Sametime Community Client protocol
rc  libunity-core-4.0-4                         4.28.0-0ubuntu2                                                             amd64        Core library for the Unity interface.
rc  libunity-core-5.0-5                         5.16.0-0ubuntu1                                                             amd64        Core library for the Unity interface.
ii  libunity-core-6.0-5                         6.10.0-0ubuntu2                                                             amd64        Core library for the Unity interface.
rc  libunity-misc0                              0.2.1-0ubuntu2                                                              amd64        Miscellaneous functions for Unity - shared library
ii  libunity-misc4                              4.0.4-0ubuntu3                                                              amd64        Miscellaneous functions for Unity - shared library
ii  libunity-protocol-private0:amd64            6.10.0-0ubuntu1                                                             amd64        binding to get places into the launcher - private library
ii  libunity-webapps0                           2.4.1-0ubuntu3.2                                                            amd64        Web Apps integration with the Unity desktop
rc  libunity4                                   3.8.4-0ubuntu1                                                              amd64        binding to get places into the launcher - shared library
rc  libunity6                                   4.0.6-0ubuntu3                                                              amd64        binding to get places into the launcher - shared library
ii  libunity9:amd64                             6.10.0-0ubuntu1                                                             amd64        binding to get places into the launcher - shared library
ii  unity                                       6.10.0-0ubuntu2                                                             amd64        Interface designed for efficiency of space and interaction.
ii  unity-asset-pool                            0.8.24-0ubuntu2                                                             all          Unity Assets Pool
ii  unity-common                                6.10.0-0ubuntu2                                                             all          Common files for the Unity interface.
ii  unity-greeter                               12.10.4-0ubuntu5                                                            amd64        Unity Greeter
ii  unity-lens-applications                     6.10.0-0ubuntu1                                                             amd64        Application lens for unity
ii  unity-lens-files                            6.6.0-0ubuntu1                                                              amd64        File lens for unity
ii  unity-lens-music                            6.8.1-0ubuntu1                                                              amd64        Music lens for unity
ii  unity-lens-photos                           0.9-0ubuntu1                                                                all          Unity Photos Lens
ii  unity-lens-shopping                         6.8.0-0ubuntu1                                                              amd64        Shopping lens for unity
ii  unity-lens-video                            0.3.14-0ubuntu1                                                             all          Unity Video lens
ii  unity-place-files                           5.10.0-0ubuntu1                                                             all          transitional package
ii  unity-scope-musicstores                     6.8.1-0ubuntu1                                                              amd64        Store music lens for unity
ii  unity-scope-video-remote                    0.3.10-0ubuntu1                                                             all          Remote videos engine
ii  unity-services                              6.10.0-0ubuntu2                                                             amd64        Services for the Unity interface
ii  unity-webapps-common                        2.4.10-0ubuntu1                                                             all          Unity WebApp integration scripts
ii  unity-webapps-googlecalendar                2.2                                                                         all          Unity Webapp for GoogleCalendar
ii  unity-webapps-service                       2.4.1-0ubuntu3.2                                                            amd64        Service for Web Apps integration with the Unity desktop
ii  xul-ext-unity                               2.4.1-0ubuntu1.1                                                            all          Firefox extension: Unity Integration

```

---

### Post by bogan on 2012-12-07
Hi!, **louis**J,

As far as your dpkg -l | grep unity Post is concerned, apart from it being for 64 bit, where mine is 32bit it is much the same though mine has later versions of many files, - "6.12.0-0ubuntu0.1" instead of: "6.10.0-0ubuntu2" - and some apparently outdated files, such as: "linunity-core-4.0-4 & 5.0-5", but I have no idea what significance that might have, I am running 3.5.0-20-generic and yours is probably -19. There does not seem to be anything important missing.

Perhaps it would be worth while running:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
sudo apt-get autoremove
```You could also run: ```
ps ax | grep unity
```but if you can not run that from a ubuntu log-in, it is not going to tell much. I will check it from gnome [no-effects] and edit this if it seems significant.

Edit: From Gnome Classic [no-effects]:```
:~$ ps ax | grep unity
 2329 ?          Sl     0:00 /usr/lib/**unity**-lens-applications/**unity**-applications-daemon
 2331 ?          Sl     0:00 /usr/lib/**unity**-lens-files/**unity-**files-daemon
 2335 ?          Sl     0:00 /usr/lib/i386-linux-gnu/**unity**-music-daemon
 3435 pts/0    S+     0:00 grep --color=auto unity
~$ 
```Chao!, **bogan.**

---

### Post by louisJ on 2012-12-11
Hi Bogan

I ran the update commands.

Then ps ax gives:
```
ThinkPad-T400:~$ ps ax | grep unity
 3006 ?        Sl     0:00 /usr/lib/libunity-webapps/unity-webapps-service
21012 pts/0    S+     0:00 grep unity
```

---

### Post by bogan on 2012-12-11
> **louisJ said:**
> 

I ran the update commands.

Then ps ax gives:
```
ThinkPad-T400:~$ ps ax | grep unity
 3006 ?        Sl     0:00 /usr/lib/libunity-webapps/unity-webapps-service
21012 pts/0    S+     0:00 grep unity
```Was that from an ubuntu log-in? or from Gnome Classic[no-effects]?? It implies that not even the basic essentials of unity
are running although they are present.

You could check in Synaptic Package Manager.  With "unity" as the Search filter, 'Status' selected on the Left, and 'installed', above left, my installation shows 30 'unity' items Green flagged as Installed.  If you do not have 'Synaptic' run: ```
sudo apt-get install synaptic.
```In your position I would run:```
sudo apt-get update
sudo apt-get install -f --fix-missing
sudo dpkg-reconfigure -a # It may take a long time, just wait it out
```If you have not already run them, then:```
sudo apt-get install --reinstall ubuntu-desktop
sudo reboot # check if any change
sudo apt-get install --reinstall unity unity-common
```Beyond that I am beginning to run out of ideas.

Chao!,** bogan.**

---

### Post by louisJ on 2013-02-11
I ran the commands from gnome classc 'no effect'..., indeed unity seems installed but doesn't work.   I ran the others commands you suggest...still nothing...  Thanks anyway Bogan!

---

### Post by bogan on 2013-02-11
Hi!, louisj,

Try:```
 setsid unity
```If it hangs, give it a few minutes and open another terminal [File menu or 'Shift+Ctrl+N'] and  enter: ```
sudo reboot
```Chao!, **bogan**.

---

### Post by louisJ on 2013-02-12
Hi Bogan

it doesn't hang but I get an error :

 X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  6513
  Current serial number in output stream:  6730

---

### Post by bogan on 2013-02-12
> **louisJ said:**
> Hi Bogan

it doesn't hang but I get an error :

 X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  6513
  Current serial number in output stream:  6730What happens when you reboot after 'setsid unity' ? 

Any change ??

Chao!, **bogan.**

---

### Post by louisJ on 2013-02-12
no still the same.

However, a LIVE USB ubuntu works perfectly...would it be possible to copy the config files from this live usb?

thanks

---

### Post by louisJ on 2013-02-12
horrible!! now I have another problem...I deleted two user accounts (through system parameters) to leave only my account....and now I can't login anymore ("I have no name" is displayed instead of my name)......
What can I do to recover my account?
thanks

---

### Post by bogan on 2013-02-12
> **louisJ said:**
> horrible!! now I have another problem...I deleted two user accounts (through system parameters) to leave only my account....and now I can't login anymore ("I have no name" is displayed instead of my name)......
What can I do to recover my account?
thanksSorry!
That is not something I know about, though i have seen many posts about similar problems.

Good Luck & Chao!,** bogan.**

---

### Post by louisJ on 2013-02-13
I finally had to let go and reinstall ubuntu....
Anyway, thank you for your precious help!

---

