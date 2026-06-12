---
title: "CDemu not properly working"
date: 2011-09-22
forum: General Help
---

### Post by Littlemud on 2011-09-22
Hi all,

First post, so hope it's in the right forum!

I've installed gCDemu(the natty version) and all it's dependencies through the synaptic package-manager. When i now start the application, it's not working. 
It gives me the following error:
```
Daemon autostart failed. Error: org.freedesktop.DBus.Error.Spawn.ChildExited
Process /usr/bin/cdemu-daemon-session.sh exited with status 255
```

I went looking around and found i should start the daemon in the init.d folder, problem is that it's not there. Neither is there a folder in the /usr/lib/ titled cdemu-daemon as some tutorial had pointed out.

Can any of you help?

Greetz

Mud

---

### Post by varunendra on 2011-09-22
Hi, and Welcome to the Forums! :)

Can you please post the link to the tutorial that you followed?

Here's how I did it last time: [http://ubuntuforums.org/showpost.php?p=9181110&postcount=7](http://ubuntuforums.org/showpost.php?p=9181110&postcount=7)

Another recent attempt I made on 10.04 following the same method went a lot more smoother (finished at step #12)

---

### Post by Littlemud on 2011-09-23
Well, the tutorial you mention is one of 'em. The problem was with the 11th step, i did not have anything in /init.d that had something to do with cdemu-daemon.

Other tut's i tried were:
-[http://ubuntuforums.org/showthread.php?t=938030]("http://ubuntuforums.org/showthread.php?t=938030")
-[http://ubuntuforums.org/showthread.php?t=69530]("http://ubuntuforums.org/showthread.php?t=69530")
-tried with the one on their site too

But none worked...

---

### Post by varunendra on 2011-09-23
> **Littlemud said:**
> Well, the tutorial you mention is one of 'em. The problem was with the 11th step, i did not have anything in /init.d that had something to do with cdemu-daemon.

Other tut's i tried were:
-[http://ubuntuforums.org/showthread.php?t=938030](http://ubuntuforums.org/showthread.php?t=938030)
-[http://ubuntuforums.org/showthread.php?t=69530](http://ubuntuforums.org/showthread.php?t=69530)
-tried with the one on their site too

But none worked...
Out of curiosity, I just tried installing cdemu on my Natty 32bit VM, and found that it has become even more easier! I didn't even require step 11 or further steps to make it work. As soon as I added the ppa and installed gcdemu via synaptic, it was already there in the applications' list - waiting to be run. Here's a screenshot:

[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Natty-gCDEmu.jpg[/IMG]


Not sure of what exact steps you followed, here I am stating the steps I followed (which were quite trivial in comparison to my previous attempts):

[LIST]
[*]First, browsing CDEmu's site for Ubuntu support, I got to this page that tells how to add ppa to your Natty repository: [https://launchpad.net/~cdemu/+archive/ppa]("https://launchpad.net/%7Ecdemu/+archive/ppa")
[/LIST]

[LIST]
[*]On the above page, I clicked "[Technical details about this ppa]("https://launchpad.net/%7Ecdemu/+archive/ppa/+index#")" under heading "Adding this ppa to your system", which gave me following lines to add to my /ect/apt/sources.list file:
[/LIST]
[INDENT]
[LIST=1]
[*]**deb [http://ppa.launchpad.net/cdemu/ppa/ubuntu](http://ppa.launchpad.net/cdemu/ppa/ubuntu) natty main**
[*]**deb-src [http://ppa.launchpad.net/cdemu/ppa/ubuntu](http://ppa.launchpad.net/cdemu/ppa/ubuntu) natty main**
[/LIST]
[/INDENT]
[LIST]
[*]After adding the above lines, I closed the file, opened synaptic, refreshed (which gave me a couple of typical errors that I ignored), typed "cdemu" in the search-box, and the whole bunch of the seven packages got listed (of which I think "image-analyzer" is a new entry).
[/LIST]

[LIST]
[*]I checked only "**gcdemu**" as usual, and the three dependencies - **cdemu-daemon, vhba-dkms **and **libmirage3**, got selected automatically (as usual:))
[/LIST]

[LIST]
[*]Installed the 4 packages, then clicked "Applications" in the Unity(2d) panel, and the good old **gcdemu icon** was sitting there! (It can also be brought up by pressing Alt+F2, then typing "gcdemu" in the "Run Application" box)
[/LIST]
As soon as I clicked the icon, it immediately got loaded, providing its controller applet in the top panel as you can see in the snapshot.

As evident from the snapshot, I copied a FreeNAS iso on the desktop to test its (cdemu's) functionality. I clicked the top panel applet > clicked the first drive (empty) > browsed to the iso image > selected it and it got loaded just the way expected! No issues, no glitches anywhere (except the step when I refreshed the repository and it gave me a couple of "not found" errors - which I knew I can ignore as long as my desired packages are available :))

I even added it to Startup Applications by just typing "gcdemu" as the command to run, and it works as expected.


Although you are right that no start-daemon or anything exists in the /etc/init.d directory, _but there is no need for it now_ with the latest packages, hence no step 11 or later ones required. It is clearly stated on the very top of CDEmu's homepage that they have merged it all in one python script (which now resides in /usr/bin directory). Here are the excerpts:
> In short, in addition to bugfixes and some cleanup, this release brings a major rewrite of both the daemon and the clients. The CDEmu daemon is not a traditional 'daemon' anymore (no more forking and PID files); instead, it is a regular application that utilizes D-Bus (auto)start facility for both session and system bus instances.[COLOR=Red]** Both cdemu-client and gCDEmu have been changed to single-file python scripts**[/COLOR]. Additionally, gCDEmu has been changed from a GNOME applet into a standalone Gtk application. For more detailed information, see the long-version highlights below or consult the subversion changelog.The user-accessible icon (desktop-configuration file) for gcdemu is located in /usr/share/applications directory.


So this was my experience with 32-bit Natty (on VMware). I'd request you to please remove all related packages and try the same way I mentioned, and see if it works the same way for you.

---

### Post by Littlemud on 2011-09-23
just tried what you've proposed, only to see it fail again... :s

I still get the same error as stated in my first post.

Could this be because of the fact i'm using 64-bit?
Or because maybe some stuff is still there when you remove those packages? should i reboot when i removed all those packages?

Thanks for your help allready!

---

### Post by varunendra on 2011-09-23
You're welcome buddy, I like experimenting.
> **Littlemud said:**
> 
Could this be because of the fact i'm using 64-bit? I don't know,.. it could be. In order to try it myself on 64bit I'll have to physically install Natty on my computer which I don't think I am going to have time for anytime soon (all my host installations are 32 bit). But I sure will try that as soon as I get time for it. After all, it is the only application I trust for 100% emulation of an optical drive.

One thing you can do to affirm the possibility of it being an issue of 32 vs 64 bit is to try the same packages on a 32 bit installation on either a vm or a physical machine. At least if it can be ensured that it runs fine on 32 bit, then you can (and should) post a bug report at their launchpad page where they have put a link for it.

Meanwhile, let's hope someone having deeper knowledge of this thing can explain the error and maybe offer a solution.


**_PS_:**
If you don't already know: To remove it fully along with its configuration files, try this-
```
sudo apt-get purge gcdemu
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by Goa'uld on 2011-09-25
> **Littlemud said:**
> I still get the same error as stated in my first post.

To see what the real error was: > cat ~/.cdemu-daemon.log Your system appears to be in a broken state. 

To fix it proper you need to undo everything from whatever prehistoric  tutorial you used. Then start Synaptic, and "completely remove" ALL  cdemu related packages. Then reinstall the way varunendra specified. 

> Could this be because of the fact i'm using 64-bit?nope. it works fine on 64-bit.

> Or because maybe some stuff is still there when you remove those  packages? yup. i'm betting the old initscripts. double-check  that they are really gone.

---

### Post by Littlemud on 2011-09-26
Thanks for jumping in!

When i check the log with the command you just gave, i just get the details of the daemon...
```
Starting CDEmu daemon with following parameters:
 - num devices: 2
 - ctl device: /dev/vhba_ctl
 - audio driver: pulse
 - bus type: session

```

I went on and just tried to get everything related to cdemu removed from my system, but i think because of my rather basic knowledge, that i did not got it all... Can you help or specify where else i might have to look? because i installed it again, just to come up with the same old error... of which i still do not now it's meaning :)

Thanks

---

### Post by Goa'uld on 2011-09-26
> **Littlemud said:**
> I went on and just tried to get everything  related to cdemu removed from my system, but i think because of my  rather basic knowledge, that i did not got it all... Can you help or  specify where else i might have to look? because i installed it again,  just to come up with the same old error... of which i still do not now  it's meaning :smile:


Just to make sure. You aren't manually trying to start the daemon  are you? You shouldn't, it starts by itself automatically the first time you try to use gcdemu or cdemu-client. A log  reporting no errors means it started successfully. You see a little  notification pop-up when that happens too.

To clean-up old cdemu files try the attached script. save it, "chmod +x cdemu-cruft.sh", then run it with "sudo cdemu-cruft.sh".

Your  system should be reasonably clean after this. And cdemu should install  and start. If it doesn't then "dmesg" and "cat ~/.cdemu-daemon.log" can  give clues.

---

### Post by Littlemud on 2011-09-28
even after performing your script(done a reboot too, you never know...) i keep getting the error...

"dmesg" gives a whole bunch of info, but nothing on cdemu(at least not what i can make of it)

"cat" gives me the same as 2 posts ago... 

So what we can conclude this far is that even when everything is removed, there still is something left that keeps preventing the daemon from being started properly by gcdemu... Could this be because of some other software? The big problem being at the moment that we can not know what the exit-code 255 means(it mostly means that the exit-status is out of range, but...)

So big boohoo at this moment! 
I do appreciate your help though!

EDIT: I've got some extra's!
I've tried creating another account and start 'gcdemu' from there and there it can start the daemon(it gives a little 'pop up' on the right side), however it does not start the actual program. I can still not emulate a cd/dvd. I've also ran it out of the root's account to see if maybe it had something to do with the rights, but had the same luck as with the other account(daemon starts, program does not)

So how come this happens for my account and how come the program itself does not run? there's probably a very easy solution for this all(reinstall ubuntu being the easiest one, but i prefer not to) and i hope someone can provide this! :)

---

### Post by Goa'uld on 2011-09-29
> **Littlemud said:**
> even after performing your script(done a reboot too, you never know...) i keep getting the error...

Damn. It should have removed any leftovers or issues preventing upgrade that I am aware of...

> The big problem being at the moment that we can not know what the exit-code 255 means(it mostly means that the exit-status is out of range, but...)I can tell you what it means: the daemon exits with that exit-code regardless what the error is. Hardly useful. 

apparently you managed to start gcdemu. and the pop-up confirms the daemon is active. trying to start it manually WILL give you an error 255. this is normal.

tried right-clicking on the gcdemu icon? remove the tick from "use system bus". you can use it by left clicking the icon and left-clicking a device. you then load an image to this device.

> I've tried creating another account and start 'gcdemu' from there and there it can start the daemon(it gives a little 'pop up' on the right side),that would suggest your main user account has been corrupted. in cases like this I'd create a new account, copy the data you want to keep, and remove the initial user.

---

### Post by sup on 2012-01-24
> **Littlemud said:**
> Hi all,

First post, so hope it's in the right forum!

I've installed gCDemu(the natty version) and all it's dependencies through the synaptic package-manager. When i now start the application, it's not working. 
It gives me the following error:
```
Daemon autostart failed. Error: org.freedesktop.DBus.Error.Spawn.ChildExited
Process /usr/bin/cdemu-daemon-session.sh exited with status 255
```

I went looking around and found i should start the daemon in the init.d folder, problem is that it's not there. Neither is there a folder in the /usr/lib/ titled cdemu-daemon as some tutorial had pointed out.

Can any of you help?

Greetz

Mud

Hi, I got the same message but solved it by purging everything related to cdemu and then reinstalling (version 1.5 from a ppa).
ie. I have run:
```
sudo apt-get remove --purge cdemu-client cdemu-deamon gcdemu vhba-dkms vhba-dkms libmirage6 libmirage3
sudo reboot 
sudo apt-get install cdemu-client cdemu-deamon gcdemu vhba-dkms vhba-dkms libmirage6 libmirage3
```
(rebooting is probably unnecessary)

(btw: unity does not play well with gcdemu, it needs to be whitelisted:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "$(gsettings get com.canonical.Unity.Panel systray-whitelist | sed -e "s:\[:\['gcdemu' ,:")"
```

---

