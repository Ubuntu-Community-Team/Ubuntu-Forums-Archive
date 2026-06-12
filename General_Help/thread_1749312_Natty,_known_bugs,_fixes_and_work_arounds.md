---
title: "Natty, known bugs, fixes and work arounds"
date: 2011-05-04
forum: General Help
---

### Post by cariboo on 2011-05-04
As with every release we open a thread about how our members have solved problems with Natty (11.04).

I personally haven't had any problems since the release, but I found a link to  [Things to tweak and fix after installing Natty (11.04) at webup8]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html")

**Unity not your cup of tea ?**

[color=blue]**Solution:** Try K/X/Lubuntu. If you prefer a light weight alternate, try Fluxbox, openbox, pekwm, awesome, xmonad, or any of the alternate window managers.[/color]

---

### Post by Frogs Hair on 2011-05-04
I had no problems with the installation or Unity working properly , but I did apply some of the options posted at the link .

---

### Post by sg1efc on 2011-05-04
Thanks a lot Cariboo907.  :)

---

### Post by timgood on 2011-05-05
Here are somethings I have found:

1. To enable all applications to put an icon into the system tray you need to circumvent the whitelist of 'approved' applications. You can do this by opening a terminal and typing:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

and then logout and back in for the changes to take place. This will enable you to use things like Shutter or RadioTray.

2. If you are experiencing problems trying to enable desktop effects in Gnome Classic, (typical problems are the loss of menu bars and window borders, Unity coming back when compiz is enabled as window manager etc.) then you can do this. This works for the classic desktop. The absense of desktop effects tab in System >> Preferences >> Appearance should provide a clue. Compiz needs a basic set of plugins activated in order to work, they are Composite, OpenGL, Window Decoration, Move Window & Resize Window. You can turn them on using Compiz Config Settings Manager which can be installed from Software Centre. Then open a terminal and:

```
compiz --replace ccp &
``` to restart compiz and then 

```
gtk-window-decorator --replace &
``` to get back menus and borders. Many thanks to afrodeity for this fix.

Edit: Oh, and I forgot. If you have Nvidia and no Plymouth following upgrade, this [script]("http://www.webalice.it/bernardi82/software/fixplymouth-natty") fixes it. Download it, make it executable by ```
chmod +x fixplymouth-natty
``` and then run it with ```
./fixplymouth-natty
```

After a reboot, Plymouth will return. Thanks for this one is due to Paolo Bernardi.

---

### Post by stinkeye on 2011-05-05
> **timgood said:**
> Here are somethings I have found:

1. To enable all applications to put an icon into the system tray you need to circumvent the whitelist of 'approved' applications. You can do this by opening a terminal and typing:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

and then logout and back in for the changes to take place. This will enable you to use things like Shutter or RadioTray.


Good tip, but sometimes for me it becomes buggy to the point where I can't
click on any indicators, after changing to 'all'.
I only wanted to add gnote so I installed **dconf-tools**.
Ran dconf-editor, navigated to /desktop/unity/panel/systray-whitelist
and added gnote to the list.

---

### Post by denisk on 2011-05-05
I had a major issue during an updating from 10.10 (and from what I've red, I'm not the only one): my machine started to freeze during the startup. Many workarounds and suggestions were applied, but finally I had to re-install from iso.
I would also mention that I had to move to classic gnome (an option which appears on the bottom of login screen) because of the following issue - after some work title bars of window just disappear. Once again - no workaround unfortunately...:(

---

### Post by LoneIgadzra on 2011-05-05
Anyone know why I get two prompts to unlock my keyring every time I log in? Never had this happen before.

---

### Post by LatinaLover93 on 2011-05-05
> **denisk said:**
> I had a major issue during an updating from 10.10 (and from what I've red, I'm not the only one): my machine started to freeze during the startup. Many workarounds and suggestions were applied, but finally I had to re-install from iso.
I would also mention that I had to move to classic gnome (an option which appears on the bottom of login screen) because of the following issue - after some work title bars of window just disappear. Once again - no workaround unfortunately...:(

I also have this problem,  to fix it i just log off n log on

---

### Post by dantesoft on 2011-05-06
When upgrading from 10.10 on my machine, Natty set the default boot image as 2.6.38-8-generic-pae, which didn't boot (stuck at the start image: ubuntu logo with 5 red circles).
Uninstalling that pae image and headers set the normal image-2.6.38-8-generic as default (available in the "previous linux" boot menu), which works!

---

### Post by rez182 on 2011-05-06
if i let installer download updates while installation of ubuntu 11.04, it download the graphics driver autometically, and the screen freezes in **mountall: Disconnected from Plymouth** (login screen never shows up)

BUT

if i turn off the wifi and dont let it download anything, i am able to start 11.04 in classic mode. later if i download the graphics driver, same thing happens. (BTW i get the old version of nvidia driver from the additional drivers eg: 260 instead of 270)

is there a work around or fix to this?

My nvidia card is geforce 310M

thanks...

---

### Post by fragos on 2011-05-06
> **LoneIgadzra said:**
> Anyone know why I get two prompts to unlock my keyring every time I log in? Never had this happen before.

Same here but I also saw this with 10.10, only there I had four password requests at point. I got the number down to two by uninstalling Gwibber and empathy. I'd hoped that a clean install of 11.04 would flush problems like that away but it didn't.

---

### Post by hawthornso23 on 2011-05-07
I think it is worthwhile warning people that attempting to tweak the appearance of unity using the compiz config settings manager is not advised. I have had natty installed for less than 24 hours and have already completely and seriously destroyed my desktop four or five times simply trying to make minor tweaks to its appearance. 

What I thought I was getting was a desktop integrated with my favorite window manager - compiz. What I actually got was a desktop apparently constructed by cannibalising compiz to the extent that compiz as I understand it, in all its fully configurable glory,  is no longer functional.

Currently unity is a "take it or leave it" desktop environment. Almost nothing about it is configurable and efforts to tweak it are likely to break it. Some aspects of its design I really quite like and want to use. But if you are used to being able to customize your desktop environment then unity's rigidity and fragility is going to drive you nuts.

---

### Post by ulsterman on 2011-05-07
Only 3 remaining bugs with my trusty Aspire One (yes they still do exist):

1) New windows do not re-size properly (new in Natty)
2) No wired network out of box (recognised in network manager but will not connect)
2) No SD card recognition when computer already on (works if inserted before start up)

Is there a method for reporting these prob's in plain english as I'm not very tech (just love Ubuntu for ease of use)?

---

### Post by henrodon on 2011-05-07
> **LatinaLover93 said:**
> I also have this problem,  to fix it i just log off n log on

I've seen several people mention that there's an option at the bottom of the login screen to switch to Classic. I don't have that option. Is there some other way to switch?

---

### Post by stinkeye on 2011-05-07
The option only appears after you type in your user name and press enter.

---

### Post by suttiwit on 2011-05-07
Well, For me graphics and display is not really good and I have a message to run Ubuntu Classic Session because the graphic is not really good and i tried to follow the steps but it did not work again, What shall i do? :confused:

---

### Post by spikoley on 2011-05-07
> **suttiwit said:**
> Well, For me graphics and display is not really good and I have a message to run Ubuntu Classic Session because the graphic is not really good and i tried to follow the steps but it did not work again, What shall i do? :confused:

> **rez182 said:**
> if i let installer download updates while installation of ubuntu 11.04, it download the graphics driver autometically, and the screen freezes in **mountall: Disconnected from Plymouth** (login screen never shows up)

BUT

if i turn off the wifi and dont let it download anything, i am able to start 11.04 in classic mode. later if i download the graphics driver, same thing happens. (BTW i get the old version of nvidia driver from the additional drivers eg: 260 instead of 270)

is there a work around or fix to this?

My nvidia card is geforce 310M

thanks...

There is a [bug with jockey]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788") that effects 3rd party drivers like NVIDIA.  It sounds like you guys might have it.  Check under System> Administration> Additional Drivers and the status message at the bottom.  Does it say, "This driver is activated but not currently in use".  If it does then add your details to the bug report.  For a work around you have to use Ubuntu Classic (gnome).  I also had to switch my video card driver to "vesa" in /etc/X11/xorg.conf.

---

### Post by polka123 on 2011-05-07
Hi can anyone help me please, I have installed 11.04 and can onlu use ubuntu classis no effects. If I use the 'Ubuntu' option with the the nice new side bar nothing works, the cursor moves but then nothing on the screen works / does anything if you try to click on them. I have a geforce 7300le graphics card and it is using the 270.41.06 driver.  Help please.
 
Thanks
Rod

---

