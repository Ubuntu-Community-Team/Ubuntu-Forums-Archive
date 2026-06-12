---
title: "Gnome3 PPA is getting ready"
date: 2011-04-06
forum: General Help
---

### Post by Harry33 on 2011-04-06
Gnome3 release versions 3.0.0 of a number of Gnome3 packages can now be downloaded
from the Gnome3 PPA.

New release versions of
devhelp, empathy, gnome-nettool, gnome-desktop3, gnome-settings-daemon, gnome-terminal, gnome-themes-standard, gnome-tweak-tool, gnome-user-share, libgnomekbd, mutter and nautilus, nautilus-sendto and totem are all already there.

For example, new gnome-shell release v. 3.0.0-0ubuntu1:
```
Changelog
gnome-shell (3.0.0-0ubuntu1~build1) natty; urgency=low
  * New upstream release
  * debian/control.in:
    + bump build-dep on mutter (>= 3.0.0)
 -- Rico Tzschichholz <email address hidden>   Tue, 05 Apr 2011 19:31:07 +0200
```

---

### Post by lucazade on 2011-04-06
Anyone tried it?

Edit:
PPA should be this one: [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
some packages are still building

---

### Post by gnomeuser on 2011-04-06
> **lucazade said:**
> Anyone tried it?

Edit:
PPA should be this one: [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
some packages are still building

I am running it day to day, it still needs a lot of work to be useable. E.g. right now to log in you have to drop to a vc, restart gdm and only then will a user list appear.

It is though other than this workable, if filled with small bugs that needs to be ironed out.

---

### Post by lucazade on 2011-04-06
> **gnomeuser said:**
> I am running it day to day, it still needs a lot of work to be useable. E.g. right now to log in you have to drop to a vc, restart gdm and only then will a user list appear.

It is though other than this workable, if filled with small bugs that needs to be ironed out.

good to know..
i'm downloading packages in virtualbox.. I hope I could drop to a vc from there to login.

thanks!

---

### Post by lucazade on 2011-04-06
Arg.. no user list in GDM
Unfortunately I cannot switch to virtual terminal to kill and restart gdm because ctrl-alt-f1 switchs to physical vts and not inside virtualmachine.

any other workarounds? :)


edit: right control + right alt + f1 does the trick!

---

### Post by paul_in_london on 2011-04-06
> Arg.. no user list in GDM
Unfortunately I cannot switch to virtual terminal to kill and restart gdm because ctrl-alt-f1 switchs to physical vts and not inside virtualmachine.

any other workarounds? 

The one I use is to delete **/var/log/ConsoleKit/history**.

You may need to reboot if you can't switch to a VC to restart GDM, but then you should see your GDM user list again.

---

### Post by lucazade on 2011-04-06
> **paul_in_london said:**
> The one I use is to delete **/var/log/ConsoleKit/history**.

You may need to reboot if you can't switch to a VC to restart GDM, but then you should see your GDM user list again.

Thanks for suggestion, I'll try it.
At the moment I avoid to upgrade gnome-session because some dependencies are broken, so gdm still works (unfortunately no gnome-shell)

---

### Post by lucazade on 2011-04-06
> **lucazade said:**
> Thanks for suggestion, I'll try it.
At the moment I avoid to upgrade gnome-session because some dependencies are broken, so gdm still works (unfortunately no gnome-shell)

Upgraded also gnome-session and deleted /var/log/ConsoleKit/history.
Now I'm able to login from gdm into "Gnome shell" session but it seems Virtualbox is not enough to handle shell and mutter even with guest addition and 3d support enabled.

---

### Post by Harry33 on 2011-04-06
The list of "ready" released Gnome3 packages (version 3.0.0) is increasing rapidly (in addition to devhelp, empathy, gnome-nettool, gnome-desktop3, gnome-settings-daemon, gnome-terminal, gnome-themes-standard, gnome-tweak-tool, gnome-user-share, libgnomekbd, mutter and nautilus, nautilus-sendto and totem):
brasero
eog
evince
file-roller
gedit
gnome-disk-utility
gnome-games
gnome-icon-theme
gnome-keyring
gnome-menus
gnome-power-manager
gnome-screensaver
gnome-themes
gnome-utils

---

### Post by Harry33 on 2011-04-06
Gnome3 will be released in less than 6 hours.

[http://ubuntuforums.org/showthread.php?t=1722627](http://ubuntuforums.org/showthread.php?t=1722627)

---

### Post by ratcheer on 2011-04-06
> **Harry33 said:**
> Gnome3 will be released in less than 6 hours.

[http://ubuntuforums.org/showthread.php?t=1722627](http://ubuntuforums.org/showthread.php?t=1722627)

Would someone who is accustomed to installing it from the PPA please provide clear instructions for installing and running it? I was able to use it in very early Natty alphas, but I've been completely unable to do so for quite some time, now. I can make apparently good installations, but I can never actually get Gnome Shell to run.

Thanks,
Tim

PS - I have pretty much had it with Unity.

---

### Post by Harry33 on 2011-04-06
> **ratcheer said:**
> Would someone who is accustomed to installing it from the PPA please provide clear instructions for installing and running it? I was able to use it in very early Natty alphas, but I've been completely unable to do so for quite some time, now. I can make apparently good installations, but I can never actually get Gnome Shell to run.
Thanks,
Tim
PS - I have pretty much had it with Unity.

The PPA itself is very easy to install (which means simply upgrading all the packages form there with synaptic for example). Just add this to your /etc/apt/sources.list
 ```
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu natty main
```
Then add the signing key for software authentication.

But I am afraid there are still some important packages missing from that PPA.
I do not see for example gdm there.

---

### Post by lucazade on 2011-04-06
> **Harry33 said:**
> 

But I am afraid there are still some important packages missing from that PPA.
I do not see for example gdm there.

Harry is right, stuff is still building and repo is not complete (I tried to use it just to make my day funny!)
it is better to wait at the moment.

---

### Post by DevHead on 2011-04-06
I too would love to try Gnome3.  Please keep us posted.

---

### Post by Quackers on 2011-04-06
Repository added and waiting :-)
Sadly I tried to build from source the other night but couldn't get one of them to build :-(

---

### Post by Harry33 on 2011-04-06
About the release  announcement:

[http://www.gnome.org/press/releases/2011-04-gnome-3.0-released.html](http://www.gnome.org/press/releases/2011-04-gnome-3.0-released.html)

---

### Post by Cenotaph on 2011-04-06
How will this work when the packaging is done? Will we need to uninstall ubuntu-desktop or anything else or will it be a clean update?

---

### Post by lucazade on 2011-04-06
> **Cenotaph said:**
> How will this work when the packaging is done? Will we need to uninstall ubuntu-desktop or anything else or will it be a clean update?

With a fully updated system with ppa enabled ubuntu-desktop is still there, and it will probably remain.

One bad thing I see is poor font rendering, it looks like lacks ubuntu patching and of course no gtk3 murrine engine and ambiance theme.

---

### Post by vaskark on 2011-04-06
> **gnomeuser said:**
> I am running it day to day, it still needs a lot of work to be useable. E.g. right now to log in you have to drop to a vc, restart gdm and only then will a user list appear.

Can you be more specific with the exact commands? Ctrl+Alt+F2 to get to a virtual console, correct? And to start gdm is it just "sudo gdm"?

---

### Post by kansasnoob on 2011-04-06
If anyone actually has gnome3 running on Natty w/gnome-shell I'd love to know how they did it :)

I tried earlier today and I can not even begin to succeed, first this:

[https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/734563](https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/734563)

But even if I try to install 'gnome3-session' I encounter a lot of problems with missing dependencies.

---

### Post by vaskark on 2011-04-06
Poo! I got my user-list gdm back, but cannot choose a session (greyed out)

:(

---

### Post by uBeer on 2011-04-06
> **vaskark said:**
> Can you be more specific with the exact commands? Ctrl+Alt+F2 to get to a virtual console, correct? And to start gdm is it just "sudo gdm"?

The right thing to do would be:
```
sudo service gdm restart
```

---

### Post by Harry33 on 2011-04-06
> **kansasnoob said:**
> If anyone actually has gnome3 running on Natty w/gnome-shell I'd love to know how they did it :)
I tried earlier today and I can not even begin to succeed, first this:
[https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/734563](https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/734563)
But even if I try to install 'gnome3-session' I encounter a lot of problems with missing dependencies.

Yes theming is kind of broken, only adwaita works (the default for gnome-shell).
I think gnome3-session package is not even meant to be run on Gnome3.
There are only session packages gnome-session_3.0.0 and gnome-session-bin_3.0.0 in the PPA. That session should automatically open gnome-shell session only.

---

### Post by vaskark on 2011-04-06
The right thing to do would be:
Code:
sudo service gdm restart


Thanks ;)

---

### Post by KegHead on 2011-04-06
Hi!

I was going to load up today, but I think I'll wait a few days.

I love 2.3, so we'll see!

KegHead

---

### Post by Harry33 on 2011-04-06
> **KegHead said:**
> Hi!
I was going to load up today, but I think I'll wait a few days.
I love 2.3, so we'll see!
KegHead

A good decision. ):P

---

### Post by vaskark on 2011-04-06
Ugh, I wish i had waited. I decided to purge the PPA for Gnome 3 but it didn't solve my problem - gdm loads fine, but the session chooser is greyed out. When i try to login i get an error message about ~/.ICEauthority (or something) and get put back to the gdm screen.

Please help! I don't want to have to reinstall.

---

### Post by KegHead on 2011-04-06
Hi!

I've decides to wait...does that make me a leader/

LOL

KegHead

---

### Post by kansasnoob on 2011-04-06
> **vaskark said:**
> Ugh, I wish i had waited. **[COLOR="Red"]I decided to purge the PPA for Gnome 3 but it didn't solve my problem[/COLOR]** - gdm loads fine, but the session chooser is greyed out. When i try to login i get an error message about ~/.ICEauthority (or something) and get put back to the gdm screen.

Please help! I don't want to have to reinstall.

From the ppa:

> This PPA is EXPERIMENTAL and MAY BREAK YOUR SYSTEM. There is no downgrade process.

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

That's why I'm calling, "pants on fire" to those who fail to provide an actual successful upgrade process :lolflag:

---

### Post by harryscode on 2011-04-06
There are no PPa for lucid lynx, isn't?. I presume that gnome 3 can be used instead 10.10, I love Lucid... i'll wait a time for upgrade:(

---

### Post by vaskark on 2011-04-06
ahaha nice

---

### Post by Quackers on 2011-04-06
Oh dear! I took the plunge and ran the upgrade, but gnome-session was broken :-( I daren't reboot for a while :-)
Nevermind there's always the backup Natty install :-)

---

### Post by Quackers on 2011-04-06
I rebooted :-) It's deceased.
I got the ICEauthority message in a pretty white box.
I'll brush up on my chroot technique and wait for some shiny new packages :-)

---

### Post by MacUntu on 2011-04-06
ICEauthority message here as well. ppa-purge really doesn't work well, left many packages, which I simply removed instead of finding out how to downgrade them, and then reinstalled ubuntu-desktop. Now everything seems back to normal, better luck next time! :D

---

### Post by Quackers on 2011-04-06
It's a lark :-)

---

### Post by Cenotaph on 2011-04-06
It looks like the PPA is missing a package for gnome-icon-theme-symbolic? which makes gnome-shell impossible to install, is there a way around this or should I just wait?

---

### Post by FEGuy on 2011-04-06
The source code for the icon theme is floating around, and I did manage to get it to build and install, but right now it's pretty useless, as everyone (myself included) seems to be having problems with the Gnome3 session manager; I'd wait a while if I was you.

---

### Post by Arrowstar on 2011-04-07
Hmm, I just tried to build it earlier today and it errored out while building.  Shame to hear there seems to be universal problems.

---

### Post by Mblackwell on 2011-04-07
I just left gnome-icon-theme "at its current version". No package conflict then.

Now it's a waiting game for gnome-icon-theme-symbolic. The 3.0 build was just released a little over a day ago.

---

### Post by Harry33 on 2011-04-07
There is a new Gnome3 ppa in Launchpad now:
**Ubuntu Gnome Remix Team**
[https://launchpad.net/~ubuntugnometeam/+archive/gnome3](https://launchpad.net/~ubuntugnometeam/+archive/gnome3)

And with this warning message:
> 
Clean, working gnome 3 ppa for Ubuntu Gnome Remix
Note: Gnome3 is currently at an unstable and experimental stage! Use caution, there is no easy revert and this may break your system!


---

### Post by Harry33 on 2011-04-07
> **Cenotaph said:**
> It looks like the PPA is missing a package for gnome-icon-theme-symbolic? which makes gnome-shell impossible to install, is there a way around this or should I just wait?

Did you see this bug report (Bug 752927)?

[https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme-symbolic/+bug/752927](https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme-symbolic/+bug/752927)

---

### Post by Cenotaph on 2011-04-07
thx, the package in that bug report did the trick. obviously there are still some issues but at least im running the thing now ;)

---

### Post by lucazade on 2011-04-07
> **Harry33 said:**
> There is a new Gnome3 ppa in Launchpad now:
**Ubuntu Gnome Remix Team**
[https://launchpad.net/~ubuntugnometeam/+archive/gnome3](https://launchpad.net/~ubuntugnometeam/+archive/gnome3)

And with this warning message:

What is it? Differences with other ppa?? :confused:

---

### Post by Bou on 2011-04-07
I managed to boot and log in by following the instructions in the bug report, and then installing the packages gnome-shell and ubuntu-desktop; but I get an empty blue screen. Are there any additional packages you have to install?

---

### Post by Harry33 on 2011-04-07
> **Cenotaph said:**
> thx, the package in that bug report did the trick. obviously there are still some issues but at least im running the thing now ;)

A new version (3.0.0-1) of the package gnome-icon-theme-symbolic is just built in the Gnome3 PPA.

---

### Post by Harry33 on 2011-04-07
> **Bou said:**
> I managed to boot and log in by following the instructions in the bug report, and then installing the packages gnome-shell and ubuntu-desktop; but I get an empty blue screen. Are there any additional packages you have to install?

One big problem right now is the missing gdm, a package built against GTK+3.

---

### Post by lucazade on 2011-04-07
> **lucazade said:**
> What is it? Differences with other ppa?? :confused:

Found the answer myself..

> This is a remix of Ubuntu to include a full version of gnome, without unity. Future regular Ubuntu versions will ship with Unity instead of Gnome.
This is a remix of Ubuntu to include a full version of gnome. Mark Shuttleworth has stated that versions of Ubuntu from 11.10 and on will not ship the classic gnome interface, opting instead for the unity interface. This project is based almost entirely on regular Ubuntu, with just a few changes to the interface.

This project is in the VERY early stages. A repository is being set up to migrate existing ubuntu installations and set up our packages. A cd .iso will come by the natty release date of April 28th.

The natty (11.04) release will include gnome 3. Fallback to old-style gnome may be available at a later date.

This project is remixed by the team at teampr0xy.net. It is not approved or sponsored by ubuntu, gnome, or cannonical in any way. It is not for profit and has no commercial objective.

adding more and more fragmentation..

---

### Post by cecilpierce on 2011-04-07
> **lucazade said:**
> Found the answer myself..



adding more and more fragmentation..

Soooo! I'd like to try it, do I add bothe ppa's ?
Or what the heck ???  :confused:

---

### Post by lucazade on 2011-04-07
> **cecilpierce said:**
> Soooo! I'd like to try it, do I add bothe ppa's ?
Or what the heck ???  :confused:

We should wait a bit, still nothing usable at the moment.
At least this is what I've experienced.
unfortunately :)

---

### Post by lucazade on 2011-04-07
> Derived works. The ability to customise Ubuntu to meet your specific needs is one of the great strengths of free software in general, and Ubuntu in particular. While we encourage customisation and derivation of Ubuntu, we must balance that freedom with the integrity of the Trademarks and the quality which they represent. To help reach that balance, we have established the following guidelines and definitions.

We recognise and encourage the concept of a “remix.” Remixes are derived versions of Ubuntu, and it is intended that any software and hardware certifications will apply to a Remix. Therefore the changes from the official Ubuntu product must be minimal to be permitted to use the Trademarks. These changes can include configuration changes through the existing Ubuntu configuration management tools, changes to artwork and graphical themes and some variance in package selection. In general, a Remix can have applications from the Ubuntu archives added, or default applications removed, but removing or changing any infrastructure components (e.g., shared libraries or desktop components) will result in changes too large for the resulting product to be called by a Trademark. Note that if the nature of the product's divergence from Ubuntu changes, the Remix naming and Trademark use may no longer apply.

Therefore, if you are creating a derivative of Ubuntu, you may use the Trademarks in association with the software product provided:

the changes are minimal and unsubstantial, as described above

there is no commercial intent associated with the new product

the Trademark is used in a way that makes it clear that your project is a development effort related to the Ubuntu source, but that the software you are working upon is not in fact Ubuntu as distributed by the Ubuntu project. The approved naming scheme to facilitate this is through designation “Remix”. For instance, a new ISO image which has been packaged special tools for software developers could be called “Ubuntu, Developers Remix”, or an image was has been created with Thai language packs could be called "Ubuntu Thai Remix". Words such as "Edition" and "Version" should be avoided, as they have specific meaning within the Ubuntu project. Prefixes, such as “ThaiBuntu” should also be avoided. Any other naming scheme will require explicit permission.

there is no suggestion (through words or appearance) that your project is approved, sponsored, or affiliated with Ubuntu or its related projects unless it has been approved by and is governed by the Ubuntu Community Council.

If you are producing a new product which is based on Ubuntu but which has more substantial changes than those described above as a Remix, you are allowed to state (and we would encourage you to do so) that your product is "derived from Ubuntu", "based on Ubuntu", or "a derivative of Ubuntu" but you may not use the Trademarks to refer to your product. In some cases you may be allowed to use the Trademarks, but we'll need to discuss that. In that event, these products will need a trademark license, and such a license can be revoked if the nature of your divergence from Ubuntu changes. Products which include very invasive changes, such as a new kernel, the inclusion of packages which are not part of the Ubuntu repositories, or anything else that significantly impacts the technical quality or user experience would fall into this category are unlikely to be approved. (Note that if you are including packages which are not part of the Ubuntu repositories, we encourage you to work within the community processes to submit and maintain those packages within the repositories in order to minimise this issue.)

[http://www.ubuntu.com/aboutus/trademarkpolicy](http://www.ubuntu.com/aboutus/trademarkpolicy)

They have to choose, from what I understand (please correct me if wrong), another name for the distro and should not use Ubuntu artwork because changes are not minimal.

---

### Post by cecilpierce on 2011-04-07
> **lucazade said:**
> We should wait a bit, still nothing usable at the moment.
At least this is what I've experienced.
unfortunately :)

Sorry to be a pain but which ppa (or both) should be used, thanks.

---

### Post by ploum on 2011-04-07
Wow, two ppa! And gnome-power-manager still crashing because of Libappindicator integration not removed.

---

### Post by Harry33 on 2011-04-07
Neither one of these Gnome3 PPA's should be installed. Yet.
This is a wise decision because ppa-purge does not work, you cannot actually return back.
It would mean all the packages upgraded from those PPA's should be removed completely (purged) + all appropriate user settings from /home/user directory. Only after that the packages from Natty repo might be reinstalled. That may be very difficult.

These are the two PPA:s concerned:

1) **Gnome3 Team** GNOME3
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

2) **Ubuntu Gnome Remix Team** Gnome 3 ppa
[https://launchpad.net/~ubuntugnometeam/+archive/gnome3](https://launchpad.net/~ubuntugnometeam/+archive/gnome3)

---

### Post by lucazade on 2011-04-07
> **cecilpierce said:**
> Sorry to be a pain but which ppa (or both) should be used, thanks.

I've tried only the first ppa and I was able to use gnome3 applications only in an "Ubuntu classic" session with some manual fixes . So no gnome-shell.

both ppa lack "gdm" packages and other important pieces so not really useful at the moment.

---

### Post by KegHead on 2011-04-07
Hi!

I'm downloading and running off a stick.

Hope it works!

KegHead

---

### Post by Hedgehog1 on 2011-04-07
I am struggling to understand: **Kbuntu** is Ubuntu with the Gnome interface replaced.  Would **Gbuntu** (or **Gnatty**) with the Unity interfaced replaced by Gnome 3.0 be that much different from a 'remix/trademark' point of view? Or the real difference because of which team is heading up the work?


***The Hedge***

:KS

---

### Post by Mblackwell on 2011-04-07
> **Harry33 said:**
> Neither one of these Gnome3 PPA's should be installed. Yet.
This is a wise decision because ppa-purge does not work, you cannot actually return back.
It would mean all the packages upgraded from those PPA's should be removed completely (purged) + all appropriate user settings from /home/user directory. Only after that the packages from Natty repo might be reinstalled. That may be very difficult.

These are the two PPA:s concerned:

1) **Gnome3 Team** GNOME3
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

2) **Ubuntu Gnome Remix Team** Gnome 3 ppa
[https://launchpad.net/~ubuntugnometeam/+archive/gnome3](https://launchpad.net/~ubuntugnometeam/+archive/gnome3)

ppa-purge does work. You just have to finagle a bit. I wouldn't recommend doing anything though unless you are REALLY familiar with apt, aptitude, package breakages, and what the suggested resolutions and such all will result in.

Also I use the gnome-team PPA (1). Works well so far.

Note that if you got an empty desktop it's likely that Gnome Shell didn't start. This can happen for any number of reasons. Your best bet is to drop to a VT and say:

```

DISPLAY=:0 gnome-shell --replace &

```

...and see what your error is.

Personally in conjunction with the PPA I also use my own personal jhbuild of Shell with a few patches applied for nvidia performance purposes. So I'm not really the one to ask about Shell breakages from the PPA.

I did notice that the ubuntu one music store crashes rhythmbox, and also the cover art plugin appears to crash playback.

Also a quick bit of info: The status menu (upper left) contains a link to System Settings. Default applications is there under System Info. I had a moment where all of a sudden FF was no longer my default, and an update had changed its value.

As of this morning I was able to update everything (previously I'd held back gnome-icon-theme).

---

### Post by lucazade on 2011-04-07
> **Hedgehog1 said:**
> I am struggling to understand: **Kbuntu** is Ubuntu with the Gnome interface replaced.  Would **Gbuntu** (or **Gnatty**) with the Unity interfaced replaced by Gnome 3.0 be that much different from a 'remix/trademark' point of view? Or the real difference because of which team is heading up the work?


***The Hedge***

:KS

The team heading up the work is really important from a trademark point of view because it uses name, brand, logo of a company. If they made a bad work nobody will know they are not affiliated with Canonical. 

About Gnome3, all this DE will be part of natty+1, only Gnome-shell3 will be available in repository and not installed by default..  is it necessary to create an ubuntu derivative? 
Was not easier: sudo apt-get install gnome-shell? :)

---

### Post by Hedgehog1 on 2011-04-07
> **lucazade said:**
> The team heading up the work is really important from a trademark point of view because it uses name, brand, logo of a company. If they made a bad work nobody will know they are not affiliated with Canonical. 

About Gnome3, all this DE will be part of natty+1, only Gnome-shell3 will be available in repository and not installed by default..  is it necessary to create an ubuntu derivative? 
Was not easier: sudo apt-get install gnome-shell? :)

Thanks lucazade.  That makes sense.


***The Hedge***

:KS

---

### Post by KegHead on 2011-04-07
I agree:

Was not easier: sudo apt-get install gnome-shell?

KegHead

---

### Post by nutmac on 2011-04-07
So is anyone having better luck with the second PPA (sudo add-apt-repository ppa:ubuntugnometeam/gnome3)?

---

### Post by KegHead on 2011-04-07
Hi!

I tried Gnome 3 w/Fedora which looks about the same.

I guess I'm old school, but I'm staying with 11.04/classic.

KegHead

---

### Post by jfernyhough on 2011-04-07
I fell for trying the Gnome3 team PPA (I haven't had any serious breakage for too long). Packages install but it looks like there are things missing (e.g. window decorations are wrong). I also have menu corruption, which may well be down to fglrx.

I wish I could find out how to disable gnome-shell and drop back to nautilus+panels. I haven't found anything via Google yet, and doing a normally good $ metacity --replace just freezes my display. :)

--edit
The Adwaita theme is in gnome-themes-standard

--edit 2
The display may be corrupted to crap, but the widgets are lovely. Modal dialog boxes are nice.

---

### Post by t.rei on 2011-04-07
For me it's the key management that is just not working (gnome3 team ppa) - It's not storing any passwords for any app. *sigh* But it shure looks sharp and works pleasantly stable. I enjoy g3 alot. Give this one another 6 months and *rrrrrr* ;)

---

### Post by kansasnoob on 2011-04-07
> **KegHead said:**
> Hi!

I tried Gnome 3 w/Fedora which looks about the same.

I guess I'm old school, but I'm staying with 11.04/classic.

KegHead

Ditto :D

---

### Post by KegHead on 2011-04-07
Hi Kansasnoob!

I wish I could still use Norton Desktop for windows!

KegHead

---

### Post by Cenotaph on 2011-04-07
honestly, I think both gnome-shell and unity have strong and weak points, but at the same time, i feel like both are a step backwards (at this point!) from the classic gnome. If this is what we will have available in the near future, KDE4 starts to feel like the desktop we can rely on the most, which is ironic in a way.

---

### Post by KegHead on 2011-04-07
Hi!

I think I've posted previously that I've tested Xubuntu 11.04b and it looks pretty cool!

I just like streamlined computing!

KegHead

---

### Post by ratcheer on 2011-04-07
I think I see the problem. Gnome3 is for Fedora and Suse. :D

Tim

---

### Post by kaapstorm on 2011-04-07
@jfernyhough: Regarding uninstalling, you'll find instructions here: [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3]("http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3")

Summary:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
```

(I haven't tried it. I'm still wondering how to get my window decorations back. :-) )

---

### Post by KegHead on 2011-04-07
copy 69 & 70.

---

### Post by Mblackwell on 2011-04-07
> **kaapstorm said:**
> @jfernyhough: Regarding uninstalling, you'll find instructions here: [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3]("http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3")

Summary:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
```

(I haven't tried it. I'm still wondering how to get my window decorations back. :-) )

sudo apt-get install mutter

This wasn't done for me by default. Even if Shell doesn't run you can always:

```
DISPLAY=:0 mutter --replace &
DISPLAY=:0 gnome-panel &
```
from a VT. This will give you mutter as the window manager with the classic interface.

Then you can try to --replace Shell and get errors and then possibly do the above again and use the intertubes to find out if its fixable.

---

### Post by Brown_ on 2011-04-07
hahaha Lucky me it was a fresh ubuntu install. 
It freezes the GDM, after installing it... letting me to do nothing but a forced restart.

---

### Post by PWill on 2011-04-07
Well, the default GTK theme is the only one that seems to work. Every other GTK theme I choose falls back on some old school look.

I was able to get Mutter themed by going to gconf-editor: desktop/gnome/gnome-shell/windows and typing the theme I want in.

Ha. Definitely not usable. Funny, though. And well designed.

---

### Post by Starks on 2011-04-07
Uninstalling the GNOME 3 PPA with no ill effects is possible.

1. sudo ppa-purge ppa:gnome3-team/gnome3 (to downgrade a few packages and remove the deb line.

2. Manually downgrade gnome-settings-daemon in aptitude or synaptic.

3. sudo apt-get install -f (to downgrade the rest of the packages)

---

### Post by cecilpierce on 2011-04-08
I just upgraded one of my Natty's to Gnome3 and when I rebooted I get a black screen and a msg (failed to load session 'ubuntu') and I goto vt1 and kill gdm but it won't let me start unless I do sudo startx, then it works pretty good! Any ideas or suggestions ?

---

### Post by Mblackwell on 2011-04-08
You want to use the Gnome Shell session.

---

### Post by cecilpierce on 2011-04-08
> **Mblackwell said:**
> You want to use the Gnome Shell session.

How do I do that from a terminal, there is no choices at the login screen and I get that error when I try, can only start it as root,

 Thanks

---

### Post by Mblackwell on 2011-04-08
There should be at the bottom when you are typing your password.

---

### Post by 23dornot23d on 2011-04-08
Ok that is working nicely now ..... the odd error about the network - but its working now ..... [LINK ]("http://img163.imageshack.us/img163/6802/screenshot14w.png")

---

### Post by cecilpierce on 2011-04-08
> **Mblackwell said:**
> You want to use the Gnome Shell session.

The choice window is blank, besides it keeps giving me (failed to load session 'ubuntu') and goes back to login screen.
The only way I can get in is through vt1 as root, kill gdm and do sudo startx.

---

### Post by Cenotaph on 2011-04-08
> **cecilpierce said:**
> The choice window is blank, besides it keeps giving me (failed to load session 'ubuntu') and goes back to login screen.
The only way I can get in is through vt1 as root, kill gdm and do sudo startx.

I assume you uninstalled the gnome-session package, a pure upgrade will do that because of dependencies. you need to reinstall it. and get rid of gnome-session-common, iirc.

---

### Post by Starks on 2011-04-08
I'm having a lot of gnome-session problems.

I get the Windows 95 look if anything at all.

---

### Post by cecilpierce on 2011-04-08
> **Cenotaph said:**
> I assume you uninstalled the gnome-session package, a pure upgrade will do that because of dependencies. you need to reinstall it. and get rid of gnome-session-common, iirc.

I can't remember what I did Ive tried so many things I'm going nuts ! I'll check it out and see but I don't have much hope, it seems really screwed up,
 thanks

---

### Post by FEGuy on 2011-04-08
Are you guys installing from the Gnome3 PPA?

---

### Post by Mblackwell on 2011-04-08
> **23dornot23d said:**
> Ok that is working nicely now ..... the odd error about the network - but its working now ..... [LINK ]("http://img163.imageshack.us/img163/6802/screenshot14w.png")

sudo apt-get install network-manager-gnome

I notice it looks like the Adwaita theme isn't working for you.

Hmmm I don't see it in /usr/share/themes/ on my box either (I'm also using a jhbuild of Shell).

Here, I attached a build of the theme. You should be able to just extract the Adwaita folder to ~/.themes/

---

### Post by Mblackwell on 2011-04-08
> **cecilpierce said:**
> I can't remember what I did Ive tried so many things I'm going nuts ! I'll check it out and see but I don't have much hope, it seems really screwed up,
 thanks

A good simple strategy if you see problems is to:

```
sudo aptitude dist-upgrade
```

It will give you options instead of making decisions for you. You can see what packages are possibly going to removed and why. You can then (after deciding yes or no) work on fixing the discrepancy.

Any time it tries to do something wicked like remove gnome-session, don't upgrade quite yet unless you can get aptitude to give you a better option.

If you're going to be using an (still unfortunately) experimental PPA on top of an experimental release it's a good idea to get used to having terminal/package-manager fun!

---

### Post by 23dornot23d on 2011-04-08
Cheers Mblackwell ...... 

I seem to be sorted now ... for Gnome Session ...... ty ....... :D

---

### Post by Mblackwell on 2011-04-08
You're welcome. I edited my post btw with a recentish copy of the Adwaita theme for those it doesn't seem to be working for.

Also make sure you have the packages gnome-themes, gnome-themes-standard, gnome-icon-theme, and gnome-icon-theme-symbolic.

---

### Post by cecilpierce on 2011-04-08
Well I appreciate all your help and ideas its finally working pretty good (even have sound now) except for windows popping up with crashes but every thing comes back. No more Root where my name is !!!

Thanks, Cec

---

### Post by Quackers on 2011-04-09
Well, this time I'm nearly there :-)
I added the gnome3 team ppa and ran the updates. I rebooted and got to the login screen. I chose the Gnome-Shell option and the desktop loaded - along with cairo dock, gnome-shell and network-manager :-)
But no theme - just a magenta background. Everything else seems fine, just no desktop background and I'm getting the "Windows 95" style windows borders.
I checked in synaptic and the only package that appears to be missing is gnome-themes-standard, which I have just tried to re-install, but I got the error below :-(
Much improved though, from the last abortive attempt :-)  At least it's usable now!
Mblackwell, I tried extracting your Adwaita theme to ~/.themes and it's there. It's showing as a theme, but it's not appearing on the desktop :-(
Suggestions please?

---

### Post by Mblackwell on 2011-04-09
Someone will probably get mad at me, but if you really want it to work right now:

```
sudo dpkg -i --force-all /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_amd64.deb
```

Otherwise you can wait for the packages to be rebuilt with the dependency resolved.

---

### Post by Quackers on 2011-04-09
Thanks, I'll take a look.
Actually an update. I just installed gnome-themes and it went ok, but on logging out and back in I got this (and still just a magenta background). Nearly there though :-)

---

### Post by Quackers on 2011-04-09
Another update.
I ran the force-all option and it seemed to go ok, but still getting just a purple background after logging out/in.
Not a big problem as everything else is usable. Just a little bit irksome :-)
A massive improvement over last week's attempt though :-)

---

### Post by Quackers on 2011-04-09
Lol, it's working now :-)
I've chosen a background too. All seems good!
Strange.

---

### Post by gnomeuser on 2011-04-09
For many things I noticed that a newer version of gtk+ is required that what seems to be present in the Natty repos:

So I simply fetched these and installed them manually. Then the install of the gnome-themes-standard package e.g. was much smoother (though still needs forcing since it overlaps one file in the a11y theme package)

[https://launchpad.net/ubuntu/+source/gtk+3.0/3.0.8-0ubuntu1](https://launchpad.net/ubuntu/+source/gtk+3.0/3.0.8-0ubuntu1)

---

### Post by laborg on 2011-04-09
when can we expect the gnome-shell to be running smooth on unity? a couple of hours? a couple of days? a couple of months?

best regards

---

### Post by gnomeuser on 2011-04-09
> **laborg said:**
> when can we expect the gnome-shell to be running smooth on unity? a couple of hours? a couple of days? a couple of months?

best regards

Never, the question is non-sensical

Unity and gnome-shell are completely different desktop shell experiences and one cannot run one on top of another.

---

### Post by laborg on 2011-04-09
> **gnomeuser said:**
> Never, the question is non-sensical

Unity and gnome-shell are completely different desktop shell experiences and one cannot run one on top of another.

arghl... of course this shouldn't be unity but natty.

---

### Post by gnomeuser on 2011-04-09
> **laborg said:**
> arghl... of course this shouldn't be unity but natty.

It already works decently, to iron out the bigger missing bits given the engagement of the community I would guess a couple of weeks to be easily installable and usable.

It is hard to tell, I don't think anyone even has a clear idea of the exact number of problems and I certainly keep hitting new places where simply installing from the PPA utterly breaks things.

I don't think anyone can give you a clear answer, the best advice is likely to peek at the GNOME3 threads to get a better idea of the current state. Going by progress as it is today, I would guess it would be okay in a couple of weeks, brilliant in 6-12 months.

---

### Post by samigina on 2011-04-09
Ok, so Gnome3 will not work with Unity on the same team...

So, What if I do a CLI install with  the Alternate CD, add the PPA and do a "sudo apt-get install gnome-shell"?
It will works?

---

### Post by wedderburn on 2011-04-09
installed this ppa a few days ago, had to chroot and do some stuff to get my system up and running, question if i were to try again now what state would my install be in?

---

### Post by Quackers on 2011-04-09
Mine booted fine, but with no desktop background and no theme, as such.
That was soon fixed with the help of the last couple of pages of this thread (Mblackwell's posts helped me - thanks :-) )
This is vastly different from my attempt last week. (I ended up re-installing 11.04 :-) Packages were in a state of total confusion. Some wouldn't complete installing, some wouldn't be removed and others just weren't available.
It's working fine now though :-)  I hope it stays that way! :-)

---

### Post by Harry33 on 2011-04-09
> **Quackers said:**
> Mine booted fine, but with no desktop background and no theme, as such.
That was soon fixed with the help of the last couple of pages of this thread (Mblackwell's posts helped me - thanks :-) )
This is vastly different from my attempt last week. (I ended up re-installing 11.04 :-) Packages were in a state of total confusion. Some wouldn't complete installing, some wouldn't be removed and others just weren't available.
It's working fine now though :-)  I hope it stays that way! :-)

Did you install only Gnome-Shell with compulsory dependencies from the Gnome3 PPA (and then use GTK+2 gdm and gnome3-session to start Gnome-Shell)
or
did you install all the packages from Gnome3 PPA including Brasero, Gedit, Rhythmbox, Nautilus?
If so, do they all work on your setup?

---

### Post by coffeecat on 2011-04-09
Hmm. Gnome-shell is - interesting. I'll need to play with it more before I decide whether I prefer it or Unity.

I'm probably being a bit dense, but...

> **Mblackwell said:**
> Also make sure you have the packages gnome-themes, gnome-themes-standard, gnome-icon-theme, and gnome-icon-theme-symbolic.

Done.

> **Mblackwell said:**
>  if you really want it to work right now:

```
sudo dpkg -i --force-all /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_amd64.deb
```Otherwise you can wait for the packages to be rebuilt with the dependency resolved.

Had to do that. But..

> **Quackers said:**
> I've chosen a background too. All seems good!

How do I change the background? :?

---

### Post by Quackers on 2011-04-09
coffeecat, click on your username and select System Settings. In the new window the background is top left item.

Harry 33, I enabled the gnome3 ppa and ran synaptic and installed everything it had to offer :-)
I haven't tested everything yet though, but all ok so far.

---

### Post by coffeecat on 2011-04-09
> **Quackers said:**
> coffeecat, click on your username and select System Settings. In the new window the background is top left item.

Indeed. :) What happened was that despite running 'sudo aptitude safe-upgrade' **and** 'sudo apt-get dist-upgrade' after installing gnome-shell from the gnome3-team ppa, Synaptic told me there were even more upgrades pending from the ppa. Once I'd installed those I was able to open System Settings from the  username drop-down menu.

All good now.

---

### Post by Quackers on 2011-04-09
Aha! :-)  Time to explore!

---

### Post by webme on 2011-04-09
Finally, the "gdm" package is in THE GNOME 3 PPA.

---

### Post by Quackers on 2011-04-09
Installed :-)
Sadly synaptic wouldn't close again after installing the package. Had to reboot.
All ok now except autologin still gives the password prompt! Strange.

ps  I'm unable to log in to Ubuntu or Ubuntu Classic desktops now. Cannot start the sessions.

---

### Post by Starks on 2011-04-09
Wait. gdm only just landed?

What other packages is the PPA still waiting on?

I'm really hesitant to give it a 3rd try until the process is problem-free.

---

### Post by coffeecat on 2011-04-09
Installed the new gdm package. Ho-hum. That's a bit blue and stripey. Reminds me of particularly bad 1970s living-room wallpaper. :( Any way of changing it?

---

### Post by Quackers on 2011-04-09
> **coffeecat said:**
> Installed the new gdm package. Ho-hum. That's a bit blue and stripey. Reminds me of particularly bad 1970s living-room wallpaper. :( Any way of changing it?

Do you have it as a desktop background or are you just talking about the login screen background?

---

### Post by jontxo on 2011-04-09
Hello

The update of the gdm hasn't gone well for me. The list of users dissapeared and I have only the option of other with which I am unable to log into the system I have downgraded the package to the previous version and now I am able to login into the system, but the theme is broken. 

Have this happened to someone else?

---

### Post by 23dornot23d on 2011-04-09
I am now running GNOME-SHELL experimental ...... everything is fantastic ...... just love this layout now
I also add cairo-dock ..... its just the way I like my layout ...... but I am getting some tearing on the screen
when using the forums and Firefox 4.0 ....

Just wanted to try to work out if others are experiencing the same thing or not ...... is it because I have cairo-dock running ...... (will disable it after I have written this just to see if it makes any difference)

But feel free to comment ...... if there are any known issues .....

---

### Post by Quackers on 2011-04-09
I'm using gnome-shell and Cairo-dock also. No tearing of any kind here (using nvidia 270.30 driver).
I did lose the ability to log in to Ubuntu or Ubuntu Classic desktops though. Still can't :-)

---

### Post by 23dornot23d on 2011-04-09
Ok thanks for the quick reply ... 

I too am using the same driver Nvidia 270.30 ,,,, with 64 bit 11.04 .... its a old graphics card in this machine though or old-ish ..... a Nvidia GeForce 6200 .....

Still doing it without Cairo-Dock ...... seems we have a small problem here ......

trying to do a screen shot of it - but as soon as I invoke the snapshot it rectifies itself ...... its not doing it constantly neither - hard to get it to replicate ...... 


Will see if I get the same problems going into CLASSIC - it was ok earlier though .....   :D

Updated :- Classic still runs fine .... 
( will update this if I get any more tearing .... but at moment seems to be just in Gnome Shell )

Also noticed in GNOME-SHELL ..... just one X in top right to close a window ...... no minimize or maximise buttons
and changing the theme layout does not alter it at all ....

Updated again - UNITY - runs fine too ......

One more thing with Gnome -shell ....... is there a way to choose the hotspot ..... top left on dual monitors in twinview it is a pain
to find the hotspot to get to the menus

---

### Post by kansasnoob on 2011-04-09
> **Quackers said:**
> I'm using gnome-shell and Cairo-dock also. No tearing of any kind here (using nvidia 270.30 driver).
I did lose the ability to log in to Ubuntu or Ubuntu Classic desktops though. Still can't :-)

I've been quite busy. Would you mind writing a sort of "review" of the steps you took to get here :D

You needn't retype every step but just:

I did such-n-such, then I did what I was told here, yada-yada so we can follow the steps you took :D

Full disclosure; probably after Beta 2 iso-testing I'll try gnome3 with both available PPA's. I almost can't wait for the Oneiric toolchain in about 8 to 10 weeks :P

---

### Post by Mblackwell on 2011-04-09
@23dornot23d: Is it only when using the overview or message tray, and only when there's an old-style (legacy) system tray icon in the message tray? Because that's a known issue.

I could have you build Shell with custom patches, or wait until NVIDIA fixes the issue in their driver, OR... you could try and mitigate it a bit by setting your Powermizer setting (in NVIDIA Settings) to Prefer Maximum Performance.

Note that the Powermizer setting will reset every login.

---

### Post by 23dornot23d on 2011-04-09
I have just moved to my laptop with a Nvidia 9300M GS and there are no problems on this ......
so as you say its a performance issue with the older graphics card ..... no real problem ,,,,,

What about the X in the top right ..... is that meant to be alone now .... no minimize maximise buttons

[IMG]http://img849.imageshack.us/img849/9527/crossm.jpg[/IMG]

---

### Post by Mblackwell on 2011-04-09
It's not a bug. You can still minimize by right clicking the title bar. Maximizing is now gestural: Simply drag the window to the top to fill the screen or to either side to do side by side tiling. Or you can double click the title bar.

Minimize isn't really something that fits with the Shell workflow generally. At least not at this point. But it's still there if you really need it via the title bar menu.

---

### Post by 23dornot23d on 2011-04-09
Thank you once again .....

Ok am happy ... can work with this now .... and moved the twinview so the main monitor is on the left now
so that I can get the hotspot to get to the menus on it easily ,,,, ( does not work at all well on the right )
but again no real problem .... think we are in business .... looking good .... 

Will start testing it now .... with all the 3D applications that I like to use ,,,,, glad the Global menu is not used here too ,,,,,, :)

Going to try Gtkrecord my desktop too as I had issues with this a while back ...... hopefully they are fixed now.

---

### Post by coffeecat on 2011-04-09
> **Quackers said:**
> Do you have it as a desktop background or are you just talking about the login screen background?

The login screen background. It's also there as the first choice of desktop backgrounds and called "Default Background". I don't remember it being there before so I assumed it had come in with the gnome 3 packages.

---

### Post by Mblackwell on 2011-04-09
It did.

---

### Post by coffeecat on 2011-04-09
Apart from how to get rid  rid of that migraine-inducing blue gdm background, I have two more questions:

Under my username I can see logout and suspend, but no shutdown or restart. No options to do so on the gdm screen either - not that I can see with that blue disaster dazzling my eyes. :wink: I'm having to 'sudo shutdown -h now' or 'sudo reboot' from a terminal. Am I missing something?

Also - calling fellow Brits. I can't get a UK keyboard layout. See screenshot. That's the correct setting but that ain't no UK keyboard layout. Am I doing something wrong or is a bug-report in order here?

---

### Post by Mblackwell on 2011-04-09
Don't know on the UK keyboard layout. For the background you'd have to probably change the image file being referenced by the gdm theme. There should be a shutdown on the lower bar in GDM.

Hold ALT to see the shutdown option in the User Menu, or simply press the power button and Shell will pull up the Shutdown/Restart screen.

---

### Post by coffeecat on 2011-04-09
> **Mblackwell said:**
> There should be a shutdown on the lower bar in GDM.

No lower bar in my gdm screen.

> **Mblackwell said:**
>  Hold ALT to see the shutdown option in the User Menu

Curious design feature, but it works. Thanks.

---

### Post by buzzmandt on 2011-04-09
> **Mblackwell said:**
> 

Hold ALT to see the shutdown option in the User Menu, or simply press the power button and Shell will pull up the Shutdown/Restart screen.
Ok thats just bizarre right there.  Hows someone suppose to know that if they don't have the forums or a 13 year old child lol.

anyway, using kdm login screen and it works quite well.  I prefer kde at this point but i like having other login options available to play with.

edit: i also have no themes options and firefox looks win98ish

---

### Post by Mblackwell on 2011-04-09
They would know it by pressing the power button. See, we've made it okay to use again!

---

### Post by Quackers on 2011-04-09
coffeecat, there's no reboot option available. For shutdown click on the username and press the Alt key.
In settings you can choose that the power button when pressed gives you the option of what you want to do. If you choose that option instead of shutdown, or whatever, you will receive a screen prompt when the button is pressed which offers a restart option.
For the desktop background change, you can click on the username and select System Settings, then the first option on the new screen is Background. Does that allow you to change backgrounds? It does here :-)

kansasnoob,
I enabled the gnome 3 team ppa (as advertised early on in this thread, I believe) and then ran synaptic. It gave loads of updates and I installed them all then rebooted.
Gnome-shell desktop started on login, but it had no theme (other than a Windows95 type thing) or background. Just a plain magenta background. But cairo-dock was working straight away :-)
I installed gnome-session as advised by cenotaph in post #82.
gnome-session-common had already been removed, so that was fine.
I then downloaded and extracted the Adwaita file that Mblackwell posted (to ~/.themes) but that had no effect. (post #86)
I then rebooted for good measure.
No change except that I could not log in to either Unity (ubuntu) or Ubuntu Classic (which I didn't check before then).
I then checked that the packages gnome-themes, gnome-themes-standard, gnome-icon-theme, and gnome-icon-theme-symbolic were installed (as per post #89) and if not I installed them. Some were, some weren't (though I think that's fixed now).
gnome-themes-standard needed the force-all option to install.
I then went to username and selected System Settings and then Background, and changed the background.
All good then, except for no proper theming.
I rebooted again and all was the same.
After some fiddling here and there (not relevant here) I rebooted again and the theme arrived :-) 
All has been well since, except for 2 instances of Synaptic "not responding" after updates had been installed. It would not shutdown and I neeeded to reboot in order to get synaptic to start up again.
I think that's it now :-)

EDIT
coffeecat for keyboard disable auto login and on logging out you will get the keyboard option bottom left at the new login (after clicking on your username iirc).

---

### Post by coffeecat on 2011-04-09
> **Quackers said:**
> For the desktop background change, you can click on the username and select System Settings, then the first option on the new screen is Background. Does that allow you to change backgrounds? It does here :-)

Oh yes, I can change the desktop background - see my screenshot. It's the gdm background I'm moaning and groaning about. :wink:

And talking of my screenshot, are you getting the not-made-in-the-UK UK keyboard "layout"?. (I had to press the @ key to get those double-quotes. And I had to press the " key to get the @ symbol... ](*,)

---

### Post by Quackers on 2011-04-09
> **coffeecat said:**
> Oh yes, I can change the desktop background - see my screenshot. It's the gdm background I'm moaning and groaning about. :wink:

And talking of my screenshot, are you getting the not-made-in-the-UK UK keyboard "layout"?. (I had to press the @ key to get those double-quotes. And I had to press the " key to get the @ symbol... ](*,)

No :-) See my edit to my previous post.

---

### Post by coffeecat on 2011-04-09
> **Quackers said:**
> No :-) See my edit to my previous post.

> **Quackers said:**
> EDIT
coffeecat for keyboard disable auto login and on logging out you will get the keyboard option bottom left at the new login (after clicking on your username iirc).

Nope. :) Never had auto login enabled anyway. There's no lower bar in my gdm screen even after clicking on my username. Ergo, no keyboard option. But the power button has appeared on my gdm screen now. Not on the non-existent lower bar, but at extreme top-right. :?

I've heard that there's this alternative shell called Unity. Seems like a good idea. I might give it a try. :lol: At least I won't have to type " for @, and @ for ".

---

### Post by Quackers on 2011-04-09
I don't know what's happened to your keyboard boss. I'm not having that problem.
You're right about the power item disappearing though! It's gone! What the ?
It's no biggy here, as I've set the power button to ask me what to do when I press it, so I can reboot or power down. Strange though.
I'll see if there are any updates I haven't run. Something else may disappear :wink:  :-)

---

### Post by FEGuy on 2011-04-09
So aside from some quirks that seem to be caused by how Gnome3 works versus other desktops, the PPA's stable to install and upgrade from? No more ICEAuthority messages on trying to log in and such? I'm really eager to try this again, but it took me 4 hours or so to undo the changes last time, and another couple days of trying to isolate and remove the bugs left behind.

---

### Post by Cam! on 2011-04-09
I just installed a fresh daily build of 11.04 an hour ago, and I'm curious to see how Gnome 3 looks and feels. Is it safe to use?

---

### Post by gnomeuser on 2011-04-09
> **FEGuy said:**
> So aside from some quirks that seem to be caused by how Gnome3 works versus other desktops, the PPA's stable to install and upgrade from? No more ICEAuthority messages on trying to log in and such? I'm really eager to try this again, but it took me 4 hours or so to undo the changes last time, and another couple days of trying to isolate and remove the bugs left behind.

You may have to manually update a few packages using dpkg but aside that the PPA provides a workable desktop. I am using it presently.

There are though major rough edges. Network-manager looks very out of place, anything using Ubuntu One seems prone to failure. Anything patched for application indicators will act in an unexpected manner (but should for the most part work). Language selector has issues. I can't get build deps for Banshee (sob).

The initial install is a bit bothersome but after that it seems to work well and improve rapidly in feel and function. The PPA people do good work.

What it lacks is full GNOME branding for things like the bootsplash which I feel would raise the experience. A GNOME3 desktop, powered by Ubuntu is what I really want. They can define the experience, Ubuntu can compliment it where it lacks. E.g. the excellent home dir encryption feature and apparmor. Adopt where it should, such as PackageKit which is very likely to see further integration and with AppStream it seems like an effort worth investing in. Likewise for systemd, it sounds like the sysd team plan to do session management in a similarly smart fashion which would provide GNOME with a set of interesting features (e.g. we can do latency, scheduling and io tracking and policy enforcement on a per application level).

---

### Post by wedderburn on 2011-04-09
sweet, gnome shell's working well atm and the gdm also tops it off, 
when can we expect epiphany to land?, on the gnome live cd's it did feel very snappy compared to firefox on the same disk.

---

### Post by cariboo on 2011-04-09
Merged two threads on the same subject.

---

### Post by t.rei on 2011-04-10
How can anyone expect it to be "safe to use" if it's a first release, from a ppa, on an alpha version of an os?

If you want safe, go LTS. :)

But yes, it works rather well, by now. I like it. I think it's a keeper. But I am going to take a look at the fedora live cd now.

---

### Post by cpatrick08 on 2011-04-10
> **t.rei said:**
> How can anyone expect it to be "safe to use" if it's a first release, from a ppa, on an alpha version of an os?

If you want safe, go LTS. :)

But yes, it works rather well, by now. I like it. I think it's a keeper. But I am going to take a look at the fedora live cd now.
or try opensuse version of gnome 3  you need to add liveinstall  to make it installable [http://download.opensuse.org/repositories/GNOME:/Medias/images/iso/](http://download.opensuse.org/repositories/GNOME:/Medias/images/iso/)

---

### Post by Bou on 2011-04-10
> **Quackers said:**
> coffeecat, there's no reboot option available. For shutdown click on the username and press the Alt key.
In settings you can choose that the power button when pressed gives you the option of what you want to do. If you choose that option instead of shutdown, or whatever, you will receive a screen prompt when the button is pressed which offers a restart option.
For the desktop background change, you can click on the username and select System Settings, then the first option on the new screen is Background. Does that allow you to change backgrounds? It does here :-)

kansasnoob,
I enabled the gnome 3 team ppa (as advertised early on in this thread, I believe) and then ran synaptic. It gave loads of updates and I installed them all then rebooted.
Gnome-shell desktop started on login, but it had no theme (other than a Windows95 type thing) or background. Just a plain magenta background. But cairo-dock was working straight away :-)
I installed gnome-session as advised by cenotaph in post #82.
gnome-session-common had already been removed, so that was fine.
I then downloaded and extracted the Adwaita file that Mblackwell posted (to ~/.themes) but that had no effect. (post #86)
I then rebooted for good measure.
No change except that I could not log in to either Unity (ubuntu) or Ubuntu Classic (which I didn't check before then).
I then checked that the packages gnome-themes, gnome-themes-standard, gnome-icon-theme, and gnome-icon-theme-symbolic were installed (as per post #89) and if not I installed them. Some were, some weren't (though I think that's fixed now).
gnome-themes-standard needed the force-all option to install.
I then went to username and selected System Settings and then Background, and changed the background.
All good then, except for no proper theming.
I rebooted again and all was the same.
After some fiddling here and there (not relevant here) I rebooted again and the theme arrived :-) 
All has been well since, except for 2 instances of Synaptic "not responding" after updates had been installed. It would not shutdown and I neeeded to reboot in order to get synaptic to start up again.
I think that's it now :-)

EDIT
coffeecat for keyboard disable auto login and on logging out you will get the keyboard option bottom left at the new login (after clicking on your username iirc).

I followed this message as a checklist in order to get a working shell, but when I log in I only get the blue wallpaper and nothing else. There's no shell, no nothing. Right clicks do nothing. When error messages pop up (nothing informative), they don't have any decorations.

Am I missing something here? Anything I can do? :confused:

---

### Post by 23dornot23d on 2011-04-10
@Bou

Open up a Classic Desktop .........

open a terminall window and type in it

gnome-shell --replace

then post the information that appears in that terminal window ...... it may give more clues .....

---

### Post by Bou on 2011-04-10
That's the funny part... it won't even let me start a classic session. I get a pop-up telling me "failed to load session classic-gnome", and only offers me to "close session".

---

### Post by 23dornot23d on 2011-04-10
( The list you followed was also a set of steps that ended up with the same problem ....... )

Can you get in any desktop without compiz running ?

Can you get into any desktop that works at all - now ?

If not try ..... 

ctrl+alt+f1 (login as USER) then do the following

sudo apt-get update
sudo apt-get install aptitude
sudo apt-get aptitude safe-upgrade

To see if updating the system will cure it ...........

---

### Post by Quackers on 2011-04-10
> **23dornot23d said:**
> ( The list you followed was also a set of steps that ended up with the same problem ....... )

That's true! :-)  I said that :-)
Mine is still the same way. Others don't seem to have that problem.

Bou, I needed to do a few restarts until everything loaded correctly. Try that, if you haven't already.

---

### Post by Bou on 2011-04-10
> **23dornot23d said:**
> Can you get into any desktop that works at all - now ?

Nope, no desktop at all.

> **23dornot23d said:**
> If not try ..... 

ctrl+alt+f1 (login as USER) then do the following

sudo apt-get update
sudo apt-get install aptitude
sudo apt-get aptitude safe-upgrade

To see if updating the system will cure it ...........

Just did, but it said everything was already up to date. Is there a way that you can ctrl+alt+f1 and tell the system to launch gnome-shell replace in display 0, so I can see if there are any error messages?

> Bou, I needed to do a few restarts until everything loaded correctly. Try that, if you haven't already. 

You mean that the shell didn't load, then after rebooting for a few times it did, just like that?

---

### Post by Quackers on 2011-04-10
No, the gnome-shell loaded, but without a theme or background.

Is post #57 what you're after?
[http://ubuntuforums.org/showthread.php?t=1722627&page=6](http://ubuntuforums.org/showthread.php?t=1722627&page=6)

EDIT
Actually, iirc, the first time I booted I got just an empty purple screen, nothing else. I then rebooted and it started up.

---

### Post by bmbaker on 2011-04-10
do you need to un-install unity before adding the gnome3 ppa ?
and do you need to re-install it after upgrading to gnome3 ?
cheers

---

### Post by Quackers on 2011-04-10
> **bmbaker said:**
> do you need to un-install unity before adding the gnome3 ppa ?
and do you need to re-install it after upgrading to gnome3 ?
cheers

I didn't uninstall unity first, and, on checking just now, it is still installed.

---

### Post by jfernyhough on 2011-04-10
I have the mozilla-daily PPA and last I tried it looks like gnome-shell doesn't like the version of libmozjs.so that xulrunner-2.0-mozjs from the PPA provides; gnome-shell doesn't load at all!

I also have Ubuntu and Ubuntu Classic sessions showing in GDM but when I try to log on with either it tells me "unable to load session". Interesting.

ppa-purge'd back for the minute. :)

---

### Post by Bou on 2011-04-10
> **Quackers said:**
> Is post #57 what you're after?
[http://ubuntuforums.org/showthread.php?t=1722627&page=6](http://ubuntuforums.org/showthread.php?t=1722627&page=6)

Absolutely! Now the only problem is that the wallpaper looks all scrambled until I change it, but that's nothing I can't fix.

I guess now that I can actually start a session, I can use the settings so that gnome-shell --replace will be run at session start, right?

---

### Post by bmbaker on 2011-04-10
> **Quackers said:**
> I didn't uninstall unity first, and, on checking just now, it is still installed.
ok thanks alot :-)

---

### Post by Quackers on 2011-04-10
> **Bou said:**
> Absolutely! Now the only problem is that the wallpaper looks all scrambled until I change it, but that's nothing I can't fix.

I guess now that I can actually start a session, I can use the settings so that gnome-shell --replace will be run at session start, right?
Hmm, it seems you have different issues to me. For some reason gnome-shell isn't starting automatically for you. Mine fires right up with no graphics problem of any kind.
Maybe differences in hardware can account for some problems.
It seems that one or two other users are having the "failed to load session" that I get if I try to load Ubuntu or Ubuntu Classic from the gdm login screen. Others are not having that problem at all.

I'm sure there are many updates yet to come (probably breakages too!).

---

### Post by cecilpierce on 2011-04-10
How do I login to Classic or Ubuntu ?

When I logout and try i get failed to load session 'ubuntu'

---

### Post by coffeecat on 2011-04-10
> **cecilpierce said:**
> How do I login to Classic or Ubuntu ?

When I logout and try i get failed to load session 'ubuntu'

Ditto here. Only gnome-shell loads from gdm.

---

### Post by KegHead on 2011-04-10
System, admin, login?

---

### Post by coffeecat on 2011-04-10
> **KegHead said:**
> System, admin, login?

No System > Admin menu in gnome-shell and Login Screen Settings utility doesn't help.

---

### Post by KegHead on 2011-04-10
system settings...control center...login screen?

---

### Post by coffeecat on 2011-04-10
> **KegHead said:**
> system settings...control center...login screen?

Login Screen settings from the applications search didn't help unfortunately - screenshot 1. If your System Settings has login screen, then it's gone awol from mine - screenshot 2.

---

### Post by Quackers on 2011-04-10
Coffeecat, when you move the pointer to the top left corner of the screen does a new screen appear which is a slightly darker background and has two headings - Windows and Applications?
If so, if you click on the Appliocations heading what happens?
Originally this opened up a screen full of icons for every installed application.
All it does now is show one icon (for additional drivers). The others have disappeared! I now need to click on the search box, top right, to search for applications.
Is this happening for you too?

---

### Post by coffeecat on 2011-04-10
> **Quackers said:**
> 
Is this happening for you too?

No. It seems OK for me. Three pictures being worth a thousand words:

Screenshot 1 = working desktop
Screenshot 2 = after pressing super key. The same happens after clicking on Activities top left.
Screenshot 3 = after clicking on Applications.

---

### Post by KegHead on 2011-04-10
Ouch!

I can only comment from gnome 2.3. 

Sorry!

I truly wish I could help.

Anyone?

KegHead

---

### Post by coffeecat on 2011-04-10
> **KegHead said:**
> 
Sorry!

I truly wish I could help.

No worries! :) I don't expect it to work 100% - I'm just comparing notes with everyone. Just the fun of trying out pre-release stuff.

---

### Post by Quackers on 2011-04-10
Hmm, this is what I'm getting after clicking on Applications, that used to be like yours :-)

---

### Post by KegHead on 2011-04-10
coffeecat,

copy!

KegHead

---

### Post by coffeecat on 2011-04-10
> **Quackers said:**
> Hmm, this is what I'm getting after clicking on Applications, that used to be like yours :-)

Hmmm, indeed! That's not much fun. :(

---

### Post by Quackers on 2011-04-10
No! They seem to have disappeared on running a couple of "minor" updates :-)
I can use the search box, so it's ok, I can still get to things. 
I've also got cairo-dock as a backup too :-) That works well.

---

### Post by bmbaker on 2011-04-10
well i have everything running quite smothly, the only thing i still haven't managed to do is log back into unity or ubuntu desktop ! anyone else managed the get this wking?
cheers

usefull link for doing some customizing :-) :-)

[URL="http://www.scribd.com/doc/52625225/Customizing-the-GNOME-3-Shell"]http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html
[/URL]

---

### Post by Bou on 2011-04-10
I just realised I'm still getting Ubuntu's notifications. How did you disable that?

---

### Post by kansasnoob on 2011-04-10
I ended up taking a different approach:

[http://ubuntuforums.org/showpost.php?p=10660251&postcount=73](http://ubuntuforums.org/showpost.php?p=10660251&postcount=73)

It works, but it's certainly not flawless.

I also mentioned here how I managed to force the "classic look" fallback:

[http://ubuntuforums.org/showpost.php?p=10662567&postcount=49](http://ubuntuforums.org/showpost.php?p=10662567&postcount=49)

**[COLOR="Red"]Just remember, if you break it you own it![/COLOR]**

---

### Post by Mblackwell on 2011-04-11
Alt+F2 ```
killall -9 notify-osd
```

Alt+F2 ```
r
```

Note that the second one restarts the Shell. This is handy for things like if you end up playing with JS files, or get some updates to Shell/Mutter/etc. No reboot/relogin necessary.

If you get weird errors with only a single icon appear in the app screen this can usually fix that as well.

---

### Post by wolfen69 on 2011-04-11
What happened to Restart/Shutdown options? Right now I have to log out, *then* shutdown.

---

### Post by Justin Trouble on 2011-04-11
> **wolfen69 said:**
> What happened to Restart/Shutdown options? Right now I have to log out, *then* shutdown.

Press the Alt key when the menu is open and "Suspend" magically changes to "Power Off..."! :o

---

### Post by t.rei on 2011-04-11
Now that alt key is not that intuitive - thanks for the hint. 

I have gnome-shell from the ppa running for a few days now - I like it.

However there are three issues I'm still having: 
1) No application stores keys in the keyring or it does not get unlocked or used
2) empathy does not remember my icq account
3) I'm still having the 'old' nm-applet - not the one like in fedora live cd (minor issue - just beauty)

---

### Post by Mblackwell on 2011-04-11
It's not really supposed to be intuitive (pressing Alt to shut down). Suspend is the default behavior if your computer supports it otherwise you're supposed to:

A) Log out and shut down.
or
B) Press the power button to bring up the shut down menu.

So Alt is really just a shortcut to either of those actions.

---

### Post by zika on 2011-04-11
Just to check if I've got it right.
If I add aforementioned ppa, upgrade, I get Gnome3 and loose Classic Desktop, as it is now available in Natty?
Also: is ppa now in a state that complete upgrade is available?
I presume that I could use FluxBox, by means of ~/.xsession, without starting Gnome3, as I do now with Gnome2... Am I right?
Gnome3 breaks Unity, I read, but does it break Unity-2d?

---

### Post by Quackers on 2011-04-11
That has been the case for both my Natty installs, which I have moved to gnome-shell with. The problems are less now. However, after updates last night I now have to login as "other" but with my normal username and password.
As I understand it, it is necessary to disable autologin before rebooting after updating using the gnome3 ppa.
Please note that although the system is eminently usable, it is not absolutely complete (I think) and obviously, as with Natty, updates could break it! I am taking care when running updates! I use synaptic for that.
(That's why I have 2 Nattys/gnome-shell running at the same time. If one gets broken, I can use the other, but run no updates on that until any problem is fixed).

---

### Post by bmbaker on 2011-04-11
yes i set up the same way, one for use and one for testing, but i think i will remove unity as its not accessible anyway.
just loving gnome3 :-)

Just checked and my login shows 
for my name and then pw
the last upgrade changed it i think!

correction it only does normal login from a full shutdown!

---

### Post by samigina on 2011-04-11
No one answer my previous question :(

... What about a CLI install with ALternate CD, add the PPA, and doing a "sudo apt-get install gnome-shell"??

I tried installing gnome-desktop-environment but aptg give me dependencies problems.

Right now Im triying with gnome-shell in a CLI install, Ill report in a while...

---

### Post by t.rei on 2011-04-11
It'll probably be something like:

```
sudo apt-add-repository ppa:gnome3-team/gnome3
sudo apt-get update && sudo apt-get dist-upgrade
```optionally, just to make shure all dependencies are installed:
```
sudo apt-get install gnome-shell gnome-session gdm
```that should actually be all you have to do on the alternate install, no?

To show the weird old style nm-applet I'm getting right now:
[IMG]http://i.imgur.com/FWr3t.jpg[/IMG]

Anyone has an idea if thats an option or something? It is the program contained in the ppa's network-manager-gnome package.

---

### Post by Quackers on 2011-04-11
I got that for one session earlier, but it's gone again now :-)

BTW, if you prefer to have the maximise/minimise buttons in the top bar (and the date showing in the top panel) you can tweak these and a few other things by installing gnome-tweak-tool - available through synaptic.

Thanks to fbmurphys blog for the info
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

---

### Post by Starks on 2011-04-11
Things seem to be somewhat stable now that I've got Adwaita set up.

When used with a worn-in install, the shell provides a somewhat more immersive experience than Unity. Not having global menus does suck hard and take up screen space.

---

### Post by sammiev on 2011-04-11
On mine when I use in a certain style, it was my wireless strength. GL :)

> **t.rei said:**
> It'll probably be something like:

```
sudo apt-add-repository ppa:gnome3-team/gnome3
sudo apt-get update && sudo apt-get dist-upgrade
```optionally, just to make shure all dependencies are installed:
```
sudo apt-get install gnome-shell gnome-session gdm
```that should actually be all you have to do on the alternate install, no?

To show the weird old style nm-applet I'm getting right now:
[IMG]http://i.imgur.com/FWr3t.jpg[/IMG]

Anyone has an idea if thats an option or something? It is the program contained in the ppa's network-manager-gnome package.

---

### Post by Starks on 2011-04-11
Grrr. Touchpad touch clicking doesn't work.

---

### Post by KegHead on 2011-04-11
Hi!

I just remembered why I'm a dyed in the wool 11.04b/classic/2.6.39-999 user!

KegHead

---

### Post by dext on 2011-04-11
> **t.rei said:**
> It'll probably be something like:

```
sudo apt-add-repository ppa:gnome3-team/gnome3
sudo apt-get update && sudo apt-get dist-upgrade
```optionally, just to make shure all dependencies are installed:
```
sudo apt-get install gnome-shell gnome-session gdm
```that should actually be all you have to do on the alternate install, no?

To show the weird old style nm-applet I'm getting right now:
[IMG]http://i.imgur.com/FWr3t.jpg[/IMG]

Anyone has an idea if thats an option or something? It is the program contained in the ppa's network-manager-gnome package.

PPA can be found here  [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

---

### Post by FEGuy on 2011-04-11
> **Starks said:**
> Grrr. Touchpad touch clicking doesn't work.
Click your name, go to system settings, and go to Mouse and Touchpad's Touchpad tab, then click 'Enable mouse clicks with touchpad'. I don't know why it's disabled by default, but it's annoying as hell.

---

### Post by t.rei on 2011-04-11
yeah, thats what I installed it from - strange thing being: the nm-applet (installed from network-manager-gnome package on that very ppa) looks and acts like the original gnome2 one. (so no pretty popup, and the 'old' optics).

Still haven't figured out what is going on there. 

And my keyring still doesn't seem to work on neither my original user or even completely new users. Or it's an empathy thing, as icq accounts are not remembered at all, either.

Well, since the rest of the UI is working so amazingly smooth, I'm just going to stick with it and see what updates might cause in the next weeks or so. :)

---

### Post by M4570D0N on 2011-04-11
> **Quackers said:**
> I got that for one session earlier, but it's gone again now :-)

BTW, if you prefer to have the maximise/minimise buttons in the top bar (and the date showing in the top panel) you can tweak these and a few other things by installing gnome-tweak-tool - available through synaptic.

Thanks to fbmurphys blog for the info
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

This was mentioned on Web Upd8 last week, as well. Also, another post on theere from last week:

[**GNOME Shell Extensions: Additional Functionality For GNOME Shell (Dock Task-Switcher, Windows Navigator, User Theme, Etc.**)]("http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html")
> **Alternative tab:** use the classic ALT + Tab

**Alternative Status Menu: **adds a "Power off" menu item visible at all time (and not just when pressing the ALT key) in the status menu.

**Dock: **shows a dock-style task switcher to the right side of the  screen and is visible all the time (unlike the Dash "dock" displayed on  the left that's only displayed in the "Activities" view). Right now, the  dock looks almost the same as the Dash dock except it's smaller.

Gnome Shell Dock Extension comes with very basic functionality: display a  list of running applications and add/remove applications as favourites:

[CENTER][[IMG]http://lh5.googleusercontent.com/_1QSDkzYY2vc/TZ2mpChfsSI/AAAAAAAAD68/7SrbE1hRqMY/s400/shell-extension1.png[/IMG]]("http://lh5.googleusercontent.com/_1QSDkzYY2vc/TZ2mpChfsSI/AAAAAAAAD68/7SrbE1hRqMY/shell-extension1.png")[/CENTER]


**Auto Move Windows:** you can assign a specific workspace to each application.

**Gajim: **Integration with Gajim, a Jabber/XMPP instant messaging client.

**User Theme**: Loads a shell theme from ~/.themes/THEME_NAME/gnome-shell.

**Windows Navigator:** Allow  keyboard selection of windows and workspaces in overlay mode: when you  hold the ALT key, a number is assigned to each window (displayed in the  top left corner) and you can then press the number to switch to that  window:


[CENTER][[IMG]http://lh6.googleusercontent.com/_1QSDkzYY2vc/TZ2mpckXulI/AAAAAAAAD7A/_DgCtJBy1Pg/s400/shell-extension2.png[/IMG]]("http://lh6.googleusercontent.com/_1QSDkzYY2vc/TZ2mpckXulI/AAAAAAAAD7A/_DgCtJBy1Pg/shell-extension2.png")[/CENTER]


**Xrandr Indicator:** Replace the  GTK+ based indicator from gnome-settings-daemon with a native one. Lets  the user rotate the laptop monitor and open display preferences quickly.


...

**You can get the extensions @ [http://git.gnome.org/browse/gnome-shell-extensions/](http://git.gnome.org/browse/gnome-shell-extensions/)**

---

### Post by Quackers on 2011-04-11
I've been busy :-)
I've resized all my applications icons and the spaces between them

---

### Post by M4570D0N on 2011-04-11
Regarding the Gnome Shell Extensions mentioned above, in the comments of that article, Andrew (aka nilarimogard/ aka dude that runs Web Upd8 ) was nice enough to also post some install instructions for those that are new to git.

> Install the GNOME Shell extensions:

cd ~/gnome-shell/source
git clone [http://git.gnome.org/browse/gn...]("http://git.gnome.org/browse/gnome-shell-extensions")
cd gnome-shell-extensions
./[autogen.sh]("http://autogen.sh/") --prefix $HOME/gnome-shell/install/
make && make install

Then simply start Gnome Shell.

By  default, only about 4 extensions are enabled. If you run it with  "./configure --prefix $HOME/gnome-shell/install/  --enable-extensions=all", you'll get some missing dependencies so you  can't build them all unless you build all the other dependencies. I've  only built 5: the 4 default extensions and the user theme extension. For  that, you just have to run configure with   "--enable-extensions=user-theme" (I don't really remember if it was  called "user-theme" exactly).


Regarding Gnome Tweak tool...  that's already in the Gnome 3 PPA. If you want to run it from source,  just get the code and run it, it should work. I've only tested it using  the Live CD though. Get the code:
git clone [http://git.gnome.org/browse/gn...]("http://git.gnome.org/browse/gnome-tweak-tool")
cd gnome-tweak-tool
./gnome-tweak-tool

That's  all I did on the Live CD. you may need to specify the path to jhbuild  like so: "./gnome-tweak-tool  -p /path/to/jhbuild/prefix".



Both have a README for more info.

---

### Post by wojox on 2011-04-11
> **Quackers said:**
> I've been busy :-)
I've resized all my applications icons and the spaces between them

I spent like two hours yesterday looking for how to do that, found it and overwrote it with a new theme. Must back up better.

---

### Post by Quackers on 2011-04-11
Ouch :-)

---

### Post by splicerr on 2011-04-11
What hardware/drivers are you guys using, nvidia?  Anyone have success with ATI GPU and fglrx?

---

### Post by wojox on 2011-04-11
> **splicerr said:**
> What hardware/drivers are you guys using, nvidia?  Anyone have success with ATI GPU and fglrx?

I've got an old 2004 nvidia chip set. Never owned ATI. Intel and nvidia. ;)

---

### Post by Visceral Monkey on 2011-04-12
Hmm, does anyone know if the proprietary ATI driver and Gnome 3 work? If I try it with the proprietary one, I get corruption on the activity bar, like something isn't rendering right. Remove that and use the open source one, and it's fine. Problem is, the open source one isn't acceptable for me. Poking around the web I'm seeing a report here and there that Gnome 3 itself is NOT going to work with the proprietary ATI driver. Not good.

---

### Post by bmbaker on 2011-04-12
> **wojox said:**
> I spent like two hours yesterday looking for how to do that, found it and overwrote it with a new theme. Must back up better.

looks good :-) what theme are you using?

---

### Post by wojox on 2011-04-12
> **bmbaker said:**
> looks good :-) what theme are you using?

GNOME Shell Dark Glass theme
AwOken Icons

---

### Post by Justin Trouble on 2011-04-12
> **t.rei said:**
> 
However there are three issues I'm still having: 
1) No application stores keys in the keyring or it does not get unlocked or used
2) empathy does not remember my icq account
3) I'm still having the 'old' nm-applet - not the one like in fedora live cd (minor issue - just beauty)

I have the same trouble with no passwords being saved. Having to re-type wireless and Empathy passwords is annoying, but comes with the territory when installing new unstable packages.

Empathy remembers my first two accounts, but not my third!

I have the old nm-applet too.

---

### Post by Guitar John on 2011-04-12
never mind

---

### Post by copernic2006 on 2011-04-12
Hello
I followed this discussion with great interest and I can not wait to install gnome 3 for the test.
Do you think a neuwbie can install it without risk? :lolflag:
Thank you

---

### Post by coffeecat on 2011-04-12
> **copernic2006 said:**
> Do you think a neuwbie can install it without risk?

Well, you joined in 2007 so you can't be a complete newbie. :)

Don't install it to your main system. Some inexperienced people have already made that mistake and regretted it. Experienced people always use a spare machine or spare partition for bleeding-edge things like this. Then, if it breaks, you still have your main system(s) to fall back on.

Given that, good luck and join the fun!

---

### Post by copernic2006 on 2011-04-12
> **coffeecat said:**
> Well, you joined in 2007 so you can't be a complete newbie. :) 

say that I am no friend-friend with the a console:)

Thank you for your advice, I'll still wait and I salivate just reading this thread

---

### Post by coffeecat on 2011-04-12
> **coffeecat said:**
> Also - calling fellow Brits. I can't get a UK keyboard layout. See screenshot. That's the correct setting but that ain't no UK keyboard layout. Am I doing something wrong or is a bug-report in order here?

Thought I'd return to this since it's bugging me. If it's bugging any other UK residents, here's an answer.

From System Settings > Region & Language > Layouts tab > 2 cogs button:

Screenshot 1 = "UK" Keyboard. No, it isn't.

Screenshot 2 = Ireland keyboard. I don't know about all the extra bits on the A-Z keys, but at least things like " @ #~ | \ / € are now in the right place. That's more like it.

Lovely country, Ireland. :)

---

### Post by Quackers on 2011-04-12
Ah, the Emerald Isle :-)
Glad you sorted it out, but not too impressed that you had that problem in the first place. It's like having that damned keyboard config problem we had a few weeks ago in Natty. Bah!

---

### Post by crishu86 on 2011-04-12
> **Justin Trouble said:**
> I have the same trouble with no passwords being saved. Having to re-type wireless and Empathy passwords is annoying, but comes with the territory when installing new unstable packages.

Empathy remembers my first two accounts, but not my third!

I have the old nm-applet too.

I have the same issues too. Does the keyring manager and the nm-applet work somewhere?

---

### Post by lan3y on 2011-04-12
Hello,

i just 'attempted' to run gnome3 on my freshly installed 11.04 beta 2 system (todays image).

when i login from gdm i hear the login sound then all there is is a purple background, then an error window pops up saying gnome settings daemon has crashed.

anyone had this problem or know how to fix?

thanks
lan3y):P

---

### Post by Visceral Monkey on 2011-04-12
Got it installed and working. Two issues however:

1.) The border around the "windows" looks like it's from the early 90's. It's horrible and I while I can change widgets within apps, I can't change this. Anyone know how I can get the default Gnome 3 "border" around apps? Or at least something not as ugly as this?

2.) Flgrx refuses to work with Gnome 3. I have a feeling this isn't just an Ubuntu issue but a Gnome 3/ATI issue. Anyone confirm?

---

### Post by Quackers on 2011-04-12
The gnome settings deamon crash seems to happen sometimes. It doesn't seem to make any difference though here.
Is there a top panel? If not try rebooting once or twice.

---

### Post by lan3y on 2011-04-12
> **Quackers said:**
> The gnome settings deamon crash seems to happen sometimes. It doesn't seem to make any difference though here.
Is there a top panel? If not try rebooting once or twice.

There is just a purple background, no panels, i have rebooted a couple of times now, same errors.

lan3y

---

### Post by coffeecat on 2011-04-12
> **Quackers said:**
> Ah, the Emerald Isle :-)
Glad you sorted it out, but not too impressed that you had that problem in the first place. It's like having that damned keyboard config problem we had a few weeks ago in Natty. Bah!

It sounds as though you don't have a keyboard layout problem, which surprises me because the screenshot I posted suggests that the coding for the UK keyboard is wrong rather than a misconfiguration on my system.

Under System Settings > Region & Language > Layouts tab > 2 cogs button, what layout do you have, and what does your keyboard layout chart look like when you press that little button with the 2 cogs? Heavens knows what it's called. 2 cogs button, I suppose. :)

---

### Post by Quackers on 2011-04-12
I don't have that problem. See below (the 2 cogs button is greyed out, presumably because I have only one choice).

---

### Post by Quackers on 2011-04-12
> **lan3y said:**
> There is just a purple background, no panels, i have rebooted a couple of times now, same errors.

lan3y

At the gdm login screen, is gnome-shell selected? Presumably it is.
Have a look at this whole thread. You may pick up an idea or two.
Do you have 3D graphics drivers installed?

---

### Post by lan3y on 2011-04-12
> **Quackers said:**
> At the gdm login screen, is gnome-shell selected? Presumably it is.
Have a look at this whole thread. You may pick up an idea or two.
Do you have 3D graphics drivers installed?

thanks for the replies,

i have the nvidia beta driver installed, ( i get the splash when starting X).
yeah i have selected that session, im going to take a skim read through the thread now

lan3y

---

### Post by Quackers on 2011-04-12
> **lan3y said:**
> thanks for the replies,

i have the nvidia beta driver installed, ( i get the splash when starting X).
yeah i have selected that session, im going to take a skim read through the thread now

lan3y
The beta version splash? Is that for the 270.30 driver, which is needed for xserver10

---

### Post by lan3y on 2011-04-12
> **Quackers said:**
> The beta version splash? Is that for the 270.30 driver, which is needed for xserver10

i believe so, heres my nvidia config: [http://bayimg.com/OahOpaaDI](http://bayimg.com/OahOpaaDI)

lan3y

---

### Post by coffeecat on 2011-04-12
> **Quackers said:**
> I don't have that problem. See below (the 2 cogs button is greyed out, presumably because I have only one choice).

You have to highlight "United Kingdom" by clicking on it and then the cogs ungrey themselves.

---

### Post by Quackers on 2011-04-12
Ian3y, yes that seems the same as mine.


Coffeecat, I see :-)  Ok, this is now my screen, with UK board

---

### Post by Visceral Monkey on 2011-04-12
> **Quackers said:**
> Ian3y, yes that seems the same as mine.


Coffeecat, I see :-)  Ok, this is now my screen, with UK board

Quackers, how do you get the default Gnome 3 window border? Mine defaults to something all together different and hideous.

---

### Post by Quackers on 2011-04-12
> **Visceral Monkey said:**
> Quackers, how do you get the default Gnome 3 window border? Mine defaults to something all together different and hideous.

Do you have the default adwaita theme in your home folder?
Use ctrl + h to show hidden files then go to the .themes folder. If Adwaita is not there download it from post 57 (I think it is) and extract the file to that folder, then reboot. I had to reboot a couple of times for it to work. Not sure why :confused:

EDIT  sorry it's post #86 on page 9, by Mblackwell

---

### Post by coffeecat on 2011-04-12
> **Quackers said:**
> Ian3y, yes that seems the same as mine.


Coffeecat, I see :-)  Ok, this is now my screen, with UK board

Aha! You have the correct layout. But compare your screenshot with mine - the keyboard diagram. Yours is headed "Keyboard Layout" and mine is headed "United Kingdom". I'm in my unsullied Natty atm but after some supper I shall reboot into my gnome3 system, open System Settings and look for a country called "Keyboard Layout". :p

---

### Post by Quackers on 2011-04-12
Hmm, if yours is different, I'm not sure why.
As I have only one keyboard option, why would the top bar show anything else?
Not sure what the difference between our systems is, except you seem to have more available options.

---

### Post by lan3y on 2011-04-12
I've had a look through this thread and have been unable to find a solution to my problem :/

i managed to open a browser in the session (from submitting a bug report) but it is anchored to the top left of the screen with no top bar and no way of moving it, 

anyone have any idea how to fix this?

lan3y

---

### Post by Quackers on 2011-04-12
See if Alt + F2 brings up a box. If so type r and hit enter. That should restart gnome-shell

---

### Post by lan3y on 2011-04-12
> **Quackers said:**
> See if Alt + F2 brings up a box. If so type r and hit enter. That should restart gnome-shell

nope, that isn't working either atl+f2 or ctrl-alt-t don't do anything

lan3y

---

### Post by 23dornot23d on 2011-04-12
I had that the other day ..... moved the browser down to the bottom screen and it locked itself there ......

No idea why it did it .......

But I ran the latest updates and rebooted and all was fine again ......

sudo apt-get install aptitude
sudo aptitude update
sudo aptitude safe-upgrade

I say this over and over but if things are not running correctly the updates and upgrades sometimes fix things ...... 
they may break other things though ......

You have the latest graphics driver the same as me ..... mine is good enough to run as my
production machine at the moment ......

Go into synaptic too and post a screen shot of the ppa's you have installed .... please ....


Mine[[COLOR=Red]** looks like this **[/COLOR]]("http://img714.imageshack.us/img714/3289/screenshot33z.png")and my system is fully uptodate ...... and everything seems to be working very well

---

### Post by Harry33 on 2011-04-12
> **23dornot23d said:**
> 
...
You have the latest graphics driver the same as me ..... mine is good enough to run as my
production machine at the moment ......
...


The latest NVidia graphics driver is not any more 270.30.
There is v. 270.41.03 available now.
You can download it from Xorg-edgers PPA or from X Updates PPA.

---

### Post by Quackers on 2011-04-12
Gnome-shell and Xorg-edgers may be pushing the boat out a bit far for me :wink:

---

### Post by 23dornot23d on 2011-04-12
I am quite happy with the 270.30 at the moment but if Ian3y is still having problems it may 
be another option to try out if the updates and upgrade fails to change anything ....

Thanks for the info though ..... Harry33 .... ;)

---

### Post by Harry33 on 2011-04-12
> **23dornot23d said:**
> I am quite happy with the 270.30 at the moment but if Ian3y is still having problems it may 
be another option to try out if the updates and upgrade fails to change anything ....

Thanks for the info though ..... Harry33 .... ;)

Well I just mentioned this for additional info. It may not help the problems here at all.
There is, however, better support for newer cards.
Here is the changelog anyway:

> nvidia-graphics-drivers (270.41.03-0ubuntu1~xup) natty; urgency=low
  * New upstream release.
  * Fixed a bug causing the X server to hang every 49.7 days on
    32-bit platforms.
  * Added support for the following GPUs:
  * GeForce GT 520
  * GeForce GT 525M
  * GeForce GT 520M
  * GeForce GT 445M
  * GeForce GT 530
  * GeForce 405
  * GeForce GTX 590
  * GeForce GTX 550 Ti
  * GeForce GT 420
  * GeForce GT 440
  * GeForce GTX 470M
  * GeForce GTX 485M
  * GeForce GT 550M
  * GeForce GT 555M
  * NVS 4200M
  * Quadro 1000M
  * Quadro 2000M
  * Quadro 2000 D
  * Quadro 400
 -- Robert Hooker <email address hidden>   Mon, 11 Apr 2011 16:17:50 -0400

---

### Post by lan3y on 2011-04-12
im back, but with still no gnome :(

i have tried using bleeding edge nvidia drivers and xorg packages but this doesn't change anything. 

there is one thing i have noticed though, there seems to be 2 gnome3 repos, i am currently using packages from the gnome3 one rather than the 'ubuntugnometeam' repo would this make a difference? only thing that seems different on my system to others.

lan3y

---

### Post by Harry33 on 2011-04-12
> **lan3y said:**
> im back, but with still no gnome :(
i have tried using bleeding edge nvidia drivers and xorg packaged but this doesnt change anything. 
there is one thing i have noticed though, there seems to be 2 gnome3 repos, i am currently using packages from the gnome3 one rather than the 'ubuntugnometeam' repo would this make a different? only thing that seems different on my system to others.
lan3y

Actually there are 3 different PPA's, 2 of which are connected to each other:
1) Gnome3 Team (Gnome3):
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

2A) Ubuntu Gnome Remix Team (Gnome 3 ppa):
[https://launchpad.net/~ubuntugnometeam/+archive/gnome3](https://launchpad.net/~ubuntugnometeam/+archive/gnome3)

2B) Ubuntu Gnome Remix Team (General packages):
[https://launchpad.net/~ubuntugnometeam/+archive/ppa-gen](https://launchpad.net/~ubuntugnometeam/+archive/ppa-gen)

---

### Post by Quackers on 2011-04-12
I've only used the gnome3 team ppa.
Have you managed to open a terminal?

---

### Post by 23dornot23d on 2011-04-12
In a word YES ........ if you want it running ....... but this is the one set up by kansasnoob with warnings ..... this is a fork away from standard

**You must NOT have the GNOME3 team's PPA installed**

_**This  is intended to be installed on a fresh install of the latest natty  beta. DO NOT install this on a production machine, THERE IS NO DOWNGRADE  PATH. THIS HAS NO WARRANTY, AND IT COULD SERIOUSLY MESS THINGS UP.  **_

1) Obtain a clean, fresh installation of the latest 11.04 Natty Narwhal beta.  Perform all applicable updates.  


2)  Configure the system to NOT login automatically.  This is needed so  that you can choose what kind of session you want.  If you do not do  this, you will still be stuck with unity.  This can be changed under  system>preferences>login screen.  


3) Add the UGR Repositories:
sudo add-apt-repository ppa:ubuntugnometeam/gnome3
sudo add-apt-repository ppa:ubuntugnometeam/ppa-gen
sudo apt-get update


4) Install UGR
sudo apt-get dist-upgrade

[COLOR=Red][B]WE ARE EXPERIENCING PROBLEMS HERE THOUGH - Gnome shell loads ok ..... 
but UGR-DESKTOP-G3 is throwing dependency errors up[/B][/COLOR]

BUT EVERYTHING IS RUNNING FOR ME ..... for GNOME-SHELL

sudo apt-get install ugr-desktop-g3 gnome-shell
sudo apt-get upgrade

---

### Post by lan3y on 2011-04-12
> **23dornot23d said:**
> In a word YES ........ if you want it running ....... but this is the one set up by kansasnoob with warnings .....

**You must NOT have the GNOME3 team's PPA installed**

_**This  is intended to be installed on a fresh install of the latest natty  beta. DO NOT install this on a production machine, THERE IS NO DOWNGRADE  PATH. THIS HAS NO WARRANTY, AND IT COULD SERIOUSLY MESS THINGS UP.  **_

1) Obtain a clean, fresh installation of the latest 11.04 Natty Narwhal beta.  Perform all applicable updates.  


2)  Configure the system to NOT login automatically.  This is needed so  that you can choose what kind of session you want.  If you do not do  this, you will still be stuck with unity.  This can be changed under  system>preferences>login screen.  


3) Add the UGR Repositories:
sudo add-apt-repository ppa:ubuntugnometeam/gnome3
sudo add-apt-repository ppa:ubuntugnometeam/ppa-gen
sudo apt-get update


4) Install UGR
sudo apt-get dist-upgrade
sudo apt-get install ugr-desktop-g3 gnome-shell
sudo apt-get upgrade

thankyou will follow this now, ill be back in 30 mins with results of some sort ):P

---

### Post by Harry33 on 2011-04-12
Here is some more info on the UGR (Ubuntu Gnome Remix team):

[http://ubuntuforums.org/showpost.php?p=10660251&postcount=73](http://ubuntuforums.org/showpost.php?p=10660251&postcount=73)

---

### Post by ricotz on 2011-04-12
FYI, so far I can see this Ubuntu Gnome Remix Team PPA is just a plain copy of packages from Gnome3-Team PPA

---

### Post by bmbaker on 2011-04-12
> **Quackers said:**
> I don't have that problem. See below (the 2 cogs button is greyed out, presumably because I have only one choice).

i just tested mine and used the plus sign on the bottom to add english keyboard

---

### Post by Quackers on 2011-04-12
What does the English keyboard look like please? Like mine or like coffeecat's?

---

### Post by bmbaker on 2011-04-12
> **Quackers said:**
> What does the English keyboard look like please? Like mine or like coffeecat's?
here you go :-)

---

### Post by lan3y on 2011-04-12
```

laney@laney-laptop:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed
  gnome-themes-standard
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/981 kB of archives.
After this operation, 6,042 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 131365 files and directories currently installed.)
Unpacking gnome-themes-standard (from .../gnome-themes-standard_3.0.0-1~~build1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_i386.deb (--unpack):
 trying to overwrite '/usr/share/themes/HighContrastInverse/index.theme', which is also in package gnome-accessibility-themes 3.0.0-0ubuntu1~build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i have reinstalled fresh beta install, latest image, i have got as far as 'sudo apt-get dist-upgrade' then the above happens, someone doesnt want me using gnome3 by the looks of it :P

any help? 

lan3y

---

### Post by Quackers on 2011-04-12
> **bmbaker said:**
> here you go :-)

Hmm, that's a US keyboard, if I'm not mistaken. For one thing the " and @ are switched on the UK keyboard.
The new Natty keyboard config made the same error when it first turned up a few weeks ago.
Thanks for the info.

I wonder if that's US English then, probably.

---

### Post by Quackers on 2011-04-12
> **lan3y said:**
> ```

laney@laney-laptop:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed
  gnome-themes-standard
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/981 kB of archives.
After this operation, 6,042 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 131365 files and directories currently installed.)
Unpacking gnome-themes-standard (from .../gnome-themes-standard_3.0.0-1~~build1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_i386.deb (--unpack):
 trying to overwrite '/usr/share/themes/HighContrastInverse/index.theme', which is also in package gnome-accessibility-themes 3.0.0-0ubuntu1~build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i have reinstalled fresh beta install, latest image, i have got as far as 'sudo apt-get dist-upgrade' then the above happens, someone doesnt want me using gnome3 by the looks of it :P

any help? 

lan3y

You appear to have entered sudo apt-get upgrade -f
not sudo apt-get dist-upgrade

From memory, gnome-themes-standard shouldn't need forcing now.

---

### Post by lan3y on 2011-04-12
oops sorry let me rephrase that, i have performed dist-upgrade, which has given me a broken package system now,  whatever package command i run i get the above error

lan3y

---

### Post by bmbaker on 2011-04-12
> **Quackers said:**
> You appear to have entered sudo apt-get upgrade -f
not sudo apt-get dist-upgrade

From memory, gnome-themes-standard shouldn't need forcing now.

i just finished re-installing about an hour or so ago and i still had to force it to install

sudo dpkg -i --force-all /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_amd64.deb
sudo dpkg -i --force-all /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_i386.deb

---

### Post by bmbaker on 2011-04-12
anyone managed to get the extra dock to install from the:

gnome-shell-extensions?

cd
git clone [http://git.gnome.org/browse/gn...]("http://git.gnome.org/browse/gnome-shell-extensions")
cd gnome-shell-extensions
./[autogen.sh]("http://autogen.sh/") --prefix=/usr
make && sudo make install      

i did this and everything went fine but no dock!!!

andrew over at webupd8 always has some great tips and info :-)

---

### Post by coffeecat on 2011-04-12
> **Quackers said:**
> Hmm, that's a US keyboard, if I'm not mistaken.

Agreed. Looks like US to me. There's a lot of things in the keyboard list, some quite odd - I've been looking at some of them. Clearly, it needs some work.

@Quackers, I've been thinking why I'm getting something different from you. I used a Maverick installation in which compiz had suddenly refused to work and I had abandoned it for some time. I then upgraded it to Natty and - hey presto - compiz worked again. Or rather, it worked in Unity but not in classic gnome. :-k I then used this somewhat battered installation to add the gnome3 ppa and try gnome shell.

I think some configuration files must have got left over from Maverick days - I had been trying different keyboard layouts, including a Mac keyboard that confusingly swaps " and @ around. But it doesn't explain why you get a UK keyboard layout called "Keyboard Layout" and I get something that is neither nowt nor summat but called "United Kingdom".

All the fun of the bleeding edge, I suppose. :)

---

### Post by bmbaker on 2011-04-12
> **coffeecat said:**
> Agreed. Looks like US to me. There's a lot of things in the keyboard list, some quite odd - I've been looking at some of them. Clearly, it needs some work.

@Quackers, I've been thinking why I'm getting something different from you. I used a Maverick installation in which compiz had suddenly refused to work and I had abandoned it for some time. I then upgraded it to Natty and - hey presto - compiz worked again. Or rather, it worked in Unity but not in classic gnome. :-k I then used this somewhat battered installation to add the gnome3 ppa and try gnome shell.

I think some configuration files must have got left over from Maverick days - I had been trying different keyboard layouts, including a Mac keyboard that confusingly swaps " and @ around. But it doesn't explain why you get a UK keyboard layout called "Keyboard Layout" and I get something that is neither nowt nor summat but called "United Kingdom".

All the fun of the bleeding edge, I suppose. :)


we would get bored if we couldn't play :-D

---

### Post by Quackers on 2011-04-12
Try
```
sudo dpkg -i --force-all /var/cache/apt/archives/gnome-themes-standard_3.0.0-1~~build1_amd64.deb
```

oops, but only if you are using 64 bit :-)

---

### Post by bmbaker on 2011-04-12
> **bmbaker said:**
> we would get bored if we couldn't play :-D
this one is the full uk one !!

---

### Post by Quackers on 2011-04-12
> **coffeecat said:**
> Agreed. Looks like US to me. There's a lot of things in the keyboard list, some quite odd - I've been looking at some of them. Clearly, it needs some work.

@Quackers, I've been thinking why I'm getting something different from you. I used a Maverick installation in which compiz had suddenly refused to work and I had abandoned it for some time. I then upgraded it to Natty and - hey presto - compiz worked again. Or rather, it worked in Unity but not in classic gnome. :-k I then used this somewhat battered installation to add the gnome3 ppa and try gnome shell.

I think some configuration files must have got left over from Maverick days - I had been trying different keyboard layouts, including a Mac keyboard that confusingly swaps " and @ around. But it doesn't explain why you get a UK keyboard layout called "Keyboard Layout" and I get something that is neither nowt nor summat but called "United Kingdom".

All the fun of the bleeding edge, I suppose. :)

CC, I suspect it's got something to do with that horrible (for me) period when the keyboard config packages were being changed. I had terrible problems, and as a consequence, deleted everything but UK keyboard. TBH that still didn't stop the problems because the US keyboard kept re-installing itself.
Having said that though, I re-installed Natty before trying gnome-shell. That could be the difference.

---

### Post by lan3y on 2011-04-12
Thanks for all the help, i now have gnome3 working


daym its beautiful :P

lan3y

---

### Post by coffeecat on 2011-04-12
> **bmbaker said:**
> this one is the full uk one !!

Agreed! :)

But compare to mine. I'll repost it. And I've just noticed that my function key row is all distorted as well, and I don't have the nice shading. Obviously something wrong with my installation. Ghost of Maverick, I reckon. :|

---

### Post by Quackers on 2011-04-12
> **lan3y said:**
> Thanks for all the help, i now have gnome3 working


daym its beautiful :P

lan3y

I'm glad you got there! :-)  I like it too.

CC, have you been swapping keys around? :wink:
Something definitely wrong there dude.

---

### Post by coffeecat on 2011-04-12
> **Quackers said:**
> 
CC, have you been swapping keys around? :wink:
Something definitely wrong there dude.

I ndo't kihnt os bceuase ttha wsa het ecsrenhsto ttha I spodet ebefor. Rdun. Hwas't nogig no? :shock:

---

### Post by Quackers on 2011-04-12
ROFL, let me get the enigma machine out :-)

---

### Post by cecilpierce on 2011-04-12
just upgraded another unity to gnome3 and still can't logout and back in to classic ?

---

### Post by kansasnoob on 2011-04-12
> **coffeecat said:**
> I ndo't kihnt os bceuase ttha wsa het ecsrenhsto ttha I spodet ebefor. Rdun. Hwas't nogig no? :shock:

How long did that take?

Thanks, I needed a laugh :D

Adding, I once mistakenly ordered a qwertz keyboard instead of a qwerty. It was a Cherry and the price was right.

---

### Post by kansasnoob on 2011-04-12
> **cecilpierce said:**
> just upgraded another unity to gnome3 and still can't logout and back in to classic ?

I think that's typical. I can run nothing but gnome-shell on mine.

---

### Post by Quackers on 2011-04-12
Yup, me too.

Coffeecat, I deciphered your question, and the answer is .................. 42

---

### Post by cecilpierce on 2011-04-12
> **kansasnoob said:**
> I think that's typical. I can run nothing but gnome-shell on mine.

Thanks, I thought some one found a cure, its aggravating to have 2 installed and can't switch:(

---

### Post by 23dornot23d on 2011-04-12
I know this probably does not help that you cannot get classic its the same here .....

But ..... KDE will work ....... E17 Enlightenment works ok ..... and Gnome shell on mine

at least we have a few choices still left till we suss out how to get the others going ....

Just a matter of time ......

Glad to see Ian is up and running too .... and coffeecat that is one good keyboard layout you have ... ;)

---

### Post by coffeecat on 2011-04-12
> **23dornot23d said:**
> But ..... KDE will work ....... E17 Enlightenment works ok ..... and Gnome shell on mine

Hi, could you clarify that, please? You mean I could choose KDE or gnome-shell at the login screen? I have a Kubuntu Natty installation which isn't doing much at the moment so it would give me an opportunity to [s]break something else[/s] do some more testing.

Thanks. :)

---

### Post by 23dornot23d on 2011-04-12
Yep I had them all working even UNITY and CLASSIC too at one point

But now its E17 ..... Gnome Shell and KDE

The way I got them was

Install Natty clean then

 KDM and KDE-FULL

Then Gnome Shell using the link I gave earlier

after all the updates load in ...... E17 .... if you want that too ....

_______________________________________________

You may have to try it slightly different ..... as you have KDE but no Gnome Shell

but I see no reason that it should not work out ok ..... but its  upto you .....

If you are anything like me I have to see what works ......

---

### Post by coffeecat on 2011-04-12
> **23dornot23d said:**
> 
The way I got them was

Install Natty clean then

 KDM and KDE-FULL

Then Gnome Shell using the link I gave earlier

after all the updates load in ...... E17 .... if you want that too ....

Thanks. You started with Natty Ubuntu/gnome. I'll start with Natty Kubuntu/KDE and see if I can meet you somewhere in the middle. :)

---

### Post by Quackers on 2011-04-12
I'll tag along for the ride :-)
Downloading Kubby beta now :-)

---

### Post by kansasnoob on 2011-04-12
> **23dornot23d said:**
> Yep I had them all working even UNITY and CLASSIC too at one point

But now its E17 ..... Gnome Shell and KDE

The way I got them was

Install Natty clean then

 KDM and KDE-FULL

Then Gnome Shell using the link I gave earlier

after all the updates load in ...... E17 .... if you want that too ....

_______________________________________________

You may have to try it slightly different ..... as you have KDE but no Gnome Shell

but I see no reason that it should not work out ok ..... but its  upto you .....

If you are anything like me I have to see what works ......

I have one that I added Lubuntu to so I can use a GUI instead of working from the terminal (I like being able to parse things in Synaptic). The one key to that is being sure to select gdm as the default over lxdm because lxdm still has a problem with booting anything but LXDE :)

I'm guessing that kdm would work OK though. I'm still just focused on getting gnome3 to do exactly what I want it to do. There's been too much talk about the panel technology going away permanently and I doubt that's actually true.

---

### Post by buzzmandt on 2011-04-12
thats how how have it, I use kubuntu/kde for my everyday use/needs.  Then switch to gnome-shell to test.  can't do unity though, wish i could.  not for everyday use, that's kde but for testing and something different now and then

---

### Post by Mblackwell on 2011-04-12
To not get any weird display bugs with the gdm background or window borders/contents/etc, you MUST have the packages:

```
gnome-themes
gnome-themes-standard
gnome-icon-theme
gnome-icon-theme-symbolic
```

If you do not you won't get a background or proper display from GDM, and you won't get the Adwaita theming on windows.

@kansasnoob:
Panels in the fallback mode are sort of similar to those in Gnome2. They don't have as many features or functions though. It's not the same experience. Gnome 2's GUI really is deprecated.

---

### Post by 23dornot23d on 2011-04-12
I would hope the panel technology does NOT go away .... its been the fastest way I know of finding applications for a long time ..... and when using my computer for quick photo edits and 3D work I like fast and organized too.

They brought Gnome-do in a long time ago that was a quick search option .... but if you did not know the name of the application - what do you do guess !!!

Things come and go and I am certain there is a large following especially older people
that will find the new layout intolerable ..... but when people design things they have a vision and a new user in mind.

My thoughts are they are heading and looking towards smaller touch screen technology.

Thats why the worry about space ..... and thats why the big icons ..... 

Eventually you will get used to the icons and what they mean and then possibly have the same on a Phone and a PDA ..... who knows ..... ?

I will help anyone who is into making this a slick as possible though ......

Less keystrokes and less clutter on the screen ...... 

Gnome 3 and a Dock does this ....

You could say UNITY does too .... but it just does not feel right to use .....
maybe with more ability to move things around and turn off the Global menu and add a panel ..... easily ..... then it will be accepted .

---

### Post by Quackers on 2011-04-12
kubuntu natty up and running updates. I'll be back :-)

---

### Post by 23dornot23d on 2011-04-12
Hope it all goes well .... let us know if it wanted to remove anything while doing it ....
I have never done it the way you are doing it ..... but will be interesting to find out if it works
the same or better ..... you might end up with UNITY and CLASSIC too ..........

---

### Post by Quackers on 2011-04-12
At the moment it's downloaded all of 407 updates, but it's stuck at 39% installing one of them. No disc activity - doesn't look too good :-(

---

### Post by Mblackwell on 2011-04-12
> **23dornot23d said:**
> I would hope the panel technology does NOT go away .... its been the fastest way I know of finding applications for a long time ..... and when using my computer for quick photo edits and 3D work I like fast and organized too.

They brought Gnome-do in a long time ago that was a quick search option .... but if you did not know the name of the application - what do you do guess !!!

Things come and go and I am certain there is a large following especially older people
that will find the new layout intolerable ..... but when people design things they have a vision and a new user in mind.

My thoughts are they are heading and looking towards smaller touch screen technology.

Thats why the worry about space ..... and thats why the big icons ..... 

Eventually you will get used to the icons and what they mean and then possibly have the same on a Phone and a PDA ..... who knows ..... ?

I will help anyone who is into making this a slick as possible though ......

Less keystrokes and less clutter on the screen ...... 

Gnome 3 and a Dock does this ....

You could say UNITY does too .... but it just does not feel right to use .....
maybe with more ability to move things around and turn off the Global menu and add a panel ..... easily ..... then it will be accepted .

Part of the bigger icons was to A) Look a bit nicer B) Decrease the number of icons on screen at once (it looked like a mess before) C) Give more space for application titles.

As for finding applications, in Shell you can do stuff like this:
[[IMG]http://img709.imageshack.us/img709/9083/findphotoapp.th.png[/IMG]](http://img709.imageshack.us/i/findphotoapp.png/)

No need to know application names.

---

### Post by 23dornot23d on 2011-04-12
> 
Part of the bigger icons was to A) Look a bit nicer B) Decrease the  number of icons on screen at once (it looked like a mess before) C) Give  more space for application titles.

As for finding applications, in Shell you can do stuff like this:
It does look nicer and you can find things .... but for speed the dock is there for the ones you use everyday ...... 

I think the Gnome -shell layout and the way it works is great .

Plus Cairo-dock ..... its excellent ..... and so fast and well organized .....
really could not ask for a lot more from it ..... but I will try to think of something
to push it towards perfection ...... ;)

Video glitches are my only gripe with it .... and that may be gtk-recordmydesktop
or something else .....


@Quackers

> 
At the moment it's downloaded all of 407 updates, but it's stuck at 39%  installing one of them. No disc activity - doesn't look too good :sad:


Sometimes if you lose connection for any reason while downloading  ... go out and come back in again ..... it clears the locks and then

sudo aptitude -f install

sudo aptitude safe-upgrade

may get you up and running ..... again ....

---

### Post by cecilpierce on 2011-04-12
> **Quackers said:**
> At the moment it's downloaded all of 407 updates, but it's stuck at 39% installing one of them. No disc activity - doesn't look too good :-(

OMG, 93 megs of wallpaper ! 
and I have slow ibternet :(

---

### Post by Quackers on 2011-04-12
> **23dornot23d said:**
> It does look nicer and you can find things .... but for speed the dock is there for the ones you use everyday ...... 

I think the Gnome -shell layout and the way it works is great .

Plus Cairo-dock ..... its excellent ..... and so fast and well organized .....
really could not ask for a lot more from it ..... but I will try to think of something
to push it towards perfection ...... ;)

Video glitches are my only gripe with it .... and that may be gtk-recordmydesktop
or something else .....


@Quackers



Sometimes if you lose connection for any reason while downloading  ... go out and come back in again ..... it clears the locks and then

sudo aptitude -f install

sudo aptitude safe-upgrade

may get you up and running ..... again ....

Thanks I may need that :-)
It has progressed a little (the progress bar, at least) but it still says 39% of libsoup-gnome installed

---

### Post by buzzmandt on 2011-04-12
main gripe i have right now is i can't set behavior to single click, well, actually it is set to single click but i still have to double click everythine.

---

### Post by 23dornot23d on 2011-04-12
Which desktop is this in , Gnome-shell I have set to single click and it works ok .....

one thing I did find odd was screenshots .... when inside the applications choose icons window .... seemed to delay doing them
till I came out of it yesterday .... but since updates seems to have fixed itself now .

---

### Post by Quackers on 2011-04-12
Wow, brand new installation and I'm chrooting into it already! Completely unbootable now - even in recovery mode, lol.
From a root shell it's saying it can't get lock.
Lovely :-)

---

### Post by 23dornot23d on 2011-04-12
Did the upgrade not fully finish then .... cannot understand why it will not boot ..... though.

how far does it get in safe recovery and are you getting any messages back ... did you run out of space

---

### Post by Quackers on 2011-04-12
Lots of space :-)
dpkg is returning errors all over the place.
Recovery gets to "the drive is not ready, press s........press m blah blah.
I'm chrooted in now and running everything I can think of :-)
It's currently running a safe upgrade, so that's progess.
It wouldn't even install aptitude at first!
I'll muddle through :-)
Thanks for the interest :-)

Oh, latest errors are
```
Errors were encountered while processing:
 avahi-daemon
 apport
 cups
 avahi-utils
 pulseaudio-module-zeroconf
 kubuntu-desktop
 apport-kde
 bluez-cups
 pulseaudio-module-raop

```
That'll be a breeze then :-)

---

### Post by 23dornot23d on 2011-04-12
Just out of interest was it 

apt-get or aptitude

you used to do the install with ....

---

### Post by Quackers on 2011-04-12
With an iso :-)
Then once I got aptitude installed I used that for the repairing - if that's what I've done :-)
I'll find out now if it boots!
Wish me luck!

---

### Post by Quackers on 2011-04-12
It's back! That's good then :-)
I'll just do the mopping up!

---

### Post by 23dornot23d on 2011-04-12
Use 

[B]aptitude safe-upgrade 
[/B]
too ....... for some reason I always find I have better success with aptitude to apt-get.

and yes I wish you luck .... ;)

ok time for some sleep .... hopefully you will be all sorted by the time I
come back on again ....

---

### Post by ranch hand on 2011-04-12
> **kansasnoob said:**
> I have one that I added Lubuntu to so I can use a GUI instead of working from the terminal (I like being able to parse things in Synaptic). The one key to that is being sure to select gdm as the default over lxdm because lxdm still has a problem with booting anything but LXDE :)

I'm guessing that kdm would work OK though. I'm still just focused on getting gnome3 to do exactly what I want it to do. There's been too much talk about the panel technology going away permanently and I doubt that's actually true.
Speaking of the terminal and synaptic; the next time you feel like bugging the devs on something you could look into the package "apt-listbugs".  This is in the Debian repo right there with "apt-listchanges" shich is also in the Ubuntu repo.

It is a great thing to have.  In terminal or in synaptic if you have an upgrade that has a bug against it you are informed of this and asked if you want to upgrade that package.  Handy little bugger.

I found it because I want to play with "live-build".  I can't install (well I can but it would be a little silly) "debian-installler-launcher".  It appears you can build your ISO and when that gets installed it breaks the whole thing.

I just try it every day to see if that tag goes away.

---

### Post by ranch hand on 2011-04-12
> **Mblackwell said:**
> Part of the bigger icons was to A) Look a bit nicer B) Decrease the number of icons on screen at once (it looked like a mess before) C) Give more space for application titles.

As for finding applications, in Shell you can do stuff like this:
[[IMG]http://img709.imageshack.us/img709/9083/findphotoapp.th.png[/IMG]]("http://img709.imageshack.us/i/findphotoapp.png/")

No need to know application names.
I like a menu without any damned religious symbols at all.  I do not mind having some on the current panel (small ones) for the most used apps that I decide need to be there and where.

You can get that kind of function, even all on the left side of the screen, by putting the panels over there.  I like mine (both) on top.  kansasnoob wants one on the bottom.  Why the hell are we stuck with some positioning that some idiot that doesn't get out enough decides is where it is best for us?

---

### Post by Visceral Monkey on 2011-04-13
Thanks Quackers, it now looks much better!

---

### Post by bmbaker on 2011-04-13
> **23dornot23d said:**
> I would hope the panel technology does NOT go away .... its been the fastest way I know of finding applications for a long time ..... and when using my computer for quick photo edits and 3D work I like fast and organized too.

They brought Gnome-do in a long time ago that was a quick search option .... but if you did not know the name of the application - what do you do guess !!!

Things come and go and I am certain there is a large following especially older people
that will find the new layout intolerable ..... but when people design things they have a vision and a new user in mind.

My thoughts are they are heading and looking towards smaller touch screen technology.

Thats why the worry about space ..... and thats why the big icons ..... 

Eventually you will get used to the icons and what they mean and then possibly have the same on a Phone and a PDA ..... who knows ..... ?

I will help anyone who is into making this a slick as possible though ......

Less keystrokes and less clutter on the screen ...... 

Gnome 3 and a Dock does this ....

You could say UNITY does too .... but it just does not feel right to use .....
maybe with more ability to move things around and turn off the Global menu and add a panel ..... easily ..... then it will be accepted .

I am using synapse instead of gnome-do it seems alot better to me and you can edit the theme css to change icon size and icon grid 
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

---

### Post by 23dornot23d on 2011-04-13
Cheers for that ... its a good link ..... 

will alter it now ...... whoops ... need to edit */usr/share/gnome-shell/theme/gnome-shell.css*

keith@keith-Aspire-7730ZG:~$ gksudo gedit
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.5/./gio/gsettings.c:338:settings_backend_path_changed: assertion failed: (settings->priv->backend == backend)
keith@keith-Aspire-7730ZG:~$ 

ran into a small problem ..... will alter it from a root login 

All ok now .... after doing this now have [smaller icons]("http://img832.imageshack.us/img832/4305/smallerv.jpg") ........ text is not in the right position on them though
anybody know which setting that is ?

---

### Post by Quackers on 2011-04-13
> **Visceral Monkey said:**
> Thanks Quackers, it now looks much better!

Lol, I think so too.

---

### Post by t.rei on 2011-04-13
> **buzzmandt said:**
> main gripe i have right now is i can't set behavior to single click, well, actually it is set to single click but i still have to double click everythine.

Strangely  this worked for me after just opening nautilus -> edit -> preferences -> behaviour 
and setting it to double-click once, and back again. Since then I have the single click behaviour.

---

### Post by 23dornot23d on 2011-04-13
@Quackers - did you manage to sort your system out ok the other night to get KDE
and Gnome Shell working ok.

---

### Post by Quackers on 2011-04-13
No gnome-shell yet. I'm still trying to get kde to function in a stable manner with unity :-)
Lots of crashes! Kpackagekit crashes every time it's used. Compiz is very hit and miss at the moment and themes just don't exist :-)

---

### Post by bmbaker on 2011-04-13
Hmm now I can't start the shell anymore! Says : error loading shared libraries : libmozjs.so:
Cannot open shared object file : no such file or directory

---

### Post by coffeecat on 2011-04-13
> **Quackers said:**
> No gnome-shell yet. I'm still trying to get kde to function in a stable manner with unity :-)

I have a (half) working gnome shell in Kubuntu now but I went a different route. I started with my Kubuntu Natty originally installed somewhere in alpha. Did an upgrade with Synaptic and then...

```
sudo add-apt-repository ppa:gnome3-team/gnome3
```..after which, for good measure..

```
sudo apt-get update
sudo apt-get upgrade
sudo aptitude safe-upgrade
```Both apt-get and aptitude brought in a few more packages. Then:

```
sudo apt-get install gnome-shell
```After which I had to install gnome-themes and gnome-themes-standard manually, but I didn't have to do a force-install of gnome-themes-standard as some people have.

Now I have a system booting with the Kubuntu plymouth and with the kdm login. I have the choice of KDE, gnome-shell, "Ubuntu" and Ubuntu classic, but the last two don't work - most likely because I have packages missing. Apart from what gnome-shell dragged in I only had a few gnome libraries installed from installing things like Synaptic when this was pure KDE.

No choice of wallpapers, I get what seems to be the Adwaita theme but with a retro Win95 look (see screenshot) and a lot of gnome utilities are missing. But I get a proper UK Keyboard layout! \o/ \o/ \o/

I've got to go out now, but later I'll see if installing Unity and some missing gnome stuff may give me the missing gnome bits and allow me to login to Unity and classic gnome.

---

### Post by 23dornot23d on 2011-04-13
> **Quackers said:**
> No gnome-shell yet. I'm still trying to get kde to function in a stable manner with unity :-)
Lots of crashes! Kpackagekit crashes every time it's used. Compiz is very hit and miss at the moment and themes just don't exist :-)

@Quackers
Did you download the theme again from [Post 86 ..... Link ]("http://ubuntuforums.org/showpost.php?p=10655293&postcount=86") 

@Coffeecat ...... Do you have the Tweak utility installed for changing Themes etc ..... ( [link to this]("http://www.webupd8.org/2011/04/introducing-gnome-tweak-tool-gui-to.html"))

This was a handy link too that was posted [LINK]("http://live.gnome.org/GnomeShell/CheatSheet")

---

### Post by bmbaker on 2011-04-13
i just realised i don't have gnome-themes installed !
gnome-themes : Depends: gtk3-engines-pixbuf but it is not installable

any ideas?

---

### Post by 23dornot23d on 2011-04-13
Someone has already raised a bug against this ..... the gtk3-engines-pixbuf

the other day did not exist at all ......

will look for the bug report ...... [LINK TO BUG REPORT]("https://bugs.launchpad.net/ugr-meta/+bug/758193") .... no solution yet

Found [this though]("http://www.ubuntuupdates.org/packages/show/298514") it looks like its in the Rcotz ppa .....

Which is [here with 1950 successful builds]("https://launchpad.net/%7Ericotz/+archive/testing/+packages")


As was pointed out earlier there appear to be 3 ppa's now ......

I guess the thing to do is STICK with the one you install that works for you ..... and the one you think 
will do the things that you need from it ..........  

[**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") - (originally used this )

[[COLOR=Red]**GNOME3 REMIX TEAM**[/COLOR]]("https://launchpad.net/%7Eubuntugnometeam/+archive/gnome3") UCG - (this is the one I am currently using - as its meant to head fro the Classic Type Menus )

[**[COLOR=SeaGreen]GNOME3 RICOTZ[/COLOR]**]("https://launchpad.net/%7Ericotz/+archive/testing") - ( I am now going to STICK with [COLOR=Red]GNOME3 REMIX TEAM[/COLOR] as the RICOTZ on gave me more problems )

I will stick with using [COLOR=Red]GNOME3 REMIX TEAM ......[/COLOR]

---

### Post by bmbaker on 2011-04-13
> **23dornot23d said:**
> Someone has already raised a bug against this ..... the gtk3-engines-pixbuf

the other day did not exist at all ......

will look for the bug report ...... [LINK TO BUG REPORT]("https://bugs.launchpad.net/ugr-meta/+bug/758193") .... no solution yet

Found [this though]("http://www.ubuntuupdates.org/packages/show/298514") it looks like its in the Rcotz ppa .....

Which is [here with 1950 successful builds]("https://launchpad.net/%7Ericotz/+archive/testing/+packages")


As was pointed out earlier there appear to be 3 ppa's now ......

I guess the thing to do is stick with the one you install that works for you ..... 

GNOME3

GNOME3 UCG - (this is the one Iam currently using - But I di start with the original GNOME3 one )

GNOME3 RICOTZ - ( I am now going to have a quick (SWAP) to this - and look at what this one does to my system )

I will then go back to using UCG ....... will let you know if i get errors or if it works ok ......

haha funny i just finshed adding [https://launchpad.net/~ricotz/+archive/testing]("https://launchpad.net/%7Ericotz/+archive/testing")
just updated seems good and the dock in wking too :-)

this is the one i am using GNOME3 UCG
and just added ricotz testing.

---

### Post by 23dornot23d on 2011-04-13
Glad it worked for you ..... ;) ....... 

I was working ok .. 

.... I now have a dependency problem lols ..... 

we swapped places

```

root@keith-Aspire-7730ZG:/home/keith# aptitude -f install
The following NEW packages will be installed:
  gir1.2-mutter-3.0{a} gnome-themes-standard 
The following packages will be REMOVED:
  anjuta-common{u} autoconf{u} autogen{u} automake{u} devhelp-common{u} 
  gimp-dbg{u} gir1.2-mutter-2.91{u} intltool{u} libdevhelp-3-0{u} 
  libdmapsharing2{u} libfontconfig1-dbg{u} libgail-gnome-dbg{u} 
  libgda-4.0-4-dbg{u} libgladeui-2-0{u} libgladeui-common{u} 
  libgoffice-dbg{u} libloudmouth1-0-dbg{u} libnspr4-dbg{u} libnss3-dbg{u} 
  liboobs-1-5-dbg{u} libopts25{u} libopts25-dev{u} libvala-0.12-0{u} 
  libxft2-dbg{u} libxml2-dbg{u} rhythmbox-dbg{u} 
The following partially installed packages will be configured:
  gnome-shell 
0 packages upgraded, 2 newly installed, 26 to remove and 1 not upgraded.
Need to get 0 B/1,002 kB of archives. After unpacking 107 MB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 229036 files and directories currently installed.)
Unpacking gir1.2-mutter-3.0 (from .../gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/mutter/Meta-3.0.typelib', which is also in package gir1.2-mutter-2.91 3.0.0-0ubuntu1~build1
Errors were encountered while processing:
 /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gir1.2-mutter-3.0 (>= 3.0.0); however:
  Package gir1.2-mutter-3.0 is not installed.
dpkg: error processing gnome-shell (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-shell
                                         
root@keith-Aspire-7730ZG:/home/keith# 


```



Logged out and logged back in again ..... at least it still seems to work ok ,,,,,,

---

### Post by Justin Trouble on 2011-04-13
**libgnome-keyring 3.0.0.1** has just been uploaded to the PPA!!
This replaces version 2.32.

I wonder if this fixes all the password forgetting problems??

That would be awesome.

---

### Post by 23dornot23d on 2011-04-13
I seem to be ok with it remembering passwords ...... I have that already installed though,

here is my latest headache ....

E: /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb: trying to overwrite '/usr/lib/mutter/Meta-3.0.typelib', which is also in package gir1.2-mutter-2.91 3.0.0-0ubuntu1~build1

Anybody know how to fix this ?


Gnome-Shell is still running well but I hate having any errors ......

---

### Post by bmbaker on 2011-04-13
> **23dornot23d said:**
> I seem to be ok with it remembering passwords ...... I have that already installed though,

here is my latest headache ....

E: /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb: trying to overwrite '/usr/lib/mutter/Meta-3.0.typelib', which is also in package gir1.2-mutter-2.91 3.0.0-0ubuntu1~build1

Anybody know how to fix this ?


Gnome-Shell is still running well but I hate having any errors ......

i did this and then did a full dist-upgrade

```
sudo dpkg -i --force-all /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb
```

---

### Post by t.rei on 2011-04-13
Todays upgrade of **libgnome-keyring 3.0.0.1** seem to have solved the forgetting of passwords, indeed. Very nice. 

Now I'm still with the 'old' nm-applet, and I'm experiencing some issues with wakeup after suspend. But it's really coming along nicely and working on gnome3 is actually very very comfortable.

*edit* forgot to mention - the upgrade of the keyring lib has also solved the issue of empathy forgetting my icq account every time. *cheers*

---

### Post by bmbaker on 2011-04-13
Actually what i do is download the deb files manually and check  them with gdebi takes a little longer but it tells you what its dependencies and conflicts are :-)
very useful when dealing with easily broken system !!

---

### Post by Justin Trouble on 2011-04-13
> **23dornot23d said:**
> I seem to be ok with it remembering passwords ...... I have that already installed though,

We're probably using different PPAs then.

I'm using the original Gnome 3 PPA.

---

### Post by Harry33 on 2011-04-13
> **bmbaker said:**
> Actually what i do is download the deb files manually and check  them with gdebi takes a little longer but it tells you what its dependencies and conflicts are :-)
very useful when dealing with easily broken system !!

I think Gdebi is way too simple and cannot resolve multiple dependencies.
I use Synaptic. Just add the PPA into sources.list + the authentication key into software-properties-gtk. That also works within Synaptic (Settings => Repositories).

---

### Post by bmbaker on 2011-04-13
> **Harry33 said:**
> I think Gdebi is way too simple and cannot resolve multiple dependencies.
I use Synaptic. Just add the PPA into sources.list + the authentication key into software-properties-gtk. That also works within Synaptic (Settings => Repositories).

ya i do this too but when i am unsure i check it with gdebi first
then synaptic :-)

---

### Post by bmbaker on 2011-04-13
> **Justin Trouble said:**
> We're probably using different PPAs then.

I'm using the original Gnome 3 PPA.


ya it fixed the password problem for me too :-)

---

### Post by 23dornot23d on 2011-04-13
> **bmbaker said:**
> i did this and then did a full dist-upgrade

```
sudo dpkg -i --force-all /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb
```


Thank you that did the trick for me ...... all loaded cleanly .....

I [**[COLOR=Red]purged everything[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10671172&postcount=111") and did as you said ..... now we are in business again and everything is oh so clean ...... no errors .......  yet ;)

I have a slightly different look now too ... and all the desktop features available too ..... [[COLOR=Blue]**NEW SCREENSHOT**[/COLOR]]("http://img402.imageshack.us/img402/7647/screenshot37v.png")

Its remembered my minimize setting too .... noticed it dd not get rid of the original config files on installing.

Good to go enjoying this ,,,, ;)

---

### Post by Mblackwell on 2011-04-13
> **23dornot23d said:**
> Someone has already raised a bug against this ..... the gtk3-engines-pixbuf

the other day did not exist at all ......

will look for the bug report ...... [LINK TO BUG REPORT]("https://bugs.launchpad.net/ugr-meta/+bug/758193") .... no solution yet

Found [this though]("http://www.ubuntuupdates.org/packages/show/298514") it looks like its in the Rcotz ppa .....

Which is [here with 1950 successful builds]("https://launchpad.net/%7Ericotz/+archive/testing/+packages")


As was pointed out earlier there appear to be 3 ppa's now ......

I guess the thing to do is STICK with the one you install that works for you ..... and the one you think 
will do the things that you need from it ..........  

[**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") - (originally used this )

[[COLOR=Red]**GNOME3 REMIX TEAM**[/COLOR]]("https://launchpad.net/%7Eubuntugnometeam/+archive/gnome3") UCG - (this is the one I am currently using - as its meant to head fro the Classic Type Menus )

[**[COLOR=SeaGreen]GNOME3 RICOTZ[/COLOR]**]("https://launchpad.net/%7Ericotz/+archive/testing") - ( I am now going to STICK with [COLOR=Red]GNOME3 REMIX TEAM[/COLOR] as the RICOTZ on gave me more problems )

I will stick with using [COLOR=Red]GNOME3 REMIX TEAM ......[/COLOR]

The last tells you to use this one:

[https://launchpad.net/%7Egnome3-team/+archive/gnome3](https://launchpad.net/%7Egnome3-team/+archive/gnome3)

Which is what I'm using mostly problem free (well, basically completely problem free at this point).

Quick note: If you get double notifications from Empathy, simply uncheck Enable Bubble Notifications (for now). You'll still get notifications from your chats with contacts, so no worries.

---

### Post by 23dornot23d on 2011-04-13
Cheers for the info .... was getting a bit confused as to which was the one to use .

My system is now flying .... and the CLASSIC is available for me at this moment in time

I just did the 

**1.........purge .**.... as I showed in the link earlier ......   [**[COLOR=Red]purged everything[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10671172&postcount=111") 

did as bmbaker said and 
**2.........forced gir1.2-mutter-3.0_3.0.0 **

**3 .........Installed Gnome3-session **
( after adding the repository you gave ..... [https://launchpad.net/%7Egnome3-team/+archive/gnome3]("https://launchpad.net/%7Egnome3-team/+archive/gnome3"))

and now even the choice for UNITY takes me into a desktop ..... without the UNITY side bar
though ...... 

I have not done a full aptitude safe-upgrade yet though ....... so things may change .... 
am quite happy as they are now though 

ok will stick with this from now on then .......

[**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") - (originally used this )


So I am happy :) ...... ty

---

### Post by coffeecat on 2011-04-13
> **coffeecat said:**
> later I'll see if installing Unity and some missing gnome stuff may give me the missing gnome bits and allow me to login to Unity and classic gnome.

Progress report from the 'starting with Kubuntu' front. I installed the meta-package ubuntu-desktop and that has given me the missing bits in gnome3. The Adwaita theme looks right now. It also installed Unity. However, I still get a failure when trying to login to classic gnome or Unity. That's from kdm which I chose to retain if only to get away from that headache-inducing stripy blue default gdm background.

I'll have a closer look at some of the recent posts because I see that some people have succeeded in getting into classic and Unity.

> **23dornot23d said:**
> @Coffeecat ...... Do you have the Tweak utility installed for changing Themes etc ..... ( [link to this]("http://www.webupd8.org/2011/04/introducing-gnome-tweak-tool-gui-to.html"))

Thanks for that. I'm probably being a bit dense but I couldn’t see where to download the source code. But I've installed the 3.0.0 version of gnome-tweak-tool from the gnome3-team ppa repository. (Isn't that the same precompiled anyway?) I'm glad of that - I've been able to set the Ubuntu font on my desktop which I prefer. Thanks.

---

### Post by 23dornot23d on 2011-04-13
Ok great to see you are getting it all sorted now .....

I am at a stage where its a do I or don't I .... 

after the purge and forcing mutter and the Gnome3 team ppa .....

I am now left with the option to upgrade everything  .....

( and as you are probably aware - this installation here started its life with a clean 11.04 UNITY ISO install )

Doing a safe-upgrade here .....
Not sure what will happen ..... but trusting that the procedure that I did before will
work again to get me back to here ..... I will now upgrade and see if it all works ok ...

fingers crossed and all that .... :)

Will see if Classic still runs after this ..... safe-upgrade .... see how safe it is ....

if not I may do it all again .... 
1    [**[COLOR=Red]purged everything[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10671172&postcount=111") >> 2 force mutter >> 3 install from [**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") -ppa

_________________________________________________________________



Update - good news

[[COLOR=Red]**CLASSIC**[/COLOR]]("http://img84.imageshack.us/img84/4269/classic1v.jpg") is still there and works ok ..... tick - BUT**[ ( with compiz the window borders disappear though)]("http://img854.imageshack.us/img854/3406/classic.jpg")**

( will try the others out E17 - KDE - UNITY now )

KDE with compiz - wobbly windows etc - this works too - BUT screen problems still - Froze on multiple widows )

[COLOR=Red]**[E17 works]("http://img831.imageshack.us/img831/8308/e17a.jpg")**[/COLOR] - and nice boot up welcome screen too .... Tick

UNITY - the selection is there - it goes into a empty desktop environment - but nothing works - CTRL ALT DEL brings up a small widget
saying it cannot find the command .....

____________________________________________________________________________________________

My advice now is to stick with the one Desktop Environment ...... that you want ....... and get it working properly

[[COLOR=Red]**GNOME SHELL**[/COLOR]]("http://img69.imageshack.us/img69/1604/screenshot3ks.png")  - tick

_____________________________________________________________________________________________
  ....  ended up doing this again ...... as far as loading in Gnome3-session

1    [**[COLOR=Red]purged everything[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10671172&postcount=111") >> 2 force mutter >> 3 install Gnome3-session from [**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") -ppa

No Safe upgrade ( as this seems to screw everything up ) ...... this is running so smooth now

also [UNITY now runs as well with compiz]("http://img64.imageshack.us/img64/9172/screenshot4se.png") (only problem window borders) ...... 
but all desktops are working ....... a lot better now,

---

### Post by bmbaker on 2011-04-13
> **23dornot23d said:**
> Ok great to see you are getting it all sorted now .....

I am at a stage where its a do I or don't I .... 

after the purge and forcing mutter and the Gnome3 team ppa .....

I am now left with the option to upgrade everything  .....

( and as you are probably aware - this installation here started its life with a clean 11.04 UNITY ISO install )

Doing a safe-upgrade here .....
Not sure what will happen ..... but trusting that the procedure that I did before will
work again to get me back to here ..... I will now upgrade and see if it all works ok ...

fingers crossed and all that .... :)

Will see if Classic still runs after this ..... safe-upgrade .... see how safe it is ....

if not I may do it all again .... 
1    [**[COLOR=Red]purged everything[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10671172&postcount=111") >> 2 force mutter >> 3 install from [**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") -ppa

_________________________________________________________________



Update - good news

[[COLOR=Red]**CLASSIC**[/COLOR]]("http://img84.imageshack.us/img84/4269/classic1v.jpg") is still there and works ok ..... tick - BUT**[ ( with compiz the window borders disappear though)]("http://img854.imageshack.us/img854/3406/classic.jpg")**

( will try the others out E17 - KDE - UNITY now )

KDE with compiz - wobbly windows etc - this works too - BUT screen problems still - Froze on multiple widows )

[COLOR=Red]**[E17 works]("http://img831.imageshack.us/img831/8308/e17a.jpg")**[/COLOR] - and nice boot up welcome screen too .... Tick

UNITY - the selection is there - it goes into a empty desktop environment - but nothing works - CTRL ALT DEL brings up a small widget
saying it cannot find the command .....

____________________________________________________________________________________________

My advice now is to stick with the one Desktop Environment ...... that you want ....... and get it working properly

[[COLOR=Red]**GNOME SHELL**[/COLOR]]("http://img69.imageshack.us/img69/1604/screenshot3ks.png")  - tick

_____________________________________________________________________________________________
  ....  ended up doing this again ...... as far as loading in Gnome3-session

1    [**[COLOR=Red]purged everything[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10671172&postcount=111") >> 2 force mutter >> 3 install Gnome3-session from [**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") -ppa

No Safe upgrade ( as this seems to screw everything up ) ...... this is running so smooth now

also [UNITY now runs as well with compiz]("http://img64.imageshack.us/img64/9172/screenshot4se.png") (only problem window borders) ...... 
but all desktops are working ....... a lot better now,

hhhmph and i still haven't managed to log into anything other than gnome3 !!
maybe i do everything over again like you have :-P

---

### Post by 23dornot23d on 2011-04-13
Well I am a lot happier now ..... the purge was the worrying bit for me as it removes so much stuff ......

But then seems to replace everything with older things ..... but they seem to work well ....
it did not take too long to go through the procedure the second time .....

Think this is it ..... the routine ..... 

__________________________________________________
all based on top of a fresh 32 bit Gnome/UNITY install 

purge .... gnome team ppa   [**[COLOR=Red]purged everything[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10671172&postcount=111")
force the mutter .... 
     Code:
     sudo dpkg -i --force-all /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb 


add gnome team ppa    [**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") -
install Gnome3-shell .....
_______________________

Hope you get to a similar point  ... :wink:  (sometime in the future a safe-upgrade may work)

LATEST PICTURES OF DESKTOPS I HAVE RUNNING NOW ... all in the same install env

1 .... [UNITY]("http://img64.imageshack.us/img64/9172/screenshot4se.png")   >>>>>> [ALSO WITH COMPIZ]("http://img820.imageshack.us/img820/5474/screenshot10ja.png")

2 .... [GNOME-SHELL]("http://img23.imageshack.us/img23/9307/screenshot7ff.png")

3 .... [KDE]("http://img59.imageshack.us/img59/6126/kdecp.jpg")

4 .... [CLASSIC]("http://img339.imageshack.us/img339/4603/classicw.jpg")

5 .... [E17 - Enlightenment]("http://img189.imageshack.us/img189/8308/e17a.jpg")

But at the moment ..... 
I will stick with what I have and upgrade individual packages ..... that I feel will not break things.
KDE / E17 / GnomeShell / Unity / Gnome Classic >>>>>>> All work now

---

### Post by bmbaker on 2011-04-13
well i just ppa-purged everything gnome3
and reinstalled from gnome3 team ppa
updated and dist-upgrade 
didn't have to force anything this time
added ppa:ricotz/testing
updated and dist-upgrade
and installed gnome-shell ..................works like a charm :-)

now to see if unity and classic works !!!

Nope!! well i like gnome3 way better anyway :P

---

### Post by 23dornot23d on 2011-04-13
Ok ..... you seem to have added some more steps into your setup .....

its easy to do it again ..... but do not do the dist-upgrades .....

gets easier ...... lols ...... but if you are happy with what you have that is the main thing 

Here is what my login menu looks like now ...... and they all work ..... 

[IMG]http://img14.imageshack.us/img14/9494/menuzz.jpg[/IMG]

I like Gnome 3 / Gnome shell and I find I go into it automatically now ..... as my main DE



These are what I ended up with in my synaptic listing ....... [URL="http://img853.imageshack.us/img853/5796/listve.jpg"]SCREENSHOT

[/URL]

---

### Post by bmbaker on 2011-04-13
wow with all that installed you'll never have time to use it you will be updating all the time 
:-D :-D

i will play some more and see if i can get gnome classic wking at least as a fall back :P

---

### Post by 23dornot23d on 2011-04-13
The thing is to know when to stick ...... lols .... its like playing cards .... pontoon ;)

Once its all running well - only update whats needed ;)

---

### Post by bmbaker on 2011-04-13
> **23dornot23d said:**
> The thing is to know when to stick ...... lols .... its like playing cards .... pontoon ;)

Once its all running well - only update whats needed ;)

ya indeed :-)

actually i was just checking synaptic and i see that unity is installed....doesn't log on !!
and ubuntu desktop is not installed at all !
hmmmmm

---

### Post by RJ12 on 2011-04-13
So I have been reading the thread... which PPA (since there seems to be 3...) is working the best for you guys? I really want to try Gnome-Shell (and installed kde just in case I need it)

---

### Post by 23dornot23d on 2011-04-13
We have bits from both the 

GNOME3 Team and the RICOTZ one ...... check the screenshot I posted earlier ..... it shows them installed in synaptic.

We have done so much but the way that seems to work is to try to install everything - purge it and then go for the GNOME 3 TEAM one

---

### Post by RJ12 on 2011-04-13
Hmm... got it installed :) very nice... still a few glitches... but not bad :)

---

### Post by 23dornot23d on 2011-04-13
What sort of glitches did you get ....... and can you still run UNITY and CLASSIC

---

### Post by RJ12 on 2011-04-13
Just GDM not having my username (had to click other), a few application crashes (expected this), and the volume notification thing looking low quality, and keyring wanting to be unlocked (I didn't even set a password though...). Here is a screenshot of the volume thingy....

Checking on unity and classic...

Also... is the desktop suppose to work? It doesn't show my icons...

---

### Post by CSimpson on 2011-04-13
The desktop is not supposed to work, no.  And yet, it still insists on making a ~/Desktop folder.  You can turn it back on, if you'd like, with Gnome Tweak Tool (which you can get from the Software Centre).

I don't think it's necessary, though, since the desktop is such a hard place to actually reach, compared to a file manager.

---

### Post by RJ12 on 2011-04-13
Ok, just checked, Unity and classic are completely borked (Can not load the session Ubuntu error message and the same for classic). I fixed the error with the keyring by switching to GDM (was using KDM when GDM wasn't working correctly) but GDM still looks classic... also is there screensavers anymore? I can't find the option...

Also, Evolution new mail notifications have no icon... (it is a black icon with the red circle in the middle)

Edit Again...: I have fixed the sound thing by switching the icon theme using gnome-tweak-tool to the default... I am willing to bet that will fix the evolution new mail notification thing too!

Edit More: Ok, didn't fix the evolution thing... and the default icons are kind of ugly to me so I will switch back...

Aww man!! I had the theme set to the right one (the Awaita default one), and I accidently changed the GTK using tweak tool to Ambiance and I don't see an option for the Awaita one... how do I change it back? It's all ugly now!!

Theme Fixed: Use this command gsettings set org.gnome.desktop.interface gtk-theme Adwaita

---

### Post by coffeecat on 2011-04-13
> **CSimpson said:**
> The desktop is not supposed to work, no.  And yet, it still insists on making a ~/Desktop folder.  You can turn it back on, if you'd like, with Gnome Tweak Tool (which you can get from the Software Centre).

I don't think it's necessary, though, since the desktop is such a hard place to actually reach, compared to a file manager.

Oh, I don't know. I like my desktop untidy - just as in real life, covered in neglected correspondence. :) Thanks for the gnome tweak tip - I've got my untidy desktop back.

---

### Post by 23dornot23d on 2011-04-13
The desktop is normally hidden .... there is a tweak tool that was mentioned earlier on in the thread that changes 
some of the appearance settings and themes .

The sound ICON / Notifier is the same on mine too ..... seems like its been oversized.

There is a cheat sheet too for changing things icon sizes etc ...... in the views that appear after moving the mouse into the 
top left corner of the screen/desktop area - to see the rest of the things available in it ...... and enter in the top right and 
corner once its open the name of the application you want .... Background ......

Will allow you to get the Blue background back again .......

If you want to try it again ......  ...... and you should end up with
everything working ....... ( do not do upgrades or dist upgrades ) 

[B]Do these command exactly as I have written them here ..... (nothing more nothing less)




[/B]**sudo apt-get install ppa-purge**

[B]sudo ppa-purge ppa:gnome3-team/gnome3
[/B]
     [B]sudo dpkg -i --force-all /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb 
[/B] 
add gnome team ppa    [**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") - into synaptic .....

also add the [**[COLOR=SeaGreen]GNOME3 RICOTZ[/COLOR]**]("https://launchpad.net/%7Ericotz/+archive/testing") - into synaptic ......

**sudo aptitude install gnome3-session**



Then let me know if you can still run Classic + UNITY + GNOME -SHELL

( has anybody else successfully got all of them running together yet - or is something else causing problems )

---

### Post by CSimpson on 2011-04-13
Screensavers are- and quite surprisingly- not available in GNOME 3, yeah.  It is the very first release of it, though; bound to be a bit spare on features.

[https://mail.gnome.org/archives/gnome-shell-list/2011-March/msg00340.html](https://mail.gnome.org/archives/gnome-shell-list/2011-March/msg00340.html)

---

### Post by RJ12 on 2011-04-13
> **23dornot23d said:**
> The desktop is normally hidden .... there is a tweak tool that was mentioned earlier on in the thread that changes 
some of the appearance settings and themes .

The sound ICON / Notifier is the same on mine too ..... seems like its been oversized.

There is a cheat sheet too for changing things icon sizes etc ...... in the views that appear after moving the mouse into the 
top left corner of the screen/desktop area - to see the rest of the things available in it ...... and enter in the top right and 
corner once its open the name of the application you want .... Background ......

Will allow you to get the Blue background back again .......

If you want to try it again ......  ...... and you should end up with
everything working ....... ( do not do upgrades or dist upgrades ) 

[B]Do these command exactly as I have written them here ..... (nothing more nothing less)




[/B]**sudo apt-get install ppa-purge**

[B]sudo ppa-purge ppa:gnome3-team/gnome3
[/B]
     [B]sudo dpkg -i --force-all /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb 
[/B] 
add gnome team ppa    [**GNOME3 TEAM**]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") - into synaptic .....

also add the [**[COLOR=SeaGreen]GNOME3 RICOTZ[/COLOR]**]("https://launchpad.net/%7Ericotz/+archive/testing") - into synaptic ......

**sudo aptitude install gnome3-session**



Then let me know if you can still run Classic + UNITY + GNOME -SHELL

( has anybody else successfully got all of them running together yet - or is something else causing problems )


Have you tried these instructions? Are they stable (or not too dangerous)

---

### Post by 23dornot23d on 2011-04-13
I have used the above on my system to get everything running ......... if they are any more dangerous 
than what we are doing in this section of the forum ...... 

I do not know how to judge that ...... it is entirely upto you if you want to follow them ........ 
All the above has come from all of the information given in this section - that has worked so far for me ......

To be safe - you could just stick with 10.10 .  or wait for 11.04 to be released on the 28th of this month ....

There is a screensaver in synaptic thats at version 3.0.0 and loaded up ......

[IMG]http://img850.imageshack.us/img850/4155/screensaver.jpg[/IMG]

---

### Post by RJ12 on 2011-04-13
> **23dornot23d said:**
> I have used the above on my system to get everything running ......... if they are any more dangerous 
than what we are doing in this section of the forum ...... 

I do not know how to judge that ...... it is entirely upto you if you want to follow them ........ 
All the above has come from all of the information given in this section - that has worked so far for me ......

To be safe - you could just stick with 10.10 .  or wait for 11.04 to be released on the 28th of this month ....

There is a screensaver in synaptic thats at version 3.0.0 and loaded up ......

[IMG]http://img850.imageshack.us/img850/4155/screensaver.jpg[/IMG]

yeah, I have that package, I don't think it does anything :(

---

### Post by Visceral Monkey on 2011-04-14
You know, I really like Gnome 3. Enough that I've been looking around for places where people are actively discussing it in detail. 

It strikes me as odd that in general there really isn't much discussion on the net going on about it. The Natty forums seems to be the most active place to talk about Gnome 3, and it's not even "officially" supported anymore! Weird and concerning..

---

### Post by Mblackwell on 2011-04-14
For Debian stuff it's currently still in the Experimental repositories so it's not a big thing yet. Maybe in the next 6 months. For Fedora/openSuse it's a much bigger deal.

---

### Post by bmbaker on 2011-04-14
useful links for using and customizing gnome-shell :-)

[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)
[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)
[http://gnome-shell.deviantart.com/](http://gnome-shell.deviantart.com/)

---

### Post by Visceral Monkey on 2011-04-14
> **bmbaker said:**
> useful links for using and customizing gnome-shell :-)

[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)
[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)
[http://gnome-shell.deviantart.com/](http://gnome-shell.deviantart.com/)

Great post, thanks! I installed the Faenza icons...very nice.

---

### Post by M4570D0N on 2011-04-14
holy carp. I tried to start gnome shell and it failed to load. It got stuck on the gdm screen after logging in so I was just staring at a blank blue screen. I dropped down to restart gdm and log in again. My fan started spinning the fastest I think I've ever heard it and I could feel my laptop starting to cook. I looked at the system monitor both CPUs were maxed at 100%. There were two gnome-settings-daemons listed. One was listed at 120% of CPU the other at 184% of CPU. I killed them both and everything as fine after that. Good times.

---

### Post by vhaarr on 2011-04-14
It's weird though if I log in to the GNOME Shell session with fallback mode enabled or forced, I get the 2.32 gnome-panel instead of the 3.0 fallback mode!

Then if I try to remove gnome-panel using synaptic, it wants to remove gnome-session as well.

Thoughts?

---

### Post by vhaarr on 2011-04-14
Hrm, I followed some instructions posted earlier and I got the old gnome-panel removed. Now I have gnome3-session and if I try to install gnome-session 3.0.0 I get some conflicts.

Logging in to a standard GNOME Shell works fine, but the fallback mode now provides nothing, just an empty desktop with no icons.

If I try to force fallback mode by editing /usr/share/gnome-session/sessions/gnome.session and changing the fallback check to /bin/false, nothing happens and I just log in to a standard GNOME Shell again.

---

### Post by 23dornot23d on 2011-04-14
If I was in that position ...... 

I would start again 

Use these commands and start the process again ........

**sudo apt-get install ppa-purge**

[B]sudo ppa-purge ppa:gnome3-team/gnome3

[/B]and after doing that ......

Just go into synaptic (settings-repositories/then choose Other Software) 
and make sure to check the boxes for the gnome3-team ppa again - [B]

[COLOR=Red]uncheck the ricotz ones to make sure that you continue the process just using the main Gnome3 ppa
[/COLOR]
[/B]as the GNOME3-team seems to be the main one to use ...... ( otherwise it will get confusing )

 After we have just the Gnome3-team PPA .....[B]

sudo aptitude update
sudo aptitute safe-upgrade 

This will get Gnome3/Gnome shell 
working ....... 

[COLOR=Red]But as far as I could work out no other system works at this moment
in time ..... UNITY and CLASSIC will give a error box saying that they cannot run AFAIK 


Here is a LINK to ANOTHER UBUNTU THREAD IN THE DESKTOP AREA more info here  >>> [LINK]("http://ubuntuforums.org/showthread.php?t=1707669&page=5")
[/COLOR]

[/B]

---

### Post by Bou on 2011-04-14
One thing I noticed is that GTK2 apps have their old look, different to those that have been updated to GTK3. You would think they would try to make all apps look the same, shouldn't they?

---

### Post by magneze on 2011-04-14
Just a quick note to say thank you to the Gnome 3 PPA maintainers. I was seriously looking at a Fedora switch but now I can stay with Ubuntu & Gnome 3. Win. :KS

---

### Post by Mblackwell on 2011-04-14
> **Bou said:**
> One thing I noticed is that GTK2 apps have their old look, different to those that have been updated to GTK3. You would think they would try to make all apps look the same, shouldn't they?

GTK2 apps look similar but not the same, it's true. But there's no way around it. There was a lot of new features introduced in GTK3 that allow the theme to be the way it is. All gnome-core apps were updated to GTK3.

---

### Post by crishu86 on 2011-04-14
Here the GTK2 apps don't look similar to GTK3 apps. Firefox has this old Win95 style and other GTK2 apps too. Really ugly!

When I tested the Fedora 15 Alpha the GTK2 apps were looking good too!

---

### Post by Mblackwell on 2011-04-14
You must not have gnome-themes or gnome-themes-standard installed.

---

### Post by crishu86 on 2011-04-14
OK, I will try this ...

---

### Post by CSimpson on 2011-04-14
Bear in mind that you will need to uninstall gnome-accessibility-themes in order to install gnome-themes-standard.

Also note that the theme can be changed to 'Adwaita' using:
```
gsettings set org.gnome.desktop.interface gtk-theme Adwaita
gsettings set org.gnome.desktop.interface cursor-theme Adwaita
```You may also need to set the cursor theme in gconf
```
gconftool-2 --set --type string /desktop/gnome/peripherals/mouse/cursor_theme "Adwaita"
```Otherwise you might still get DMZ-White in certain places.  I still get DMZ-White on the GDM.  No idea why.

EDIT:  The following command will get GDM use the right cursor.  I cannot, however, seem to get it to use a nice font, or to turn off the onscreen keyboard that I had on at the time I added the GNOME3 Team PPA...
```
sudo -u gdm gconftool-2 --set --type string /desktop/gnome/peripherals/mouse/cursor_theme "Adwaita"
```

---

### Post by Visceral Monkey on 2011-04-14
Noooooo. This:

gconftool-2 --set --type string /desktop/gnome/peripherals/mouse/cursor_theme "Adwaita"

Seems to have given me some funky black cursor instead of the nice looking white one I had before. Any suggestions?

Edit: NM, it appears that *is* the correct cursor theme for Adwaita and I was just unaware of it until now. Doh!!

---

### Post by CSimpson on 2011-04-14
Just change the word "Adwaita" to "DMZ-White" and run the commands again, in order to go back to the white, Ubuntu cursor.

---

### Post by Visceral Monkey on 2011-04-14
> **CSimpson said:**
> Just change the word "Adwaita" to "DMZ-White" and run the commands again, in order to go back to the white, Ubuntu cursor.

Ah, my thanks!

---

### Post by jcrow on 2011-04-14
I've been running gnome-shell sandboxed and wanted to try it as a native installed. I tried it several ways and I always run into the same problem. I log in on the gdm screen and when I try to get into a gnome shell session, it freezes and goes nowhere. If I just install the gnome3-session (it is not in the gnome-3 repository) it installs gnome shell and a few other packages. When that loads, I det the desktop but no overview or top panel. For some reason, I don't think gnome-shell is running. I don't think it is a driver issue because unity and the sandboxed gnome shell work fine.

---

### Post by Rifester on 2011-04-14
For those of you that are successfully running Gnome 3 on Ubuntu 11.04 is there any way to remove the non-functioning login selections from the login menu (Unity, classic, etc.)?    I have been testing Unity 11.04 and Fedora 15.    I am having problems with wireless on Fedora and may attempt Ubuntu Gnome 3 install tonight.   If successful it will fix my need to switch to Fedora.    I am really liking Gnome 3 and want to watch it develop.  For me, it is the more coherent desktop environment.

---

### Post by RJ12 on 2011-04-14
I just noticed... the delete key does not work for me when trying to delete files... it does nothing :(

---

### Post by nanouser on 2011-04-14
I have manged to get my Ubuntu and Ubuntu Classic sessions back by rolling back a few packages. Here is what is what worked for me. Your mileage may vary.

1) Fire up Synaptic.

2) Six packages need to be removed. They are:[INDENT][INDENT]         gnome-session
        ubuntu-desktop
        gnome-session-bin
        gdm
        gdm-guest-session
        nautilus-share 
[/INDENT][/INDENT]If you select gnome-session and gnome-session-bin to be removed this should automatically select the other packages to remove.

3) Disable all Gnome 3 repositories and Reload package information.

4) Install the following packages:[INDENT][INDENT]         gdm (2.32.1-0ubuntu1)
        gdm-guest-session (0.23)
        gnome-session (2.32.1-0ubuntu19)
        gnome-session-bin (2.32.1-0ubuntu19)
        gnome-session-common (2.32.1-0ubuntu19)
        nautilus-share (0.7.2-14ubuntu1)
        ubuntu-desktop (1.219)
[/INDENT][/INDENT]Other packages such as Orca may be auto selected during this process. You can always remove them later.

5) Re-enable Gnome 3 repositories and Reload package information.

6) Upgrade gdm to get gdm3 back.

7) Reboot! A reboot seems to be a must. Just logging out and logging back in caused me problems.

Notes: 

- When you do updates do not update the packages in step 4 otherwise you'll need to do the above again. 
- Gnome network manager icon does only shows up in Gnome3. I had to force a rollback of the network-manager-gnome package to get it to show up in Unity and Gnome Classic.


One other thing. If you are having problems with power manager crashing try forcing a rollback of the gnome-power-manager package.

---

### Post by CSimpson on 2011-04-14
> **RJ12 said:**
> I just noticed... the delete key does not work for me when trying to delete files... it does nothing :(

I think that's normal, yes; I have this bug, too.

For now, dragging things to the rubbish bin has been convenient enough.

---

### Post by magneze on 2011-04-15
> **Rifester said:**
> For those of you that are successfully running Gnome 3 on Ubuntu 11.04 is there any way to remove the non-functioning login selections from the login menu (Unity, classic, etc.)?    I have been testing Unity 11.04 and Fedora 15.    I am having problems with wireless on Fedora and may attempt Ubuntu Gnome 3 install tonight.   If successful it will fix my need to switch to Fedora.    I am really liking Gnome 3 and want to watch it develop.  For me, it is the more coherent desktop environment.In /usr/share/xsessions there are a bunch of .desktop files. Just remove or (better) rename the ones you don't want.

---

### Post by magneze on 2011-04-15
Anyone else noticed that copy/paste is broken today after the latest updates? Is that a Gnome 3 bug or a Natty one? :confused:

---

### Post by Harry33 on 2011-04-15
> **magneze said:**
> Anyone else noticed that copy/paste is broken today after the latest updates? Is that a Gnome 3 bug or a Natty one? :confused:

At least I do not see that issue in Natty Ubuntu Classic session with all the latest updates installed. Not in terminal nor in LibreOffice.

---

### Post by magneze on 2011-04-15
Must be a Gnome 3 thing then.

---

### Post by bmbaker on 2011-04-15
its not a gnome thing i have copy and paste.
do a full system restart and it should fix itself :-)

---

### Post by coffeecat on 2011-04-15
> **nanouser said:**
> I have manged to get my Ubuntu and Ubuntu Classic sessions back by rolling back a few packages. Here is what is what worked for me.

Thanks for this. It works for me too but a couple of comments.

> **nanouser said:**
>  4) Install the following packages:
 gdm (2.32.1-0ubuntu1)
        

At this point Synaptic was offering me gdm 2.32.1-0ubuntu3.

> **nanouser said:**
> When you do updates do not update the packages in step 4 otherwise you'll need to do the above again. 

Presumably you could lock the packages in Synaptic, but you wouldn't want to do that for gdm I guess because that would now be back to the gnome3 version.

One thing I noticed is that when I logged into Unity or classic, the upper panel was in the Adwaita colour, which didn't really work. There was no way to reset the Unity/classic gnome2 themes because gnome-control-center was now at the gnome3 version. I didn't try downgrading gnome-control-center to the gnome2 version because that would probably have broken something else. I guess there's always going to be unresolvable issues mixing gnome2 and gnome3 elements. Roll on Oneiric! :)

---

### Post by magneze on 2011-04-15
> **bmbaker said:**
> its not a gnome thing i have copy and paste.
do a full system restart and it should fix itself :-)Yep, that sorted it. Cheers.

---

### Post by nothingspecial on 2011-04-15
Anyone else noticed that /usr/games isn't in your $PATH or is that just me?

---

### Post by CSimpson on 2011-04-15
> **nothingspecial said:**
> Anyone else noticed that /usr/games isn't in your $PATH or is that just me?

I also have this bug.  It aught to be relatively easy to add it, if it bothers you.

---

### Post by 23dornot23d on 2011-04-15
I have just been [looking here]("http://bobthegnome.blogspot.com/") at the System Monitor that can be built and altered ,,,

but I get this error 

```



make[2]: Leaving directory `/home/keith/gnome-system-monitor/help'
make[1]: Leaving directory `/home/keith/gnome-system-monitor/help'
make[1]: Entering directory `/home/keith/gnome-system-monitor'
make[2]: Entering directory `/home/keith/gnome-system-monitor'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/keith/gnome-system-monitor/install/share/applications" || /bin/mkdir -p "/home/keith/gnome-system-monitor/install/share/applications"
 /usr/bin/install -c -m 644 gnome-system-monitor.desktop '/home/keith/gnome-system-monitor/install/share/applications'
make[2]: Leaving directory `/home/keith/gnome-system-monitor'
make[1]: Leaving directory `/home/keith/gnome-system-monitor'



GLib-GIO-ERROR **: Settings schema 'org.gnome.gnome-system-monitor' is not installed

```Does anybody know what I may be missing ..... ( so that I can compile/make this )

---

### Post by bmbaker on 2011-04-16
> **23dornot23d said:**
> I have just been [looking here]("http://bobthegnome.blogspot.com/") at the System Monitor that can be built and altered ,,,

but I get this error 

```



make[2]: Leaving directory `/home/keith/gnome-system-monitor/help'
make[1]: Leaving directory `/home/keith/gnome-system-monitor/help'
make[1]: Entering directory `/home/keith/gnome-system-monitor'
make[2]: Entering directory `/home/keith/gnome-system-monitor'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/keith/gnome-system-monitor/install/share/applications" || /bin/mkdir -p "/home/keith/gnome-system-monitor/install/share/applications"
 /usr/bin/install -c -m 644 gnome-system-monitor.desktop '/home/keith/gnome-system-monitor/install/share/applications'
make[2]: Leaving directory `/home/keith/gnome-system-monitor'
make[1]: Leaving directory `/home/keith/gnome-system-monitor'



GLib-GIO-ERROR **: Settings schema 'org.gnome.gnome-system-monitor' is not installed

```Does anybody know what I may be missing ..... ( so that I can compile/make this )

did you change any of the steps from the blog post you linked?

---

### Post by bmbaker on 2011-04-16
this how  i built the gnome-system-monitor from git :-)
[B][FONT=Arial][SIZE=2]
[/SIZE][/FONT][/B]```
[B][FONT=Arial][SIZE=2][FONT=&quot]cd 
[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=&quot]sudo apt-get build-dep gnome-system-monitor[/FONT][/SIZE][/FONT][/B]
[B][FONT=Arial][SIZE=2][FONT=&quot]git clone git://git.gnome.org/gnome-system-monitor[/FONT][FONT=&quot][FONT=inherit][FONT=inherit]
[FONT=&quot]cd gnome-system-monitor
./autogen.sh --prefix=/usr/install
[/FONT][/FONT][/FONT][/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2]make && sudo make install[/SIZE][/FONT][/B]
```then i ran it from the terminal and it wks just fine :-)

---

### Post by 23dornot23d on 2011-04-16
Nice work looks good too ...... will have another play ...... ;)

Thanks for that ......

I have it running now - ty

---

### Post by bmbaker on 2011-04-16
> **23dornot23d said:**
> Nice work looks good too ...... will have another play ...... ;)

Thanks for that ......

I have it running now - ty

Ur welcome :-)

---

### Post by bmbaker on 2011-04-16
for anyone who is having freezes or things stop wking with the shell try  upgrading to this kernel, i did it yesterday and have been running with  no force closes or crashes :-)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/)

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-13-natty/linux-headers-2.6.39-999-generic_2.6.39-999.201104130905_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-13-natty/linux-headers-2.6.39-999_2.6.39-999.201104130905_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-13-natty/linux-image-2.6.39-999-generic_2.6.39-999.201104130905_i386.deb
sudo dpkg -i *.deb 
```

---

### Post by BigCityCat on 2011-04-16
I have it working. I still need to get unity and classic desktop back but I really don't need em right now.

---

### Post by 23dornot23d on 2011-04-16
Must admit I am running the same  linux-image-2.6.39-999-generic and all is going very well for me too ..... in gnome shell .... this to me seems more stable than anything else I have on my machine at the moment ........

I lost the outside borders to the windows in UNITY a while back - so I cannot grab and move them around ...... although UNITY reset does bring them back again .....

The very next time after I log out and back in they have gone again ...........

---

### Post by BigCityCat on 2011-04-16
With the Tweak Tool under shell I see User Theme extension not enabled. What am I missing?

---

### Post by bmbaker on 2011-04-16
> **BigCityCat said:**
> With the Tweak Tool under shell I see User Theme extension not enabled. What am I missing?
i don't know its the same for me !

---

### Post by 23dornot23d on 2011-04-16
Mine looks like this ......



[IMG]http://img856.imageshack.us/img856/300/tweak1.jpg[/IMG]



and this .... dont know if this helps or not ....... 

same with me ..... says not enabled too


[IMG]http://img863.imageshack.us/img863/2378/tweak3jpg.png[/IMG]

---

### Post by BigCityCat on 2011-04-16
> **23dornot23d said:**
> Mine looks like this ......



[IMG]http://img856.imageshack.us/img856/300/tweak1.jpg[/IMG]



and this .... dont know if this helps or not ....... 

same with me ..... says not enabled too


[IMG]http://img863.imageshack.us/img863/2378/tweak3jpg.png[/IMG]

You look to be missing a lot more, because the interface on yours looks incomplete. I wish I could help but I'm winging it here myself. All though I did manage to get a custom theme installed, but installed the extension pack and I have no idea how to use it lol.

---

### Post by BigCityCat on 2011-04-16
I got this far, but the icon in the taskbar is too big and i installed the extension pack but don't really know how to use it. Fire fox does not cover the dock on the side of the screen and I don't like it.
[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-4.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-4.png)

---

### Post by Visceral Monkey on 2011-04-16
> **BigCityCat said:**
> I got this far, but the icon in the taskbar is too big and i installed the extension pack but don't really know how to use it. Fire fox does not cover the dock on the side of the screen and I don't like it.
[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-4.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-4.png)

The task bar icons are always like that for me, I assumed it was correct.

---

### Post by BigCityCat on 2011-04-16
Yeh I was just thinking that. I guess it is supposed to be like that. I thought it was a bug. Certain icons it looks wrong and others it looks pretty cool. Like the Firefox icon.

The only issue I am having right now is that dock that was installed when I installed the extension pack through git.
1. I don't know how to uninstall it and
2. I don't like how a maximized window will not cover it.

---

### Post by BigCityCat on 2011-04-16
Also my laptop is running hot. I'm not seeing a lot of cpu usage. I wonder if the fan is working?

---

### Post by 23dornot23d on 2011-04-16
I think that It looks like AWN .... 

You could un-install it from the synaptic package manager ..... or maybe .... this from the terminal

sudo apt-get remove avant-window-navigator

should do it ........

---

### Post by BigCityCat on 2011-04-16
No that is the dock that gets installed with gnome-shell-extensions that I installed with git. I have never used git before and I am not sure how to remove the extensions. I do not see it listed in synaptic.

---

### Post by cariboo on 2011-04-16
> **BigCityCat said:**
> No that is the dock that gets installed with gnome-shell-extensions that I installed with git. I have never used git before and I am not sure how to remove the extensions. I do not see it listed in synaptic.

This is offtopic, but if you didn't install using a .deb, it won't show up on synaptic.

---

### Post by Visceral Monkey on 2011-04-16
Does anyone know if there is a Gnome shell repo that would have gnome-shell-extensions? Or is this only way currently with git?

---

### Post by sammiev on 2011-04-16
Installed Gnome3 about 1 hour a go now. So far so good. One error on loading of desktop but the rest is working great. Like the looks and the setup, the only down fall is the size of the icons. Will test for a few more days before I post any more about it unless it crashes or I change back. GL :)

---

### Post by M4570D0N on 2011-04-17
I used ppa-purge to remove gnome 3 so that I could get back on to Natty and it worked for the most part. However, now dockbarx refuses to load in AWN. It shows an icon for a split second that looks like the terminal icon with an "L" shaped arrow that goes down and to the left. Then it disappears and there is just an empty space on AWN. I'd check the messages log, but I dont have a messages log file, nor a daemon log file, which I still don't understand. I tried 
```
logrotate -f /etc/logrotate.d/rsyslog
```but that did not appear to do anything.

---

### Post by 23dornot23d on 2011-04-17
> **sammiev said:**
> Installed Gnome3 about 1 hour a go now. So far so good. One error on loading of desktop but the rest is working great. Like the looks and the setup, the only down fall is the size of the icons. Will test for a few more days before I post any more about it unless it crashes or I change back. GL :)


There is a link to change icon sizes etc ........ [HERE]("http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html") ...... look down towards the bottom of it
it does require altering a few things in the editor though ..... but its easy to do
then the results for the icon sizes and spacing are good too .....

---

### Post by bmbaker on 2011-04-17
> **23dornot23d said:**
> There is a link to change icon sizes etc ........ [HERE]("http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html") ...... look down towards the bottom of it
it does require altering a few things in the editor though ..... but its easy to do
then the results for the icon sizes and spacing are good too .....


Also if you check through the link posted you'll notice something called gsettings you can play around with it and try and remove the dock if you want :-) a good excercise :-)
personally i find it helpful :-)

---

### Post by 23dornot23d on 2011-04-17
Cheers for that - I missed the gsettings completely .....

Now added the date in the Top-panel - title bar ...... with this 
```

gsettings set  org.gnome.shell.clock show-date true

```Thanks for mentioning it ..... will have a play with the setting now on 
other things ......;)

---

### Post by bmbaker on 2011-04-17
if you want to adjust the dock extension....
sudo nautilus

and navigate to:-

/usr/share/gnome-shell/extensions/dock@gnome-shell-extensions.gnome.org

extension.js
 and open with gedit and you can change the icon size to allow more space :-)

line 28 const DOCKICON_SIZE = 48;

i changed mine to 36

---

### Post by sammiev on 2011-04-17
TY 23dornot23d and bmbaker, was looking at that last night and thought I would try this today sometime. :)

---

### Post by rajeev1204 on 2011-04-17
Hi

I just installed this,how do i change theme ? I cant seem to find the appearances thing in here.

I also tried the force install of gnome themes standard for 64 bit and i have a theme now but its rounded off at the corners.

---

### Post by BigCityCat on 2011-04-17
> **rajeev1204 said:**
> Hi

I just installed this,how do i change theme ? I cant seem to find the appearances thing in here.

I also tried the force install of gnome themes standard for 64 bit and i have a theme now but its rounded off at the corners.

Install gnome-tweak-tool

---

### Post by clivejo on 2011-04-17
I've been using Gnome 3 for a while now and I dont like it.  The fonts and icons are too big (even after tweaking).  I find myself in a day dream wondering how to get into common applications or how to switch windows!  It just looks horrible and seems very unproductive to me.  It seems like is was designed for someone who has very bad eye sight! It has broken Unity so I cant downgrade, so I will have to stick it out until Natty is released. 

I'm not sure where to go now, I really dont like unity very much either and I gave up on KDE years ago.  Maybe KDE is worth a revisit!

---

### Post by 23dornot23d on 2011-04-17
@clivejo

Try Linux Mint or Debian .......

I quite iike Sabayon too ......  there are so many other choices ...... just stick with Linux ......

But find one that you enjoy using ...... not everything appeals to everyone ..... but with choices and customisation 
we can do almost anything we want here ......

[ whoops - could not help myself here ..... ( why did I bash windows .... no idea - feel like going back to it God no )
Tell me what the choice is in Windows 7 Nowadays ..... can they choose their own virus protection and firewall ..... 
and cleaners and defrag tools and things to make it look like Linux.
I just wish  I had the choices of virus protection and firewalls here as in windows ........ seem to miss them nowadays ...... 
wish I could run defrag and waste an hour ......
 or wait for updates installing and re-boot ...... to see if it accepeted them or not ........ or as this all changed now ..... who knows ... ]


Gnome shell is one of many choices

Lubuntu

Kubuntu

Enlightenent .... theme if you fancy that type of desktop ---- tried it and it did not appeal to me ....... although they have some very nice themes ..... 
and their startup screens are better than any other system I have used ..........

UNITY ..... now whats wrong with that .....

Gnome 2 and Classic .......

The list goes on ......... one day they will find one that I like too ...... ;)

> 
TY 23dornot23d and bmbaker, was looking at that last night and thought I would try this today sometime. :smile:
Your welcome ..... I like the fact its becoming more cusomizable ...... its still very early development though ....... this to me is
the closest I have got to a quick and organised system ...... 

I live in a cluttered environment usually ...... but this keeps everything tidy ..........

---

### Post by pulpo69 on 2011-04-17
i only get a purple screen when starting gnome-shell (via gdm).

gnome-shell: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

any idea?

---

### Post by 23dornot23d on 2011-04-17
Ok my latest upgrade - 

Now to see if I still have Gnome-shell .... will post this before trying to restart it ....

```

root@keith-Aspire-7730ZG:/home/keith# aptitude safe-upgrade
Resolving dependencies...                
The following packages will be upgraded:
  gnome-shell 
1 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 786 kB of archives. After unpacking 0 B will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://ppa.launchpad.net/ricotz/testing/ubuntu/ natty/main gnome-shell i386 3.0.0.2+git20110415.1d2eadb9-0~11.04~ricotz0 [786 kB]
Fetched 786 kB in 1s (613 kB/s)      
(Reading database ... 328455 files and directories currently installed.)
Preparing to replace gnome-shell 3.0.0.2+git20110413.42e26a86-0~11.04~ricotz0 (using .../gnome-shell_3.0.0.2+git20110415.1d2eadb9-0~11.04~ricotz0_i386.deb) ...
Unpacking replacement gnome-shell ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
WARNING: Failed to parse default value `' for schema (/schemas/apps/devhelp/state/main/contents/books_disabled)
Processing triggers for libglib2.0-0 ...
No such key `exit-with-last-window' in schema `org.gnome.nautilus.preferences' as specified in override file `/usr/share/glib-2.0/schemas/nautilus.gschema.override'; ignoring override for this key.
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up gnome-shell (3.0.0.2+git20110415.1d2eadb9-0~11.04~ricotz0) ...
                                         
Current status: 8 updates [-1].
root@keith-Aspire-7730ZG:/home/keith#  


```just in case things should go wrong here ......


Ok for anyone wanting to try the way I do things here is a link ..... this got me successfully running Gnome-shell

I purge everything and start from scratch so if you are not prepared to do this - then carry on as normal ........

( its not neat and its not pretty - but its pretty neat if it works for you too - progress sometimes starts by knocking everything down and starting again )

But if you want to use it - use it in a Testing environment and not on your main system ....... [**[COLOR=Red]LINK[/COLOR]**]("https://sites.google.com/site/000menu/home/gnome---3")

After doing all the available updates and now I m running the latest kernel the latest Nvidia driver and the latest Gnome Shell with no 

apparent errors ....... yet ...... lols 

other than a warning ...... and I have no idea how to fix this .... (sorted devhelp -upgrade needed)

```

WARNING: Failed to parse default value `' for schema (/schemas/apps/devhelp/state/main/contents/books_disabled) Processing triggers for libglib2.0-0 ... No such key `exit-with-last-window' in schema `org.gnome.nautilus.preferences' as specified in override file `/usr/share/glib-2.0/schemas/nautilus.gschema.override'; ignoring override for this key. Processing triggers for python-gmenu ...

```keith@keith-Aspire-7730ZG:~$ uname -a
Linux keith-Aspire-7730ZG 2.6.39-999-generic #201104151156 SMP Fri Apr 15 13:24:11 UTC 2011 i686 i686 i386 GNU/Linux
keith@keith-Aspire-7730ZG:~$ 

[IMG]http://img851.imageshack.us/img851/1706/sound5.jpg[/IMG]



Update ...... all went well - [Latest screen shot]("http://img859.imageshack.us/img859/4404/screenshot70d.png") ... not that it tells you a lot

updated to the latest now and running ok ...... ;)

---

### Post by hype on 2011-04-17
Just wondering, i just tried to add the oficial gnome3 PPA, but, as a few weeks ago, it only shows a "partial upgrade" option. 
 Is there anything particular to do to be able to use Gnome3 and it's shell on ubuntu Natty?

---

### Post by bmbaker on 2011-04-17
> **hype said:**
> Just wondering, i just tried to add the oficial gnome3 PPA, but, as a few weeks ago, it only shows a "partial upgrade" option. 
 Is there anything particular to do to be able to use Gnome3 and it's shell on ubuntu Natty?
read this first see if it applies to your situation.
[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

if it doesn't the do:
[B]sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install aptitude

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
[/B]

---

### Post by Mblackwell on 2011-04-17
> **clivejo said:**
> I've been using Gnome 3 for a while now and I dont like it.  The fonts and icons are too big (even after tweaking).  I find myself in a day dream wondering how to get into common applications or how to switch windows!  It just looks horrible and seems very unproductive to me.  It seems like is was designed for someone who has very bad eye sight! It has broken Unity so I cant downgrade, so I will have to stick it out until Natty is released. 

I'm not sure where to go now, I really dont like unity very much either and I gave up on KDE years ago.  Maybe KDE is worth a revisit!

Maybe something like this would be helpful for you?

[http://www.youtube.com/user/GNOMEDesktop](http://www.youtube.com/user/GNOMEDesktop)

In reality, to explain it better, it's a paradigm shift from Desktop based interaction to Workspace based interaction. Or to put it another way: The idea of Gnome Shell is to make computing based on task easier.

I always currently use 4 workspaces in shell: 1 for chatting, one for programming, one for file/document management, and one for web browsing. I add additional workspaces as my tasks increase. The overview is an easy way to see every window on the current workspace as well as to see what's going on on other workspaces should I need to change focus and get a quick look at other things. Switching between apps then is as fast as either:

A) Clicking on the appropriate workspace for the task I'm wanting to do (or scrolling to it)
B) Clicking on the app icon on the Dash
C) Alt Tabbing to the app I want. 

If the app uses more than one window you can use Alt+<Above_Tab> (the key above tab. On US Keyboards this is `, but it depends on your locale) to flip between them quickly. 

You can also tile windows side by side by dragging them to the screen edges so you can see two documents at once easily.

It's definitely a shift if you haven't been using your computer that way at all (I hadn't been when I first started using Shell 2 years ago). But once you pick it up it makes other interfaces feel downright clunky. Additionally it's worth noting that people I've shown it to seem to pick it up right away, and for most people basic interaction was intuitive to them.


This will sound terrible (and of course I'm biased), but I saw a short video of multitasking in Unity recently, and while helpful for people that want to stick to the interface it seemed like a very hackish way of doing things involving lots of keyboard shortcut memorization. I only mention it because Gnome Shell was designed from the start with multitasking in mind with the caveat that it should also allow you to more easily focus on the task you want to do *right now*.

Note: Not trying to say you absolutely have to love it or you're a bad person, just trying to explain some of the logic behind the way it is, and what it expects from the user.

---

### Post by bmbaker on 2011-04-17
well said :-)

---

### Post by Visceral Monkey on 2011-04-17
> **Mblackwell said:**
> Maybe something like this would be helpful for you?

[http://www.youtube.com/user/GNOMEDesktop](http://www.youtube.com/user/GNOMEDesktop)

In reality, to explain it better, it's a paradigm shift from Desktop based interaction to Workspace based interaction. Or to put it another way: The idea of Gnome Shell is to make computing based on task easier.

I always currently use 4 workspaces in shell: 1 for chatting, one for programming, one for file/document management, and one for web browsing. I add additional workspaces as my tasks increase. The overview is an easy way to see every window on the current workspace as well as to see what's going on on other workspaces should I need to change focus and get a quick look at other things. Switching between apps then is as fast as either:

A) Clicking on the appropriate workspace for the task I'm wanting to do (or scrolling to it)
B) Clicking on the app icon on the Dash
C) Alt Tabbing to the app I want. 

If the app uses more than one window you can use Alt+<Above_Tab> (the key above tab. On US Keyboards this is `, but it depends on your locale) to flip between them quickly. 

You can also tile windows side by side by dragging them to the screen edges so you can see two documents at once easily.

It's definitely a shift if you haven't been using your computer that way at all (I hadn't been when I first started using Shell 2 years ago). But once you pick it up it makes other interfaces feel downright clunky. Additionally it's worth noting that people I've shown it to seem to pick it up right away, and for most people basic interaction was intuitive to them.


This will sound terrible (and of course I'm biased), but I saw a short video of multitasking in Unity recently, and while helpful for people that want to stick to the interface it seemed like a very hackish way of doing things involving lots of keyboard shortcut memorization. I only mention it because Gnome Shell was designed from the start with multitasking in mind with the caveat that it should also allow you to more easily focus on the task you want to do *right now*.

Note: Not trying to say you absolutely have to love it or you're a bad person, just trying to explain some of the logic behind the way it is, and what it expects from the user.

I hated the first hour I spent using Gnome 3 Shell. Seriously didn't like it. I ended sticking with it though and after a couple of days, was hooked. 

It does work, very well, when you let it. The trick is understanding how it's supposed to work. Most people have zero need to give up the old desktop paradigm and I totally understand that, so it might not be for you. I was bored though and did some reading on the design decisions it was based on and how they envisioned workflow, and I get it now. In comparison, Unity feels like something thrown together to "ape" Gnome 3. It looks similar but the design decisions behind it are missing, it's just cosmetic. In any case, no one would blame you for wanting to stick with what works, that's pretty normal.

---

### Post by M4570D0N on 2011-04-17
> **bmbaker said:**
> if you want to adjust the dock extension....
sudo nautilus

and navigate to:-

/usr/share/gnome-shell/extensions/dock@gnome-shell-extensions.gnome.org

extension.js
 and open with gedit and you can change the icon size to allow more space :-)

line 28 const DOCKICON_SIZE = 48;

i changed mine to 36

Additionally, according to the gnome site there is a program called looking glass which is the integrated debugger/inspecting tool for gnome shell. I haven't tried it myself yet, though, so I can't comment on the interface or usability of it from experience:

> **Anatomy of an extension**

 When creating an extension, you must pick a *uuid*.   This is a globally-unique identifier for your extension, similar in  form to an email address, but need not be an actual email address.  An  extension, when installed on the filesystem, is a directory whose name  is the same as your extension's uuid. 

Inside the directory, the bare bones of an extension are two files, **metadata.json** and **extension.js**.  The content of a **metadata.json** looks like this: 
```

{ 'uuid': 'myextension@myname.example.com',
   'name': 'My Cool Extension',
   'description': 'Make windows burst into flame',
   'url': 'http://example.com/~myname/myextension',
   'shell-version': [ '2.91.5' ] }
```The **extension.js** file is simply a [JavaScript]("https://live.gnome.org/JavaScript") file; it must however have a function called **main**, which will be invoked right after the Shell has completed initialization and is awaiting user input. 


You may optionally include a stylesheet file, **stylesheet.css**. 

So an extension will typically look like this: 
```
/.local/share/gnome-shell/extensions/myextension@myname.example.com
     extension.js
     metadata.json
     stylesheet.css
```...

**Extension installation locations**

 Extensions can be installed per-user in *~/.local/share/gnome-shell/extensions*, or systemwide in */usr/share/gnome-shell/extensions* and */usr/local/share/gnome-shell/extensions*. 
 
**Viewing installed extensions**

 Installed extensions are listed in** [LookingGlass]("https://live.gnome.org/GnomeShell/LookingGlass")**. 
 
**Disabling extensions**

 Per-user and systemwide extensions can be disabled with the GSettings key *org.gnome.shell.disabled-extensions*

[https://live.gnome.org/GnomeShell/Extensions](https://live.gnome.org/GnomeShell/Extensions)

> Looking Glass is GNOME Shell's integrated debugger and inspector tool. It aims to be the [Firebug]("http://getfirebug.com/") of GNOME Shell.  It is not related to the older project [Sun Looking Glass]("http://www.oracle.com/technetwork/articles/javase/lookingglass-138583.html"). 
You currently run it by pressing *Alt-F2*, typing **lg**, then *Return*. 

You can leave Looking Glass by pressing *Esc* in its Evaluator pane. 

Looking Glass has four major panes (Evaluator, Windows, Errors, and Extensions) and one tool (the Picker). 
 
**Evaluator**

 This  is an interactive JavaScript prompt.  You can type arbitrary JavaScript  at the prompt, and it will be evaluated.  Try, in order: 
```
1+1   

global.get_window_actors()  

global.get_window_actors().forEach(function (w) { Tweener.addTween(w, { time: 3, transition: 'easeOutQuad', scale_x: 0.3, scale_y: 0.3 })})

global.get_window_actors().forEach(function (w) { w.set_scale(1, 1) }) 

global.get_window_actors()[0]  

it.scale_x
```...

**Extensions**

 This is a list of all currently installed extensions. You can use the *View Source* link to quickly access the extension folder. [https://live.gnome.org/GnomeShell/LookingGlass](https://live.gnome.org/GnomeShell/LookingGlass)

---

### Post by clivejo on 2011-04-17
Ok one problem which is really annoying me, how do you launch multiple instances of the same app in Gnome 3.  Clicking on the app again just refocus to the previously launched version.

---

### Post by cecilpierce on 2011-04-17
Any body tried SuSE Gnome3 live cd ?
I installed it and works great !

---

### Post by bulldog on 2011-04-17
@clivejo,
Try middle mouse click on the app launcher.
This should work.

---

### Post by BigCityCat on 2011-04-17
> **bulldog said:**
> @clivejo,
Try middle mouse click on the app launcher.
This should work.

Thanks been looking for that.

---

### Post by 23dornot23d on 2011-04-17
Just to keep things uptodate and keep a record here .....

I have just done another safe-upgrade today ....... got rid of one warning ...... before by adding the latest 

devhelp  >>>> found this as a solution loooking at this bug report >>>> [URL="https://bugzilla.redhat.com/show_bug.cgi?id=624198"]Bug Report
[/URL] 
now the returned error after a update relates to something else ?

will sort after reboot if it works ok ........

```

Setting up python-ubuntuone-client (1.6.1-0ubuntu1) ...
Setting up ubuntuone-client (1.6.1-0ubuntu1) ...
Setting up libsyncdaemon-1.0-1 (1.6.1-0ubuntu1) ...
Setting up ubuntuone-client-gnome (1.6.1-0ubuntu1) ...
Setting up plymouth-theme-ubuntu-logo (0.8.2-2ubuntu22) ...
update-initramfs: deferring update (trigger activated)
Setting up software-center (3.1.26.5) ...
No protocol specified
/usr/lib/pymodules/python2.7/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Updating software catalog...this may take a moment.
Software catalog update was successful.


root@keith-Aspire-7730ZG:/home/keith# aptitude safe-upgrade
Resolving dependencies...                
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
root@keith-Aspire-7730ZG:/home/keith# 




```
Latest [Screenshot]("http://img822.imageshack.us/img822/4423/screenshot72k.png") .... everything seems to be going ok upto just ....

---

### Post by clivejo on 2011-04-17
> **bulldog said:**
> @clivejo,
Try middle mouse click on the app launcher.
This should work.

Thank you!

---

### Post by BigCityCat on 2011-04-17
> **23dornot23d said:**
> I am now running GNOME-SHELL experimental ...... everything is fantastic ...... just love this layout now
I also add cairo-dock ..... its just the way I like my layout ...... but I am getting some tearing on the screen
when using the forums and Firefox 4.0 ....

Just wanted to try to work out if others are experiencing the same thing or not ...... is it because I have cairo-dock running ...... (will disable it after I have written this just to see if it makes any difference)

But feel free to comment ...... if there are any known issues .....

I have this too but I also noticed some of this in unity and it isn't happening in chromium.

---

### Post by nothingspecial on 2011-04-17
> **pulpo69 said:**
> i only get a purple screen when starting gnome-shell (via gdm).

gnome-shell: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

any idea?
I got that, till I did this

```
sudo apt-get remove gnome-accessibility-themes
```

---

### Post by 23dornot23d on 2011-04-17
> **BigCityCat said:**
> I have this too but I also noticed some of this in unity and it isn't happening in chromium.

Ok found this only related to my desktop machine which has a lower spec processor and Nvidia card than my laptop ...... laptop is fine with the Nvidia 9300 GS

The Desktop I am not sure of the Nvidia number its a (5000 series) I think maybe 5600 ..... will check tomorrow ..... but only happened on that machine .....

---

### Post by kejar31 on 2011-04-17
Ok I think I am really going to prefer Gome3 over Unity. Got everything up and going only issue at this point it the font... It really looks like crap..

---

### Post by BigCityCat on 2011-04-17
The font grew on me. I love it. I agree Gnome 3 is better than unity right now.

---

### Post by Mblackwell on 2011-04-17
> **kejar31 said:**
> Ok I think I am really going to prefer Gome3 over Unity. Got everything up and going only issue at this point it the font... It really looks like crap..

Make sure you're only using Slight Hinting for fonts.

---

### Post by drfox on 2011-04-17
Does anyone know of a wallpaper-changer that works with Gnome-Shell. I have desktopnova/desktopnova-tray installed, and I can see the tray app, but it doesn't change (cycle) my pictures as wallpaper.
Larry

---

### Post by cariboo on 2011-04-17
You can create your own wallpaper slide-show using the instructions [here]("http://www.howtogeek.com/howto/25549/how-to-create-a-wallpaper-slideshow-in-ubuntu/").

---

### Post by FEGuy on 2011-04-18
I noticed a couple comments about not being able to delete files with the Delete key. For some reason, this appears to be a new 'security' feature, akin to not being able to select 'Power Off' from the menu without holding Control. The solution is the same here - to delete files without dragging them to the Trash, the new key binding is Ctrl+Del.

---

### Post by CSimpson on 2011-04-18
> **FEGuy said:**
> I noticed a couple comments about not being able  to delete files with the Delete key. For some reason, this appears to be  a new 'security' feature, akin to not being able to select 'Power Off'  from the menu without holding Control. The solution is the same here -  to delete files without dragging them to the Trash, the new key binding  is Ctrl+Del.

Thank God the boys at GNOME are here to save us from ourselves by hiding features, eh?

God knows, I've often clicked "shutdown" by accident and then failed to address the issue within 60 seconds, and the number of times I've selected all of my work, pressed the delete key and then reacted, in my horror, by immediately clearing the recycle bin...  why it numbers in the zeros!

---

### Post by as2000 on 2011-04-18
I tried Gnome 3 with Fedora 15 beta and although it's pretty, more confusing than Unity. No, I don't like the fact that you are extremely limited in customizing the thing. That is one feature that I liked about Gnome 2.5, but I am sure in time, there will be those that develop customization. Perhaps Gnome 2.5 could be forked and developed as a alternative desktop. I am sure that can be done.

---

### Post by CSimpson on 2011-04-18
> **as2000 said:**
> I tried Gnome 3 with Fedora 15 beta and although it's pretty, more confusing than Unity. No, I don't like the fact that you are extremely limited in customizing the thing. That is one feature that I liked about Gnome 2.5, but I am sure in time, there will be those that develop customization. Perhaps Gnome 2.5 could be forked and developed as a alternative desktop. I am sure that can be done.

The GNOME Panel remains in GNOME 3, as detailed here:
[URL="http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead%2C-long-live-gnome-panel%21"] http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead%2C-long-live-gnome-panel!
[/URL] 
Vincent Untz's blog seems to be down right now, so here it is in Google's cache:
[http://webcache.googleusercontent.com/search?q=cache:lbRCdHwnFXMJ:www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel!]("http://webcache.googleusercontent.com/search?q=cache:lbRCdHwnFXMJ:www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel%21")

It's also available via planet.gnome.org, for the moment:
[http://planet.gnome.org/](http://planet.gnome.org/)

EDIT:
Oh, and for the record, they got all the way up to to GNOME 2.32, which is somewhat further than 2.5 (it's not a decimal). :D

---

### Post by t.rei on 2011-04-18
Uhm, how is gnome3 NOT customizable? It's absolutely and totally extendible, changable, twistable. Right now you have to do it yourself, as it's too new for a large community-site like gnome-look.org to provide you with lots of premade layouts.

It's so freakin easy to write mods and themes for g3... just give it like 6 months or a year, or take a look at /usr/share/gnome-shell/ yourself. Look at stuff like [http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html](http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html) ... or wait.

One theme that crossed my path:
[http://www.omgubuntu.co.uk/2011/01/awesome-elementary-gnome-shell-theme/](http://www.omgubuntu.co.uk/2011/01/awesome-elementary-gnome-shell-theme/)

So yeah, It's customizable. And the extensions will be free to choose from, and probably very very powerfull.

---

### Post by BigCityCat on 2011-04-18
Yeh it's not customizable at all.

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-1-2.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-1-2.png)
[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-4.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-4.png)

---

### Post by Visceral Monkey on 2011-04-18
Does anyone know if Kubuntu is installable on Natty if you have Gnome 3 installed? I'd like to try it out along side my Gnome 3 install. If so, what's the install process?

---

### Post by vhaarr on 2011-04-19
> **BigCityCat said:**
> Yeh it's not customizable at all.

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-1-2.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-1-2.png)
[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-4.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot-4.png)

Oh my, that icon theme looks wonderful for Gnome Shell! Give us a hint? :)

---

### Post by coffeecat on 2011-04-19
> **Visceral Monkey said:**
> Does anyone know if Kubuntu is installable on Natty if you have Gnome 3 installed? I'd like to try it out along side my Gnome 3 install. If so, what's the install process?

I started with Kubuntu Natty and installed gnome shell in that. See my posts #298 and #316 in the thread. I retained the kdm login screen if only because I never worked out how to change that ghastly stripy background in the gnome3 gdm screen. 

My guess is that if you are starting with a working Ubuntu Natty with gnome-shell, then installing the package kubuntu-desktop will bring in everything you need. You should then be able to choose whether to enable gdm or kdm. Good luck!

---

### Post by 23dornot23d on 2011-04-19
Once I got everything running as I wanted ,,,,

just did these after doing a update ..... 

sudo aptitude install kdm
sudo aptitude install kde-full


run it with cairo-dock too ..... 

I like consistency through all the workspaces and this seems to work well in everything .....

---

### Post by cecilpierce on 2011-04-19
Does anyone know the differance between Natty and SuSE Gnome 3 ?
I've got both and suse seems to have desktop effects if you log out and back in after enabling them.
This is too complecated for an ole man like me !!!
:confused:

---

### Post by CSimpson on 2011-04-19
> **cecilpierce said:**
> Does anyone know the differance between Natty and SuSE Gnome 3 ?
I've got both and suse seems to have desktop effects if you log out and back in after enabling them.
This is too complecated for an ole man like me !!!
:confused:

What exactly is the problem that you are having?

That screenshot is of GNOME 3 in fallback mode, which you get when your hardware doesn't support the hardware acceleration features required for the normal GNOME 3 user interface.

---

### Post by cecilpierce on 2011-04-19
> **CSimpson said:**
> What exactly is the problem that you are having?

That screenshot is of GNOME 3 in fallback mode, which you get when your hardware doesn't support the hardware acceleration features required for the normal GNOME 3 user interface.

The screen shot was with desktop effects and works but now I can't get back to the gnome3 desktop unless I use in a terminal [gnome-shell --replace &] works but if I close the terminal it goes back to what was in the screenshot, this may be different since its suse.
Natty g3 did'nt do this !
Thanks

---

### Post by CSimpson on 2011-04-19
> **cecilpierce said:**
> The screen shot was with desktop effects and works but now I can't get back to the gnome3 desktop unless I use in a terminal [gnome-shell --replace &] works but if I close the terminal it goes back to what was in the screenshot, this may be different since its suse.
Natty g3 did'nt do this !
Thanks

Ah, I see.  Three possible solutions:
1. Go to System Settings > System Info, and make sure force fallback isn't on
( [http://www.vuntz.net/photoblog/20110413_force-fallback-mode.png](http://www.vuntz.net/photoblog/20110413_force-fallback-mode.png) )

2. Make sure you have a GNOME Shell session selected in the GDM.

3. You need to run
$ disown
to untie your `gnome-shell --replace &` from the terminal it's in.
You could also try running it from <alt>f2, instead of the terminal.

---

### Post by cecilpierce on 2011-04-19
> **CSimpson said:**
> Ah, I see.  Three possible solutions:
1. Go to System Settings > System Info, and make sure force fallback isn't on
( [http://www.vuntz.net/photoblog/20110413_force-fallback-mode.png](http://www.vuntz.net/photoblog/20110413_force-fallback-mode.png) )

2. Make sure you have a GNOME Shell session selected in the GDM.

3. You need to run
$ disown
to untie your `gnome-shell --replace &` from the terminal it's in.
You could also try running it from <alt>f2, instead of the terminal.

Thanks, I try it in a bit, been on suse forum looking and posting but nuttin yet :confused:

---

### Post by cecilpierce on 2011-04-19
Wow what a life saver, now I can go take my senior nap !

Thanks again,
Cecil

ps it was ON !

---

### Post by Rifester on 2011-04-19
Is anybody else having problems with Gnome Power Manager in Gnome 3?  I am not getting any crashes or warnings at startup at this point, but the battery/power applet is not loading.

---

### Post by Quackers on 2011-04-19
Are you sure it's not in the panel? It's very small now! :-)

---

### Post by Rifester on 2011-04-19
I know my eyes are going bad, but it is not there... :)   I have tried starting it in terminal and it does not load....  And I am getting errors.

---

### Post by thezood on 2011-04-19
> **Rifester said:**
> Is anybody else having problems with Gnome Power Manager in Gnome 3?  I am not getting any crashes or warnings at startup at this point, but the battery/power applet is not loading.

I'm having problems as well, but with crashes and warnings aplenty. :)  Updating now to see if there's fixes on the way.

---

### Post by CSimpson on 2011-04-19
> **cecilpierce said:**
> Wow what a life saver, now I can go take my senior nap !

Thanks again,
Cecil

ps it was ON !

I'm only sorry I wasn't faster to respond.

I ran the GNOME 3 PPA, and the Fedora 15 beta with GNOME 3, for a few days and so I have already had a good chance to feel out the new environment, and get a handle on its idiosyncrasies.

For the record, if anyone is thinking of trying the Ubuntu PPA or Fedora 15 and would like to hear someone else's experience, I'm back on Ubuntu 10.10 for now, for the following reasons:
- Fedora's font rendering is quite incurably bad
- Fedora refused to use a Western font (namely Cantarell) and fall back to Japanese glyphs, so I was stuck with VL Gothic a-z (yuck!) when working in English (which is lots).  Ubuntu does this correctly by default.
- Fedora's add/remove software and update manager program are a bit ”blegh”.

- The Ubuntu PPA is not yet very complete and is full of bugs.

None of my reasons have to do with the actual GNOME 3 experience, which, I think, is superb.

---

### Post by xebian on 2011-04-19
> **CSimpson said:**
> I'm only sorry I wasn't faster to respond.

I ran the GNOME 3 PPA, and the Fedora 15 beta with GNOME 3, for a few days and so I have already had a good chance to feel out the new environment, and get a handle on its idiosyncrasies.

For the record, if anyone is thinking of trying the Ubuntu PPA or Fedora 15 and would like to hear someone else's experience, I'm back on Ubuntu 10.10 for now, for the following reasons:
- Fedora's font rendering is quite incurably bad
- Fedora refused to use a Western font (namely Cantarell) and fall back to Japanese glyphs, so I was stuck with VL Gothic a-z (yuck!) when working in English (which is lots).  Ubuntu does this correctly by default.
- Fedora's add/remove software and update manager program are a bit &#8221;blegh&#8221;.

- The Ubuntu PPA is not yet very complete and is full of bugs.

None of my reasons have to do with the actual GNOME 3 experience, which, I think, is superb.

Am using Fedora 15 beta live right now and Gnome shell looks pretty and quite intuitive as this is my first time to see/use  it.  IMHO natty would have looked pretty as well.

Quite impressive, worked out of the box, radeon x1200, which I could never get Unity to work.

---

### Post by cecilpierce on 2011-04-19
@CSimpson

I tried the fedora & suse live cd's and suse was the only one that had install, besides natty g3 screwed up so bad I had to purge it and took a lot of natty with it, finally got it back to normal and tried suse, its alot better then fedora so i'll wait till the ppa's catch up before I install it again,
Thanks again for the help.

---

### Post by 23dornot23d on 2011-04-19
Has anybody noticed increases in temperature of their graphics card ..... while running Firefox ......

I say this because my temp is usually @ 61 when in google chrome.

[screenshot chrome]("http://img862.imageshack.us/img862/4658/screenshot28s.png")

If I switch to firefox ...... it climbs straight upto 68 .....
at which point I switch out of firefox  ..... 

[screenshot firefox]("http://img855.imageshack.us/img855/951/screenshot29d.png")

as it still appears to be rising ....... ( I have more tabs open in firefox - but did not expect to see such a large increase in temperature >>>> 7 degrees more <<<< )

as soon as I drop out of firefox and back into chrome 
it starts to drop quite significantly until it comes back to 61 again

---

### Post by CSimpson on 2011-04-19
> **xebian said:**
> Am using Fedora 15 beta live right now and Gnome shell looks pretty and quite intuitive as this is my first time to see/use  it.  IMHO natty would have looked pretty as well.

Quite impressive, worked out of the box, radeon x1200, which I could never get Unity to work.

It is a beautiful shell.  Shame about how fat the theme is- I imagine the designer must have been on a very high resolution screen.  Epiphany is just plain silly, in Adwaita.  On that note: the Epiphany devs are supposedly redesigning their interface, though, and given the switch to webkit2, they'll soon have tab/process isolation and all that jazz.

“One of the main themes of the release will be further integration of the  browser with the new GNOME UI and design. We are still in the  brainstorming phase, but some of the front runners are replacing our  menubar with the Shell’s global app menu (more space for your web  content!)”

“We believe a split process model has quickly become a must-have for  modern browsers, so we want to announce our commitment to port Epiphany  to WebKit2 as soon as it is ready, and make this the default and only  configuration available, as in Chrome.”
-- [http://blogs.gnome.org/xan/2011/04/11/the-web-comes-to-gnome-ready-or-not/](http://blogs.gnome.org/xan/2011/04/11/the-web-comes-to-gnome-ready-or-not/)

So hey.  Epiphany.  *Meanwhile, in On Topic:*

> **cecilpierce said:**
> @CSimpson

I tried the fedora & suse live cd's and suse was the only one that had install, besides natty g3 screwed up so bad I had to purge it and took a lot of natty with it, finally got it back to normal and tried suse, its alot better then fedora so i'll wait till the ppa's catch up before I install it again,
Thanks again for the help.

The Fedora CD that you get to via gnome3.org, curiously, is uninstallable by design, yeah.  They do have an installable beta disc out, though.  It's nothing you won't have seen on Suse, I don't think.

I'm looking forward to using GNOME 3 a whole lot; I prefer it to Unity by a mile.

---

### Post by lucazade on 2011-04-19
> **CSimpson said:**
> ...Shame about how fat the theme is- I imagine the designer must have been on a very high resolution screen...

..I imagine the designer must have used a switched-off monitor..

---

### Post by Visceral Monkey on 2011-04-19
I tired Gnome 3 on Fedora before trying it on Ubuntu. It looked horrible, font wise. 

I've had very few problems with the Ubuntu PPA for Gnome 3. I've even uninstalled it, tried out unity again, removed unity and put gnome 3 back on, all without major problems.

I just installed KDE 4.6 as well. It reminds me of Paris Hilton, all bling and not much substance. The usability in KDE is non-existent compared to Gnome 3.

---

### Post by CSimpson on 2011-04-19
> **Visceral Monkey said:**
> I've had very few problems with the  Ubuntu PPA for Gnome 3. I've even uninstalled it, tried out unity again,  removed unity and put gnome 3 back on, all without major  problems.

I didn't have many, but the lack of the proper network manager applet  was a shame, the GDM fonts looked quite bad, and I had minor crashes here  and there of various things, none of which I have in 10.10.  I'll be  straight back to 11.04/GNOME 3 as soon as the release is out and the PPA  is sorted.

I've been keeping an eye on, among others, the blog of Rodrigo Moya, to see what's going on with the PPA.

[http://blogs.gnome.org/rodrigo/](http://blogs.gnome.org/rodrigo/)

---

### Post by thezood on 2011-04-20
> **23dornot23d said:**
> Has anybody noticed increases in temperature of their graphics card ..... while running Firefox ......

I say this because my temp is usually @ 61 when in google chrome.

[screenshot chrome]("http://img862.imageshack.us/img862/4658/screenshot28s.png")

If I switch to firefox ...... it climbs straight upto 68 .....
at which point I switch out of firefox  ..... 

[screenshot firefox]("http://img855.imageshack.us/img855/951/screenshot29d.png")

as it still appears to be rising ....... ( I have more tabs open in firefox - but did not expect to see such a large increase in temperature >>>> 7 degrees more <<<< )

as soon as I drop out of firefox and back into chrome 
it starts to drop quite significantly until it comes back to 61 again

Yes, I noticed this yesterday evening. I haven't got a temp reading but the fan worked constantly and my laptop got quite hot. Not sure if it's Firefox or something with the Gallium drivers. I bet power consumption is up too.

I tried installing fglrx because it's always nicer power- and heatwise but then I got all kinds of artifacts and garbled screens. In the end I had only static on the screen. I had to uninstall it from a terminal blindly since not even that worked.

If anyone has gotten fglrx to work, feel free to write how, and if temperatures were better.

---

### Post by celticbhoy on 2011-04-20
Using Natty with Gnome3 for a week or so now without any real issues on an old AAO ZG5 except one, in nautilus my right click menu has no scripts sub menu, even though I have some installed, and I have no Dropbox sub menu within my Dropbox folder. This is all on a clean install.

---

### Post by 23dornot23d on 2011-04-20
> **thezood said:**
> Yes, I noticed this yesterday evening. I haven't got a temp reading but the fan worked constantly and my laptop got quite hot. Not sure if it's Firefox or something with the Gallium drivers. I bet power consumption is up too.

I tried installing fglrx because it's always nicer power- and heatwise but then I got all kinds of artifacts and garbled screens. In the end I had only static on the screen. I had to uninstall it from a terminal blindly since not even that worked.

If anyone has gotten fglrx to work, feel free to write how, and if temperatures were better.


All seems ok now - temps are much lower after switching the kernel to the 2.6.39-rc4-generic

I also now use firefox 4 that I downloaded from the mozilla site ..... [no addons enabled]("http://img833.imageshack.us/img833/3869/screenshot38c.png")

[Firefox Now Screenshot]("http://img40.imageshack.us/img40/9663/screenshot35j.png")

Running temp now 60 - 61 ...... which is quite normal for this laptop with no real graphics load on it ...

---

### Post by rbrick49 on 2011-04-20
Have lost the plot or something I thought we were testing Natty with unity not gnome3 you can abuse me do what you like, but when it all boils down gnome 3 is not part of this distro its confusing to some that they think gnome 3 is going to be included in this build. why not fix the problems at hand and get this distro up and running then do after stable release install gnome3 and see what gives for somebodys sake let the devs get the distro right first

---

### Post by Justin Trouble on 2011-04-20
> **rbrick49 said:**
> Have lost the plot or something I thought we were testing Natty with unity not gnome3 you can abuse me do what you like, but when it all boils down gnome 3 is not part of this distro its confusing to some that they think gnome 3 is going to be included in this build. why not fix the problems at hand and get this distro up and running then do after stable release install gnome3 and see what gives for somebodys sake let the devs get the distro right first

This thread is titled "Gnome3 PPA is getting ready" - nothing to do with Unity (which is the official desktop in Natty) or graphics card temperatures caused by Firefox :tongue:

I'll add that I'm still using Gnome 3 from the Gnome Team PPA and I'm loving it. I haven't touched KDE since!

---

### Post by rbrick49 on 2011-04-20
aw well good luck

---

### Post by nothingspecial on 2011-04-20
> **rbrick49 said:**
> Have lost the plot or something I thought we were testing Natty with unity not gnome3 you can abuse me do what you like, but when it all boils down gnome 3 is not part of this distro its confusing to some that they think gnome 3 is going to be included in this build. why not fix the problems at hand and get this distro up and running then do after stable release install gnome3 and see what gives for somebodys sake let the devs get the distro right first

That's what all the other threads are about. We are testing natty with gnome-shell.

---

### Post by rbrick49 on 2011-04-20
> **thezood said:**
> Yes, I noticed this yesterday evening. I haven't got a temp reading but the fan worked constantly and my laptop got quite hot. Not sure if it's Firefox or something with the Gallium drivers. I bet power consumption is up too.

I tried installing fglrx because it's always nicer power- and heatwise but then I got all kinds of artifacts and garbled screens. In the end I had only static on the screen. I had to uninstall it from a terminal blindly since not even that worked.

If anyone has gotten fglrx to work, feel free to write how, and if temperatures were better.
hmmmm my fglrx works quite well on natty and my card is a 6950

---

### Post by jcrow on 2011-04-20
I was able to get gnome 3 working on my work laptop and home desktop. I uninstalled the gnome-accessibility-themes and installed the gnome-themes and gnome-themes-standard packages and everything now works except for dropbox. Is anyone else having issues with gnome 3 and dropbox? I also installed epiphany browser and it is really fast, but there is no flash! From what I understand, flash does not work with GTK+, so the developers blacklisted it.

---

### Post by Bou on 2011-04-20
> **CSimpson said:**
> On that note: the Epiphany devs are supposedly redesigning their interface, though, and given the switch to webkit2, they'll soon have tab/process isolation and all that jazz.

Since I guess you're using Epiphany, are you having a problem where flas content isn't shown in Epiphany whereas it's shown in Firefox? Is there a specific package you have to install?

---

### Post by bulldog on 2011-04-20
> **jcrow said:**
> I was able to get gnome 3 working on my work laptop and home desktop. I uninstalled the gnome-accessibility-themes and installed the gnome-themes and gnome-themes-standard packages and everything now works except for dropbox. Is anyone else having issues with gnome 3 and dropbox? I also installed epiphany browser and it is really fast, but there is no flash! From what I understand, flash does not work with GTK+, so the developers blacklisted it.

Did you install the propietary part of Dropbox?
I have Dropbox installed with no issues in Gnome-shell.

---

### Post by jcrow on 2011-04-20
I was getting a weird permissions error when I started the daemon. I had a development version of it when I was running unity. I'm not sure what the solution was because I tried a whole bunch of things, but I ended up downloading an older version of the .dropbox-d package and replacing the one in my home folder. I also reestablished my Dropbox folder. Part of the issue is that my Dropbox folder is a symlink to a folders on my Windows partition (I haven't booted it in months). I'ts working now, but I don't have the sync icons in nautilus. Notifications work fine.

---

### Post by jcrow on 2011-04-20
Flash is fine for me in Firefox and chromium. I found this on epiphany 3:

What's new in Epiphany 2.91.4:
December 21st, 2010

· Blacklist Flash plugin, since it will just crash in our GTK+ 3.x process.

---

### Post by Bou on 2011-04-20
> **jcrow said:**
> Flash is fine for me in Firefox and chromium. I found this on epiphany 3:

What's new in Epiphany 2.91.4:
December 21st, 2010

· Blacklist Flash plugin, since it will just crash in our GTK+ 3.x process.

Aaaaaalright, so no Flash for us Epiphany users :-(

---

### Post by CSimpson on 2011-04-20
> **Bou said:**
> Since I guess you're using Epiphany, are you having a problem where flas content isn't shown in Epiphany whereas it's shown in Firefox? Is there a specific package you have to install?

Actually, I use Firefox, for now.  Criteria for switching to Epiphany, for me, are:

[LIST]
[*]More space efficient interface
[*]Relevant animations for tabs (Firefox actually falls down on getting this quite right- they resize tabs right after they're closed.  Chrome gets this right.)
[*]Support for Flash, for as long as BBC iPlayer requires flash, i.e. the foreseeable future (although there is this, but I don't think it will necessarily be relevant here: [http://arstechnica.com/apple/news/2011/04/adobe-throws-in-towel-adopts-http-live-streaming-for-ios.ars](http://arstechnica.com/apple/news/2011/04/adobe-throws-in-towel-adopts-http-live-streaming-for-ios.ars) )
[/LIST]
I don't even need add blocking.  I'm happy without it.  I look forward to a competitive Epiphany.  A proper GTK browser focused  on GNOME would be nice, instead of getting whatever Firefox can pull  together when they're not too busy with Windows development.  Examples  of poor GNOME integration in Firefox include such things as what happens  when you choose to set an image as the background picture using the  browser.  Hardly optimal.

I only mentioned Epiphany because it is GNOME 3's browser, and this is a thread about GNOME 3. :D  I thought it might be interesting info to people reading this thread.

On that note, I know a lot of people have been irked by the default theme, and how there are no GTK 3 alternatives.  I haven't tried this, but Andrea Cimitan did port the Ambiance/Radiance themes long, long ago.  There are some out-of-date PPAs:
[http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/](http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/)

---

### Post by screaminj3sus on 2011-04-20
> **CSimpson said:**
> Actually, I use Firefox, for now.  Criteria for switching to Epiphany, for me, are:

[LIST]
[*]More space efficient interface
[*]Relevant animations for tabs (Firefox actually falls down on getting this quite right- they resize tabs right after they're closed.  Chrome gets this right.)
[*]Support for Flash, for as long as BBC iPlayer requires flash, i.e. the foreseeable future (although there is this, but I don't think it will necessarily be relevant here: [http://arstechnica.com/apple/news/2011/04/adobe-throws-in-towel-adopts-http-live-streaming-for-ios.ars](http://arstechnica.com/apple/news/2011/04/adobe-throws-in-towel-adopts-http-live-streaming-for-ios.ars) )
[/LIST]
I don't even need add blocking.  I'm happy without it.  I look forward to a competitive Epiphany.  A proper GTK browser focused  on GNOME would be nice, instead of getting whatever Firefox can pull  together when they're not too busy with Windows development.  Examples  of poor GNOME integration in Firefox include such things as what happens  when you choose to set an image as the background picture using the  browser.  Hardly optimal.

I only mentioned Epiphany because it is GNOME 3's browser, and this is a thread about GNOME 3. :D  I thought it might be interesting info to people reading this thread.

On that note, I know a lot of people have been irked by the default theme, and how there are no GTK 3 alternatives.  I haven't tried this, but Andrea Cimitan did port the Ambiance/Radiance themes long, long ago.  There are some out-of-date PPAs:
[http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/](http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/)
The firefox nightlies now have the same tab resizing behavior as chrome.

---

### Post by lucazade on 2011-04-20
> **CSimpson said:**
> 
On that note, I know a lot of people have been irked by the default theme, and how there are no GTK 3 alternatives.  I haven't tried this, but Andrea Cimitan did port the Ambiance/Radiance themes long, long ago.  There are some out-of-date PPAs:
[http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/](http://www.cimitan.com/blog/2010/10/14/murrine-and-ubuntus-light-themes-ported-to-gtk-30-with-a-ppa/)

Unfortunately that port needs more work, will be probably ready for 11.10.
The author has been busy with overlay-scrollbar during natty dev cycle.

---

### Post by Visceral Monkey on 2011-04-20
> **rbrick49 said:**
> hmmmm my fglrx works quite well on natty and my card is a 6950

Are you talking about Natty using Unity or Natty using Gnome 3? Using Gnome 3, fglrx should give you all sorts of graphical artifacts..

Unity is fine.

---

### Post by magneze on 2011-04-20
> **Visceral Monkey said:**
> I tired Gnome 3 on Fedora before trying it on Ubuntu. It looked horrible, font wise. 

I've had very few problems with the Ubuntu PPA for Gnome 3. I've even uninstalled it, tried out unity again, removed unity and put gnome 3 back on, all without major problems.

I just installed KDE 4.6 as well. It reminds me of Paris Hilton, all bling and not much substance. The usability in KDE is non-existent compared to Gnome 3.What's the best way to remove Unity? I plan on sticking with Gnome 3, so I don't really want a load of updates to something I'll never use..

---

### Post by Bou on 2011-04-20
By the way, I'm getting the old style nm-applet, which doesn't fit gnome-shell at all. I take it some of you guys got the new one? How can I do that? I seem to have the latest version in the PPA.

---

### Post by Visceral Monkey on 2011-04-20
> **magneze said:**
> What's the best way to remove Unity? I plan on sticking with Gnome 3, so I don't really want a load of updates to something I'll never use..

I'm not sure if you can totally remove it. Just installing Gnome 3 seems to remove parts of it.

---

### Post by Visceral Monkey on 2011-04-20
Does anyone know how far behind Fedora Gnome 3 is on Ubuntu? Or are they pretty much both current...?

I tried Gnome 3 on Fedora and it seemed a tad different, but I can't remember the little details now. What killed it for me was the horrible Fedora fonts, no codecs and bad package system. Apparently you still have to jump though several hoops that Ubuntu did away with a while back.

---

### Post by vaskark on 2011-04-20
Just a few questions about Gnome 3 and Unity:

1) Is it safe yet to try out the gnome 3 team PPA? Safe for someone with moderate skills, that is.
2) When Gnome 3 is finally released (next week?) will we have the option of switching between Unity and Gnome 3 interface from the login manager?

Thanks.

---

### Post by CSimpson on 2011-04-20
> **Bou said:**
> By the way, I'm getting the old style nm-applet, which doesn't fit gnome-shell at all. I take it some of you guys got the new one? How can I do that? I seem to have the latest version in the PPA.

Ubuntu's PPA only contains the old applet for now.

> **vaskark said:**
> Just a few questions about Gnome 3 and Unity:

1) Is it safe yet to try out the gnome 3 team PPA? Safe for someone with moderate skills, that is.
2) When Gnome 3 is finally released (next week?) will we have the option of switching between Unity and Gnome 3 interface from the login manager?

Thanks.

It's safe to try now, though there are some bugs and other hiccups.  There are no GTK 3 themes other than the default in GNOME 3.  After installation, if the theme is bad, you may have to uninstall gnome-accessibility-themes so that you are able to install gnome-themes and gnome-themes-standard.

You may then need to install gnome-tweak-tool, so that you can set the GTK theme to Adwaita.

You can (theoretically) switch between sessions via GDM, but so far, GNOME 3 does not sit right with Unity, probably because Canonical have patched a lot of libraries to make Unity work, and those patches haven't gone upstream.

GNOME 3 has been out now since April 6th. [http://gnome3.org/](http://gnome3.org/)

> **Visceral Monkey said:**
> Does anyone know how far behind Fedora  Gnome 3 is on Ubuntu? Or are they pretty much both current...?

I tried Gnome 3 on Fedora and it seemed a tad different, but I can't  remember the little details now. What killed it for me was the horrible  Fedora fonts, no codecs and bad package system. Apparently you still  have to jump though several hoops that Ubuntu did away with a while  back.

As far as I can tell, GNOME 3 on Ubuntu is missing quite a bit of the guts of the system.  Fedora has GNOME 3 right up to date; the whole thing is in place.  It's hard to judge Ubuntu's progress, because thus far I haven't found a page tracking what they have and haven't done.  Debian has such a page: [http://www.0d.be/debian/debian-gnome-3.0-status.html](http://www.0d.be/debian/debian-gnome-3.0-status.html)

The user facing differences are slight:
Fedora has the right nm-applet, and everything in System Settings will actually work. ;)  There are various small things like that.

---

### Post by vaskark on 2011-04-20
> **CSimpson said:**
> 
It's safe to try now, though there are some bugs and other hiccups.  There are no GTK 3 themes other than the default in GNOME 3.  After installation, if the theme is bad, you may have to uninstall gnome-accessibility-themes so that you are able to install gnome-themes and gnome-themes-standard.

You may then need to install gnome-tweak-tool, so that you can set the GTK theme to Adwaita.

You can (theoretically) switch between sessions via GDM, but so far, GNOME 3 does not sit right with Unity, probably because Canonical have patched a lot of libraries to make Unity work, and those patches haven't gone upstream.

GNOME 3 has been out now since April 6th. [http://gnome3.org/](http://gnome3.org/)

Thanks for your quick reply. I think I'll wait a bit longer ;)

---

### Post by CSimpson on 2011-04-20
> **vaskark said:**
> Thanks for your quick reply. I think I'll wait a bit longer ;)

I gave it a good go, and LOVED the experience, but I'm back on Maverick, for now, myself. :D

I'm really looking forward to a thorough and complete Ubuntu/GNOME 3 experience.  It's different- you'll be surprised if you don't know what to expect, but I think pleasantly so.

EDIT:  Also, I just happened to swing by at the right time, is all.  I'm checking in on the thread every now and then to make sure there isn't anything I can help with. :)

---

### Post by splicerr on 2011-04-20
> **Visceral Monkey said:**
> I tried Gnome 3 on Fedora and it seemed a tad different, but I can't remember the little details now. What killed it for me was the horrible Fedora fonts, no codecs and bad package system. Apparently you still have to jump though several hoops that Ubuntu did away with a while back.

For codecs you can add the [RPM Fusion repositories]("http://rpmfusion.org/Configuration"), then just try to play any video with Totem and the codec installation process is basically the same as in Ubuntu. I'm sure there is a solution to the ugly fonts as well, haven't tried it yet.

---

### Post by Visceral Monkey on 2011-04-20
> **splicerr said:**
> For codecs you can add the [RPM Fusion repositories]("http://rpmfusion.org/Configuration"), then just try to play any video with Totem and the codec installation process is basically the same as in Ubuntu. I'm sure there is a solution to the ugly fonts as well, haven't tried it yet.

Yeah, the people on the Fedora forums have been pretty helpful with tips on those issues. My problem is, they are issues that no Linux distro should really have these days. And it appears they are all issues caused by "open source principals" which for them means nothing closed source in the distro by default, which to be frank is something I left behind years ago and have zero desire to endure again.

---

### Post by gnomeuser on 2011-04-21
> **splicerr said:**
> For codecs you can add the [RPM Fusion repositories]("http://rpmfusion.org/Configuration"), then just try to play any video with Totem and the codec installation process is basically the same as in Ubuntu. I'm sure there is a solution to the ugly fonts as well, haven't tried it yet.

freetype-freeworld from the same repository will enable the patented font hinting which should increase visual quality.

---

### Post by screaminj3sus on 2011-04-21
> **gnomeuser said:**
> freetype-freeworld from the same repository will enable the patented font hinting which should increase visual quality.

It makes it *slightly* better but even with that fedoras fonts are still pretty bad, and nowhere near the quality of ubuntu's font rendering.

---

### Post by cecilpierce on 2011-04-21
> **screaminj3sus said:**
> It makes it *slightly* better but even with that fedoras fonts are still pretty bad, and nowhere near the quality of ubuntu's font rendering.

just dowloaded fedora/g3 to give it a shot. took me 3 hours to get kubuntu with g3 on it ! so far i like suse g3, i think they are up to 3.0.0.192 on updates. cant keep up with all this malarkey...
 :P

---

### Post by magneze on 2011-04-21
Latest updates seem to have broken font rendering, icon settings and gnome3-tweak tool. :(

Not Gnome 3 PPA updates I might add - updates to Natty.

---

### Post by Bou on 2011-04-21
> **screaminj3sus said:**
> It makes it *slightly* better but even with that fedoras fonts are still pretty bad, and nowhere near the quality of ubuntu's font rendering.

Just tried Fedora for the first time and the font is definitely too small. That aside I feel surprisingly at home, though.

---

### Post by Quackers on 2011-04-21
> **magneze said:**
> Latest updates seem to have broken font rendering, icon settings and gnome3-tweak tool. :(

Not Gnome 3 PPA updates I might add - updates to Natty.

gnome-tweak-tool is still working here and my fonts still look ok - on both Natty/gnome-shell systems.

---

### Post by gnomeuser on 2011-04-21
[http://blog.crozat.net/2011/04/gnome-30-available-for-opensuse-114.html](http://blog.crozat.net/2011/04/gnome-30-available-for-opensuse-114.html)

GNOME3 can now be installed on a standard openSUSE 11.4 as well.

---

### Post by cecilpierce on 2011-04-21
> **gnomeuser said:**
> [http://blog.crozat.net/2011/04/gnome-30-available-for-opensuse-114.html](http://blog.crozat.net/2011/04/gnome-30-available-for-opensuse-114.html)

GNOME3 can now be installed on a standard openSUSE 11.4 as well.

Thanks for that, I have the live version and its working great but it says repo's are changeing so I guess I'll do the upgrade thing.

---

### Post by Visceral Monkey on 2011-04-21
Holy GOD, I just cannot find *anything* using the crappy fedora package thing. It always pulls ups crap and never what I need. How do people find and install new software using Fedora? This is insane!

---

### Post by pferraro on 2011-04-21
> **Bou said:**
> By the way, I'm getting the old style nm-applet, which doesn't fit gnome-shell at all. I take it some of you guys got the new one? How can I do that? I seem to have the latest version in the PPA.

AIUI, Network-Manager 0.9 supposedly includes better integration with gnome-shell.  There are packages for the latest release candidate in debian experimental:
[http://packages.debian.org/experimental/network-manager](http://packages.debian.org/experimental/network-manager)

There are, however, no 0.9 builds for the plugins (vpn, etc.).

---

### Post by cecilpierce on 2011-04-21
> **Visceral Monkey said:**
> Holy GOD, I just cannot find *anything* using the crappy fedora package thing. It always pulls ups crap and never what I need. How do people find and install new software using Fedora? This is insane!

check out:

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by gnomeuser on 2011-04-21
> **Visceral Monkey said:**
> Holy GOD, I just cannot find *anything* using the crappy fedora package thing. It always pulls ups crap and never what I need. How do people find and install new software using Fedora? This is insane!

Await AppStream and be amazed it's glory.

[http://www.omgubuntu.co.uk/2011/02/appstream-the-unified-app-store-for-linux/](http://www.omgubuntu.co.uk/2011/02/appstream-the-unified-app-store-for-linux/)

---

### Post by benerivo on 2011-04-21
Is AppStream going to work like Arch's AUR, where it can install any application using a small installation script?

---

### Post by M4570D0N on 2011-04-21
Has anyone been able to install the user-theme extension of gnome-shell-extensions?

Whenever I try to configure it I get a Makefile error

```
Makefile:431: *** missing separator.  Stop.
```

Line 431 just says
```
@GSETTINGS_RULES@
```

Here's a little more of it(lines 423-435):
```
metadata.json: metadata.json.in $(top_builddir)/config.status
	$(AM_V_GEN) sed -e "s|[@]LOCALEDIR@|$(datadir)/locale|" \
	    -e "s|[@]uuid@|$(uuid)|" \
	    -e "s|[@]shell_current@|$(PACKAGE_VERSION)|" \
	    -e "s|[@]url@|$(extensionurl)|" $< > $@

%.xml:       %.xml.in       $(INTLTOOL_MERGE) ; LC_ALL=C $(INTLTOOL_MERGE) -x -u /tmp $< $@

@GSETTINGS_RULES@

# Tell versions [3.59,3.63) of GNU make to not export all variables.
# Otherwise a system limit (for SysV at least) may be exceeded.
.NOEXPORT:
```

---

### Post by gnomeuser on 2011-04-21
> **benerivo said:**
> Is AppStream going to work like Arch's AUR, where it can install any application using a small installation script?

AppStream builds on PackageKit (and a bunch of other technologies), all of which layer ontop of your existing Package Manager.

Anything the PackageKit backend for AUR supports, it will do. So without knowing the right answer (due to unfamilarity with recent Arch) - hopefully.

AppStream is basically taking the Ubuntu Software Center, building on PackageKit and standardizing on a number of technologies such as debtags to bring the USC experience to every Linux desktop and improve upon it for all.

People have misunderstood PackageKit for years, hopefully with AppStream and the strong cross distribution collaboration built around it, PackageKit will finally be allowed to shine.

---

### Post by el_koraco on 2011-04-21
Dunno what's wrong witk PackageKit, it's like almost exactly like Synaptic.

---

### Post by gnomeuser on 2011-04-21
> **el_koraco said:**
> Dunno what's wrong witk PackageKit, it's like almost exactly like Synaptic.

Actually that is just the default PackageKit frontend currently. The power of PackageKit is in giving a common interface to your distros package manager. E.g. for installing support in file-roller when you try to unpack an unsupported format, or say play an unsupported file in a GStreamer application.

---

### Post by M4570D0N on 2011-04-21
> **FEGuy said:**
> I noticed a couple comments about not being able to delete files with the Delete key. For some reason, this appears to be a new 'security' feature, akin to not being able to select 'Power Off' from the menu without holding Control. The solution is the same here - to delete files without dragging them to the Trash, the new key binding is Ctrl+Del.

Additionally, I was doing some exploring with dconf editor and noticed that if you go to org>>gnome>>nautilus>>preferences there is an entry for "enable-delete" which is unchecked. This enables you to use the delete key (at least I think it does. Have not tried it), but it does not send it to the trash can. It immediately deletes the file/folder permanently.

> Schema: org.gnome.nautilus.preferences
Summary: Whether to enable immediate deletion
Description: If set to true, then Nautilus will have a feature allowing you to delete a file immediately and in-place, instead of moving it to the trash. This feature can be dangerous, so use caution.
Type: Boolean
Default: False

Found it after coming across this very helpful site:
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

Unfortunately, that link still does not help me with my attempts to install the user-theme extension. :(

edit: never mind. That's just the same as going to preferences in Nautilus and checking the box in the behavior tab for "Include a Delete command that bypasses Trash"

---

### Post by el_koraco on 2011-04-21
> **gnomeuser said:**
> Actually that is just the default PackageKit frontend currently. The power of PackageKit is in giving a common interface to your distros package manager. E.g. for installing support in file-roller when you try to unpack an unsupported format, or say play an unsupported file in a GStreamer application.

I know that, but the thing most people hate about it is the interface and its searching capabilities. In that regard, the gnome version looks and works almost exactly like Synaptic, which is loved by almost everybody, except for a few clicks here, a few there. I've also not encountered a single dependency resolution or speed problem with the kde version. 

Although, discovering Muon has been oh so nice.

---

### Post by cariboo on 2011-04-21
> **M4570D0N said:**
> Additionally, I was doing some exploring with dconf editor and noticed that if you go to org>>gnome>>nautilus>>preferences there is an entry for "enable-delete" which is unchecked. This enables you to use the delete key (at least I think it does. Have not tried it), but it does not send it to the trash can. It immediately deletes the file/folder permanently.

The same setting is available in Nautilus->Edit->Preferences->Behavior->Trash

---

### Post by BigCityCat on 2011-04-21
Don't want to jinx it but I am using Gnome 3 with very little issues. Firefox seems to hang at times.

---

### Post by BigCityCat on 2011-04-21
> **vhaarr said:**
> Oh my, that icon theme looks wonderful for Gnome Shell! Give us a hint? :)

Feanza wolfe. lol it's on gnome look. Just copy and paste into usr/share/icons and use gnome tweak tool to change the icon theme. I think you need Faenza as well because Faenza Wolfe is a variant and only changes the folders. Not sure.

---

### Post by BigCityCat on 2011-04-21
Here is the shell theme. Use gksudo nautilus and copy paste the theme folder into usr/share/gnome-shell(replacing the default theme folder). It is my understanding that you have to copy and paste and not remove the current theme folder for it to work. Make a back up copy of your original themes folder or you will lose it. These instructions assume you installed shell via a ppa.

[http://browse.deviantart.com/?qh=&section=&q=gnome+shell#/d371nhf](http://browse.deviantart.com/?qh=&section=&q=gnome+shell#/d371nhf)

---

### Post by Visceral Monkey on 2011-04-21
Back on the subject of Gnome 3 for 11.04, does anyone even know if it will be ready in time for 11.04 to launch next week? It looks like it's not feature complete and won't be in time...

---

### Post by cariboo on 2011-04-21
> **Visceral Monkey said:**
> Back on the subject of Gnome 3 for 11.04, does anyone even know if it will be ready in time for 11.04 to launch next week? It looks like it's not feature complete and won't be in time...

Gnome 3 won't be included in this release, that's why there is a ppa.

---

### Post by Visceral Monkey on 2011-04-21
> **cariboo907 said:**
> Gnome 3 won't be included in this release, that's why there is a ppa.

Right, but I was under the impression the Gnome team was going to try and have the finished version in the PPA at launch..maybe I misread something.

---

### Post by Justin Trouble on 2011-04-22
> **Visceral Monkey said:**
> Right, but I was under the impression the Gnome team was going to try and have the finished version in the PPA at launch..maybe I misread something.

Gnome 3 isn't the official desktop in Natty, which is why it's packaged in a third party PPA by the Gnome 3 Team volunteers.

It's a user contributed effort, and I believe the Gnome 3 Team PPA guys are busy fixing bugs in Natty, which is probably more important right now.

---

### Post by DevHead on 2011-04-22
> **Visceral Monkey said:**
> Right, but I was under the impression the Gnome team was going to try and have the finished version in the PPA at launch..maybe I misread something.

That's my impression too.

I know that Gnome3 isn't part of the Natty release (thus the PPA).  I just want to try Gnome3 without anything breaking.  Hopefully the bugs will be squashed by the time Natty is released so that users can have the option of Unity and Gnome3.

---

### Post by xebian on 2011-04-22
> **Visceral Monkey said:**
> Back on the subject of Gnome 3 for 11.04, does anyone even know if it will be ready in time for 11.04 to launch next week? It looks like it's not feature complete and won't be in time...

I have never seen natty in unity but since installing Gnome-shell from the ppa for the last 2 days it looks like I'm going to like it and quite stable/impressive.

---

### Post by pulpo69 on 2011-04-22
is there anybody with a working gnome3 install and having fglrx enabled?
i've fglrx enabled because it works much better with my ati-card, but every gnome3 installation borked my system and i had to do a freh install.

Any ideas?

---

### Post by Visceral Monkey on 2011-04-22
> **pulpo69 said:**
> is there anybody with a working gnome3 install and having fglrx enabled?
i've fglrx enabled because it works much better with my ati-card, but every gnome3 installation borked my system and i had to do a freh install.

Any ideas?

Fglrx doesn't work with Gnome 3 and apparently won't for the near future. Huge bummer. This is across all distro's, not just Ubuntu. It has corrupted graphics on the top "bar", etc. You can "fix" it by just using the video card driver program thing (Jockey?) and disabling the ATI driver which will switch it back to the open source one.

---

### Post by xebian on 2011-04-22
> **pulpo69 said:**
> is there anybody with a working gnome3 install and having fglrx enabled?
i've fglrx enabled because it works much better with my ati-card, but every gnome3 installation borked my system and i had to do a freh install.

Any ideas?

I have ati Radeon X1200 built in card using radeon drivers and is working nicely with gnome-shell but NEVER in unity.

---

### Post by skibler on 2011-04-22
> **M4570D0N said:**
> Regarding the Gnome Shell Extensions mentioned above, in the comments of that article, Andrew (aka nilarimogard/ aka dude that runs Web Upd8 ) was nice enough to also post some install instructions for those that are new to git.

Sorry to quote this out of the blue, but I used these instructions to download, compile, and install the gnome3 extensions. I am a bit stuck on how to use them :p. I have restarted gnome, but how does it know to load them?



Also, unrelated question. Is there a battery level indicator that integrates with gnome3/gnome-shell?

---

### Post by Rifester on 2011-04-22
There is but it is not showing up in Gnome 3 on 11.04 for quite a few people.

---

### Post by cariboo on 2011-04-22
The battery level indicator works on my netbook running gnome 3/gnome-shell, it even shows a percentage, which it hasn't done in any release since Lucid.

---

### Post by Quackers on 2011-04-22
> **cariboo907 said:**
> The battery level indicator works on my netbook running gnome 3/gnome-shell, it even shows a percentage, which it hasn't done in any release since Lucid.
My laptop too :-)

---

### Post by terry_gardener on 2011-04-22
i have used the mini iso and installed via cli and then installed the gnome-desktop-environment. 

then when it finished installing i added the gnome3 ppa and install gnome shell and gnome 3 components. 

when i load into gnome shell it seems that the theme is not very nice, quite  old looking is there any way to change this. 

i am using the nvidia current driver.

i have installed gnome-tweak and  change the gtk theme to clearlooks but still doesn't look right

---

### Post by seeker5528 on 2011-04-22
> **el_koraco said:**
> I know that, but the thing most people hate about it is the interface and its searching capabilities. In that regard, the gnome version looks and works almost exactly like Synaptic, which is loved by almost everybody, except for a few clicks here, a few there. I've also not encountered a single dependency resolution or speed problem with the kde version.

I think often it's less about what you like and more about what fits your level of need, the different front ends have their different things to like or dislike.

Package kit is good for those specialized tools, codec installer, command not found, firefox plugin installer, etc...

It's good for basic package management front ends like you would use in a stable release where you expect to only get bug fixes, and not new versions of stuff.

Not as good for Debian unstable, following and Ubuntu development cycle, etc... and not intended to provide the range of features that would allow the front ends to have the range of features that Synaptic has.

I have not used any of the package kit front ends for a while, but they did have some significant quirks and stability issues in the past, there may or may not still be some issue in that area.

Synaptic will show you broken packages and attempt to resolve the issues, success rate may be a bit questionable, but it works if the problem is not too bad. You can see changelogs of a selected package, see dependencies of the currently installed and available versions of a package, and allow you to pin packages. Synpatic will let you force a downgrade, but there are significant limitations in the way it deals with this, it gets a little quirky if you have to let it mark stuff for removal because of dependencies then go through the list of marked changes and start forcing the downgrade of additional related packages and unmarking others that you want to keep.

For me personally, before you even get into any of that other stuff, Synaptic shows you the packages that are new, if the packagekit frontends could/would do that I might be more willing to run them more and save the use of Synaptic for when I want those other features, assuming of course that apt-changes won't cause any issues for package kit or it's front ends.

Unless the development priorities for package kit change to allow the front ends to be more capable it doesn't make sense to compare these front ends to Synaptic. Package kit front ends will be good for your basic installation tasks, in some cases a better choice to include OOB than Synaptic. If you start adding PPAs that provide backports, add 3rd party repositories, or start following the stuff that's in development, you may find Synaptic preferable.

But then again maybe you just prefer to handle all the advanced stuff at the command line, in which case you might like [aptsh](http://packages.ubuntu.com/natty/aptsh).

Later, Seeker

---

### Post by FEGuy on 2011-04-22
> **Quackers said:**
> My laptop too :-)
Strange. For me it shows a charged battery icon when it's fully charged, but if I switch to batter power it crashes - the icon vanishes and all I have left is the notification that the battery is discharging.

Also, anyone having problems getting Conky to play nice with GNOME 3? Everything opens up just fine, but just a bit off, and if I switch focus to the desktop by minimizing everything else open it starts to overlap things when I restore or open them. If I try to kill and restart Conky, the process seems to start right, but nothing actually comes up on screen.

---

### Post by Visceral Monkey on 2011-04-23
Does anyone know when the last update to the Gnome PPA was?

---

### Post by t.rei on 2011-04-23
You can see for yourself when the last update was:

[https://code.launchpad.net/~gnome3-team]("https://code.launchpad.net/%7Egnome3-team")

---

### Post by terry_gardener on 2011-04-23
i have fixed the theming issues i had earlier in this thread, seems it was because it was missing the default theme adwaita  

to do this i downloaded the default shell theme from earlier in this thread and extracted it into /usr/share/themes folder. 

theme logged off and back on for the changes to apply.

them changed the icon theme to humanity (using gnome-tweak-tool) as it seemed abit grey for me.

---

### Post by BigCityCat on 2011-04-23
Here is a tutorial on webupd8 for GNOME 3. I changed the window decorations to egtk.

[http://www.webupd8.org/2011/04/change-gnome-3-gnome-shell-or-classic.html](http://www.webupd8.org/2011/04/change-gnome-3-gnome-shell-or-classic.html)

---

### Post by Visceral Monkey on 2011-04-23
> **t.rei said:**
> You can see for yourself when the last update was:

[https://code.launchpad.net/~gnome3-team]("https://code.launchpad.net/%7Egnome3-team")

Awesome! Thank you!

---

### Post by ratcheer on 2011-04-23
I am late to the party, but I finally got Gnome3 and gnome-shell installed and working, this afternoon.

I have been cruising through this huge thread trying to get things set up properly. I managed to get the adwaita theme activated. My mouse pointers still look awful, though.

My biggest problem is that it is now constantly using 100% of my CPU (both hyperthreads). Is that fixable? top says that command "gnome-settings-" is using all the CPU. How do I troubleshoot it? I don't recall seeing this mentioned, elsewhere.

Tim

---

### Post by ratcheer on 2011-04-23
> **ratcheer said:**
> 

My biggest problem is that it is now constantly using 100% of my CPU (both hyperthreads). Is that fixable? top says that command "gnome-settings-" is using all the CPU. How do I troubleshoot it? I don't recall seeing this mentioned, elsewhere.



Never mind. After rebooting the system, CPU usage returned to normal.

Tim

---

### Post by ratcheer on 2011-04-23
> **ratcheer said:**
> My mouse pointers still look awful, though.


It turns out that the ugly mouse pointers are only in Firefox. Which is what I use about 90% of the time. Any idea how to fix mouse pointers for Firefox, only?

Tim

---

### Post by bulldog on 2011-04-23
@ratcheer.

You should take a look at this post [http://ubuntuforums.org/showpost.php?p=10676041&postcount=352](http://ubuntuforums.org/showpost.php?p=10676041&postcount=352)

There you can find how to setup your mouse pointer,at least it did a good yob for mine.

---

### Post by ratcheer on 2011-04-23
> **bulldog said:**
> @ratcheer.

You should take a look at this post [http://ubuntuforums.org/showpost.php?p=10676041&postcount=352](http://ubuntuforums.org/showpost.php?p=10676041&postcount=352)

There you can find how to setup your mouse pointer,at least it did a good yob for mine.

Ok. I really do appreciate the advice, but now instead of having the ugly mouse pointers only in Firefox, I have them everywhere. :(

Tim

---

### Post by wedderburn on 2011-04-23
> **ratcheer said:**
> Ok. I really do appreciate the advice, but now instead of having the ugly mouse pointers only in Firefox, I have them everywhere. :(

Tim

That black cursor is the default one for gnome, though if you like the one ubuntu uses change "Adwaita" to "DMZ-White" in the commands given.

theres a fair few usablity reasons for choosing a black cursor though :)

---

### Post by ratcheer on 2011-04-23
> **wedderburn said:**
> That black cursor is the default one for gnome, though if you like the one ubuntu uses change "Adwaita" to "DMZ-White" in the commands given.

theres a fair few usablity reasons for choosing a black cursor though :)

Thanks. I admit it is easier to see, but it sure is ugly. Especially the tiny black hand that displays when hovering over a hyperlink.

Tim.

---

### Post by M4570D0N on 2011-04-24
> **ratcheer said:**
> Never mind. After rebooting the system, CPU usage returned to normal.

Tim

I've had it happen to me twice. post #342:
> **M4570D0N said:**
> holy carp. I tried to start gnome shell and it  failed to load. It got stuck on the gdm screen after logging in so I was  just staring at a blank blue screen. I dropped down to restart gdm and  log in again. My fan started spinning the fastest I think I've ever  heard it and I could feel my laptop starting to cook. I looked at the  system monitor both CPUs were maxed at 100%. There were two  gnome-settings-daemons listed. One was listed at 120% of CPU the other  at 184% of CPU. I killed them both and everything was fine after that.  Good times.

---

### Post by uninventiveheart on 2011-04-24
My experience: ASUS G72GX Laptop with NVidia GTX 260M, got it installed on 11.04.  

I first had to enter in Fallback Mode knowing nothing about how the graphic setup was.  I installed the proprietary driver, and did a restart.  Bye-bye fallback mode.

When I came back the desktop would refuse to update.  I can see the top bar, but any window opened would go through one redraw then wouldn't reflect any changes.  The menus worked if I moved to the top left corner, and if I clicked on a menu (The social menu, Sound, Accessibility, etc.) and each time I opened one, the desktop would update once.  A fix for this I've found out is to open Accessibility and turn Zoom mode on.  For some reason, everything drew fine when zoomed in, but wouldn't function when I shut it off.

So, after turning off the NVidia driver and turning on Nouveau, everything started working again.  That's when I found the second issue: under Nouveau, the menu icons were all washed out.  Second fix: I read on the ArchLinux forums about what a user did: [https://bbs.archlinux.org/viewtopic.php?pid=912091#p912091](https://bbs.archlinux.org/viewtopic.php?pid=912091#p912091)  Essentially, Alt-F2, gksudo gedit, open /usr/share/gnome-shell/js/ui/appDisplay.js, then turn vfade off by changing the variable to "false" (use Find to locate it), then immediately below it, in the ensureIconVisible() function, comment out each line mentioning "vfade" with two slashes "//" at the front.  This is a hack, and may be undone with updates if the same code returns.

Third, Adwaita doesn't get installed by default.  If you want something better than 1999-era Linux Window Management, install the gnome-themes-default package with Gnome 3 PPA in your repository collection, then gnome-tweak-tool.  Once both are installed, Log Out and log back in to add the new themes to memory.  Finally, Activities, search Tweak, click on the first Icon that appears and under "Interface" change GTK+ and Icon themes to Adwaita.  And with that...

[IMG]http://img97.imageshack.us/img97/3448/screenshotlh.png[/IMG]

Welcome to Gnome 3!

---

### Post by ratcheer on 2011-04-24
> **M4570D0N said:**
> I've had it happen to me twice. post #342:

Oh yes, I do remember that. The situations seemed so different, I don't think I related them to each other.

In my case, it was gnome-settings-daemon using all the CPU.

Tim

---

### Post by RJ12 on 2011-04-24
Ok, I'm getting back into Gnome-Shell, I made a separate partition for it so I can break it all I want :) anyone know how to install gnome-shell themes? I wanted to try to install the Atolm theme that is on WebUpd8, but when I installed it, and did the "rt" command and even the "r" command, it looked incomplete and a lot of elements where missing, I had to resort to the default theme. This happened when trying to use the Smooth Inset theme that was on OMG! Ubuntu!

Edit: I just noticed, I only get the battery icon appear for about two seconds then it disappears (I am on Battery power when this happens) I'm guessing something is crashing...

---

### Post by Quackers on 2011-04-24
Does the battery icon appear if you plug the AC adaptor in?
Mine does after a reboot. Haven't tried logging out/in. I'll try that now.

---

### Post by RJ12 on 2011-04-24
> **Quackers said:**
> Does the battery icon appear if you plug the AC adaptor in?

nope :(

---

### Post by Quackers on 2011-04-24
See edit :-)

---

### Post by RJ12 on 2011-04-24
> **Quackers said:**
> 
Mine does after a reboot. Haven't tried logging out/in. I'll try that now.

It will, but then as soon as I remove the plug the battery icon shows up, then it disappears again

---

### Post by Quackers on 2011-04-24
oops! It wouldn't let me log in again! I've rebooted and it's fine again.
My battery icon disappears when the AC adaptor is unplugged. If I plug it back in the icon still doesn't appear. If I reboot, it returns. If I unplug AC again the icon will disappear.

---

### Post by RJ12 on 2011-04-24
> **Quackers said:**
> oops! It wouldn't let me log in again! I've rebooted and it's fine again.
My battery icon disappears when the AC adaptor is unplugged. If I plug it back in the icon still doesn't appear. If I reboot, it returns. If I unplug AC again the icon will disappear.

I think some kind of program is probably crashing causing the icon to not return

---

### Post by akand074 on 2011-04-24
I have Gnome 3 working now in Ubuntu 11.04 x64 on my desktop (specs listed in my signature) after mindless hours of reinstalling/trying other things. I finally have it working using the open-source drivers. All the graphics become all messed up with the proprietary drivers. I have a few major problems:

1. I can't file share? :S Usually I can just right click a folder and choose to share it. That option no longer exists? How do I file share in gnome 3.. this is really important.

2. The delete button on my keyboard no longer works? I have to right click and select "move to trash" which is annoying

3. Other misc bugs like dragging lag or missing file names occasionally

4. I can't get conky to work! I load it and nothing comes up.

5. Started using Evolution + Empathy. Do I not get a notification when I have an email? I believe there was a notification icon for it in regular Ubuntu.

One thing I really don't like is that when I search an application and press enter, if the application is already running it brings me to the open one. I really would like to be able to open a new firefox instance without having to go to my mouse. I'm finding myself more dependent on my mouse than I had hoped. I installed gnome 3 mainly because I thought it would be the least mouse-dependent.

Has anyone done file sharing yet? That's a big one for me right now. This shell can be efficient and useful but they have really dumbed stuff down and took away a lot of customizability which is frustrating. Worst case I may have to drop back to Unity, which is too bad I think gnome 3 is a better overall design for what I do on my desktop.

---

### Post by Visceral Monkey on 2011-04-24
If your main interest right now is Gnome 3 more-so than Ubuntu, you might want to try out SuSE 11.4.They just finished Gnome 3 on the recently released SuSE 11.4 and it's literally one click to install Gnome 3. So far, it's been a smooth experience and a much better one than the Fedora Gnome 3 experiment I tried.

[http://software.opensuse.org/developer](http://software.opensuse.org/developer)

And one click Gnome 3 install once that's installed:
[http://en.opensuse.org/openSUSE:GNOME_3.0](http://en.opensuse.org/openSUSE:GNOME_3.0)

Gnome 3 on Ubuntu hasn't been touched in almost a week so this would probably give you a better idea of the finished product until it catches up, if you have the time.

---

### Post by Quackers on 2011-04-24
A couple of clues for conky in here

[http://ubuntuforums.org/showthread.php?t=1732803](http://ubuntuforums.org/showthread.php?t=1732803)

---

### Post by akand074 on 2011-04-24
> **Visceral Monkey said:**
> If your main interest right now is Gnome 3 more-so than Ubuntu, you might want to try out SuSE 11.4.They just finished Gnome 3 on the recently released SuSE 11.4 and it's literally one click to install Gnome 3. So far, it's been a smooth experience and a much better one than the Fedora Gnome 3 experiment I tried.

[http://software.opensuse.org/developer](http://software.opensuse.org/developer)

And one click Gnome 3 install once that's installed:
[http://en.opensuse.org/openSUSE:GNOME_3.0](http://en.opensuse.org/openSUSE:GNOME_3.0)

Gnome 3 on Ubuntu hasn't been touched in almost a week so this would probably give you a better idea of the finished product until it catches up, if you have the time.

I have been focused more on Gnome 3 on Ubuntu. But that would be nice to see a better setup. Perhaps I'll be able to tell whether or not it's worth continuing to use Gnome 3 in the near future. I have figured out work arounds for a few things already.

> **Quackers said:**
> A couple of clues for conky in here

[http://ubuntuforums.org/showthread.php?t=1732803](http://ubuntuforums.org/showthread.php?t=1732803)

Thanks I'll check this out!

EDIT: switched own_window_type to "desktop" and boom fixed!

---

### Post by akand074 on 2011-04-24
Found another fix. The "delete" button no longer deletes because it was changed to ctrl+delete (why?). Apparently it's fixable from a post in the archlinux forums:

> Quick fix:
Run dconf-editor, and open:
org -> gnome -> desktop -> interface
Enable "can-change-accels".
Open nautilus, select any file/directory, then click "Edit" from menubar, and hover on "Move to Trash" menuitem.
While hovering, click on your delete key. The accel should change from "cntrl+del" to "del".
Make sure you have selected a file, else the "Move to Trash" menuitem will be greyed out.
I suggest you disable "can-change-accels" afterwards, to prevent accidental accel changes.


I had to actually install "gconf-tools" first to be able to access gconf-editor. But fixed it now I can use the delete button again woohoo. Figuring out share folders is my biggest issue.

---

### Post by jtfolden on 2011-04-25
> **DevHead said:**
> That's my impression too.

I know that Gnome3 isn't part of the Natty release (thus the PPA).  I just want to try Gnome3 without anything breaking.  Hopefully the bugs will be squashed by the time Natty is released so that users can have the option of Unity and Gnome3.

Yes, I was really hoping this PPA would be complete by the official release of Natty but, so far, several packages are missing including the Gnome 3 release of Evolution.

I tend to prefer Ubuntu over other distros and didn't particularly mind Unity but I think Gnome Shell is much better for my own uses. I'm thinking maybe OpenSUSE may end up being a better choice for my over the near future, sadly.

---

### Post by Visceral Monkey on 2011-04-25
Ugh, 7 days with no update for Gnome 3. Disappointing. I know that Unity is the preferred choice for Ubuntu but I was really hoping for those of us who wanted Gnome 3 that it would be ready for the launch of Natty :(

---

### Post by gnomeuser on 2011-04-25
> **Visceral Monkey said:**
> Ugh, 7 days with no update for Gnome 3. Disappointing. I know that Unity is the preferred choice for Ubuntu but I was really hoping for those of us who wanted Gnome 3 that it would be ready for the launch of Natty :(

I suspect that most of the hands on deck are working on finiing up the Natty release. I am sure that after the release we will see work resume, till then the PPA works fairly well already.

---

### Post by akand074 on 2011-04-25
> **gnomeuser said:**
> I suspect that most of the hands on deck are working on finiing up the Natty release. I am sure that after the release we will see work resume, till then the PPA works fairly well already.

Mostly likely. You can't really blame them, I often forget that I'm running a development release still. Gnome 3 is now working pretty well for me after fixing little things here and there. Still has some bugs but they aren't major. It's pretty much fully usable except for the fact that I can't figure out how to set up share folders. I think by 11.10 both Unity and Gnome 3 should be pretty well integrated.

---

### Post by shaneo1 on 2011-04-25
I like gnome 3 as well but I've lost my task panel at the top and can't reset it using alt f2 , then r, is there another way?

---

### Post by sammiev on 2011-04-25
I have one little bug with gnome3 on boot up with natty 11.04 but all other software I tested gnome3 with was without any error. I'm sure the results will be soon. Noticed with Natty as well the battery icon doesn't display but with other releases it works great. GL :)

---

### Post by bulldog on 2011-04-25
> **shaneo1 said:**
> I like gnome 3 as well but I've lost my task panel at the top and can't reset it using alt f2 , then r, is there another way?

You could try ALT F2 and type gnome-shell --replace,so the shell will start again.

---

### Post by IWantFroyo on 2011-04-25
I went over to Arch Linux for a little to try the gnome-shell. Pretty good, but window switching is a little annoying. I like the notifications, though.

---

### Post by akand074 on 2011-04-25
Has anyone here managed to share a folder in gnome 3? I still can't figure out how to do it :/ In regular Ubuntu you just right click and then choose share.

---

### Post by jtfolden on 2011-04-25
> **akand074 said:**
> Has anyone here managed to share a folder in gnome 3? I still can't figure out how to do it :/ In regular Ubuntu you just right click and then choose share.

I installed the Samba Server Configuration Tool. You have to create the shares there instead of via Nautilus but it's simple and works fine.

---

### Post by t.rei on 2011-04-26
Does anyone know of a guide,howto or trustworthy ppa to get the network-manager 0.9 for ubuntu? It's not in the gnome3-team ppa, probably due to dependency hell?

Or do you guys think it's going to be there after the natty release? :D Am going to stick with gnome3. It's just smooth as a hot knife - no a lightsabre though butter.

---

### Post by akand074 on 2011-04-26
> **jtfolden said:**
> I installed the Samba Server Configuration Tool. You have to create the shares there instead of via Nautilus but it's simple and works fine.

I added the three folders I wanted to share and made them visible and accessible to all. Yet I couldn't connect to my network at all on my laptop. Maybe I'll try a reboot... and play around a bit.

---

### Post by M4570D0N on 2011-04-26
Up to this point I have still been unable to install the user-theme extension for gnome-shell-extensions from git and I have not seen anyone else mention that they have been able to do this successfully.  I always get the same makefile error. However, I found a way to install it and thought I would pass this along. I noticed that on Fedora there is a gnome-shell-extension-user-theme rpm package available. I downloaded the package, converted it to a .deb package via alien and was able to successfully install it.

for example, there is  a Fedora 15 version and a  Fedora 16 version of the build here (for both 32bit and 64bit):
[https://admin.fedoraproject.org/pkgdb/builds/search/gnome-shell-extensions-user-theme?_csrf_token=5b0dbaed3fb0741436f417df2b99cc144754ace8](https://admin.fedoraproject.org/pkgdb/builds/search/gnome-shell-extensions-user-theme?_csrf_token=5b0dbaed3fb0741436f417df2b99cc144754ace8)

assuming you grab the one for Fedora 15, download it to  /home/yourname/Downloads (doesn't matter where), you would enter the following 3 commands:

```
cd Downloads
sudo alien gnome-shell-extensions-user-theme-3.0.0-5.6d56cfgit.fc15.noarch.rpm --scripts
sudo dpkg -i gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb

```

Done. :D

---

### Post by mxt on 2011-04-27
> **t.rei said:**
> Does anyone know of a guide,howto or trustworthy ppa to get the network-manager 0.9 for ubuntu? It's not in the gnome3-team ppa, probably due to dependency hell?

Or do you guys think it's going to be there after the natty release? :D Am going to stick with gnome3. It's just smooth as a hot knife - no a lightsabre though butter.

You can find it in ricotz/staging:
[https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging)

I use it since some days without problems. To activate the network indicator remember to install also the package gir1.2-networkmanager-1.0.

---

### Post by 23dornot23d on 2011-04-27
> **M4570D0N said:**
> Up to this point I have still been unable to install the user-theme extension for gnome-shell-extensions from git and I have not seen anyone else mention that they have been able to do this successfully.  I always get the same makefile error. However, I found a way to install it and thought I would pass this along. I noticed that on Fedora there is a gnome-shell-extension-user-theme rpm package available. I downloaded the package, converted it to a .deb package via alien and was able to successfully install it.

for example, there is  a Fedora 15 version and a  Fedora 16 version of the build here (for both 32bit and 64bit):
[https://admin.fedoraproject.org/pkgdb/builds/search/gnome-shell-extensions-user-theme?_csrf_token=5b0dbaed3fb0741436f417df2b99cc144754ace8](https://admin.fedoraproject.org/pkgdb/builds/search/gnome-shell-extensions-user-theme?_csrf_token=5b0dbaed3fb0741436f417df2b99cc144754ace8)

assuming you grab the one for Fedora 15, download it to  /home/yourname/Downloads (doesn't matter where), you would enter the following 3 commands:

```

sudo alien gnome-shell-extensions-user-theme-3.0.0-5.6d56cfgit.fc15.noarch.rpm --scripts
sudo dpkg -i gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb

```Done. :D

I tried it and got a couple of errors ...... 

```

keith@keith-Aspire-7730ZG:~/Downloads$ sudo alien gnome-shell-extensions-user-theme-3.0.0-5.6d56cfgit.fc16.noarch.rpm --scripts
[sudo] password for keith: 
Use of uninitialized value $postinst in length at /usr/share/perl5/Alien/Package/Deb.pm line 750, <GETPERMS> line 5.
gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb generated
keith@keith-Aspire-7730ZG:~/Downloads$ sudo dpkg -i gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb
Selecting previously deselected package gnome-shell-extensions-user-theme.
(Reading database ... 397501 files and directories currently installed.)
Unpacking gnome-shell-extensions-user-theme (from gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb) ...
Setting up gnome-shell-extensions-user-theme (3.0.0-6.6) ...
Processing triggers for libglib2.0-0 ...
No such key `exit-with-last-window' in schema  `org.gnome.nautilus.preferences' as specified in override file  `/usr/share/glib-2.0/schemas/nautilus.gschema.override'; ignoring  override for this key.
keith@keith-Aspire-7730ZG:~/Downloads$ 


```The option _**Shell Theme**_ is now open and available for use though ..... it was yellow before and not selectable .........

[IMG]http://img708.imageshack.us/img708/3714/shell1.jpg[/IMG]


One more step in the right direction ...... good one (M4570) Don ..... ;)

---

### Post by cecilpierce on 2011-04-27
Just tried all that, mine is still yellow !
Must have done something wrong as usual !!!
:confused:

---

### Post by cecilpierce on 2011-04-27
> **cecilpierce said:**
> Just tried all that, mine is still yellow !
Must have done something wrong as usual !!!
:confused:

reboot has it showing now but how to get a theme ?   :D

---

### Post by henrichg on 2011-04-27
[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html]("http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html")
[http://www.webupd8.org/2011/04/adwaita-improved-reduced-padding-for.html]("http://www.webupd8.org/2011/04/adwaita-improved-reduced-padding-for.html")
;)

---

### Post by macozz on 2011-04-27
Hi,
I tried to find if someone is having the same issue, but I failed to found any similar. 
The shell works fine here, since the natty beta 1. However there is an annoying problem. When I boot the computer (or re-boot it) and try to login the first time I do it, the shell do not load. If I logout and login again, all runs fine. 
Of course it is not a critical issue, but is quite disturbing having to log twice to get the working environment up!
Any ideas? Some one experiences something similar?

Cheers

---

### Post by macozz on 2011-04-27
I tried to get this file, but I clicking in the file to download opens a 404 page saying the file is not in the server. Right-click on
it and download it produce an empty file.
Where can I get this rpm??

Thanks,


> **M4570D0N said:**
> Up to this point I have still been unable to install the user-theme extension for gnome-shell-extensions from git and I have not seen anyone else mention that they have been able to do this successfully.  I always get the same makefile error. However, I found a way to install it and thought I would pass this along. I noticed that on Fedora there is a gnome-shell-extension-user-theme rpm package available. I downloaded the package, converted it to a .deb package via alien and was able to successfully install it.

for example, there is  a Fedora 15 version and a  Fedora 16 version of the build here (for both 32bit and 64bit):
[https://admin.fedoraproject.org/pkgdb/builds/search/gnome-shell-extensions-user-theme?_csrf_token=5b0dbaed3fb0741436f417df2b99cc144754ace8](https://admin.fedoraproject.org/pkgdb/builds/search/gnome-shell-extensions-user-theme?_csrf_token=5b0dbaed3fb0741436f417df2b99cc144754ace8)

assuming you grab the one for Fedora 15, download it to  /home/yourname/Downloads (doesn't matter where), you would enter the following 3 commands:

```
cd Downloads
sudo alien gnome-shell-extensions-user-theme-3.0.0-5.6d56cfgit.fc15.noarch.rpm --scripts
sudo dpkg -i gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb

```

Done. :D

---

### Post by M4570D0N on 2011-04-27
> **macozz said:**
> I tried to get this file, but I clicking in the file to download opens a 404 page saying the file is not in the server. Right-click on
it and download it produce an empty file.
Where can I get this rpm??

Thanks,

Hmmm. Weird. They worked at the time I made my post, but they are no longer working for me either.

However, Web Upd8 just posted some info on an unofficial theme selector GUI today:
[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)

---

### Post by bulldog on 2011-04-27
> **M4570D0N said:**
> Hmmm. Weird. They worked at the time I made my post, but they are no longer working for me either.

However, Web Upd8 just posted some info on an unofficial theme selector GUI today:
[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)

I can confirm that this works like a charm.
You have to install the theme-extension from GIT first,there's a terminal command on this page,so it's not a big deal.
Currently there are six themes to select and it's working very well on Natty.

---

### Post by macozz on 2011-04-27
Thanks! I manages to get the rpms from the link below, but after install the debs derived from them, the user extension option in gnome-tweak-tool remains inactive.
I am missing something?


> **M4570D0N said:**
> Hmmm. Weird. They worked at the time I made my post, but they are no longer working for me either.

However, Web Upd8 just posted some info on an unofficial theme selector GUI today:
[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)

---

### Post by bulldog on 2011-04-28
@macozz,

I was speaking about the webup8 way.
You don't need a RPM,just get it from GIT and the 

[http://fpmurphy.com/public/themeselector-0.8.tar.gz](http://fpmurphy.com/public/themeselector-0.8.tar.gz)

Read this post

[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)

and you will have six themes to choose from.

The theme selector in gnome-tweak-tool doesn't work with this,but you don't need it to work because you get a new tab in activities where you can select your theme.

---

### Post by macozz on 2011-04-28
OK. But when I try to install the theme extension from git I get that:


Now type `make' to compile gnome-shell-extensions
mario@paleolaptop:~/gnome-shell/source/gnome-shell-extensions$ make && sudo make install
Making all in extensions
make[1]: Entering directory `/home/mario/gnome-shell/source/gnome-shell-extensions/extensions'
Making all in user-theme
make[2]: Entering directory `/home/mario/gnome-shell/source/gnome-shell-extensions/extensions/user-theme'
Makefile:432: *** missing separator.  Stop.
make[2]: Leaving directory `/home/mario/gnome-shell/source/gnome-shell-extensions/extensions/user-theme'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mario/gnome-shell/source/gnome-shell-extensions/extensions'
make: *** [all-recursive] Error 1

What I missed?

---

### Post by macozz on 2011-04-28
Forget it. I cannot install it from the git, but installing it from the debs work and I have now the theme tab.
Thanks!!!

---

### Post by Dobbie03 on 2011-04-28
I still get the ugly borders, how do I fix that?

EDIT: I worked it out, I had to change the theme in gconf-editor from Ambiance to Adwaita! Yay.

---

### Post by cariboo on 2011-04-28
Moved from Natty Testing and Discussion.

---

### Post by bulldog on 2011-04-28
> **Dobbie03 said:**
> I still get the ugly borders, how do I fix that?

EDIT: I worked it out, I had to change the theme in gconf-editor from Ambiance to Adwaita! Yay.

Did you install gnome-tweak-tool yet?
You can find it in the gnome3 ppa {natty only!}

With this tool you can set the GTK-theme to adwaita
You may have to look at gconf-editor what theme is selected by gnome.

---

### Post by macozz on 2011-04-28
Gnome-tweak-tools do not change the window borders. You have to change manually in the gconf editor the theme for windows.

---

### Post by cecilpierce on 2011-04-28
Wow! took me so long to find the thread I forgot what I was gonna say.
Seems like Gnome3 should have stayed under Development & Programming ? oh well.

---

### Post by thezood on 2011-04-28
> **macozz said:**
> Hi,
I tried to find if someone is having the same issue, but I failed to found any similar. 
The shell works fine here, since the natty beta 1. However there is an annoying problem. When I boot the computer (or re-boot it) and try to login the first time I do it, the shell do not load. If I logout and login again, all runs fine. 
Of course it is not a critical issue, but is quite disturbing having to log twice to get the working environment up!
Any ideas? Some one experiences something similar?

Cheers

I have the same issue. Sometimes when I start my Ubuntu I get a list of my users (which is just mine). If I try to login, it just hangs. I do CTRL-ALT-F1 at run "sudo restart gdm" and when gdm restarts, I don't get a list, only a dialog asking me for my username. And then it works fine. Weird and a bit annoying.

---

### Post by RJ12 on 2011-04-28
> **thezood said:**
> I have the same issue. Sometimes when I start my Ubuntu I get a list of my users (which is just mine). If I try to login, it just hangs. I do CTRL-ALT-F1 at run "sudo restart gdm" and when gdm restarts, I don't get a list, only a dialog asking me for my username. And then it works fine. Weird and a bit annoying.

Yeah, the same exact thing was happening to me...

---

### Post by gwoodruff on 2011-04-30
I am happy with gnome3 and have tweaked the icons and spacing, window controls, etc. The only two complaints I have are with the desktop. 

1) Is there a way to have icons (shortcuts to folders) on the desktop or favorites bar?

2) Can usb drives show up on the desktop or at least on the favorites bar on the left?

These two things will make it much more functional for me!

Thanks, Gary

---

### Post by mxt on 2011-04-30
> **gwoodruff said:**
> I am happy with gnome3 and have tweaked the icons and spacing, window controls, etc. The only two complaints I have are with the desktop. 

1) Is there a way to have icons (shortcuts to folders) on the desktop or favorites bar?

2) Can usb drives show up on the desktop or at least on the favorites bar on the left?

These two things will make it much more functional for me!

Thanks, Gary

1) From gnome-tweak-tool you can select the option "Have file manager handle the desktop"
2) There is a new extension for this "Removable Drive Menu". You can find it here: [http://git.gnome.org/browse/gnome-shell-extensions/](http://git.gnome.org/browse/gnome-shell-extensions/)

---

### Post by gwoodruff on 2011-04-30
I am finding the shell extension page you linked a little cryptic. Can someone give me direction with the extensions?
Thanks, Gary

---

### Post by bmbaker on 2011-04-30
> **gwoodruff said:**
> I am finding the shell extension page you linked a little cryptic. Can someone give me direction with the extensions?
Thanks, Gary


cd
git clone _[http://git.gnome.org/browse/gnome-shell-extensions](http://git.gnome.org/browse/gnome-shell-extensions)_
cd gnome-shell-extensions
./[autogen.sh]("http://autogen.sh/") --prefix=/usr
make && sudo make install      

after you have done this you need to go to gksudo nautilus from your terminal
then navigate to /usr/share/gnome-shell/extensions
in each extension you'll need to modify the metadata.json and change the "shell version"
to 3.0.0 or whatever your shell version is :-)
enjoy :-)

---

### Post by bmbaker on 2011-04-30
some usful links for gnome-shell :-)

[www.google.com](www.google.com)
[http://www.webupd8.org/search/label/gnome%20shell?max-results=10]("http://www.webupd8.org/search/label/gnome%20shell?max-results=10")
[http://gnome-shell.deviantart.com/gallery/28081982](http://gnome-shell.deviantart.com/gallery/28081982)
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)
[http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html](http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html)
[http://blog.fpmurphy.com/2011/04/replace-gnome-shell-activities-text-string-with-icon.html](http://blog.fpmurphy.com/2011/04/replace-gnome-shell-activities-text-string-with-icon.html)
[http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html](http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html)

and i found this one last night which looks to be shaping up into a good blog as well

[http://www.gnomeshell.com/](http://www.gnomeshell.com/)

enjoy :-)

---

### Post by gwoodruff on 2011-04-30
Thanks for the links, I will look through them tonight. I have found that selecting file manager to handle the desktop in gnome-tweak to work although a little buggy. On boot it does not draw the Icons or background on the desktop until I launch the file manager. There still will be no link to any USB drives until I browse one via file manager. This will create the link but disable the background so all I have is a white background. If I then right click and reselect the background jpg It will display the background, icons and USB drives during mounts and dismounts until I reboot and start the whole process over again! It is workable as is but should be fixed further down the road. I am very happy with gnome 3 with a working desktop. I do like it better then Unity and once the bugs are worked out I think more will use it. My next chore is to figure out why evolution 3.0 is crashing on me! I tried to build it from scratch but had unmet dependencies I could not resolve and installed from a ppa I found. At least I am not bored! Thanks again, Gary

---

### Post by dim_par on 2011-05-02
I cannot create a new workspace. When i drag and drop an application to the empty workspace that appears on the right preview window it does nothing. Is it something tha has to do with configuration?

---

### Post by philnice on 2011-05-02
After natty 11.04 release, we've all found ourselves in a rush to install gnome 3 on top of ubuntu. Until version 11.10 when gnome would be officially supported, i think this is the way to go: [http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

---

### Post by sgage on 2011-05-02
> **philnice said:**
> After natty 11.04 release, we've all found ourselves in a rush to install gnome 3 on top of ubuntu. Until version 11.10 when gnome would be officially supported, i think this is the way to go: [http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

It says on that page:

"The Natty (11.04) release will include Gnome 3. Fallback to old-style Gnome will be available."

Natty does NOT include Gnome 3. It runs the Unity UI on top of a Gnome 2.32.1 stack. But yes, it does fall back to the 2-panel interface.

Gnome - a desktop environment project
Gnome 2.32.1 - the last 2.x version of the stack, as far as I know.
2-panel interface - the stock UI for Gnome 2.x. NOT the same as Gnome 2.x
Gnome 3.0 - the latest, greatest, Gnome stack.
Gnome Shell - the stock UI for Gnome 3. NOT the same as Gnome 3

Unity in Natty runs on top of a Gnome 2.32.1 stack. It will be rewritten to run on top of the Gnome 3.x stack for Oneiric.

Can we please use the terms correctly? People are casually referring to Gnome Shell as Gnome 3 and the 2-panel interface as Gnome 2. It is wrong usage, even if a lot of folks (some who should know better) do it.

---

### Post by philnice on 2011-05-02
> **sgage said:**
> It says on that page:

"The Natty (11.04) release will include Gnome 3. Fallback to old-style Gnome will be available."

Natty does NOT include Gnome 3. It runs the Unity UI on top of a Gnome 2.32.1 stack. But yes, it does fall back to the 2-panel interface.

Gnome - a desktop environment project
Gnome 2.32.1 - the last 2.x version of the stack, as far as I know.
2-panel interface - the stock UI for Gnome 2.x. NOT the same as Gnome 2.x
Gnome 3.0 - the latest, greatest, Gnome stack.
Gnome Shell - the stock UI for Gnome 3. NOT the same as Gnome 3

Unity in Natty runs on top of a Gnome 2.32.1 stack. It will be rewritten to run on top of the Gnome 3.x stack for Oneiric.

Can we please use the terms correctly? People are casually referring to Gnome Shell as Gnome 3 and the 2-panel interface as Gnome 2. It is wrong usage, even if a lot of folks (some who should know better) do it.
Thanks for the corrections, appreciate that.

---

### Post by ipx on 2011-05-02
Installed Gnome3 yesterday and Gnome Shell works like a charm. However, I do play Quake Live quite often and I need that to float like a boat. This does not work very well with the 3d-interface of Gnome Shell and I am now looking for a solution (I get mouse input lag)

I tried to launch Gnome Classic which supposedly should be like what I am used to from Gnome 2.3, however I get error message: "Failed to launch session "classic-gnome"". What is the latest on this fallback-mode? Is there an easy way to get it working? There's too many pages and different solutions to try, but maybe there's a definite solution now?

I also looked for a way to disable 3d effects in Gnome Shell but could not find any. I guess this is working as intended and that the classic Gnome is the solution for now?

Thank you in advance. :)

Edit: I installed this from the official PPA.

---

### Post by bmbaker on 2011-05-02
if you goto system settings and click on system info there isa graphics list.
try putting it into forced fall back mode and see if that helps
it should put you into gnome 3 desktop as opposed too the gnome-shell :-)
let me know if it wks for you :-)

---

### Post by ipx on 2011-05-02
> **bmbaker said:**
> if you goto system settings and click on system info there isa graphics list.
try putting it into forced fall back mode and see if that helps
it should put you into gnome 3 desktop as opposed too the gnome-shell :-)
let me know if it wks for you :-)

Thank you very much for this quick reply, however it didnt help me. I set it to Forced Fallback Mode (ON), but after a logout/login it still looks the same although the setting is still on. The input lag in quake caused by the effects are still there. :(

---

### Post by ratcheer on 2011-05-02
Ok. I bit the bullet this morning and converted my production Natty installation to Gnome 3. It went pretty well, but my Firefox application is now displayed with a generic icon. I have searched Google and read fpmurphy's blog on customizing Gnome 3. He says he is telling how to change an application icon, but what hes says makes no sense to me, at all.

Is there any understandable way to fix my Firefox icon?

Tim

---

### Post by bmbaker on 2011-05-02
> **ipx said:**
> Thank you very much for this quick reply, however it didnt help me. I set it to Forced Fallback Mode (ON), but after a logout/login it still looks the same although the setting is still on. The input lag in quake caused by the effects are still there. :(

hmmm well the only other thing i can think of is maybe try looking into changing your graphics driver, you'll have to do a forum search for it!

or do what i did and set up to dual boot, one for using gnome-shell and one to use ubuntu-classic/unity.
 i find that i don't need to fall back to classic/unity as i don't play games ;-)

---

### Post by bmbaker on 2011-05-02
> **ratcheer said:**
> Ok. I bit the bullet this morning and converted my production Natty installation to Gnome 3. It went pretty well, but my Firefox application is now displayed with a generic icon. I have searched Google and read fpmurphy's blog on customizing Gnome 3. He says he is telling how to change an application icon, but what hes says makes no sense to me, at all.

Is there any understandable way to fix my Firefox icon?

Tim
why don't you try down loading a nice icon set to your downloads folder and extract it to your /usr/share/icons and use gnome tweak tool to change the icon set :-)

---

### Post by jtfolden on 2011-05-02
> **philnice said:**
> After natty 11.04 release, we've all found ourselves in a rush to install gnome 3 on top of ubuntu. Until version 11.10 when gnome would be officially supported, i think this is the way to go: [http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

,,,but isn't the PPA for this behind the official Gnome 3 PPA (which itself is a complete revision  behind the current release? 3.0.0 vs 3.0.1)?

---

### Post by ratcheer on 2011-05-02
> **bmbaker said:**
> why don't you try down loading a nice icon set to your downloads folder and extract it to your /usr/share/icons and use gnome tweak tool to change the icon set :-)

Thank you. I seriously don't understand any of this stuff, yet. I resolved the issue by changing the icon theme from adwaita to unity-icon-theme. Does adwaita not know about Firefox, or is something else wrong?

Of the supplied icon themes, which ones are considered "good"?

Tim

---

### Post by philnice on 2011-05-02
> **jtfolden said:**
> ,,,but isn't the PPA for this behind the official Gnome 3 PPA (which itself is a complete revision  behind the current release? 3.0.0 vs 3.0.1)?
The important thing for me is that there is a team working on it, otherwise no matter what ppa you've got, there would always be conflicts since gnome 3 is officially unsupported by natty.

---

### Post by bmbaker on 2011-05-02
you can also add the [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)
ppa which may break your system!!
so far i haven't had any issues crashes etc with using it  ..... so far :-)
which will bring you to gnome-shell 3.0.1
if you do try it out make sure you have ppa-purge installed....just in case ;-)

---

### Post by bmbaker on 2011-05-02
> **ratcheer said:**
> Thank you. I seriously don't understand any of this stuff, yet. I resolved the issue by changing the icon theme from adwaita to unity-icon-theme. Does adwaita not know about Firefox, or is something else wrong?

Of the supplied icon themes, which ones are considered "good"?

Tim
"good" is purely a question of what "you" like ;-)

---

### Post by philnice on 2011-05-02
> **bmbaker said:**
> you can also add the [https://launchpad.net/~ricotz/+archive/testing]("https://launchpad.net/%7Ericotz/+archive/testing")
ppa which may break your system!!
so far i haven't had any issues crashes etc with using it  ..... so far :-)
which will bring you to gnome-shell 3.0.1
if you do try it out make sure you have ppa-purge installed....just in case ;-)
Nice to hear you haven't got into any troubles. Does this include running games, etc? Also could you please post your graphics card chipset and drivers you currently using?

---

### Post by bmbaker on 2011-05-02
no i don't play games ;-)

i am running a samsung r50 plus external monitor
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
06:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
06:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
06:09.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
06:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
06:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 03)

```

---

### Post by philnice on 2011-05-02
**Bmbaker**, thanks. I do also use ati but, unlike you, screen's flickering anytime i launch a game or, an extra icon is opening on the desktop. Also my unity interface is completely broken meaning i can't login to it. I do have kde also installed and that's what i use now. Seems to work slightly better than gnome.

---

### Post by bmbaker on 2011-05-03
> **philnice said:**
> **Bmbaker**, thanks. I do also use ati but, unlike you, screen's flickering anytime i launch a game or, an extra icon is opening on the desktop. Also my unity interface is completely broken meaning i can't login to it. I do have kde also installed and that's what i use now. Seems to work slightly better than gnome.

unfortunatly at this moment ubuntu doesn't support gnome-shell, so if your wanting to use the gnome-shell, unity and ubuntu desktop will not work!
and also gnome-shell is really still being developed so it will need tweaking to get it fully functioning.
perhaps you should try building it from git using jhbuild as posted 
[HTML]http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html[/HTML]
then it will run indepentant of unity etc :-)

---

### Post by philnice on 2011-05-03
> **bmbaker said:**
> unfortunatly at this moment ubuntu doesn't support gnome-shell, so if your wanting to use the gnome-shell, unity and ubuntu desktop will not work!
and also gnome-shell is really still being developed so it will need tweaking to get it fully functioning.
perhaps you should try building it from git using jhbuild as posted 
[HTML]http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html[/HTML]then it will run indepentant of unity etc :-)
Even if i do that, it won't work i think, because my current natty installation is broken after the distro upgrade to gnome. I could see the errors in terminal during installation.
So, i need a clean natty install first. Then, i would propably go with this, [http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)
since it seems to be the safest way.
My only problem is that i have to keep my current cfgs, apps, etc and that would be a pain.... :) Thanks.

---

### Post by philnice on 2011-05-03
Some people who have tried  UGR, reporting that it worked pretty well for them: 
[http://ubuntuforums.org/showthread.php?t=1742343&page=8](http://ubuntuforums.org/showthread.php?t=1742343&page=8)

---

### Post by gwoodruff on 2011-05-04
After the last round of updates that included Nautilus 3.0 I can no longer launch Nautilus from the favorites sidebar? It also does not run from a terminal unless I am root? It does launch from a folder link on my desktop. I have tried deleting the link in the favorites bar and creating a new from a open window but it still does not launch? Please help!

Gary

---

### Post by bmbaker on 2011-05-04
which ppa are you using?
the **ppa:gnome3-team/gnome3**
is nautilus                                               1:3.0.0-0ubuntu1~build4                                
and i see no problems with it!

---

### Post by gwoodruff on 2011-05-04
I am using the same ppa on two different machines and both have the same problem. One was an upgrade the other a clean install. Both are buggy, from Nvidia driver issues, themes, background and desktop display, number lock and keyboard issues. I have also tried the Fedora 15 and at first found it slow but the updates have brought it up to speed and it so far has none of the bugs (on the same machine that has a clean install of natty + gnome3)! I would love to resolve these issues but may be switching to Fedora if I cant. I have used Ubuntu gnome and xfce since 6.0 and this latest release has more issues then any of the previous. I know some of it is my own fault as I did not like unity but do love gnome3. I am looking for a way to get a clean version of the two combined but the closest I see to date is Fedora!

---

### Post by bmbaker on 2011-05-06
> **gwoodruff said:**
> I am using the same ppa on two different machines and both have the same problem. One was an upgrade the other a clean install. Both are buggy, from Nvidia driver issues, themes, background and desktop display, number lock and keyboard issues. I have also tried the Fedora 15 and at first found it slow but the updates have brought it up to speed and it so far has none of the bugs (on the same machine that has a clean install of natty + gnome3)! I would love to resolve these issues but may be switching to Fedora if I cant. I have used Ubuntu gnome and xfce since 6.0 and this latest release has more issues then any of the previous. I know some of it is my own fault as I did not like unity but do love gnome3. I am looking for a way to get a clean version of the two combined but the closest I see to date is Fedora!

hmmm try adding [B]ppa:ricotz/testing
i have had no breakages and really no problems :-)
[/B]

---

### Post by jtfolden on 2011-05-06
> **gwoodruff said:**
> I am using the same ppa on two different machines and both have the same problem. One was an upgrade the other a clean install. Both are buggy, from Nvidia driver issues, themes, background and desktop display, number lock and keyboard issues. I have also tried the Fedora 15 and at first found it slow but the updates have brought it up to speed and it so far has none of the bugs (on the same machine that has a clean install of natty + gnome3)! I would love to resolve these issues but may be switching to Fedora if I cant. I have used Ubuntu gnome and xfce since 6.0 and this latest release has more issues then any of the previous. I know some of it is my own fault as I did not like unity but do love gnome3. I am looking for a way to get a clean version of the two combined but the closest I see to date is Fedora!

The Gnome 3 PPA for Ubuntu is currently incomplete and what is there is outdated. Fedora has the latest Gnome 3.0.1 with quite a lot of fixes and will have 3.0.2 by the end of the month.

I expect Ubuntu will catch up eventually but right now it's fairly broken (from certain System Settings not working, no flash in Epiphany, etc...). It works the smoothest in Fedora right now.

---

### Post by cecilpierce on 2011-05-06
I have suse, fedora and ubuntu, the network connecting died on fedora and I can't get it going, got tired of ubuntu and purged it back, and suse is just there to see how far it goes, its really faster on upgrades then fedora was !

---

### Post by ratcheer on 2011-05-06
> **jtfolden said:**
> The Gnome 3 PPA for Ubuntu is currently incomplete and what is there is outdated. Fedora has the latest Gnome 3.0.1 with quite a lot of fixes and will have 3.0.2 by the end of the month.

I expect Ubuntu will catch up eventually but right now it's fairly broken (from certain System Settings not working, no flash in Epiphany, etc...). It works the smoothest in Fedora right now.

Actually, the latest Gnome 3 came to the PPA, today.

Tim

---

### Post by dugh on 2011-05-19
The gnome3 ppa doesn't work for me.

When I try to login to a gnome 3 shell session, there is no interface at all, just a desktop background.  I have to hit the power button to restart.

If I login to ubuntu classic with no effects, everything works, but the theme and fonts are all messed up, everything is white and the fonts are weird.

I've tried suggested fixes here and elsewhere:
[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

Nothing worked

---

### Post by philnice on 2011-05-19
> **dugh said:**
> The gnome3 ppa doesn't work for me.

When I try to login to a gnome 3 shell session, there is no interface at all, just a desktop background.  I have to hit the power button to restart.

If I login to ubuntu classic with no effects, everything works, but the theme and fonts are all messed up, everything is white and the fonts are weird.

I've tried suggested fixes here and elsewhere:
[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

Nothing worked
[http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)
[http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)
Pick whatever suits your needs. :)

---

### Post by ratcheer on 2011-05-20
I had a problem updating Gnome 3 this morning. Apport was unable to report the problem because "this is not an Ubuntu package". I went to the Gnome 3 team page on Launchpad and I can find no way to report a bug there, either. I also tried "Answers", but that gives me no opportunity to submit a question.

So, here is my problem:

```

Unpacking libevince3-3 (from .../libevince3-3_3.0.0-4ubuntu1~natty1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libevince3-3_3.0.0-4ubuntu1~natty1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libevdocument3.so.3.0.0', which is also in package libevdocument3 3.0.0-0ubuntu1~build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace evince-common 3.0.0-0ubuntu1~build1 (using .../evince-common_3.0.0-4ubuntu1~natty1_all.deb) ...
Unpacking replacement evince-common ...
dpkg: error processing /var/cache/apt/archives/evince-common_3.0.0-4ubuntu1~natty1_all.deb (--unpack):
 trying to overwrite '/usr/share/glib-2.0/schemas/org.gnome.Evince.gschema.xml', which is also in package evince 3.0.0-0ubuntu1~build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)


```

Is this a common problem for others this morning? Is there any way to report it to the Gnome 3 team?

Thanks,
Tim

---

### Post by t.rei on 2011-05-20
Same problem. Removed evince to get rid of the apt-get error. Now lets wait and see how long it takes them to realize this. I don't know about how to report the bug to the gnome3-team ppa dudes. I guess it'll be in the mailinglists. Since we are probably not alone, and pdf reader evince bing kind of a critical component for any kind of work, this will probably be noticed already.

---

### Post by cbowman57 on 2011-05-20
Is that running a simple upgrade or a dist-upgrade?  I haven't run into that problem yet but I'm doing a dist-upgrade periodically.

---

### Post by t.rei on 2011-05-20
If it was done as a simple upgrade, the error would not have occured. 

Right now - as I type this - on: [https://launchpad.net/~gnome3-team/+archive/gnome3]("https://launchpad.net/%7Egnome3-team/+archive/gnome3")
it says "currently building" for evince and gnome-control-center. and "waiting to build" on gnome-settings-daemon. So Just wait and do an upgrade again. ;)

---

### Post by t.rei on 2011-05-20
*update* and here we go: updated, upgraded, reinstalled evince and everything is back to smooth-enough-to-make-you-cry. :)

---

### Post by balax86 on 2011-05-20
> **ratcheer said:**
> I had a problem updating Gnome 3 this morning. Apport was unable to report the problem because "this is not an Ubuntu package". I went to the Gnome 3 team page on Launchpad and I can find no way to report a bug there, either. I also tried "Answers", but that gives me no opportunity to submit a question.

So, here is my problem:

```

Unpacking libevince3-3 (from .../libevince3-3_3.0.0-4ubuntu1~natty1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libevince3-3_3.0.0-4ubuntu1~natty1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libevdocument3.so.3.0.0', which is also in package libevdocument3 3.0.0-0ubuntu1~build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace evince-common 3.0.0-0ubuntu1~build1 (using .../evince-common_3.0.0-4ubuntu1~natty1_all.deb) ...
Unpacking replacement evince-common ...
dpkg: error processing /var/cache/apt/archives/evince-common_3.0.0-4ubuntu1~natty1_all.deb (--unpack):
 trying to overwrite '/usr/share/glib-2.0/schemas/org.gnome.Evince.gschema.xml', which is also in package evince 3.0.0-0ubuntu1~build1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)


```Is this a common problem for others this morning? Is there any way to report it to the Gnome 3 team?

Thanks,
Tim

Same problem with Document viewer. Please help

---

### Post by sammiev on 2011-05-20
I used Ubuntu Tweak updater and it corrected the problem. GL :)

---

### Post by drfox on 2011-05-20
> **balax86 said:**
> Same problem with Document viewer. Please help

Evince is the document viewer
sudo apt-get install evince
will solve your problems.
Larry

---

### Post by ratcheer on 2011-05-20
> **t.rei said:**
> *update* and here we go: updated, upgraded, reinstalled evince and everything is back to smooth-enough-to-make-you-cry. :)

Here is what I got:

```

Resolving dependencies...                
Unable to resolve dependencies for the upgrade: no solution found.
Unable to safely resolve dependencies, try running with --full-resolver.

```

Tim

---

### Post by ratcheer on 2011-05-20
And here is what --full-resolver gave:

```

The following NEW packages will be installed:
  libebackend-1.2-1{a} libedata-book-1.2-9{a} libedata-cal-1.2-11{a} libedataserverui-3.0-0{a} libevince3-3{a} 
  libgtkhtml-4.0-0{a} libgtkhtml-4.0-common{a} libgtkhtml-editor-4.0-0{a} libgvnc-1.0-0{a} libgweather-3-0{a} 
The following packages will be REMOVED:
  evolution-exchange{a} libevdocument3{a} libevview3{a} 
The following packages will be upgraded:
  evince evince-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-plugins 
  gcalctool gnome-control-center gnome-control-center-data gnome-settings-daemon libevolution libgnome-control-center1 
  libgtk-vnc-1.0-0 
14 packages upgraded, 10 newly installed, 3 to remove and 0 not upgraded.


```

I hope everything is ok.

Tim

---

### Post by t.rei on 2011-05-24
I really wish there was something like a comprehensive "and this is new today" list on the ppa. Or maybe I'm just too blind to see. 

Anyways, big update, some problems that made me do some fixing on the terminal login regarding gnome-session: 
sudo service gdm stop 
sudo apt-get dist-upgrade
sudo apt-get remove gnome-session
sudo apt-get install --reinstall gnome-shell 
sudo apt-get install gnome-session
sudo service gdm start

Some error about a file bing in gnome-shell and gnome-session package. Workd fine now, can't seem to find what it is that changed. :D

---

### Post by satanselbow on 2011-05-24
> Some error about a file bing in gnome-shell and gnome-session package.  Workd fine now, can't seem to find what it is that changed.


Have you  got Gnome3 back up without any broken packages?

---

### Post by t.rei on 2011-05-25
I don't backup the system, I backup my data. But considering how viciously well it works right now, I might actually go and take a look on "how to take a snapshot"... I remember dd.. long time since I used that, though.

Right now I am looking for some other things, thb:
a) turn off the feature that enables keystroke delay if holding a key for more than 10 seconds. Happens while gaming :P
b) Find out how to get emblem support back in nautilus (and if that works). I liked that little visual aid.

---

### Post by CSimpson on 2011-05-25
> **satanselbow said:**
> Have you  got Gnome3 back up without any broken packages?

I found that it was a simple case of running
$ sudo apt-get -f dist-upgrade
in a terminal to resolve the recent broken package problem with gnome-shell and gnome-session.

---

### Post by karmila on 2011-05-25
Hi, I have problem with gnome-shell theme which is always revert to default every time I hit Super button and window control won't respect gtk-3 theme i use, it always use default Adwaita theme.

Anyone has this problem too?

---

### Post by Brushstroke on 2011-05-25
I've been considering doing a minimal install of 11.04 with Gnome 3 for awhile but I want to be careful, that's all. I have a good 10.04 LTS setup now that I would want to revert back to if things get severely screwed up. So, I just want to ask if this would be the proper procedure for doing a minimal install with Gnome 3?

After doing the minimal install and TTY'ing into the command line since for some reason it seems to give a black screen (where the graphical login would normally be) on boot:

                                 > sudo vi /etc/apt/sources.list &#8592; uncomment everything

 sudo apt-get update && sudo apt-get dist-upgrade

Reboot.

 Then:

 sudo apt-get install xorg xserver-xorg-core xserver-xorg-video-ati xserver-xorg-video-radeon python-software-properties
 
sudo add-apt-repository ppa:gnome3-team/gnome3 && sudo apt-get update

 sudo apt-get install gnome-shell gnome-tweak-tools
Also, has anyone experienced any problems with Gnome 3 at this point since it's been officially released? Any rough edges that you've had to take care of? What about problems with ATI or Radeon drivers?

Thank you.

---

### Post by ratcheer on 2011-05-25
Brushstroke, that is not the way I would do it. But, I suppose you are doing it that way to try your "minimal install". I have no idea whether that will work. I do the dist-upgrade *after* adding the Gnome 3 Team PPA.

I only have a couple of small problems. One is that when I restart the system, sometimes it seems to "forget" the theme, giving me some generic icons and other oddities. Another reboot or two fixes it. Another very small problem is that when I play Aisle Riot, sometimes the screen does not redraw after I "deal another round". Clicking in the title bar makes the screen redraw.

My biggest problem is that there does not seem to be a way to report bugs or other problems. On Launchpad, there are no bug reports or Answers. There is a little line on their page that says you can ask questions in the #ubuntu-desktop channel on IRC. I tried that one time and was informed that the channel is only for developers. I said I did not know I was not welcome there and mentioned the Team page directing me there for questions. They said they did not mean I wasn't welcome, but they still weren't going to answer my questions. So, if there are problems, I guess the only thing you can do is wait.

I am downloading Fedora 15, now. I'll see how it does.

Tim

---

### Post by Brushstroke on 2011-05-25
> **ratcheer said:**
> Brushstroke, that is not the way I would do it. But, I suppose you are doing it that way to try your "minimal install". I have no idea whether that will work. I do the dist-upgrade *after* adding the Gnome 3 Team PPA.

I only have a couple of small problems. One is that when I restart the system, sometimes it seems to "forget" the theme, giving me some generic icons and other oddities. Another reboot or two fixes it. Another very small problem is that when I play Aisle Riot, sometimes the screen does not redraw after I "deal another round". Clicking in the title bar makes the screen redraw.

My biggest problem is that there does not seem to be a way to report bugs or other problems. On Launchpad, there are no bug reports or Answers. There is a little line on their page that says you can ask questions in the #ubuntu-desktop channel on IRC. I tried that one time and was informed that the channel is only for developers. I said I did not know I was not welcome there and mentioned the Team page directing me there for questions. They said they did not mean I wasn't welcome, but they still weren't going to answer my questions. So, if there are problems, I guess the only thing you can do is wait.

I am downloading Fedora 15, now. I'll see how it does.

Tim
I think someone else tried something similar to what I just posted and it's working quite well for them. Ubuntu's minimal installation option gives you a simple command-line system. That means no GUI, no Unity, no programs, nothing but the basics. Just a black screen with "user@system:~$" It should work since there won't be anything like Unity, with all of its Gnome 2 dependencies, for Gnome 3 to conflict with.

I love Fedora 15, by the way. :)

---

### Post by ratcheer on 2011-05-25
I installed Gnome 3 to my well-used Ubuntu 11.04 system (which had been upgraded from 10.10 which had probably been upgraded from 10.04....). I ran the dist-upgrade from a Gnome 2 panel session and Gnome 3 came up without a hitch. As always, YMMV.

Tim

---

### Post by Brushstroke on 2011-05-25
I see. That's odd, because all of the things I've read about installing Gnome 3 from within a default 11.04 installation (that is, *with *a GUI) results in many dependency problems (because of Gnome 2) and ultimately a broken system. How did the Gnome 3 installation deal with all of the Gnome 2 stuff already on your system?

---

### Post by ratcheer on 2011-05-25
> **Brushstroke said:**
> I see. That's odd, because all of the things I've read about installing Gnome 3 from within a default 11.04 installation (that is, *with *a GUI) results in many dependency problems (because of Gnome 2) and ultimately a broken system. How did the Gnome 3 installation deal with all of the Gnome 2 stuff already on your system?

Oh, I see. It broke that stuff. But, Gnome 3 is doing just fine.

Tim

---

### Post by 23dornot23d on 2011-05-25
If when you upgrade you use **aptitude safe-upgrade** - there are rarely any dependency problems - but when there are ....
 (it looks for a better way of sorting them for you)
sometimes it downgrades packages ....... but later it will allow for a full upgrade again.

Done this so often now and over the years have come to rely on it ..... never once had to
try to sort out problems using dpkg .... yet I seem to see that being used quite a lot after using apt-get ..... 
but I guess its what works for your individual system the best.

---

### Post by sammiev on 2011-05-25
Running Gnome3 after installing 11.04 with no problems. Actually ran 11.04 for 3 weeks before installing Gnome3. I have no issues to report. GL :)

---

### Post by magneze on 2011-05-26
So, I was just switching between windows using the Activities view and my stepson walks in. "Wow, what's that? That's really cool."

Kudos Gnome 3 devs. :KS

---

### Post by ratcheer on 2011-05-27
The weirdest thing just happened to my system. I have been running Gnome 3 from the Gnome 3 Team PPA since about 4 days after the Natty release. So, for almost a month. Today, i ran "sudo aptitude update" then "sudo aptitude safe-upgrade". I rebooted my system and, when it came back up, I am in Unity again!

Dern!

Tim

---

### Post by t.rei on 2011-05-27
I think they fixed the gnome-session in an upgrade. Logout and check what kind of desktop session is selected for your user.

Something else that bugs me right now: I was getting to love the search functionality of nautilus. But somewhere within the past few days the **Ctrl+F** shortcut just keeps opening the little guick search at the bottom right corner - the same thing that pops up, when just typing - not the search-mode.

If anyone has any hint on this one, I'd be a happy camper. Really that was a cool time, while it worked properly.

*edit again* Ok, something is definately odd. I just looked around all the menus of nautilus again, and lo and behold: Goto->Search for files is set to "Ctrl+F". It's not working properly, unless I click the search button or use that entry in the menu. Ctrl+A, Ctrl+I, Ctrl+C and so on are all working, just not the ctrl+f combination.

[I][SOLVED] And something else that totally pains me: the touchpad disabled while and shortly after typing. I like to work quickly and use the touchpad a lot to move between windows. This removes a lot of smoothness from my workflow, and I can't seem to find out how to turn that off. 
[/I]**The solution was:**
apt-get install dconf-tools
dconf-editor
org/gnome/settings-daemon/peripherals/touchpad/disable-while-typing => turned this off.

---

### Post by ratcheer on 2011-05-27
> **t.rei said:**
> I think they fixed the gnome-session in an upgrade. Logout and check what kind of desktop session is selected for your user.



The Gnome 3 shell is no longer on the menu, just Gnome and Ubuntu. Ubuntu is what came up in Unity. I will log out and back in and see what Gnome does - I am expecting the Gnome 2 panel DE.

Tim

---

### Post by 23dornot23d on 2011-05-27
I personally like to use **aptitude safe-upgrade** ..... it always gives a list of the changes
and checks dependencies .......

Sometimes things do not always change and make things better ....

Always be careful what your upgrades are ..... sometimes they feel like downgrades
when functionality is lost ..... Alt+F2 ..... what does that do on each individual system

Does it swap workspaces or choose an application to run .... :confused:

---

### Post by ratcheer on 2011-05-27
> **ratcheer said:**
> The Gnome 3 shell is no longer on the menu, just Gnome and Ubuntu. Ubuntu is what came up in Unity. I will log out and back in and see what Gnome does - I am expecting the Gnome 2 panel DE.

Tim

Selecting Gnome did not work. It accepted my password, blanked the screen for a very few seconds, and gave the login dialog, again. I'm still in Unity, which seems to be working just fine, except for the Win NT style main panel decorations. The application windows themselves look fine.

Tim

---

### Post by 23dornot23d on 2011-05-27
> **ratcheer said:**
> Selecting Gnome did not work. It accepted my password, blanked the screen for a very few seconds, and gave the login dialog, again. I'm still in Unity, which seems to be working just fine, except for the Win NT style main panel decorations. The application windows themselves look fine.

Tim

If it ran ok before .... Gnome-shell that is ..... ( also check and see if gnome-shell is still loaded in synaptic )

Go into classic mode .......

Alt+f2 ......  ( or do it from a terminal - it will give you more information - if there is a problem ) and type in ....

[B]gnome-shell --replace
[/B] 
Tell me what happens .... please

---

### Post by ratcheer on 2011-05-27
> **23dornot23d said:**
> If it ran ok before .... Gnome-shell that is ..... ( also check and see if gnome-shell is still loaded in synaptic )

Go into classic mode .......

Alt+f2 ......  ( or do it from a terminal - it will give you more information - if there is a problem ) and type in ....

[B]gnome-shell --replace
[/B] 
Tell me what happens .... please

Well, what a surprise. That put me back in Gnome 3 / gnome-shell. And it looks no worse for wear.

I thought that couldn't co-exist with Unity.  ](*,)

Tim

---

### Post by ratcheer on 2011-05-27
> **ratcheer said:**
> And it looks no worse for wear.



I spoke too soon. The windows are in the Win NT style.

Tim

---

### Post by ratcheer on 2011-05-27
> **23dornot23d said:**
> I personally like to use **aptitude safe-upgrade** ..... it always gives a list of the changes
and checks dependencies .......



I ***did*** use aptitude safe-upgrade...

Tim

---

### Post by cbowman57 on 2011-05-27
> **ratcheer said:**
> I spoke too soon. The windows are in the Win NT style.

Tim

Still looking goofy?  Try this & see what it does, if anything.

killall gnome-settings-daemon
gnome-settings-daemon &

---

### Post by ratcheer on 2011-05-27
> **cbowman57 said:**
> Still looking goofy?  Try this & see what it does, if anything.

killall gnome-settings-daemon
gnome-settings-daemon &

```
tim@tim-mav-prod:~$ killall gnome-settings-daemon
tim@tim-mav-prod:~$ gnome-settings-daemon &
[1] 3928
tim@tim-mav-prod:~$ 
** (gnome-settings-daemon:3928): WARNING **: Name taken or bus went away - shutting down

(gnome-settings-daemon:3928): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

[1]+  Done                    gnome-settings-daemon
tim@tim-mav-prod:~$ 

```

Things still look the same. Thanks, though.

Tim

---

### Post by 23dornot23d on 2011-05-27
> 
I spoke too soon. The windows are in the Win NT style.
The thing is Gnome-shell and UNITY will sit happily together ..... and you can even switch from one to the other .....

The next part is just getting it set up as before .... extensions and themes ......

You are in good hands now ..... 

Cheers Charles .... ;)

-------------------------------------------

Ok just seen where your at ..... 

If it works then all the programs are still probably there .....  but just check and see if you have 
the gnome tweak tool loaded ......

**sudo apt-get install gnome-tweak-tool**

Then go to menu >> preferences >> advanced settings

and see if we can set the themes back as they should be

---

### Post by ratcheer on 2011-05-27
I reinstalled gnome-themes-standard. Now, after reboot, the login screen has a Gnome 3 style background, but the login choices are still just Gnome or Ubuntu (and recovery console and user defined login). "Gnome" still cannot login and start. "Ubuntu" still starts Unity. I assume I can still do "gnome-shell --replace" and get back into gnome-shell.

What a mess. I am thinking it is about time to reinstall Ubuntu.

Tim

---

### Post by 23dornot23d on 2011-05-27
Well up to you ...... clean install if you want to .......  

You have not installed anything that should make it a mess ..... as far as I can see .....

But who knows .......

( I think all the rumours of them not working together is enough to put a lot of people off - stick with one  UNITY looks 
like the one they are concentrating on ....... and you could be fighting a loosing battle with Gnome-shell )

I am going to battle away against all the odds though ..... as I like working in both ......

---

### Post by eurekabru on 2011-05-27
> **ratcheer said:**
> I reinstalled gnome-themes-standard. Now, after reboot, the login screen has a Gnome 3 style background, but the login choices are still just Gnome or Ubuntu (and recovery console and user defined login). "Gnome" still cannot login and start. "Ubuntu" still starts Unity. I assume I can still do "gnome-shell --replace" and get back into gnome-shell.

What a mess. I am thinking it is about time to reinstall Ubuntu.

Tim

I'm in the exact same situation as **ratcheer**. 
I tried purging gnome3 and reinstalling everything. It brought me back to Unity and now I can't install gnome-shell anymore.

---

### Post by tgm4883 on 2011-05-27
> **eurekabru said:**
> I'm in the exact same situation as **ratcheer**. 
I tried purging gnome3 and reinstalling everything. It brought me back to Unity and now I can't install gnome-shell anymore.

I haven't followed this thread from the beginning, but I installed Gnome3 using the following instructions on 11.04
[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

:EDIT: Didn't finish that though.

I used the cmd line instructions.

What errors are you getting that you cannot install gnome-shell anymore? What version is gnome-session?

---

### Post by ratcheer on 2011-05-27
> **23dornot23d said:**
> Well up to you ...... clean install if you want to .......  



I will try to restrain myself. Everything is basically working, and I am supposed to be getting a new PC in the next week or so. Once I get that one running and configured, I should be able to tinker with this one to my heart's content. If I can find a physical place to put it.

I can always start using the Fedora 15 installation on my testing partition, if I want a pretty gnome-shell.

Tim

---

### Post by eurekabru on 2011-05-27
> **tgm4883 said:**
> I haven't followed this thread from the beginning, but I installed Gnome3 using the following instructions on 11.04
[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

:EDIT: Didn't finish that though.

I used the cmd line instructions.

What errors are you getting that you cannot install gnome-shell anymore? What version is gnome-session?

That's the same guide I used.

gnome-session is: 2.32.1-0ubuntu20  

```
~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: gnome-bluetooth (>= 3.0.0) but 2.91.2.is.2.32.0-0ubuntu3 is to be installed
               Depends: libcamel-1.2-23 (>= 3.0) but it is not installable
               Depends: libcamel-1.2-23 (< 3.1) but it is not installable
               Depends: libebook1.2-10 (>= 3.0.0) but 2.32.2-0ubuntu2 is to be installed
               Depends: libecal1.2-8 (>= 3.0.0) but 2.32.2-0ubuntu2 is to be installed
               Depends: libedataserver1.2-14 (>= 3.0.0) but 2.32.2-0ubuntu2 is to be installed
               Depends: libedataserverui-3.0-0 (>= 3.0.0) but it is not installable
               Depends: libstartup-notification0 (>= 0.11) but 0.10-1build1 is to be installed
               Depends: gnome-settings-daemon (>= 2.91.5.1) but 2.32.1-0ubuntu13.1 is to be installed
               Depends: gnome-icon-theme-symbolic (>= 2.91) but it is not going to be installed
               Depends: gir1.2-gkbd-3.0 but it is not installable
               Depends: gir1.2-gnomebluetooth-1.0 but it is not installable
E: Broken packages

```

---

### Post by tgm4883 on 2011-05-27
> **eurekabru said:**
> That's the same guide I used.

gnome-session is: 2.32.1-0ubuntu20  

```
~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: gnome-bluetooth (>= 3.0.0) but 2.91.2.is.2.32.0-0ubuntu3 is to be installed
               Depends: libcamel-1.2-23 (>= 3.0) but it is not installable
               Depends: libcamel-1.2-23 (< 3.1) but it is not installable
               Depends: libebook1.2-10 (>= 3.0.0) but 2.32.2-0ubuntu2 is to be installed
               Depends: libecal1.2-8 (>= 3.0.0) but 2.32.2-0ubuntu2 is to be installed
               Depends: libedataserver1.2-14 (>= 3.0.0) but 2.32.2-0ubuntu2 is to be installed
               Depends: libedataserverui-3.0-0 (>= 3.0.0) but it is not installable
               Depends: libstartup-notification0 (>= 0.11) but 0.10-1build1 is to be installed
               Depends: gnome-settings-daemon (>= 2.91.5.1) but 2.32.1-0ubuntu13.1 is to be installed
               Depends: gnome-icon-theme-symbolic (>= 2.91) but it is not going to be installed
               Depends: gir1.2-gkbd-3.0 but it is not installable
               Depends: gir1.2-gnomebluetooth-1.0 but it is not installable
E: Broken packages

```

Odd. Do you still have the gnome 3 team ppa activated? Does an 'apt-get update' fail on anything?

---

### Post by 23dornot23d on 2011-05-27
> **ratcheer said:**
> I will try to restrain myself. Everything is basically working, and I am supposed to be getting a new PC in the next week or so. Once I get that one running and configured, I should be able to tinker with this one to my heart's content. If I can find a physical place to put it.

I can always start using the Fedora 15 installation on my testing partition, if I want a pretty gnome-shell.

Tim


Ok Fedora is starting to look good to me too ......

---

### Post by eurekabru on 2011-05-27
> **tgm4883 said:**
> Odd. Do you still have the gnome 3 team ppa activated? Does an 'apt-get update' fail on anything?

It is activated. I'm guessing that's a problem ? I followed what the guide said and it says to add that ppa. Or have I gone insane ?

Update doesn't fail on anything.

---

### Post by tgm4883 on 2011-05-27
> **eurekabru said:**
> It is activated. I'm guessing that's a problem ? I followed what the guide said and it says to add that ppa. Or have I gone insane ?

Update doesn't fail on anything.

Yea it should be activated, odd that it says the package upgrades can't be installed.

What is the output of 

```
cat /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
```

---

### Post by eurekabru on 2011-05-27
> **tgm4883 said:**
> Yea it should be activated, odd that it says the package upgrades can't be installed.

What is the output of 

```
cat /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
```

~$ cat /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
# deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main

---

### Post by tgm4883 on 2011-05-27
> **eurekabru said:**
> ~$ cat /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
# deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main

yea that PPA is disabled. You need to remove the comment from the front of the 'deb' line. Or you can go into software sources and readd them

That is why you cannot install gnome-shell or any of the other packages.

---

### Post by eurekabru on 2011-05-27
> **tgm4883 said:**
> yea that PPA is disabled. You need to remove the comment from the front of the 'deb' line. Or you can go into software sources and readd them

That is why you cannot install gnome-shell or any of the other packages.

It's installing now. Thank you. 

Let's see if it fixed my previous issue.

---

### Post by ratcheer on 2011-05-27
> **23dornot23d said:**
> Ok Fedora is starting to look good to me too ......

Yes, the main problem is that my configuration, apps, and data are all on Natty. And my Fedora is on a 10 GB partition.

Tim

---

### Post by bmbaker on 2011-05-27
i really recommend adding the testing ppa
```
sudo add-apt-repository ppa:ricotz/testing
```
there seems to alot less problems with updates etc when you have this active :-)

---

### Post by Pompano on 2011-05-27
I heard it is not worth it. Is this true?

---

### Post by tgm4883 on 2011-05-27
> **Pompano said:**
> I heard it is not worth it. Is this true?

I really like Gnome 3. That said, I liked Unity as well. I think both are far ahead of Gnome 2 and the classic desktop. Really though, it's up to you and how you use your computer. I multi-task pretty frequently and use a lot of the functionality built into gnome 3 (plus I think it looks great), but most of it can be done with Compiz in Gnome 2.

---

### Post by cbowman57 on 2011-05-28
> **ratcheer said:**
> I will try to restrain myself. Everything is basically working, and I am supposed to be getting a new PC in the next week or so. Once I get that one running and configured, I should be able to tinker with this one to my heart's content. If I can find a physical place to put it.

I can always start using the Fedora 15 installation on my testing partition, if I want a pretty gnome-shell.

Tim

I don't think it get's much prettier than this. :)

---

### Post by ratcheer on 2011-05-28
Yes, that is excellent, Chuck. Do you use gnome-extensions to get those effects?

I was just saying that my Ubuntu Gnome 3 is not pretty since it became semi-broken. It was also very pretty until yesterday.

Tim

---

### Post by cbowman57 on 2011-05-28
> **ratcheer said:**
> Yes, that is excellent, Chuck. Do you use gnome-extensions to get those effects?

I was just saying that my Ubuntu Gnome 3 is not pretty since it became semi-broken. It was also very pretty until yesterday.

Tim

Yes, all the icons upper left are the result of fpmurphy's eureka extension, combines about 5 extensions into one, just started trying that out last night.


ok, you've got:

1. ricotz/testing
2. ricotz/staging
3. gnome3-team/gnome3
4. ubuntugnomeeteam/gnome3  <<< dead as of this morning
5. ubuntugnometeam/ppa-gen

(Though one of the ubuntugnometeam repos seems dead this morning, not sure which one yet, maybe both)

---

### Post by ratcheer on 2011-05-28
I finally gave up and did a fresh install of Natty. Both Gnome 3 and Unity worked for the most part, but both were somewhat messed up. I could not get in to the Gnome 2 Panel DE.  So, when my new PC comes, I have to decide whether to stick with Ubuntu or switch to Fedora 15. 99% of my Linux experience is on Ubuntu, but I really prefer Gnome 3 and it is not quite ready for Ubuntu, yet. On the other hand, I have had some mysterious crashes on a fresh install of Fedora 15. Maybe crash is too strong a word, but I will be doing something innocuous like clicking on a web link and all of a sudden, I will be back at the DE logon screen.  In the past few weeks, I have tried Debian, Lucid Puppy, Fedora 15, and Xubuntu 11.04. Should I try Mint 11?  Tim

---

### Post by t.rei on 2011-05-29
I actually did a fresh install of natty and installed gnome3 smoothly. Just added gnome3-team ppa and did the driver-install/update/upgrade/install thing.

so basically:
install natty -> boot natty -> open a terminal -> update/dist-upgrade -> add repos -> update-dist-upgrade -> install gnome-shell -> reinstall gdm, gnome-session (to be shure) -> reboot

works. done. the whole thing was up and running within ~30 minutes including the natty install.

---

### Post by t.rei on 2011-05-30
I am kindof stuck at one thing that bugs me on my gnome-shell:

Does anyone know of an option to hide menubars? Or a global-Menu (I know there is thought being thrown around at gnome3). It's just wasting space 90% of the time and just ugly, old win3.11 style, imho. (thing I liked best so far, was the elementaryOS "menu-button" that resides in the toolbar).

---

### Post by midfingr on 2011-05-31
> **t.rei said:**
> I am kindof stuck at one thing that bugs me on my gnome-shell:

Does anyone know of an option to hide menubars? Or a global-Menu (I know there is thought being thrown around at gnome3). It's just wasting space 90% of the time and just ugly, old win3.11 style, imho. (thing I liked best so far, was the elementaryOS "menu-button" that resides in the toolbar).

I don't know if this will help: [http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html](http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html)

And yeah, I thought the same thing; Windows 3.1 all over again.

---

### Post by t.rei on 2011-06-01
Well, no. I don't see that working at all. Since the gtk3 code is not even reacting to any menu proxy or whatnot. 

For now I've settled to adjusting the theme to look ok, in my opinion, but the menubars are still omnipresent. *grumbles something about interface regression* [U]
[/U][http://www.informatik.uni-bremen.de/~timorei/Bildschirmfoto.png]("http://www.informatik.uni-bremen.de/%7Etimorei/Bildschirmfoto.png")

---

### Post by skibler on 2011-06-03
I did a command-line only install of 11.04, added the gnome3 ppa, and then installed x11-xorg, gnome-shell, and gdm. Worked perfectly. Not a single mote of unity on here.

You do have to pull in all the gnome apps you want by yourself, as there doesn't seem to be a "gnome-standard" -type package in the gnome3 ppa. But I am not sure that is really a bad thing.

The only issue I have come across now, is that I don't seem to have the Cantarell font set installed. It does not appear to be available in any standard ubuntu repository, or any other ppa I have searched. Why is this? Isn't it the standard gnome3 font? You can download it from the gnome3 git, or even google web fonts, but wouldn't it make sense for there to be a package for it?

---

### Post by cbowman57 on 2011-06-03
> **skibler said:**
> I did a command-line only install of 11.04, added the gnome3 ppa, and then installed x11-xorg, gnome-shell, and gdm. Worked perfectly. Not a single mote of unity on here.

You do have to pull in all the gnome apps you want by yourself, as there doesn't seem to be a "gnome-standard" -type package in the gnome3 ppa. But I am not sure that is really a bad thing.

The only issue I have come across now, is that I don't seem to have the Cantarell font set installed. It does not appear to be available in any standard ubuntu repository, or any other ppa I have searched. Why is this? Isn't it the standard gnome3 font? You can download it from the gnome3 git, or even google web fonts, but wouldn't it make sense for there to be a package for it?

Look in one of the ubuntugnometeam ppa's.

---

### Post by skibler on 2011-06-03
> **cbowman57 said:**
> Look in one of the ubuntugnometeam ppa's.

:o I some how missed that with google, thank you!

---

### Post by DarkTide on 2011-06-04
I seem to be ok with it remembering passwords ...... I have that already installed though,

here is my latest headache ....

E: /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb:  trying to overwrite '/usr/lib/mutter/Meta-3.0.typelib', which is also in  package gir1.2-mutter-2.91 3.0.0-0ubuntu1~build1

Anybody know how to fix this ?


Gnome-Shell is still running well but I hate having any errors ......

---

### Post by tgm4883 on 2011-06-04
> **DarkTide said:**
> I seem to be ok with it remembering passwords ...... I have that already installed though,

here is my latest headache ....

E: /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb:  trying to overwrite '/usr/lib/mutter/Meta-3.0.typelib', which is also in  package gir1.2-mutter-2.91 3.0.0-0ubuntu1~build1

Anybody know how to fix this ?


Gnome-Shell is still running well but I hate having any errors ......

That is a packaging error. Looks like someone didn't tell gir1.2-mutter-3.0 that it conflicts/replaces gir1.2-mutter-2.91

---

### Post by cbowman57 on 2011-06-04
> **DarkTide said:**
> I seem to be ok with it remembering passwords ...... I have that already installed though,

here is my latest headache ....

E: /var/cache/apt/archives/gir1.2-mutter-3.0_3.0.0-0ubuntu1_i386.deb:  trying to overwrite '/usr/lib/mutter/Meta-3.0.typelib', which is also in  package gir1.2-mutter-2.91 3.0.0-0ubuntu1~build1

Anybody know how to fix this ?


Gnome-Shell is still running well but I hate having any errors ......

You already try **sudo apt-get -f install** ?

---

### Post by tgm4883 on 2011-06-04
> **cbowman57 said:**
> You already try **sudo apt-get -f install** ?

apt-get -f install isn't magic

---

### Post by cbowman57 on 2011-06-05
> **tgm4883 said:**
> apt-get -f install isn't magic

No, but sometimes it gets the job done.

What was your helpful suggestion?

---

### Post by tgm4883 on 2011-06-05
> **cbowman57 said:**
> No, but sometimes it gets the job done.

What was your helpful suggestion?

> That is a packaging error. Looks like someone didn't tell gir1.2-mutter-3.0 that it conflicts/replaces gir1.2-mutter-2.91

Guess I forgot to mention that someone should file a bug

---

### Post by Interruptor on 2011-07-04
My friend's Asus EeePC T101MT stopped booting into X after gdm upgrade from 3.0.2 to 3.0.4. Anyone else experiencing this?
It started with startx command after deleting .Xauthority and .ICEauthority files, but a bunch of another problems...

---

