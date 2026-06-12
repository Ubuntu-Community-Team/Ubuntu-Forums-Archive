---
title: "Working with multiple Window Managers"
date: 2009-12-01
forum: General Help
---

### Post by Mahngiel on 2009-12-01
**Preface:** I am a novice who is trying to learn.  I have a habit of learning the hard way.  My experiences are italicized, and if they are not correct, they are what I experienced, or at least felt happened during these actions.  I decided to put this here to give a bit of information to what I was trying to do, and what happened to me.  This is in no way an expert tutorial, just what one noob did, and is trying to do to help others.  Your experience my differ, and your input is valued.

I decided to post a quick Tip about working with multiple Window Managers after I really messed up my system.  Being a tinkerer, I began swimming without a paddle and soon found myself up [a very dirty] creek.  :P  See: [_My help thread_]("http://ubuntuforums.org/showthread.php?t=1342165&page=2")

The default that comes on 9.10 is Metacity; however, there are many window managers available for the Unix systems, two good sites for WM info are _[LinuxLinx]("http://www.linuxlinks.com/article/20081209153125602/WindowManagers.html")_ and _[XWinMan]("http://xwinman.org/")_.  Finding one that works with GNOME may be the best and easiest for novices like myself, though there are several viable options, depending on your expertise.

First, and foremost, you do not need to be rid of Metacity in order utilize another WM.
[I]This I did NOT know, and after several reboots and a real interest in trying these other WMs and not getting them to load, I uninstalled Metacity.  Doing this uninstalls dependecies with gnome that can crash your system.

[/I]If you are a single user, like myself, you need to enable login at boot.
*System > Administration > Login Screen - set option to 'show the screen for choosing who will log in'*
 At the login screen's bottom you will see *Session:* with a drop down menu.  By default, you get *GNOME* and *xterm*.  I installed _[e16]("http://www.enlightenment.org/p.php?p=about/e16&l=en")_ and _[iceWM]("http://www.icewm.org/")_.  These work well with Gnome so all the dependencies are already installed.

You'll have a session option for each of your new Win Mgrs now, well, you'd think.  You don't have one set up to use Metacity.  So, after you check out the other WMs, and you head back to the login screen and select the GNOME session, you'll notice that GNOME doesn't know what to do - there'll be no WM set up as default.  You won't be able to draw the windows so you can resize, alt+tab, close, etc, so you'll need to set up a default WM - why not use Metacity since you're using GNOME session to be your default anyways?
*Either terminal 'gconf-editor' or open the Configuration Editor.* [I] Under the tree Desktop > Gnome > Session > Required Components you'll see 'windowmanager' with value either e16, icewm, or whichever WM you installed.  Right click > Edit Key and set the Value to 'metacity'

[/I]There you go.  You now have multiple Window Managers to toy with and can always go back to your default session with Gnome and Metacity.

---