### Post by hvbakel on 2011-05-07
For point 1, you might try to disable the new resize "grippers" in the bottom right of windows, they have been causing some problems for me as well: [http://blog.patshead.com/2011/04/disable-the-resize-window-grippers-in-ubuntu-1104-natty-narwhal.html](http://blog.patshead.com/2011/04/disable-the-resize-window-grippers-in-ubuntu-1104-natty-narwhal.html)

---

### Post by ulsterman on 2011-05-07
Thank you hvbakel, looks a bit complex for me. Just hope it fixes itself in updates. Just looking for perfection I suppose.

---

### Post by Allavona on 2011-05-08
Gave Unity its go around. It is highly functional, but is a train wreck to customize. As stated in an earlier post, playing with it may result in a completely useless environment. I also had some problems while in the Unity environment where I would open, say, Firefox, and the screen would go black, and I was back at the login screen. this happened numerous times. So I started using the classic desktop and have had no issues what-so-ever since.

---

### Post by Corgo on 2011-05-08
> **Allavona said:**
> Gave Unity its go around. It is highly functional, but is a train wreck to customize. As stated in an earlier post, playing with it may result in a completely useless environment. I also had some problems while in the Unity environment where I would open, say, Firefox, and the screen would go black, and I was back at the login screen. this happened numerous times. So I started using the classic desktop and have had no issues what-so-ever since.

Lucky you, such a "step-back" did not work for me.


Anyone else knows how to solve this, before I have to reinstall my laptop?
And also I would like to damage any files on my hdd!:confused:

---

### Post by francis000 on 2011-05-08
I update ubuntu from 10.04 to natty and found one problem. When I minimize the windows, the buttons (clos, minimize and maximize)are not displayed. Anyone know a solution?

[IMG]http://www.subirimagenes.com/imagen-pantallazo-6371994.html[/IMG]

---

### Post by shao.lo on 2011-05-08
I had the error below..discussed in [http://ubuntuforums.org/showthread.php?t=1677888](http://ubuntuforums.org/showthread.php?t=1677888)

error: symbol not found: 'grub_env_export'

Then display "grub rescue>".

I tried the solutions listed but didn't help...tho my situation was a bit different.  I had two disks in my box /dev/sda and /dev/sdb.  The sda disk was cloned from the sdb disk a while back.  I don't use the sdb disk, but its still plugged in.

My problem is that when grub went to boot my system it got confused by both sda and sdb having the same uuid.  I confirmed this by issuing the blkid command.

I used the steps listed at the following url to fix my problem.... [http://www.linuxconfig.org/how-to-retrieve-and-change-partitions-universally-unique-identifier-uuid-on-linux](http://www.linuxconfig.org/how-to-retrieve-and-change-partitions-universally-unique-identifier-uuid-on-linux)

Once I had given the sdb disk a different id, the system booted off sda as expected.

Hope this helps..if anyone else is in that boat :)

---

### Post by Martin_sensei on 2011-05-09
> **LoneIgadzra said:**
> Anyone know why I get two prompts to unlock my keyring every time I log in? Never had this happen before.

I had this,

Basically, I had provided a password during my live session before I installed, which meant all my passwords were stored unter the "Default" keyring.  When I logged on that created a "Login" keyring which was empty.

I just deleted the Default keyring, and made "Login" the new default.

Of course you have to reenter all your passwords if you do this.

There maybe a way to export, but I took the heavy handed approach.

---

### Post by Martin_sensei on 2011-05-09
Here is my origional post, I fixed it myself :-)

[http://ubuntuforums.org/showthread.php?t=1752805]("http://ubuntuforums.org/showthread.php?t=1752805")

---

### Post by dscott422 on 2011-05-09
11.04 does not shutdown or restart.  Has something to do with Plymouth-upstart can't connect.  Any ideas?

---

### Post by fragos on 2011-05-09
Using "Passwords and Encryption Keys" I looked inside the "Passwords:default" folder and found a number of entries and that I had 2 "Desktop Couch user authentication" entries and deleted one of those. That seems to have fixed my problem.

---

### Post by Python Jedi on 2011-05-09
Anyone here have a problem that keeps windows from resizing (The mouse pointer changes, but it won't resize), and windows that are blank white until making them smaller?

Thanks!

---

### Post by alexfish on 2011-05-09
[B]
usb_modeswitch[/B]:

have see post where users are installing usb_modeswitch + data_package, (reason device not recognised)

**First check this post **  #[**2**]("http://ubuntuforums.org/showpost.php?p=10736509&postcount=2")  ref to Network Manager

latest usb_modeswitch should be installed at default + the data package
the **dir usb_modeswitch.d** may be empty. {if reading this from a link (reference Ubuntu 10.10 this may not be the case). the usb_modeswitch data is in " /usr/share/usb_modeswitch/configPack.tar"

From the overrides readme
> ===== usb-modeswitch-data =====

=== Overriding entries from the database tarball ===

From its 1.1.7 version, usb-modeswitch searches for device switching data in
the usb-modeswitch-data database tarball [0]. This heavily reduces the
database disk space, but makes configuration investigation harder. To solve
this issue, usb-modeswitch is shipped with a patch that allows administrators
to override the database entries from the tarball [0] with files under /etc.

[0] /usr/share/usb_modeswitch/configPack.tar.gz 

= Example =

Let's assume one has a 3G dongle "05c6:1000 Qualcomm", which matching database
entry [1] is 05c6:1000:uMa=Option , but isn't correctly switched. Hacking this
database entry can be done as following:

# cd /etc/usb_modeswitch.d
# tar /usr/share/usb_modeswitch/configPack.tar.gz 05c6:1000:uMa=Option

Now the /etc/usb_modeswitch.d/05c6\:1000\:uMa=Option file will get used by
usb_modeswitch_dispatcher when the "05c6:1000 Qualcomm" device gets plugged
in.

When a correct database entry is found, please report it on the upstream
forum:

    [http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

[1] One can find exactly which database entry is matching a given device gets
    matched with by activating logs (/etc/usb_modeswitch.conf) and reading
    them from /var/log/usb_modeswitch*.if have a device switching but no drivers loading suggest use Sakis3g , it may load a driver if usb_modeswitch failing to place the ids in the driver new_id .  the sakis 3g script indications are it will look in the /etc/usb_modeswitch.d for switching devices

to install all of the data ;** Reminder Read the above overrides**
```
sudo su
cd /etc/usb_modeswitch.d
tar xvf /usr/share/usb_modeswitch/configPack.tar[FONT=monospace].[/FONT]gz
```**if the device is not switching:**

**1. do not** reinstall usb_modeswitch from external sources .
site still states "Note that the Debian package is not 100% compatible with recent Ubuntu versions"
only use the data package directly from the site (if reinstalling )

**2.** check the listing in network manager with nm-tool from the terminal
```
nm-tool 
```, if the device is listing then check your configuration data

**3.** if have alternate method of internet connection update the usb_ids from the terminal
```
sudo /usr/sbin/update-usbids
```**4.** if still not recognised list the device with lsusb command
```
lsusb
```**5. check the device_reference.txt) . check to see if device is listed.** (had to check this before post Looks up-to date) do not use this for the modeswitch
[device_reference.txt]("http://www.draisberghof.de/usb_modeswitch/device_reference.txt") 
download the latest data package
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
**do not install this package** ,[COLOR=Blue]**save it**[/COLOR]. unzip the file , look for the /etc/usb_modeswitch.d folder . Locate the file for device as listed from lsusb command.double click the file to open up in gedit (Text Editor).

**6.** open up gedit (Text Editor)from the terminal as super user
```
sudo gedit /etc/usb_modeswitch.d/xxxx:yyyy
```where xxxx : yyyy is the same ID for the device. copy the contents from user gedit to the root gedit . 
save and exit

**7. **check the usb_modeswitch rules. 
```
cat /lib/udev/rules.d/40-usb_modeswitch.rules
```check to see if the device ID,s are listed

if the device is not listed add the rule
```
sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
```add a line within the main rules below the (LABEL="modeswitch_rules_begin")
```
ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="yyyy", RUN+="usb_modeswitch '%b/%k'"
```where xxxx and yyyy is the device ID's.  IE 19d2:2000 = xxxx:yyyy
save and exit, reconnect the device

Bugs should be reported direct to usb_modeswitch at link given (also helpful if you have a device not recognised by usb_modeswitch . they have a forum).

ADDED: **Sporadic modem detection** problems : IE Network  Manager sometimes fails to see the modem . try the below from the terminal
```
sudo killall modem-manager
```some newer modem devices may have a port which is not listed in the databases of udev and modem manager:.

**Sakis3g** is a connection manager with device switching + modem port detection ability; can suggest downloading sakis3g as a matter of course , it should work if problems arise before and after updating the system , one can then try reinstall usb_modeswitch.[*   Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&sqi=2&ved=0CBgQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=vVviTcbfMcOWhQe1s-3pBw&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")

**Debugging: Network Manager , PPP  and Modem-manager**
stop NetworkManager
```
sudo killall NetworkManager
```stop NetworkManager
```
sudo stop network-manager
```restart modemmanager with --debug and put output in /tmp/modem.log.txt
```
sudo killall modem-manager; sudo modem-manager --debug 2>&1 | tee /tmp/modem.log.txt
```enable PPP debugging too:
```
export NM_PPP_DEBUG=1
```start networkmanager and put log in /tmp/nm.log.txt
```
sudo NetworkManager --no-daemon 2>&1 | tee /tmp/nm.log.txt
```~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
testing modem-manager : need to download mm-test.py
```
wget http://cgit.freedesktop.org/ModemManager/ModemManager/plain/test/mm-test.py
```run modem-manager test
```
python ./mm-test.py
```

---

### Post by trystan830 on 2011-05-10
[s]i'm not sure if this is where this goes, but i poked around a few places and didn't see it anywhere.

so the menu bar down the side - Unity, right?  if i search for my program - in this case, i've installed the GIMP - from the dashboard - and when i find it, i drag the icon into Unity... why does it give me a blank space, and not an icon for the program?  is there something else i need to do?  thanks! 

edit... forgot to mention that i just upgraded to 11.04 tonight.[/s]

edit2: i restarted.... and my icons were there.

---

### Post by klm3030 on 2011-05-11
This is the sorriest piece of untested garbage that Ubuntu has released yet. At the very least users should be warned not to install on machine with Nvidia graphics. What makes it even worse is there seems to be no one in charge of fixing it, just a bunch of try this, try that with the result of an even more messed up machine. I will be going back to 10.10 and looking for a new Linux OS.

---

### Post by timgood on 2011-05-11
> **klm3030 said:**
> This is the sorriest piece of untested garbage that Ubuntu has released yet. At the very least users should be warned not to install on machine with Nvidia graphics. What makes it even worse is there seems to be no one in charge of fixing it, just a bunch of try this, try that with the result of an even more messed up machine. I will be going back to 10.10 and looking for a new Linux OS.

I've encountered various problems and also don't like Unity - however I have stuck with Natty (classic mode) and it does seem to be getting slowly better as updates come in. However, I must agree with you and say that I've seen more people leave Ubuntu with this release than I have ever seen before. If I can't get the same functionality and stability (it's stability that is the main issue now) then I will revert to 10.10 as well.

---

### Post by d@rk on 2011-05-11
Noone else is having firegpg problems? I cannot find any info in the problem, but after upgrading to Natty Firegpg says it can't load the IPC library.  I made a thread, but noone has responded. Firegpg forums are dead. I have disabled all addons trying to isolate the problem, but I just cant seem to figure it out. Sorry to make another post, but I am in real need for a new frontend I can use for GPG or a fix. What happened to privacy-gaurd?

---

### Post by linikz on 2011-05-11
I just updated from 10.10 to natty and my laptop wouldn't boot anymore. I'm stuck with a black screen (backlight on) after the splash. It was working for me for about a week. From various posts I guess it's a video card driver problem. I used my Fedora 14 LiveCD to get in (since natty livecd's wouldn't boot either). I edited \etc\X11\xorg.conf to "vesa" but it still didn't work for me. Any suggestions guys???

---

### Post by Anthorn on 2011-05-11
I did a fresh install of 11.04, got the Unity desktop, installed the Nvidia driver and no desktop. The only way then to get any kind of desktop is to load the basic desktop no effects (click the button at the bottom of the login screen) but then graphics and flash were very slow. Then I did a fresh install of 10.10 and got rid of Natty.

I'll hit the proverbial nail on the head here: Natty doesn't work with the driver for the graphics that most Linux desktop users have - Nvidia. Could well be a case of R.I.P. Ubuntu especially when we consider that newcomers to Ubuntu will be downloading Natty! Bordering on insanity? Probably!

---

### Post by fragos on 2011-05-11
If you updated online I suggest you download the ISO and do a clean install.

---

### Post by spikoley on 2011-05-11
> **Anthorn said:**
> I did a fresh install of 11.04, got the Unity desktop, installed the Nvidia driver and no desktop. The only way then to get any kind of desktop is to load the basic desktop no effects (click the button at the bottom of the login screen) but then graphics and flash were very slow. Then I did a fresh install of 10.10 and got rid of Natty.

I'll hit the proverbial nail on the head here: Natty doesn't work with the driver for the graphics that most Linux desktop users have - Nvidia. Could well be a case of R.I.P. Ubuntu especially when we consider that newcomers to Ubuntu will be downloading Natty! Bordering on insanity? Probably!

It's a [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Hopefully they will fix it soon.

---

### Post by spikoley on 2011-05-11
> **spikoley said:**
> It's a [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Hopefully they will fix it soon.  The work around is to switch to Ubuntu Classic mode.  On the log in screen click your user name and then at the bottom select Ubuntu Classic.  Make sure to update the bug, so they know how big the issue is.

---

### Post by klm3030 on 2011-05-11
Saying this is a bug is like saying the Titanic had a leak. In my case I downloaded the ISO and did a complete new install ( four times now) so that's not the problem and in trying all the various fixes I have not been able to run Classic either. If they don't know the scope of this problem by now, adding to their bug report won't help.

---

### Post by slooksterpsv on 2011-05-12
Ok so I'm back to using Ubuntu thanks to that guide:
globalmenu - gone
overlay scroll bars - gone

You know what, in Oneric they should ASK the user how they want those items setup. I'm sorry but the overlay scrollbars are horrible, I can barely get them to show and a lot of apps I use are file menu intensive and I have to click on the right window to find the file menu and it just is a pain. Thank goodness for that link, omg I was going to leave Ubuntu due to those issues. I'm so happy now =D

---

### Post by mitulv4u on 2011-05-12
I like unity as it saves lot of my workspace, but its running really slow on Netbook...it runs superfast on my desktop i3 processor.

Any ideas to make it run faster? I dnt want to go back to Classic Gnome.

---

### Post by GuiGuy on 2011-05-12
> **spikoley said:**
> It's a [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Hopefully they will fix it soon.

Hopefully. Like the USB flash memory transfer speeds. Three, or is it four (?) years on and still no fix. And the same issue has made it through to 11.04.

---

### Post by trystan830 on 2011-05-12
i'm not sure where this would go, but i have a question about the Unity toolbar... i there somehow i could resize the icons to be a little smaller?  i mean, the size of the icons on my monitor is just fine, but i think in my case it's just a preference thing....

---

### Post by timgood on 2011-05-12
> **trystan830 said:**
> i'm not sure where this would go, but i have a question about the Unity toolbar... i there somehow i could resize the icons to be a little smaller?  i mean, the size of the icons on my monitor is just fine, but i think in my case it's just a preference thing....

Install Compiz Config Settings Manager, and then click on the Unity plugin. There you will find the option to scale down the launchbar and the icons in it. 

Hope this helps.

---

### Post by trystan830 on 2011-05-12
> **timgood said:**
> Install Compiz Config Settings Manager, and then click on the Unity plugin. There you will find the option to scale down the launchbar and the icons in it. 

Hope this helps.
it does!  i'll check it out tonight when i'm finally home and on my Ubunutu box. thanks! :)

---

### Post by sparkler on 2011-05-12
ive used 11.04 i doesn't like my encrypted disks so the installer doesn't get to the partition screen. the windows are laggy when moving them around and i don't like unity they should of stuck with gnome and put unity on kubuntu

---

### Post by Cfhs_1 on 2011-05-12
> **sparkler said:**
> ive used 11.04 i doesn't like my encrypted disks so the installer doesn't get to the partition screen. the windows are laggy when moving them around and i don't like unity they should of stuck with gnome and put unity on kubuntu

Uhm, what?

---

### Post by trystan830 on 2011-05-12
> **timgood said:**
> Install Compiz Config Settings Manager, and then click on the Unity plugin. There you will find the option to scale down the launchbar and the icons in it. 

Hope this helps.
i went into the Software Center, and found Simple  CompizConfig Settings Manager and clicked on install.  it asked for my password, and the gave me this message:

> Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details:
The following packages have unmet dependencies:

simple-ccsm: 
so sounding like the unexperienced user i am, what do i do now?

---

### Post by stinkeye on 2011-05-13
The package you want is **compizconfig-settings-manager**

You can install through the terminal with
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by kaefert66014235 on 2011-05-13
I've got a problem with the "Classic Ubuntu" Desktop of 11.04 --> In Ubuntu-Version 10.10 and before I was able to resort the windows in the lower gnome panel by use of drag'n'drop, but in 11.04 when you try to drag a Window from that panel you always get a desktop-launcher to place inside the unity-bar, but you can't drop it in the gnome panel for resorting purposes anymore.. Is there a fix for that?

EDIT: after being scolded that this thread is for fixes and workarounds: here is what fixed the problem for me: reboot. If I drag the windows now they can still be used as desktop launcher if I drag them somewhere where that makes sense, but I can also drag'n'drop them to resort them inside the panel.

---

### Post by pheonix00785 on 2011-05-13
i have this bug were i have 1 or 2 windows open and i cant sellect any thing with my mouse (aka click butons exit out of or sellect a page) and end up only able to use my keyboards tab and enter, making ubuntu unuseble. any ideas?:confused:

---

### Post by stinkeye on 2011-05-13
This isn't a whinge thread, it's for posting your workarounds for bugs.
:mad:#-o

---

### Post by pheonix00785 on 2011-05-13
srry

---

### Post by stinkeye on 2011-05-13
> **pheonix00785 said:**
> srry
That's ok ,I was a bit rude.
Just start a new help thread.
:wink:

---

### Post by trystan830 on 2011-05-13
> **stinkeye said:**
> The package you want is **compizconfig-settings-manager**

You can install through the terminal with
```
sudo apt-get install compizconfig-settings-manager
```
thank you so much! that totally worked.  i'm still learning these things when it comes to Ubuntu. :)

---

### Post by Total Noob on 2011-05-13
Complete failure of network manager, so no wifi on my laptop. Inexplicable intermittent behavior, sometimes on, mostly not, no way of knowing when.

Had to go back in the face of godawful functionality regression.

Those are just the bugs. 

I was very dissatisfied with the new appearance and the failure to be able to identify everything running at once with bottom or top tabs and without having to shuffle the cursor to the corner to find out. Finding apps is much, much more effort because you have to click several times through various layers within categories on the newfangled menu with its vertical list of apps to find what you are looking for rather than being able to find everything by category not more than two clicks away with the prior horizontal list.  

The services and preferences controls are also bizarrely placed with the on/off switch making it just like Start -- and I thought Ubuntu was for people who didn't think Start was a good place for apps or shut down!

And I'm still at a loss for the foolishness of switching X from the top right to the top left. What exactly was that about?

11.4 is a step backwards for certain; makes me think of Vista.

---

### Post by deathm00n on 2011-05-13
Hello, I'm a little noob, started using linux this february if you can help me I would be very grateful

I've tried to install the compiz settings manager in the 11.04 to enable the desktop cube(I've already had it on 10.10) and now my desktop doesn't have the top bar or the new side bar, only my desktop picture and the archives, when I try to open any program it don't have the top bar to close, maximize or resize it

I've tried that command timgood said in the first page but after I input the command nothing happens only appear: [2](random number)

Can someone help me?

---

### Post by fragos on 2011-05-13
There appears to be a bug associated with the online upgrade process that doesn't start "unity". Open a terminal window by typing Ctrl-Alt-t and at the command line prompt type "unity" followed by the Enter key and unity will start. You may also be missing the Title bar from the top of windows that open. Running "metacity" will give you that. As a work around I put both of those in the "Startup Applications" in order to run them when the system boots. Being unsure what else might be missing I decided to do a clean install from a Live-CD which installed correctly for me.

---

### Post by Duncan Williams on 2011-05-13
*I was very dissatisfied with the new appearance and the failure to be able to identify everything running at once with bottom or top tabs and without having to shuffle the cursor to the corner to find out. Finding apps is much, much more effort because you have to click several times through various layers within categories on the newfangled menu with its vertical list of apps to find what you are looking for rather than being able to find everything by category not more than two clicks away with the prior horizontal list.* 

All it takes is one click on the dash button (top left).
Type 2-4 letters of the start of the name of the app or file/folder.
bang , you have an icon to click on. To easy for most I suppose.

---

### Post by spoon_ on 2011-05-14
The new interface is definitely very type-happy. If you like typing to find things, it should work great for you. If you like using the mouse, you're gonna have a miserable time finding anything in Unity's menus. It's a shame that they had to sacrifice one way of doing things to enhance another.

---

### Post by caulkins on 2011-05-14
> **Duncan Williams said:**
> 
All it takes is one click on the dash button (top left).
Type 2-4 letters of the start of the name of the app or file/folder.
bang , you have an icon to click on. To easy for most I suppose.

So I have to move my hand from the mouse to the keyboard just to type a couple of letters?  Yeah, that's efficient.  Also, with less-commonly-used apps, I might not remember the exact name, but I'll recognize it when I see it.  Drop-down menus are far quicker to scan through than multiple icon grids.

---

### Post by spoon_ on 2011-05-14
> **caulkins said:**
> So I have to move my hand from the mouse to the keyboard just to type a couple of letters?  Yeah, that's efficient.  Also, with less-commonly-used apps, I might not remember the exact name, but I'll recognize it when I see it.  Drop-down menus are far quicker to scan through than multiple icon grids.

Not that I disagree with you or anything, but I'll point out that you don't actually have to click. You can press the windows key instead.

---

### Post by spoon_ on 2011-05-14
The sad thing is that there exist menu systems that are good both at mouse and keyboard navigation. For example Windows 7's start menu, Cardapio, or any organized menu system with gnome-do on top. So it's not like you HAVE to sacrifice mouse navigation for easy keyboard access.

---

### Post by Duncan Williams on 2011-05-14
Thanks for the press `windows key to open dash' tip.
Didn't realise you could do that.
If you want to use the mouse its just click on dash icon, click on `more apps', click installed.
all apps onboard are available to choose from icons.
Any way you look at it, it's different than classic or windows., but it works and it's easy once you have spent a bit of time with it.

---

### Post by boujarmouneismail on 2011-05-14
plz help me when i write "vi programnoun.c" in ubuntu terminal and i go inner that the keyboard became crazy plz help me and i so need it i have exam in O.S next week plz help me . i have last version of ubuntu i will so recognize you help.

---

### Post by sgage on 2011-05-14
I find that the Classic - No Effects session is a very nice Ubuntu indeed. I have never had any use for compiz myself. 

Anyway, Natty is fast, stable, up-to-date with the apps - a great Ubuntu!

---

### Post by Duncan Williams on 2011-05-14
Aside from other platforms and distros and there choice of gui, etc.
I can quickly and easily start my computer up in one of the following ways (1 click - slight delay whilst booting)

> Ubuntu Unity (3D)
> Ubuntu Unity (2D)
> Ubuntu Classic
> Windows XP-sp3
> Peppermint Ice

But of course, I always use unity 3D, coz for me that is the best option.
I use windows for home theatre coz little bit better with my graphics card. 
(slightly better performance, overclocking, higher refresh, etc available as options)

---

### Post by rockstar2577 on 2011-05-15
cariboo907, thank you for this info!

---

### Post by Robertjm on 2011-05-15
What happened to the poll on upgrade vs. update vs. clean install that's usually stickied at the top when a new version gets released?

I've been using Lucid and wondered if there are any pratfalls with doing the upgrade path directly to Natty?

Robert

---

### Post by fragos on 2011-05-15
> **Robertjm said:**
> What happened to the poll on upgrade vs. update vs. clean install that's usually stickied at the top when a new version gets released?

I've been using Lucid and wondered if there are any pratfalls with doing the upgrade path directly to Natty?

Robert

My upgrade installed unity but never started it or the metacity necessary for for window title bars. I got it all working but didn't feel comfortable that there wasn't something else missing so I did a clean install.

---

### Post by Duncan Williams on 2011-05-15
If you update from previous version.
You will download probably 500 mb to update.
You may end up with errors.

So why not take the opportunity to:
Do a complete backup of all your important data. (preferably on a spare hard-drive or [_64gig usb stick_]("http://www.google.com/search?q=64%20gig%20usb"))

Download the latest distro of natty (minimal updates to have latest build) 

Install and set it up as you prefer it.

---

### Post by denisk on 2011-05-17
I have faced the strangest issue with natty this morning. After I had come to work and turned on my computer, it just didn't boot. Grub screen, selecting the most recent kernel, and that's it - a black screen. I have turned it off and on 4 or 5 times - the same thing. I then booted in recovery mode and went to command prompt. It has notified me that some updates are available - so I ran ```
sudo aptitude update
``````
sudo aptitude full-upgrade
```. After that I ran ```
sudo reboot
``` and the system started! However, the booting process is very slow now (I use ubuntu classic theme with no effects, Unity is still too buggy), but the system itself looks OK. I wonder, what it was? Are there any logs that can be investigated? :confused:

---

### Post by Robertjm on 2011-05-17
That's what I've ended up doing in the past. However, I remember peoples' comments when Meerkat came out that suggested the upgrade path had gotten pretty robust, with very little problems, so was considering it.

Robert

> **Duncan Williams said:**
> If you update from previous version.
You will download probably 500 mb to update.
You may end up with errors.

So why not take the opportunity to:
Do a complete backup of all your important data. (preferably on a spare hard-drive or [_64gig usb stick_]("http://www.google.com/search?q=64%20gig%20usb"))

Download the latest distro of natty (minimal updates to have latest build) 

Install and set it up as you prefer it.

---

### Post by AlanInVancouverBC on 2011-05-17
Yep. It froze on the desktop image (nothing, NOTHING, worked (mouse or keyboard). Re-installed w/o Nvidia and installed suggested driver and it froze. re-installed w/o Nvidia but couldn't use compiz. Tried nvidia driver again, desktop froze. Wiped drive and installed 10.10....No issues now!

---

### Post by NormanFLinux on 2011-05-18
Install Unity 2D. It runs fast even on devices that don't have accelerated graphics cards.

---

### Post by NormanFLinux on 2011-05-18
Do you have a Broadcom card? You have probably noticed the desktop works when you run Ethernet but it locks up when your wireless connection is active. 

You'll need to upgrade the kernel to fix the issue. 2.6.39.0 did it for me.

11.04 just runs fine now.

---

### Post by timgood on 2011-05-18
If you are running 64bit and experiencing distorted audio in Skype, there is a problem with ia32libs which can be simply fixed by:

```
cd /usr/lib32
sudo chmod ugo-r libpulse.so.0.12.2
sudo chmod ugo-r libpulse-simple.so.0.0.3 
```

Hope this helps.

---

### Post by oklinuxyo on 2011-05-18
if u hav problem with ati like lag you ned to get new widnow manager, compiz not work with ati now
also if your boot screen hang for 2-5min you need to:
```

sudo nano /etc/default/grub
```
and add acpi=off to the custom line that is empty (between "")
acpi=off means acpi disabled and no hibernate and cool and quiet function etc...

after that u ned:
```
sudo update-grub
```

---

### Post by jefelex on 2011-05-18
my bad - I replied in haste

> **hawthornso23 said:**
> I think it is worthwhile warning people that attempting to tweak the appearance of unity using the compiz config settings manager is not advised. I have had natty installed for less than 24 hours and have already completely and seriously destroyed my desktop four or five times simply trying to make minor tweaks to its appearance. 

What I thought I was getting was a desktop integrated with my favorite window manager - compiz. What I actually got was a desktop apparently constructed by cannibalising compiz to the extent that compiz as I understand it, in all its fully configurable glory,  is no longer functional.

Currently unity is a "take it or leave it" desktop environment. Almost nothing about it is configurable and efforts to tweak it are likely to break it. Some aspects of its design I really quite like and want to use. But if you are used to being able to customize your desktop environment then unity's rigidity and fragility is going to drive you nuts.

---

### Post by athenroy on 2011-05-18
I see a lot of posts about Nvidia video cards.  If you install "additional drivers" there are a lot of Nvidia drivers in that package that might help you out.  Personally, I find the Unity desktop too "left hand oriented" so I use the classic desktop.

---

### Post by tanken on 2011-05-19
When I connmect to a wireless lan and have to type in the password my computer totally freezes so I have to physically reboot it, and then it freezes when it starts up again.

It freezes using both installed and USB-version when I try to connect to a wireless lan.

I've got an Asus Eee 1001px.

Is this a known bug?

---

### Post by jejones3141 on 2011-05-20
> **timgood said:**
> Here are somethings I have found:
Edit: Oh, and I forgot. If you have Nvidia and no Plymouth following upgrade, this [script]("http://www.webalice.it/bernardi82/software/fixplymouth-natty") fixes it. Download it, make it executable by ```
chmod +x fixplymouth-natty
``` and then run it with ```
./fixplymouth-natty
```

After a reboot, Plymouth will return. Thanks for this one is due to Paolo Bernardi.

Tried this... after rebooting, I didn't see the Plymouth screens, and when I log in there are various and sundry colors that show up while the background and panel are setting up. No problem afterwards, but it wasn't what I was hoping for.

---

### Post by timgood on 2011-05-20
> **jejones3141 said:**
> Tried this... after rebooting, I didn't see the Plymouth screens, and when I log in there are various and sundry colors that show up while the background and panel are setting up. No problem afterwards, but it wasn't what I was hoping for.

Are you sure you selected the right resolution for your card and display? You need to input it *as shown* in the instructions. Let me know what res you are trying and how you are entering it.

---

### Post by killr0y on 2011-05-20
not quite sure if this was covered, 11.04 boots, i can login, but once in i have a mouse cursor, but nothing get highlighted when the mouse goes over it. i also have nothing on the top info bar.
thank you.

---

### Post by muctadir on 2011-05-22
I am having a major problem installing 11.04 on my desktop computer. I tried to install ubuntu several times and failed. While installing the installer says> Installation failed. The installer failed to install ubuntu input/output error errorno 5This happens at the stage of copying files. I tried ext4/ext3 but no luck. I googled it and saw several of bugs reported. But, i could not find any solution. It seems that not too many people are facing the problem.

Well my computer is having a 2GB ram, Core2Duo 2.66GHz processor and i am using bootable USB to boot and install 11.04. I ensured that it is 32bit.

Please, anyone help me. I am dying to install it on my pc.

---

### Post by Larkspur on 2011-05-22
I'd recommend remaking the LiveUSB from the .iso.  When I was using the Natty beta, the USB worked on the first computer I tried, but on others it wouldn't even start to load, reporting "boot error."  I thought maybe it was incompatible with them, but I tried remaking the LiveUSB and it worked.

---

### Post by 9000cse on 2011-05-22
Hi, I have had no problems. My system upgraded from V10 to V11 last night. Works fine.  APART from. I cannot receive mail and the Software center just keeps going. Star just keeps turning.
Help here would be great?
Cheers
Andy

---

### Post by PinUpGeek on 2011-05-22
Where is this "password and encryption keys" program or folder, it seems to be where I ened to go to solve a lot of my problems but I cannot locate it.

---

### Post by Larkspur on 2011-05-22
> **PinUpGeek said:**
> Where is this "password and encryption keys" program or folder, it seems to be where I ened to go to solve a lot of my problems but I cannot locate it.

If you're using Unity, hit the Super key and start typing "password".  If you're using Classic Gnome, go to the Preferences menu and it'll be there.

---

### Post by hawthornso23 on 2011-05-22
The zeitgeist-datahub process starts up as a zombie. It seems a second instance tries to start and fails because a first instance is already running. Attempting to kill or kill -9 the zombie doesn't work. The problem has apparently been fixed but the fix has not been backported to natty. 

A workaround to get rid of the zombie process is to run 

```
zeitgeist-daemon --replace &
```

This is my own workaround. Would appreciate confirmation that it works for other people.

---

### Post by imasynper on 2011-05-23
> **NormanFLinux said:**
> Do you have a Broadcom card? You have probably noticed the desktop works when you run Ethernet but it locks up when your wireless connection is active. 

You'll need to upgrade the kernel to fix the issue. 2.6.39.0 did it for me.

11.04 just runs fine now.

I have this exact issue, however updating the kernel didn't solve the problem. Is there anything else I can try?

---

### Post by scientist434 on 2011-05-23
I had a problem with the synaptic packet manager not recognizing my password. I would click the packet mannager then it would pop up the window to enter the password and it just kept saying wrong password. I solved the problem by switching to KDE desktop since I could still install things via terminal. 

Here is my post and what I tried to get it working in unity.

[http://ubuntuforums.org/showthread.php?t=1765999](http://ubuntuforums.org/showthread.php?t=1765999)

---

### Post by srinathduraisamy on 2011-05-24
Hi

After upgrading from ubuntu 10.10. to 11.04 my touch pad is not working in my Dell vostro 1510 laptop.

any help.

regards
srinath

---

### Post by sullivanjc on 2011-05-24
I've noticed an issue with the middle mouse button.  Clicking the middle mouse button on a link in firefox or chrome often opens multiple links.

Similarly, this happens on the launcher.  If I middle click a launcher with no open windows, I get one window.  If I middle click with a window already open, I get two new windows.

This is becoming somewhat annoying.

---

### Post by novinick on 2011-05-25
Hi, i can not search for right thread. Ubuntu 11.04 is making huge trouble for mycity  enthusiast that are trying to support ubuntu users.    It seems that dual boot systems of both windows and linux dual boot are completly erased , while partitioning (that means shipped natty 11.04 equals no data on disk)    I am a bit frustrated about this , can you pleas fix it asap ?   [http://www.mycity.rs/Linux/Ubuntu-11-04-problemi-posle-instalacije_4.html](http://www.mycity.rs/Linux/Ubuntu-11-04-problemi-posle-instalacije_4.html)   For example in this thread are 24 pages of trying to recover erased data (heroicaly-epic thread btw ). [http://www.mycity.rs/Linux/Hocu-LINUX-ali-se-zaglavih.html](http://www.mycity.rs/Linux/Hocu-LINUX-ali-se-zaglavih.html)

---

### Post by novinick on 2011-05-25
I would also like to point that  this behaviour was noticed in alpha 3 , do you have information about it ?    [http://askubuntu.com/questions/30791/all-files-erased-after-installing-ubuntu-11-04-alpha-3](http://askubuntu.com/questions/30791/all-files-erased-after-installing-ubuntu-11-04-alpha-3)   is this a bug or a feature.

---

### Post by fidamehran on 2011-05-25
> **dscott422 said:**
> 11.04 does not shutdown or restart.  Has something to do with Plymouth-upstart can't connect.  Any ideas?

No body helped this guy. I am having the same problem myself.

---

### Post by lance23dillon on 2011-05-25
> **denisk said:**
> I had a major issue during an updating from 10.10 (and from what I've red, I'm not the only one): my machine started to freeze during the startup. Many workarounds and suggestions were applied, but finally I had to re-install from iso.
I would also mention that I had to move to classic gnome (an option which appears on the bottom of login screen) because of the following issue - after some work title bars of window just disappear. Once again - no workaround unfortunately...:(

I had a similar problem and to fix it, go to the terminal and enter
unity --reset

and that should reset it.

---

### Post by katykat on 2011-05-26
> **klm3030 said:**
> This is the sorriest piece of untested garbage that Ubuntu has released yet. At the very least users should be warned not to install on machine with Nvidia graphics. What makes it even worse is there seems to be no one in charge of fixing it, just a bunch of try this, try that with the result of an even more messed up machine. I will be going back to 10.10 and looking for a new Linux OS.


I wount go near Natty. 
I have a barely supported legacy Nvidia card, and I wont change it since it works fine with the other two sysems (it triple bookts) . 


Stick with Meerkat - never hasd a problem with video,  wich had been a nightmare since Jaunty. 

Besides, As Ubuntu keeps forking away from traditional linux, will migrate more to Fedora , where at least you can run an real OS the way it was meant to. 


Unity??? NO!!!

Gnome has ALOT of development around it - and Open Source means not to have to reinvent the wheel at every turn...


I also hate upstart...

---

### Post by shakma on 2011-05-26
My Asus 1005HA (any many others' netbooks and notebooks) experienced severe video corruption upon returning from hibernate after the 11.04 upgrade.  This was true in both unity and "classic" gnome shells.  The work-around is to go to standby or sleep mode, then return.  The fix (as posted by Sgozz here: [http://ubuntuforums.org/showthread.php?p=10863597#post10863597](http://ubuntuforums.org/showthread.php?p=10863597#post10863597) in post #11) is to enable the "Proposed" updates in Synaptic then reboot.  This will download an updated kernel and xorg changes.

I also experienced VERY SLOW wake from standby, and the proposed repository cured this as well.

I like Unity well enough, but until they fix VGA out functionality, I'm back to Gnome 2.

Peace.

---

### Post by lieudusty on 2011-05-26
When the screen saver is activated when I move my mouse the computer gets frozen.:confused:

---

### Post by DAB4970 on 2011-05-27
Natty installed on HP Pavilion DV6835NR notebook.

When I "Safely Remove" usb hard drive, it auto remounts.  It also happened when I had Fedora 14 installed on same laptop.  I've looked for ways to disable this auto remount.  I haven't found anything that works yet.  When I use the "Safe Removal" button in the Disk Utility, it returns with an error message saying "The device is busy".  The device is a 1TB ext WD Passport 0730, according to this error message (not sure about the number 0730).

And I just now noticed when the hard drive is plugged in, the light is on full time.  With it plugged into my Lucid 64 bit desktop (and a previous install of Lucid 32 bit on laptop), it blinks on and off, like 1 second on and 1 second off.

---

### Post by fragos on 2011-05-27
After flushing the write buffers with "Safely Remove", "Eject" might work for you.

---

### Post by badbod on 2011-05-27
unrelated but a search did not provide any answers.

watching youtube videos fullscreen works fine, unless you try to interrupt them by pressing escape, ALT-TAB fails slightly less,  Letting them finish fails even less than that. White screen on exit or escape or ALT-TAB. 

It is a problem with the 64 bit flash , 

if stuck, try   CTRL-ALT-F12,  wait for flashing cursor,  then CTRL-ALT- F7  this should restore your screen though the browser will be hung for a minute or two, wait and it will free and you can repeat. 

Only experienced since the latest release of Adobe flash x86_64 plugin

Does not matter how long the vid's are as they will play perfectly until you try to exit. As above, usually they will exit on their own fine, but 'Escape' will reproduce 100%, ALT-TAB will reproduce after 3 minutes , Allowing to exit will reproduce 25% of the time.

Regards
BaDboD

---

### Post by rykel on 2011-05-28
Sorry I posted this in another thread before I saw this main one...

Hi, I installed Maverick alongside Windows 7. Then I upgraded Maverick to Natty, removed and reinstalled the latest kernel and ubuntu-desktop using Synaptic Package Manager. But now GRUB does NOT show any option to boot into Ubuntu Natty.

Please help me! Thank you.

**UPDATE - 30 May 2011**
I decided to format/reinstall Karmic, then upgraded through Update Manager back to Natty. STILL NO LUCK! Natty's GRUB is back to normal, but when I boot, I get a blank screen. When I tried to boot into Recovery Mode, my system went into an infinite loop. Based on this, I also believe that Natty's GRUB will again exhibit the same buggy problem. When will Natty be patched??

---

### Post by DinoT1985 on 2011-05-29
> **klm3030 said:**
> This is the sorriest piece of untested garbage that Ubuntu has released yet. At the very least users should be warned not to install on machine with Nvidia graphics. What makes it even worse is there seems to be no one in charge of fixing it, just a bunch of try this, try that with the result of an even more messed up machine. I will be going back to 10.10 and looking for a new Linux OS.

lol I'm sorry but I have an NVIDIA graphics card and this is the best OS Ubuntu has put out yet in my opinion. I actually had problems with 10.10 which made me use Windows 7 until Natty was released. Ubuntu actually called for testers regarding NVIDIA cards. If you didnt take part of the alphas or betas to help Canonical, which makes Ubuntu for free, that's their fault? 

The WHOLE point of Open Source is to be free and community made. That means WE help them build it better and give support, thus this forum.

---

### Post by yapxk on 2011-05-30
Hi All,

I'm unable to upgrade to Natty from ver 10.
It giving me this error
Failed to fetch 
[http://id.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.6-6ubuntu7_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.6-6ubuntu7_i386.deb) .

Is there any way to overcome this issue ?
Many Thanks

---

### Post by ugm6hr on 2011-05-30
AR2413 workaround:
[http://ubuntuforums.org/showpost.php?p=10760406&postcount=7](http://ubuntuforums.org/showpost.php?p=10760406&postcount=7)

Wifi drops intermittently. Solved as per post above.
```
sudo su
apt-get install subversion
cd /usr/src
svn checkout http://madwifi-project.org/svn/madwifi/trunk madwifi
tar cfvz madwifi.tgz 
cd madwifi
make && make install
 
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
echo "ath_pci" >> /etc/modules
 
modprobe ath_pci

sudo reboot
```

---

### Post by charliewhizbeez on 2011-05-31
I guess unity is fine but I don't like the new menu.  Having no categories annoys me.
Oh well, I just use classic.

---

### Post by Telumel on 2011-05-31
Alttempting to load xim (via the statement 'export  GTK_IM_MODULE="xim"' in .gnomerc) for its compose key settings caused a complete failure of the  compose key.

---

### Post by creuynni on 2011-06-03
i like the layout etc of unity, it didnt take me long to find everything i needed by just having an explore.

however i can't install any updates or software using the software centre, or the synaptic package manager of the terminal....the following happens :
 (Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'libgail-gnome-module': Input/output error 

Also, similar happens if I try use the computer janitor.
And the system test doesn't start at all.

I tried suggestion of sudo-apt autoclean etc, but didn't work either. with errors such as 'read only' locks etc.

I guess I'm going to have to reluctantly go back to 10.10 or before, as I am missing watching youtube, and listening to soundcloud tracks etc.

---

### Post by fragos on 2011-06-03
I suggest you try running Synaptic Package Manager, click the Edit menu and select "Fix Broken Packages". I'm not positive this will work but it's easy to try.

---

### Post by zyrorl on 2011-06-03
> **AlanInVancouverBC said:**
> Yep. It froze on the desktop image (nothing, NOTHING, worked (mouse or keyboard). Re-installed w/o Nvidia and installed suggested driver and it froze. re-installed w/o Nvidia but couldn't use compiz. Tried nvidia driver again, desktop froze. Wiped drive and installed 10.10....No issues now!

 Same here.tired clean install too. No fix. Even live cd is horrible. 10.10 live cd was a breeze. Na-ttytanic is a dud. Dead in the water.

---

### Post by zyrorl on 2011-06-03
> **DinoT1985 said:**
> lol I'm sorry but I have an NVIDIA graphics card and this is the best OS Ubuntu has put out yet in my opinion. I actually had problems with 10.10 which made me use Windows 7 until Natty was released. Ubuntu actually called for testers regarding NVIDIA cards. If you didnt take part of the alphas or betas to help Canonical, which makes Ubuntu for free, that's their fault? 

The WHOLE point of Open Source is to be free and community made. That means WE help them build it better and give support, thus this forum.

Clearly didn't do it's job. I'm using a nvidia 240M chip and it takes minutes to get to a login screen andj about 10 mins for unity or gnome classic to load. 2.8 ghz dual core CPU 4 gb ram . Not exactly a slow laptop.

---

### Post by Orographic on 2011-06-05
> **denisk said:**
> I had a major issue during an updating from 10.10 (and from what I've red, I'm not the only one): my machine started to freeze during the startup. Many workarounds and suggestions were applied, but finally I had to re-install from iso.
I would also mention that I had to move to classic gnome (an option which appears on the bottom of login screen) because of the following issue - after some work title bars of window just disappear. Once again - no workaround unfortunately...:(

Yes, Ubuntu 10.10 has worked flawlessly for me since day one but Natty is a bit problematic on this same system. I get a blank screen just before log-in whether I automatically log-in or log-in manually and whether I use Unity or Classic menu. It may happen once every ten boots or once every fifty boots, it seems random.

I thought it may have been a faulty disk or iso file, so I re-downloaded the iso from another server and did an MD5 check on it and also checked the disk for problems. All passed, no issues, but the blank screen on boot still occured. Its interesting as this issue didn't occur in Natty RC. 

With Xubuntu 11.04 and Mint 11 I've had no such problems although I am using Mint 11 RC with all updates so maybe Mint 11 final release also has this blank screen on boot issue as well? 

I have set my power button to turn off when pressed via the power settings in Natty and I can still use this option to shut-down relatively safely during a screen freeze on boot but its a pretty significant problem.

This is one of the real issues with Ubuntu, the same computer is not guaranteed to work with the next version of the distro. I have used Ubuntu for the last three years for 99.9% of my work but this is the first time were I've really had to seek alternatives. I think distro watch is showing this in the number of folks using other distros now as well. Ubuntu is sliding a bit.

I don't want to use Mint or Xubuntu but once Ubuntu 10.10 is no longer supported, I may have no option.

Edit: I should add that I have installed CCSM vis synaptic and reduced icon size in the launcher (they looked awfully big and toy like before) and also turned back-light off. Both of these settings were in 'experimental' tab, so is it possible that this change could have caused my blank screen at boot up?

My system is:

Intel core i3 first generation, Gigabyte H55 motherboard, 4G of RAM, on-chip GPU.

---

### Post by denisk on 2011-06-06
> **Orographic said:**
> 
I don't want to use Mint or Xubuntu but once Ubuntu 10.10 is no longer supported, I may have no option.


I use Lucid (10.04) on my laptop - and I get  updates regularly. For some reason, it never prompted me to upgrade, and I don't rush it. However, I can say for sure that Lucid starts much, much faster then Natty (I have Natty on more powerful laptop, and it is starts much slower)

---

### Post by donpaolo1 on 2011-06-06
Hi. Been using Ubuntu since 9.10. Had no issues whatsoever. It was super fast booting up, loading programs and such.

I bought a new laptop with Win7 pre-installed. I installed 11.04 (dual boot with win7). Win7 boots faster and outperforms 11.04. This has never happened to me before (i always dual boot my pc's with linux and windows) because 9.10 and 10.10 blew XP out of the water. 

11.04 boots a bit slower, programs load slow and are sluggish, and it freezes (froze on me while typing this actually). Banshee freezes when you choose to play all your music. What could be the problem? Is this because its fairly new and they haven't squashed the bugs yet? Im using a Samsung R439 right now. My old laptop was an Acer Aspire 4250g.

---

### Post by Orographic on 2011-06-06
Yes, I have three identical sata drives in my system and only have one drive plugged in at a time. Ubuntu 10.10 is my production drive and is very stable, W7 is on another drive for occasional tasks and is also very stable, then my third drive is a testing drive for other distros. 

On my testing drive, 11.04 with Unity or Classic Mode will produce these random boot freezes just before the log in screen. It generally runs well except for this random issue.

11.04 KDE also had this same boot freeze issue for me.

Mint 11 and Xubuntu 11.04 have been excellent though, without issue. Its confusing.

I'd encourage folk to check out Xubuntu, its improved a lot and you can set up the menu now as a side panel/launcher, quite like Unity. Its been very stable for me thus far:

[https://picasaweb.google.com/100456268555819903528/WhirlpoolImages?authkey=Gv1sRgCPjZqsekvcu08AE#slideshow/5615355543087954930](https://picasaweb.google.com/100456268555819903528/WhirlpoolImages?authkey=Gv1sRgCPjZqsekvcu08AE#slideshow/5615355543087954930)

---

### Post by wcks48 on 2011-06-07
[QUOTE=timgood;10772119]Here are somethings I have found:

1. To enable all applications to put an icon into the system tray you need to circumvent the whitelist of 'approved' applications. You can do this by opening a terminal and typing:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

and then logout and back in for the changes to take place. This will enable you to use things like Shutter or RadioTray.


This method not works well with my ubuntu 11.04. After reboot the system, when search the radiotray from the apps serach interface, after click, the radiotray not loaded still. any option to make it alive?

---

### Post by stinkeye on 2011-06-07
> **wcks48 said:**
> [QUOTE=timgood;10772119]Here are somethings I have found:

1. To enable all applications to put an icon into the system tray you need to circumvent the whitelist of 'approved' applications. You can do this by opening a terminal and typing:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

and then logout and back in for the changes to take place. This will enable you to use things like Shutter or RadioTray.


This method not works well with my ubuntu 11.04. After reboot the system, when search the radiotray from the apps serach interface, after click, the radiotray not loaded still. any option to make it alive?
You can set it back to default with...
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service']"
```

---

### Post by AlbaKirkee on 2011-06-08
Greetings:  I'm using Natty after having moved over from Ubuntu 8.4.  That older version of Ubuntu had a button in the panel that you could use to minimize all current, open windows.  What happened to that button in 11.04?

Newbie............................

---

### Post by tlq123 on 2011-06-08
thanks for sharing.

---

### Post by stinkeye on 2011-06-08
> **AlbaKirkee said:**
> Greetings:  I'm using Natty after having moved over from Ubuntu 8.4.  That older version of Ubuntu had a button in the panel that you could use to minimize all current, open windows.  What happened to that button in 11.04?

Newbie............................

You can just use Super+d or if you prefer using the mouse you need to create a launcher.

This launcher uses wmctrl to toggle showing the desktop.

Install wmctrl
```
sudo apt-get install wmctrl
```

Copy and paste this in gedit and
then save in **~/.local/share/applications** (hidden folder in your home directory ...ctrl+h to show hidden)
as **showdesktop.desktop**
[COLOR="#ff0000"]Before saving change to your username.[/COLOR]
```
[Desktop Entry]
Name=Toggle Desktop
Exec=/home/[COLOR="Red"]glen[/COLOR]/scripts/wmctrldesktoggle
Icon=desktop
Terminal=false
Type=Application
StartupNotify=false

X-Ayatana-Desktop-Shortcuts=Show Desktop;Show Windows

[Show Desktop Shortcut Group]
 Name=Show Desktop
 Exec=wmctrl -k on
 TargetEnvironment=Unity

[Show Windows Shortcut Group]
 Name=Show Windows
 Exec=wmctrl -k off
 TargetEnvironment=Unity
```


Save this as **wmctrldesktoggle** in **~/scripts**
Create the scripts folder if you don't have one.
```
#!/bin/bash

STATUS=$(wmctrl -m | grep desktop | awk '{print $7}')

if [ "$STATUS" == "OFF" ]; then
	wmctrl -k on
else
	wmctrl -k off

fi
```
Right click on wmctrldesktoggle 
properties > permissions and tick **Allow executing**


Now go to **~/.local/share/applications** and drag the showdesktop.desktop file to the launcher.

Unity launchers have a quirk where you can't left click on them again for about 10 seconds.
During this time though middle clicking works.
This launcher also has a a right click menu for **show desktop** and **show windows**

---

### Post by mkstallings1 on 2011-06-08
Just thought I'd add my two cents.  I tried to do a clean install of 11.04 and, no matter what I tried, I couldn't get wireless to work.  So, I restored a backup of 10.10 and had it upgrade to 11.04. Now everything works just fine.  I have a HP dv8000 laptop with the Broadcom BCM4318 wireless card.  I actually kind of like Unity, but wish it was more customizable.  As a side note, I tried Linux Mint 11 and wireless wouldn't work with it either.  I'm wondering if it is because of the kernel they are both based on.

---

### Post by CJ_Hudson on 2011-06-09
Please, does anyone know where my bookmarks in Firefox have gone?!
These slick new browsers may be a great minimalistic "concept" but where is my missing functionality?!

Also, I cannot fathom out the toolbar down the left hand side. It seems to appear and disappear with a mind of its own.

EDIT:
...and another thing, I find the new style scrollbars a bit fiddly to use. I am not the world's most accurate mouse-pointer!

I can see this taking wee while to get used to, but I think overall 11.04 is an improvement over 10.10.

Any hints and tips gratefully received.:D

EDIT 2:
I have now installed 11.04 on 2 computers, a laptop and a desktop, one for my boss's kid who is 16 to do his schoolwork on! I hope he likes it. I am also thinking of installing something Ubuntu-ey on my aged netbook which is dead slow running XP at the mo. and has 2 GB RAM and a 900 MHz processor. Please can anyone suggest anything?

---

### Post by LarryNG on 2011-06-09
I posted a longer version in a different thread but I wanted to mention the black screen problem and one possible solution here as well.

I installed Ubuntu 11.04 on two older PCs, a P3 and P4 that previously worked well with XP. Both machines had a black screen shortly after Ubuntu began its boot. Puppy worked well, and AntiX almost got it right, but Ubuntu refused to cooperate.

I was experiencing black screens, inability to set resolutions (when Ubuntu did finally boot with a modern AGP card), inability to retain resolutions after rebooting, and a mess of other funky stuff that appeared to point to the AGP video cards.

After some hours of installing other distros, video cards, drivers, etc., I realized that the problem was the old HP Pavilion M90 monitor not being recognized. I switched to a small and equally old 15" CRT and now Ubuntu runs marvelously. 

The next time I run up against a similar problem I will know to use one of my LCD monitors for testing.

---

### Post by thenudehamster on 2011-06-11
> **mkstallings1 said:**
> Just thought I'd add my two cents.  I tried to do a clean install of 11.04 and, no matter what I tried, I couldn't get wireless to work.  So, I restored a backup of 10.10 and had it upgrade to 11.04. Now everything works just fine.  I have a HP dv8000 laptop with the Broadcom BCM4318 wireless card.  I actually kind of like Unity, but wish it was more customizable.  As a side note, I tried Linux Mint 11 and wireless wouldn't work with it either.  I'm wondering if it is because of the kernel they are both based on.
I too have an hp Pavilion (dv9646em) laptop with a Broadcomm card, and mine works perfectly. There was an option when I ran my first liveCD tryout of 11.04 to upgrade third party drivers; taking this option loaded  a Broadcomm driver (along with one from nVidia to enable me to run Unity) which seems to work perfectly. I suspect that the upgrade operation installs the Broadcomm driver rather than the generic Ubuntu one installed from the install ISO. You'll need to check the settings on the Upgrade Manager to see if it is set to install third party drivers, that'll give you a hint. 

For other suffering a similar problem on a clean install of 11.04, I suggest trying this:
Go your your System Settings panel (click on the 'on/off swich' on the right of the taskbar, choose System Settings from the drop down menu) and choose Additional Drivers; this will search for whichever third party drivers may be needed to help your system run properly under Unity (among other things). When it displays a list of drivers, select the Broadcomm one and Install. Then it should all work nicely.

Of course, if you've already done this and it doesn't, you may need to do some investigation at Broadcomm..

---

### Post by dver on 2011-06-12
I use dell studio 1555 laptop. the screen resolution used to be 1366x768 initially. for some time after booting it automatically adjusts to 1024x768. and after a couple of re-start becomes 1366 x 768. 

the screen flickers also some times - meaning goes to blank and quickly comes back

what could be the problem - some bug or what

---

### Post by DinoT1985 on 2011-06-13
> **dver said:**
> I use dell studio 1555 laptop. the screen resolution used to be 1366x768 initially. for some time after booting it automatically adjusts to 1024x768. and after a couple of re-start becomes 1366 x 768. 

the screen flickers also some times - meaning goes to blank and quickly comes back

what could be the problem - some bug or what
sounds like your xorg file needs correcting. flickering is a low refresh rate. i'm a noob when it comes to xorg sorry but i know thats what it can do as i had to edit mine to force 1440x900 on startup. it was booting in low res.

---

### Post by Telumel on 2011-06-14
> **MogBug said:**
> Please, does anyone know where my bookmarks in Firefox have gone?!
These slick new browsers may be a great minimalistic "concept" but where is my missing functionality?!
The F10 key will restore the file menu, and you should be able to find your bookmarks from there.  The book icon does the same thing, while taking up a bit less room.

---

### Post by FALL3N on 2011-06-15
I am using an Apple Keyboard with Natty... I tried to set the keyboard Layout to 'U.S.A. Apple' but that didn't do anything... I also tried to remap the keys manually via xev and xmodmap.. it didn't work, I think I did it wrong... anyone else know of a way to remap the keys?

I am trying to get the Apple Command Keys to take the place of the Control keys in Ubuntu...
ie:
right now, control + 't' opens a new tab in firefox, but I want it to be Command (apple) + 't'

---

### Post by CJ_Hudson on 2011-06-15
1. > **Telumel said:**
> The F10 key will restore the file menu, and you should be able to find your bookmarks from there.  The book icon does the same thing, while taking up a bit less room.

Thanks. And now I have used it a bit more I understand how the side bar thingy works.

2. I too have an Apple keyboard, but have never used the 'Apple' symbol. I just selected 'Apple keyboard' and 'UK Layout' when I installed Natty. Sorry but I can't understand why someone would want to reprogram the 'Apple' key as the 'Control' key, if I understand you correctly. Personally I have trouble with the "|" symbol (used for some terminal-window commands) which on my keyboard is on a key marked with something totally different.
*C'est la vie*, as the French say!

---

### Post by huminflame on 2011-06-16
I am having a problem trying to login. After I installed from a live disk (written at 4x speed) it wont let me login. It keeps flickering the screen. Any idea what that is from. Im using an IMB desktop model 8310. Thnx

---

### Post by TheManno1 on 2011-06-18
I have been having issues with the internet speed ever since I got netgear 300.linux natty 64 bit

---

### Post by gregzeng on 2011-06-21
> **cariboo907 said:**
> As with every release we open a thread about how our members have solved problems with Natty (11.04).

I personally haven't had any problems since the release, but I found a link to  [Things to tweak and fix after installing Natty (11.04) at webup8]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html")

**Unity not your cup of tea ?**

[color=blue]**Solution:** Try K/X/Lubuntu. If you prefer a light weight alternate, try Fluxbox, openbox, pekwm, awesome, xmonad, or any of the alternate window managers.[/color]

Seems that you are not using the Intel I3 CPU, with on core GPU.

AFTER MANY STUPIDLY TEDIOUS & WASTED hours with "Upgrade" from 10.10, I reluctantly tried the upgrade, inside 10.10 Ubuntu.  "Safe Mode" told me that this crazy upgrade cannot work with my latest Intel CPU.  More stuffing around, removing Unity.  Luckily it returned my 10.10 settings ... EXCEPT ...

Normally I do my academic work on my PORTRAIT-MODE 24 inch LED-LCD screen.  All my hardcopy is portrait mode.  Serious work with text is rarely in landscape mode.  Now I need to read many forums & posts in the hours & days ahead, to male this silly unfriendly Linux operating system more that a child's play toy.

Android is much more user friendly than silly Linux.  The most arrogant Linux version I've tried is PC-LINIX.   Ubuntu is like Windows XP, experimenting towards Windows ME.  So user hostile.  I will not ever recommend Linux to anyone, except for debugging Window crashes.

---

### Post by gregzeng on 2011-06-21
> **denisk said:**
> I had a major issue during an updating from 10.10 (and from what I've red, I'm not the only one): my machine started to freeze during the startup. Many workarounds and suggestions were applied, but finally I had to re-install from iso.
I would also mention that I had to move to classic gnome (an option which appears on the bottom of login screen) because of the following issue - after some work title bars of window just disappear. Once again - no workaround unfortunately...:(
  Same here in Australia.

Ubuntu & Canonical are guilty of FRAUD.  I was happy with my 10.10 setup.  "Upgrading" as their idiot operating system told me, was my worst computer disaster ever in the last 40 years.  After many silly, wasted days, I solved it by removing Unity & Compiz.  My hardware is a new notebook commputer, running the latest Intel I3 CPU, with onboard Intel GPU.

Natty "upgrade" in safe mode, gives the message that it will not work work with this Intel CPU-GPU combination.  Most operating systems have the intelligence to not install silly rubbish.  Canonical & Ubuntu are as silly as the alphaware that they falsely label as user-ready.

Since they are legally sue-able, we should launch a class action against them for faulty advertising & faulty goods.

---

### Post by stinkeye on 2011-06-21
> **gregzeng said:**
> Same here in Australia.

Ubuntu & Canonical are guilty of FRAUD.  I was happy with my 10.10 setup.  "Upgrading" as their idiot operating system told me, was my worst computer disaster ever in the last 40 years.  After many silly, wasted days, I solved it by removing Unity & Compiz.  My hardware is a new notebook commputer, running the latest Intel I3 CPU, with onboard Intel GPU.

Natty "upgrade" in safe mode, gives the message that it will not work work with this Intel CPU-GPU combination.  Most operating systems have the intelligence to not install silly rubbish.  Canonical & Ubuntu are as silly as the alphaware that they falsely label as user-ready.

Since they are legally sue-able, we should launch a class action against them for faulty advertising & faulty goods.
Out of curiosity I read some of your previous posts which are equally
negative about Linux and pro Windows.
Why are you even here?
Just buy windows and be done with it.

I also noticed in your older posts you had a sig...
> Retired (medical) IT Consultant
 Australian Capital Territory.
IT consultant to who ....your grandmother?
PS. I doubt your Australian also.

---

### Post by 1992kris on 2011-06-21
Before Ubuntu 11.04 I was using Lubuntu 11.04 and used to download movies to watch and it worked beautifully! After a slight RAM upgrade I decided to go for Ubuntu and use Unity 2D as my hardware is too old for the standard Unity version. However I can no longer watch films at all fullscreen or not, the screen blacks out and I have to close VLC.

---

### Post by alphaamanitin on 2011-06-22
I have horrible graphical errors rendering the install worthless.  [COLOR=Red]**IMPORTANT NOTE, I USE UEFI!!!**[/COLOR]

Anyway, had the graphics errors while trying to boot from USB, about 1 out of 5 boots would work correctly.  Got it installed, no errors, rebooted and the screen is messed up, cannot see anything except a bit of the Ubuntu log in back ground at the very top of the screen, maybe a cm of screen.  It is flashing gray and white, and generally messed up.  No idea what to do.  Thinking of switching to Archlinux but would like to stay with Ubuntu.  Any ideas guys?  

Setup:

ASRock 880G Pro3 MOBO
128gb Crucial SSD III running Windows 7 x64
64gb Crucial SSD III running (or trying to run) Ubuntu 11.04 AMD64
2 TB Seagate SATA III
AMD Radeon HD 6850 Asus brand
16 gb (4gbx4) Critical 1333 mHz Ram
AMD Phenom II x6 1100T (3.3ghz 6 cores)
Corsair TX750 750 W PSU

I need this machine soon.  I use it for phylogenetic work in my Biology PhD program, and lots of these programs and scripting languages are best on linux machines.  I know they work on Ubuntu, never tested or read anything about Archlinux.

Id

---

### Post by srs5694 on 2011-06-22
> **alphaamanitin said:**
> I have horrible graphical errors rendering the install worthless.  [COLOR=Red]**IMPORTANT NOTE, I USE UEFI!!!**[/COLOR]

Anyway, had the graphics errors while trying to boot from USB

I *strongly* recommend that you start your own thread to resolve this problem. Although it probably is a bug in Natty (or one of its components), it's specific enough that it really requires its own thread, with a descriptive title such as "Unviewable display on installation."

That said, I recommend you see if you can get a text-mode session by hitting Ctrl+Alt+F1 or by using a recovery boot mode. If you can do that, you'll at least be able to debug the problem from a regular boot rather than from a recovery disc's boot.

---

### Post by alphaamanitin on 2011-06-22
Yeah, I was will make a thread tomorrow probably.  I just smacked it up here because I am sure it is a bug with the UEFI booting, and I know they have had problems with UEFI and 11.04 and graphical errors.  Like the fact that it boots best from a USB no a CD.  Boots fine in BIOS legacy mode, but to boot both Windows 7 and Ubuntu without having to unplug hard drives they either both need to be in UEFI or both in BIOS.  My Windows is in UEFI and I don't want to reinstall it again.

AlphaA

---

### Post by Windwoodtrader on 2011-06-22
> **denisk said:**
> I had a major issue during an updating from 10.10 (and from what I've red, I'm not the only one): my machine started to freeze during the startup. Many workarounds and suggestions were applied, but finally I had to re-install from iso.
I would also mention that I had to move to classic gnome (an option which appears on the bottom of login screen) because of the following issue - after some work title bars of window just disappear. Once again - no workaround unfortunately...:(

I had a similar issue and the same outcome. I re-loaded 9 times altogether- First two as sharing Windows Vista and the other seven just getting to work alone after I cleaned out the HD. At first could not even get a terminal. Everything worked in Unity until I did a re-boot then freeze-up requiring hard kill.

The cause was because Unity is fussy over hardware and got stuck. I did not pick Unity the loader did so I'm surprised about that it didn't work but now I have a working 11.04 without Unity.
I'm happy.
WindwoodTrader

:D

---

### Post by Hex99 on 2011-06-23
I was running Natty as is out of the box without problems, then today I awoke to a completely different title bar (it looks like some throwback to windows 95 !!!) and I went through all the themes options etc but there is no changing it.
All the menus of things like when you right click and get the copy/paste menus also look different. I have no idea how or why this happened and if it was an automated "update" by Ubuntu then it sucks that they didn't ask.

or maybe I have been hacked by someone with poor taste...i really do not know...I am a Ubuntu newb. but PLEASE can someone tell me how to get my original title bar from Unity back please, pretty please?

Thank you.

---

### Post by shadowninty on 2011-06-23
I find a lot of bugs when using image editing (I can move the cursor but not do anything o.0) and a few Unity bugs. Better than WIndows 7 !

---

### Post by bnjmnlrd on 2011-06-23
10.10 Naty is love.....that is all....

---

### Post by shadowninty on 2011-06-23
> **bnjmnlrd said:**
> 10.10 Naty is love.....that is all....

Natty Narwhal is 11.04 8)

---

### Post by sneakyimp on 2011-06-24
I have assembled a computer which should be blazing fast and Natty 64-bit just isn't working for me:
*[Gigabyte 880GM-USB3 Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128440)
* [AMD Phenom II X6 1100T 3.3Ghz](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103913)
* [8GB of G. SKILL ripjaws DDR3 running at 1600Mhz](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231314)

I'm using the built-in video (ATI Radeon HD 4250).

Problems:
* Takes 4 mins 15 seconds from POST screen to login prompt when booting or rebooting.
* System hangs on shutdown or reboot, requiring me to force shutdown by holding power button.
* Unity Interface is sluggish
* Unable to add Eclipse to my dashboard and change the icon to the one included with the Eclipse download

I have faith in Ubuntu and expect they'll be able to get things moving, but the 4+ minute boot time and hang on shutdown problems are just too much.  I'll be moving back to 10.10 in the meantime.

---

### Post by slooksterpsv on 2011-06-24
> **sneakyimp said:**
> I have assembled a computer which should be blazing fast and Natty 64-bit just isn't working for me:
*[Gigabyte 880GM-USB3 Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128440)
* [AMD Phenom II X6 1100T 3.3Ghz](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103913)
* [8GB of G. SKILL ripjaws DDR3 running at 1600Mhz](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231314)

I'm using the built-in video (ATI Radeon HD 4250).

Problems:
* Takes 4 mins 15 seconds from POST screen to login prompt when booting or rebooting.
* System hangs on shutdown or reboot, requiring me to force shutdown by holding power button.
* Unity Interface is sluggish
* Unable to add Eclipse to my dashboard and change the icon to the one included with the Eclipse download

I have faith in Ubuntu and expect they'll be able to get things moving, but the 4+ minute boot time and hang on shutdown problems are just too much.  I'll be moving back to 10.10 in the meantime.

Have you done a memory test? Sounds like you may have bad memory in the system. I'd do a check on it, if that's all good, create a new thread.

---

### Post by srs5694 on 2011-06-25
> **sneakyimp said:**
> I have assembled a computer which should be blazing fast and Natty 64-bit just isn't working for me:
*[Gigabyte 880GM-USB3 Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128440")
* [AMD Phenom II X6 1100T 3.3Ghz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103913")
* [8GB of G. SKILL ripjaws DDR3 running at 1600Mhz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231314")

I'm using the built-in video (ATI Radeon HD 4250).

Problems:
* Takes 4 mins 15 seconds from POST screen to login prompt when booting or rebooting.
* System hangs on shutdown or reboot, requiring me to force shutdown by holding power button.

According to its manual, that motherboard includes (U)EFI support. This presents both problems and opportunities. It's conceivable that at least some of your problems are related to UEFI, and can be overcome through UEFI-specific means. As this thread is huge and seems to be a general dumping ground for bugs in 11.04 rather than a trouble-shooting thread, I *strongly* recommend that you begin a new thread for your specific problems. To get you started, though, I recommend you edit your boot loader configuration to make the following changes:


[list]
[*]Edit your kernel boot option to remove the "quiet" and "splash" options. This should enable you to see the ugly but informative text-mode boot messages that are very helpful. This may give you a clue about why the computer is taking so long to boot -- for instance, you might see a line that reads "waiting for foo device to come online," and that might repeat half a dozen times over a period of three minutes before going on.
[*]Add the option "reboot=a,w" to the kernel options. This changes the way the computer reboots. It might fix the kernel panic on reboot problem, although it's not likely to fix the kernel panic on shutdown problem. See [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/721576) for information on this known bug.
[/list]


You can make these changes on a test basis by selecting your kernel entry and then pressing the "E" key to edit your entry. (There are on-screen prompts showing details for how to edit things and boot from there.) Changes made in this way are non-permanent (they apply to just one boot), so there's no risk of hosing your system in this way.

Incidentally, you can learn if you're booting in EFI mode by typing the following command soon after booting:

```

$ **dmesg | grep EFI**
[    0.000000] Command line: BOOT_IMAGE=atapi0:\EFI\ELILO\bzImage-2.6.39 root=/dev/seeker/u1104  reboot=a,w ro
[    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000048000) (0MB)

```

On an EFI-booted system, the output will go on quite a way showing memory details, then it concludes with a few lines about the EFI framebuffer device. On a non-EFI system, you'll see few or no lines of output from that command, and any that are present will be coincidental matches -- some other word that contains the string "EFI".

---

### Post by shadowninty on 2011-06-25
> **Hex99 said:**
> I was running Natty as is out of the box without problems, then today I awoke to a completely different title bar (it looks like some throwback to windows 95 !!!) and I went through all the themes options etc but there is no changing it. 
 
All the menus of things like when you right click and get the copy/paste menus also look different. I have no idea how or why this happened and if it was an automated "update" by Ubuntu then it sucks that they didn't ask. 
 
 
 
or maybe I have been hacked by someone with poor taste...i really do not know...I am a Ubuntu newb. but PLEASE can someone tell me how to get my original title bar from Unity back please, pretty please? 
 
 
 
Thank you. 
That happened to another User account I made on Natty. Best start a thread :L

---

### Post by arno48 on 2011-06-26
If I leave my computer alone for half an hour, when I come back the screensaver is steady.
*The mouse moves on it  but neither clicks nor keyboard have effected.*
*I am obliged to shutdown and to  reboot.*

---

### Post by arno48 on 2011-06-26
When I boot my Natty I have to type several  times (2 or 4 times) my password.
As none else  uses  my computer I would prefer to access directly, without any typing password.

---

### Post by arno48 on 2011-06-26
[B][FONT=Georgia]Sometimes the Launcher Bar pops out and does not return back, hiding bookmarks.
The only way is to shutdown Firefox[/FONT][/B]

---

### Post by maxe on 2011-06-28
> If I leave my computer alone for half an hour, when I come back the screensaver is steady. The mouse moves on it but neither clicks nor keyboard have effected. I am obliged to shutdown and to reboot.

I have this exact same problem. The screen turns into nothing but a white display with the mouse cursor. You can move it and click or type but nothing happens. It's like the whole system vanished and all you have is a mouse cursor. I have to reboot again. What could be causing this?

---

### Post by sirkeith on 2011-06-29
> **Hex99 said:**
> I was running Natty as is out of the box without problems, then today I awoke to a completely different title bar (it looks like some throwback to windows 95 !!!) and I went through all the themes options etc but there is no changing it.
All the menus of things like when you right click and get the copy/paste menus also look different. I have no idea how or why this happened and if it was an automated "update" by Ubuntu then it sucks that they didn't ask.

or maybe I have been hacked by someone with poor taste...i really do not know...I am a Ubuntu newb. but PLEASE can someone tell me how to get my original title bar from Unity back please, pretty please?

Thank you.

I have the same deal sorta. Every few days Natty starts with an awesome theme, not the one I have installed. It lasted for 2 days once but most often it is gone on a reboot. This theme is nowhere to be found on my machine, at least for me, but I would love to run it.

---

### Post by saleki on 2011-06-30
I installed ubuntu 11.04 with wubi on my laptop. Everything went fine and I like it a lot :) I'm new in this kind of os, but I find it quite user friendly and easy for beginners. Using it for a week now and I have only one issue.

Sometimes when I shut down or restart through options from panel I got some pretty strange zippy shutting sound like the one when laptop freeze and you're force shutting it down... But when I go with power button, I got options to choose and shutting down or restart with this method gives nice quiet shut down.

I'm on MSI EX610X-U91EU with AMD Athlon64 X2 Dual-Core and ATI Mobility Radeon 2400
using ubuntu 11.04 64-bit

---

### Post by trungvkvk on 2011-07-02
I want to install ubuntu. I asked to install ubuntu but easy to use as the other operating system.

---

### Post by tomaasj on 2011-07-02
> **maxe said:**
> I have this exact same problem. The screen turns into nothing but a white display with the mouse cursor. You can move it and click or type but nothing happens. It's like the whole system vanished and all you have is a mouse cursor. I have to reboot again. What could be causing this?
same problem here,

Inspiron 6400

if solution please report,

Thanx,

T

---

### Post by elianto on 2011-07-02
[SIZE=4]**If your disk start behaving crazy on kde startup**[/SIZE]
and never ends doing who knows what eating all the memory slowing the interface and bringing your computer to knees [COLOR=Red]no worries[/COLOR] it's **[SIZE=2]akonadi[/SIZE]**.
I have this bug since 10.4 and I think it's triggered when, for some rare circumstance, (read every 6 month for some ATI problems) kde got killed in the middle.
The workaround I found it's pretty [COLOR=Magenta]painless[/COLOR][COLOR=Black] : before login switch to a terminal (ctrl+alt+f1) login, rm -rf .config/akonadi[/COLOR] then login as normal (ctrl+alt+f7)
I wonder why this bug it's still here!

---

### Post by goldshirt9 on 2011-07-02
the only problem i have and cannot seem to be rid of is on start up
from laptop turn on i loose about 20 seconds to a black screen before i enter my password
and post password another 10 seconds to the Ubuntu wallpaper  before my desktop starts.

---

### Post by Redsoul90 on 2011-07-04
one thing ive noticed is the abi keyboard not switching back and forth like it should. 

ill click japanese and it stays on english then when i finally get it to change it wont go back.

---

### Post by Demon1986 on 2011-07-08
how can i sort ubuntu out so that downloaded archives dont go read-only when i want to open them, its annoying either when its just a temporary place, or in my dl folder, they are read only, and require admin to extract, seemed to have begun after i upgraded to natty

/Demon

---

### Post by brunobliss on 2011-07-10
**DosBox:**

Running Fullscreen mode and back will freeze with Ubuntu 11.04

**Wireless:**

Connecting to SMC or non protected Wireless Networks (one or the other, maybe both?) will clog the system untill it freezes completely

---

### Post by ascendancyelf on 2011-07-10
Hey all, only problem I've been experiencing so far since my new 11.04 installation is that my laptop doesn't seem to recognize USB Flash Drives or External/Portable hard-disks. Is there a work around for this? any help would be appreciated, thanks in advance. :)

~ ascendancyelf

---

### Post by trungvkvk on 2011-07-11
I had a major issue during an updating from 10.10  my machine started to freeze during the  startup. Many workarounds and suggestions were applied, but finally I  had to re-install from iso.

---

### Post by trungvkvk on 2011-07-12
sorry. but do not know why I post here on the next day I did not see all.
 thanks.
 themselves as new members.
  Please help yourself to use Ubuntu
 [http://ubuntuforums.org/showthread.php?p=11004029](http://ubuntuforums.org/showthread.php?p=11004029)

---

### Post by shashanksingh on 2011-07-14
[http://ubuntuforums.org/showthread.php?t=1802878](http://ubuntuforums.org/showthread.php?t=1802878)

---

### Post by norm.h on 2011-07-18
I'm not sure if these are bugs, but don't know where else to post.

Having successfully upgraded my 32bit, custom built desktop from Ubuntu 10.10 to 11.04, I decided to do the same on the 64bit laptop.

My first attempt was via Update Manager, which didn't install the Unity desktop, the pointer kept sticking, and the wifi connection kept dropping out, which made me suspect a driver issue.
Each time I rebooted, the desktop icons were in different positions.
The on-board video is ATI Radeon X1200 with 3D/2D graphic accelerator.

I then tried a clean install using a cover CD, which although it installed the Unity desktop, I still had a sticking pointer and the dropping wifi connection, so I then decided to return to 10.10.

All is now well on the laptop, but the desktop, which until last night was also OK, is now slow to the point of being inoperable.
Takes an age to even load the desktop,and trying to run anything takes at least 10 minutes. To shut down I had to power off at the mains switch, (not a good idea I know, but was the only way)

Will have to go back to 10.10 which is a shame because I quite liked Natty.

---

### Post by dilidon on 2011-07-25
> **FALL3N said:**
>  I also tried to remap the keys manually via xev and xmodmap.. it didn't work, I think I did it wrong... anyone else know of a way to remap the keys?

I was struggling with Natty failing to load ~/.Xmodmap (fresh 11.04 install, but still no go). I've experienced this before but now I found a solution suggesting a little edit in gconf via this thread:

[http://superuser.com/questions/185345/why-wont-my-xmodmap-command-run-on-startup-login]("http://superuser.com/questions/185345/why-wont-my-xmodmap-command-run-on-startup-login")

Solution was offered by someone called Alan and confirmed and reexplained jt512: "In order for your ~/.Xmodmap file to have an effect, ".Xmodmap" has to appear in both the "known_file_list" and the "update_handlers" list under  /desktop/gnome/peripherals/keyboard/general in gconf-editor."

If it is unclear, take a look at that link and scroll to the very end.

---

### Post by thunderbirdje on 2011-07-28
> **ascendancyelf said:**
> Hey all, only problem I've been experiencing so far since my new 11.04 installation is that my laptop doesn't seem to recognize USB Flash Drives or External/Portable hard-disks. Is there a work around for this? any help would be appreciated, thanks in advance. :)

~ ascendancyelf

Same here! Don't know if it's a bug. I can however mount them with the command 'mount' manually. However, that's taking so much time!

---

### Post by Swordspirit2 on 2011-07-28
Guys, sorry to interrupt... But I really need some help with this.

Been needing this help all day actually.
I don't know what else to do.

[http://ubuntuforums.org/showthread.php?t=1813763](http://ubuntuforums.org/showthread.php?t=1813763)

---

### Post by trungvkvk on 2011-08-01
What a good idea :popcorn: Nice

---

### Post by Nightcrawlers on 2011-08-17
I tried 11.04 and had issues....but....I really want to try it again (32 bit?), on my laptop (HP Pavilion G6, ATI graphics and AMD 64 cpu, 4 gig DDR3 ram).  If I upgrade my 10.10 install to 11.04, do I lose my folders, music and other stuff that I have right now?  Either way, I am itchin to give 11.04 another try on this here laptop.  Waitin for your advice, Thanks!

---

### Post by Demon1986 on 2011-08-17
if you just do an upgrade from the update thingy, all your stuff will be there when its done, ive upgraded mine since 7.04, and its been in several machines since then, still running fine, with a few minor issues

---

### Post by Nightcrawlers on 2011-08-17
Ok thanks!. I will be starting the upgrade now.  :)  Let's see how this goes!

---

### Post by Nightcrawlers on 2011-08-17
I have completed the upgrade to Natty 11.04 and so far......so good!  I am hoping that I do not run into any of the issues that some have.....anyway, back to checking it out!

---

### Post by CrusaderAD on 2011-08-19
Anyone seen the bug where the top window bar disappears. Re-sizing it fixes the issue at the time, but this pops up every once in a while.

---

### Post by vikash_chandola on 2011-08-21
(1) shut down bug it does not shut down by itself i need to press CPU button to close it.
(2) sound controller bug. If i increase sound to full then unmanaged sound comes from my speaker it is really too..... loud , even can burst speaker. This problem is only in case of ubntu not in case of other OS i have tried.
if anybody know the solution of shut down bug then send message to me. Does it hampering mu computer?

---

### Post by vanjadjurdjevic on 2011-08-22
I noticed that mouse cursor doesn't disappear anymore when playing video using flash and then using fullscreen.

---

### Post by Nightcrawlers on 2011-08-22
On my HP Pavilion G6 laptop, Natty rocks, no problems except perhaps from time to time I lose mouse control on the desktop.  I have not determined whether or not this is due to my hitting a function key (?) or combination of special keys (?) by accident or if this is a bug that has already been mentioned somewhere here.  All in all I like Natty, and although I opted for the classic desktop, I am happy with it on this machine.

I also tried to upgrade an older machine I have, an IBM ThinkCentre 8189 (now) running 1 gig of ram, and it did not seem to like Natty at all.  In fairness, I found that 1 gig of the original 2 gig that I had put in during the first upgrade attempt, were bad.  I would like to and may try natty on this older archive machine again after getting some opinions from you all.  Should it be able to handle natty with only 1 gig installed or what?  At the moment I am running this box with 10.10 Maverick (as before) and it seems to like it.  On the other hand, I kinda suspect that the 1 gig of bad ram that I took out, most likely  explains the strange effects I observed during what turned out to be a really whack failed upgrade.  Opinions welcomed, thanks in advance! :popcorn:

---

### Post by JazzPotato on 2011-08-23
I don't know if this helps but...

I'm on a laptop. When opening the laptop lid after it going to sleep, i can use the system as normal for about 2 minutes. It then unavoidably crashes and i must reboot.

You asked for known bugs :-)

---

### Post by Nightcrawlers on 2011-08-23
> **JazzPotato said:**
> I don't know if this helps but...

I'm on a laptop. When opening the laptop lid after it going to sleep, i can use the system as normal for about 2 minutes. It then unavoidably crashes and i must reboot.

You asked for known bugs :-)

I am sort of new in here but..please tell what model laptop, ram, etc so that others have more info to go on, thanks. :P

---

### Post by Martin Houlton on 2011-08-26
One thing I have found out by experience, is don't use a flat screen TV as a monitor for Ubuntu.:)

---

### Post by Demon1986 on 2011-08-26
[QUOTE=Nightcrawlers]I am sort of new in here but..please tell what model laptop, ram, etc so that others have more info to go on, thanks. :p[/QUOTE] easy way to say that, whats your specs, i myself dont run on a laptop, since the gfx burned out a year ago (shiity hp) currently desktop tower custom my specs: asus p5gd1 3.0 ghz p4 775 1.2 gb ram and 40gb maxtor fireball 3 hd with a pinnacle tv tuner and my old geforce 8500gt pci-e ^^ who knows how the next setup will be, its nice i can get it moved around and ubuntu wont care, only X will sometimes xD

---

### Post by NLinTKO on 2011-08-27
> **Redsoul90 said:**
> one thing ive noticed is the abi keyboard not switching back and forth like it should. 

ill click japanese and it stays on english then when i finally get it to change it wont go back.
I noticed something similar. I want to toggle between alphabet and Japanese. Pressing Alt and Shift_L gets me from alphabet to Japanese. Hitting Alt Shift_L once more does not bring me back to alphabet. This is annoying as I am now forced to move my mouse to the menu and click the radio button.

---

### Post by JazzPotato on 2011-08-28
> **Nightcrawlers said:**
> I am sort of new in here but..please tell what model laptop, ram, etc so that others have more info to go on, thanks. :P

My specs are:
Dell studio 1558
4gig RAM
intel core i5 (not sure exactly what mhz, but its a realy low spec one)
Hard drive is probably irrelevant, and i have no idea what bios i have. 

There you go!

---

### Post by mullanerd on 2011-08-28
> **Python Jedi said:**
> Anyone here have a problem that keeps windows from resizing (The mouse pointer changes, but it won't resize), and windows that are blank white until making them smaller?

Thanks!
Yes mainly with Firefox or really any browser that I use does it then will clear up I don't know what causes it or corrects it??

---

### Post by Pabbajati on 2011-09-03
Many thanks for your tweaking ideas...

---

### Post by pdlethbridge on 2011-09-04
I have been using a Ubuntu  9.04 disk  to load on my computer and have only been able to get Natty to run is by using a earlier kernel and uninstalling unity. Maybe having a choice at log in like what is in Kubuntu, a choice between gnome an unity

---

### Post by thunderbirdje on 2011-09-05
> **pdlethbridge said:**
> I have been using a Ubuntu  9.04 disk  

I think you refer to 11.04? In fact you can choose the environment at the login screen: Ubuntu = Unity env.; Ubuntu classic = GNOME environment, ... I'm not sure about KDE. I think you have to install KDE-desktop first with Ubuntu software center (unless you downloaded a KDE-desktop .iso)

Good luck!

---

### Post by bilijoe on 2011-09-07
> **klm3030 said:**
> Saying this is a bug is like saying the Titanic had a leak. In my case I downloaded the ISO and did a complete new install ( four times now) so that's not the problem and in trying all the various fixes I have not been able to run Classic either. If they don't know the scope of this problem by now, adding to their bug report won't help.

Have you calculated the md5sum for your [downloaded] .iso file, and checked it against the published value? It's amazing what one little dropped or flipped bit can do, and it happens surprisingly often during [long] downloads.

---

### Post by agklimit on 2011-09-08
Can I post?

---

### Post by IanW on 2011-09-09
> **agklimit said:**
> Can I post?

Apparently. :D

---

### Post by vikash_chandola on 2011-09-12
I have felt some problems 
problem 1:   network manager is not working as it should. I uses MTS moderm which uses dial up connection. if i stop using internet for 5 minutes or more than it disconnects by self and doesn't reconnect even if i try(every time it fails). The only way to reconnect again is to restart computer or forcibly remove it from port and then reinsert. 
network manager takes around a minute to detect modern and connect(it comes in disk utility chart as i insert)Windows 7 takes less 10 seconds to connect. so why so lag of time.

problem 2:   second one is also related with my moderm. I can't safely remove it. I tried disk utility there is a option of ZTE USB moderm option but when i click safely remove drive then it shows error.it says **NO such file in directory** and some other stuff lines.

problem 3:  sound problem. Sound control is not fine. It is hard to manage sound from sound icon on upper left sidebar(I am using classic ubuntu instead of unity my hardware doesn't support that). If i increase it by very little than sound increase enormously. My speakers just came bursting. It's not fine sound but disturbed sound something like this.

problem 4:  well known shut down bug. My system doesn't shut down by self i need to press my CPU button at end to let it shut down. When i click on shut down a black screen appear saying a lot of things and at lat system halted. After that nothing happen i need to press CPU button.

during the time i write this para my network is disconnected and i need to remove USB moderm and reinsert it to connect.(It's not good way of working but what can i do?)

---

### Post by searchfgold6789 on 2011-09-21
PROBLEM: Kubuntu: Amarok will not show Audio CD's. Official bug. No fix any time soon. 
WORKAROUND: [http://ubuntuforums.org/showthread.php?p=11270885#post11270885](http://ubuntuforums.org/showthread.php?p=11270885#post11270885)
Workaround courtesy of [Lisiano]("http://ubuntuforums.org/member.php?u=1108763").

[LIST=1]
[*]Install cdfs-source:```
sudo apt-get install cdfs-src
```
[*]Compile it:```
sudo module-assistant
```
[*]Update -> Prepare -> Select -> Mark cdfs -> Build -> Install -> Exit
[*]You can now mount the CD in the following way: (replace /dev/sr0 with your CD device) ```

sudo mkdir /media/sr0 && sudo mount -t cdfs /dev/sr0 /media/sr0 
```
[*]And play the CD using Amarok, the directory is wherever you mounted it above.
[*]You can add it to your fstab too:```

    /dev/sr0       /media/sr0       auto        noauto,users,ro  0   0
```
[/LIST]

---

### Post by simonp2 on 2011-09-27
Hi tim thanks...your advice is really help full .

---

### Post by jamesgthang on 2011-09-27
Skype doesn't behave well with Unity's Launcher and tries to run multiple instances of itself when the Skype icon in the Launcher is clicked.

Here is a workaround using a python script:
[http://ubuntuforums.org/showthread.php?t=1851256](http://ubuntuforums.org/showthread.php?t=1851256)

to ensure only a single instance is run when clicking the the Skype icon in the Unity Launcher.

---

### Post by rafahugo on 2011-09-28
Hello everybody.

I just installed Ubuntu 11.04 64 bits dual boot with windows 7 and the install went fine, but Software center not opening neither the upgrade manager. They just blink, and then disappear.

I am a beginner regarding Ubuntu.

Can anyone help me? Thanks.

---

### Post by rafahugo on 2011-09-28
rafael@ubuntu:~$ update-manager
Segmentation fault
rafael@ubuntu:~$ software center
software: command not found
rafael@ubuntu:~$ software-center
/usr/share/software-center/softwarecenter/app.py:1190: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-09-28 19:12:54,298 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-09-28 19:12:54,298 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
2011-09-28 19:12:54,734 - softwarecenter.app - INFO - software-center-agent finished with status 0
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
Segmentation fault
rafael@ubuntu:~$

---

### Post by FSoares on 2011-09-30
Backlight problems! After upgrading from 10.10 there's no chance of doing anything, because screen goes dark. Very annoying problem.

---

### Post by checoimg on 2011-10-01
> **hawthornso23 said:**
> I think it is worthwhile warning people that attempting to tweak the appearance of unity using the compiz config settings manager is not advised. I have had natty installed for less than 24 hours and have already completely and seriously destroyed my desktop four or five times simply trying to make minor tweaks to its appearance. 

What I thought I was getting was a desktop integrated with my favorite window manager - compiz. What I actually got was a desktop apparently constructed by cannibalising compiz to the extent that compiz as I understand it, in all its fully configurable glory,  is no longer functional.

Currently unity is a "take it or leave it" desktop environment. Almost nothing about it is configurable and efforts to tweak it are likely to break it. Some aspects of its design I really quite like and want to use. But if you are used to being able to customize your desktop environment then unity's rigidity and fragility is going to drive you nuts.

I love Unity just how it is. many things are inetresting but not much practical. I found Unity very practical. And I used to spend hours tweaking Compiz.

Keep Ubuntuing

---

### Post by alcapony007 on 2011-10-02
Hi guys, I have a big problem with Linux BackTrack 5 GNOME 32 bit.
First of all I installed windows 7 and than on the same partition C I installed backtrack 5. I have many files on both systems. Few days after I was doing something with partitions and after reeboot I didn't have grub ... I had only:
"Error unknown file system
grub rescue>"

I read about grub and I tried to reinstall grub. No sucssess cause I can't mount my partition and i dont know why...
I tried everything: do this manually, Timos rescue CD set, boot repair disk and that last one repaired my Windows 7 MBR so now when i restart computer it load windows. 
Help me to reisntall/rebuild grub or just tell me how to copy few files from linux partition. I need only few text files. Please help me. It's very important to me. Have any ideas?
Sorry if thread not in correct place.

---

### Post by checoimg on 2011-10-02
> **alcapony007 said:**
> Hi guys, I have a big problem with Linux BackTrack 5 GNOME 32 bit.
First of all I installed windows 7 and than on the same partition C I installed backtrack 5. I have many files on both systems. Few days after I was doing something with partitions and after reeboot I didn't have grub ... I had only:
"Error unknown file system
grub rescue>"

I read about grub and I tried to reinstall grub. No sucssess cause I can't mount my partition and i dont know why...
I tried everything: do this manually, Timos rescue CD set, boot repair disk and that last one repaired my Windows 7 MBR so now when i restart computer it load windows. 
Help me to reisntall/rebuild grub or just tell me how to copy few files from linux partition. I need only few text files. Please help me. It's very important to me. Have any ideas?
Sorry if thread not in correct place.

No problem, Two Ideas:

1) Make another temporary small installation of ubuntu to updeta Grub. Sorry I don't remember how to reinstall it maybe with an alternate install CD. 

2) From Windows Use EasyBCD to restore Grub. [http://download.cnet.com/windows/3055-2094_4-10556865.html?tag=pdl-redir]("http://download.cnet.com/windows/3055-2094_4-10556865.html?tag=pdl-redir") ( scan for viruses )

You should read about EasyBCD before. Hope this helps.

Keep Ubuntuing!

---

### Post by asmahakkim on 2011-10-09
i just installed ubuntu 11.04 with wubi and my battery indicator is not working when i unplug it. :(
Toshiba L645-4104 pls help im new to ubuntu :)

---

### Post by agrayray on 2011-10-10
Remote Desktop aka vino

major screen refresh issues in that it practically doesn't.

consistently with natty on unity and gnome :(

although I do believe this is well known at least from when i first tried it, i found many postings here saying the same, no workaround or fix that i am aware of.

---

### Post by NLinTKO on 2011-10-11
Issue with Language Support.

I use English as main input language. However, sometimes I want to use Japanese. So I have installed Japanese as a second language via System Settings -> Language Support.
By pressing Shift + Left Alt can I change from alphabet input to Japanese input. HOWEVER: pressing the same key sequence once more does not return me to alphabet input. So it does not work as a toggle (the way it works in Windows). There was a workaround to this: an icon would appear in the bar at the upper right hand corner with the symbol of a keyboard. Via this icon would it be possible to go back from Japanese to alphabet. Recently however, does this icon no longer appear. I have to exit and restart the application (e.g. Firefox, Thunderbird) to reset the input language from Japanese to alphabet.

Correction, one day later: I found that I can activate the icon I mentioned by going to System Settings -> Keyboard Input Methods. I also found that I can disable Japanese input and return to alphabet by hitting "Ctrl Space". Now I am looking for a way to get this activated when I log on.

---

### Post by Aditya Telang on 2011-10-13
Help......](*,)
I installed Ubuntu 11.4 on my Compaq Presario CQ61 quite a few months back as i switched from Windows 7.Everything was fine with no concern what so ever.......
Then i installed Kubuntu recently....all was well for quite some time but then a problem started...
As i was busy when i switched on my laptop the grub screen came up.I could not choose Ubuntu as i was busy so it automatically came to Kubuntu. But instead of logging in i directly restarted the laptop from my login screen. When again the Grub screen came i chose Ubuntu from there and it directed me to disk check.
I waited but it checked the disk till 4% and got stuck there for a long time.....
So i force shut down using the power button and again started..Everything was good till i chose ubuntu from the Grub menu..

Instead of taking me to Login screen it showed:

[COLOR=Red]"There is a problem with configuration server /usr/lib/lib conf 2-4/gconf-sanity-check-2 excited with status 256"[/COLOR]

I clicked on CLOSE then it showed the login screen from where i logged in .It again showed me the same prob.
And now Ubuntu looks like a cheap imitation of Windows 95
[IMG]http:///home/adityatelang/Desktop/Photo0021.jpg[/IMG][IMG]http:///home/adityatelang/Desktop/Photo0022.jpg[/IMG]

---

