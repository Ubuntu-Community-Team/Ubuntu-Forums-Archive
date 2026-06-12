---
title: "login problem due to xdmcp"
date: 2009-08-12
forum: General Help
---

### Post by grimng on 2009-08-12
Hello,
I'm a new user of Linux base os. I am using Ubuntu 9.04.
I have inadvertently done this: login windows preferences>confihure x server...
the result is that now i get "dialog box" that ask me a server name or to choose from a list. When i click on the refresh button i get the message that there are no servers...
I tried to give the name of my laptop : alex-laptop and i get this new message that tells me it cannot connect to alex-laptop because it has tried for 3 seconds etc.

I don't know what i did because i didn't meant to do something in particular but just getting accustomed to the different applications. I don't know how to login.

P.s. I'm not very accustom to command line

---

### Post by P4man on 2009-08-12
Im not sure how you managed to get there lol, but is it an XDMCP login window you have now ? If so, isn't there simply a cancel button that gets you back to the normal gdm login?

If not, perhaps try this: press control+alt+F2 to get a console. Log in with your user name/pw. Then type:

```
sudo /etc/init.d/gdm restart
```

---

### Post by grimng on 2009-08-12
:P If i tell you, you'll probably lyao till madness. It's so stupid that i'm ashamed to the point of kicking my ***!:lolflag: 

yeah it's an xdmcp window and clicking on cancel send me effectively to somewhere but not the normal gdm but a command line. But studpidly i've set the login time to 10 seconds (i think) so whenever i start typing my username the xdmcp window get back. anyhow I've just learn that i can type 6 characters in 1 second.

 
Anyway thanks i'm gonna try this and come back to tell you the results!
Your answer has comfort me in my choice to equip all my machines with ubuntu:popcorn:

---

### Post by grimng on 2009-08-12
I am sorry to come back and it pain me to be such a ****** but you are my last chance to egt out of this mess.

so here;s the situation: I've followed the steps suggested up but  when i hit enter for 

sudo /etc/init.d/gdm restart

i get back to the xdmcp window asking me for server host. 

I am actually using the live cd to write all this, i have access to the file system...do you think we can change things from the live session. I've tried to logging from but with no results.

Once again i am sorry to be such a dumb a--h-- and taking your time for such a stupid error.

Btw great key board shortcut!

oh i forgot one important thing: I don't mind reinstalling coz it's a new installation but i got vista partition on the hdd and all my work's there

---

### Post by grimng on 2009-08-12
in relation to my last post i've took this from the gdm.conf-custom :

GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libkeymouselistener:/usr/lib/gtk-2.0/modules/libdwellmouselistener

AddGtkModules=true

AlwaysLoginCurrentSession=false


AutomaticLoginEnable=false

[security]

[xdmcp]

[gui]

GtkRC=



[greeter]






































GraphicalThemes=Human




































GraphicalThemedColor=#120b07


BackgroundType=1





BackgroundImage=/usr/share/pixmaps/backgrounds/cosmos/helix-nebula.jpg

BackgroundColor=#903d3d























































DefaultFace=/usr/share/pixmaps/gnome-logo-icon.png










[chooser]

[debug]

[servers]

[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
chooser=true
handled=true
flexible=true
priority=0

---

### Post by P4man on 2009-08-12
stop apologizing please :) One of the reason i like helping out is because it teaches me a lot. So  it might help (and satisfy my curiosity) if I had an idea how you managed to get where you are, because if someone would ask me how replace the gdm login screen with xdmpc only one, i wouldnt know where to start looking lol. i tried google and came up empty.

Anyway, lets try the simple stuff first:

```
sudo dpkg-reconfigure gdm
```

Run that from the console (ctrl+alt+F1/2/3/4/5/6/..anything but 7).

---

### Post by grimng on 2009-08-12
OK :P! sor...
So I tried the dpkg reconfigure, as before i get back to the XDMCP window. I then do ctrl+alt+f2 again and i see this message:

*Changes will take effect when all current X sessions have ended

Now I've been thinking about what steps brought me here :

Like i said i was trying different appearance settings when i entered the Login window preferences: 

Part 1 : I think that i have untick Disable multiple logins for a single user (I'm almost sure coz i wanted to create and account for my wife but i am sure i haven't created her account)

Part 2: I went to the local tab and choosed the human theme (style: themed with face browser and Theme :selected only)

Part 3: that's where i am unsure, i think i went to accessibility tab and enable accessible login but i can't guarantee coz i can't see why i'd done that.

Part 4: I'm almost sure of that: i went to the security tab and untick Enable automatic login (coz i wanted to have a protected account like windows, main reason kids are worst than me) then i saw the configure X server...button and i clicked to have a look. there i think (almost sure) the launch from greeter to chooser. That's the unintentional part, i'm use to windows where for everything  you get a button to say apply. I think i just close the window without verifying.

Part 5: i'm totally sure I changed the default face for gnome ping. I really like feet ;-)

well after that someone call me and i forgot all about it, then i just shutdown and when i came back i was on XDMCP

---

### Post by P4man on 2009-08-12
Ok, it has to be the xserver settings. I guess you where right posting the contents of gdm.conf-custom. FWiW, here is mine:
```

# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# Older versions of GDM used the "gdm.conf" file for configuration.  If your
# system has an old gdm.conf file on the system, it will be used instead of
# this file - so changes made to this file will not take effect.  Consider
# migrating your configuration to this file and removing the gdm.conf file.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# /usr/share/gdm/defaults.conf file for information about each option.  Also
# refer to the reference documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# e.g, the "Enable" key in the "[debug]" section would be "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

AutomaticLoginEnable=false

[security]


[xdmcp]

[gui]

[greeter]







GraphicalTheme=aquadreams


































[chooser]

[debug]

[servers]

```

Probably wont hurt copy/pasting that, just change the theme name to something you have (human)

---

### Post by grimng on 2009-08-12
sadly I don't have permission to edit gdm.conf-custom from the live session:( 
I've tried to open the gdm.conf-custom from the console but i'm not experienced enough and only get denial. I think i'm going to sleep on this, i'm starting to get a headache. I'll be there in 10 hours approximately by then i'll try to make some search and ask some friends. Thanks for the help and if you get an answer i'll be very grateful

---

### Post by P4man on 2009-08-13
to edit the file from the console, type:

```
sudo nano /etc/gdm/gdm.conf-custom 
```

works like most editors, to save, press ctrl+x, and reply "y" to the prompt.

But from a livecd, it ought to work as well with:

```
gksudo gedit /path/to/gdm.conf-custom
```

or if you prefer:

```
gksudo nautilus
```

to open the file manager with root permission, then browse to the file, and edit it.

Another thing you could try , is to start gnome from the terminal:

```
gnome-session
```

---

### Post by grimng on 2009-08-13
Guess What?:P

You've done it! I'm on my good new Ubuntu jaunty!!!!!!!!!!!

kudos!

My wife send you kisses (she's young and attractive:lolflag:) and saying thanks that you've relieve her of that "stupid husband" (though she was of some help i hope she remember i got it repair) awful mood since ubuntu went down!

Anyway we are both grateful and the kids too (you brought back their games).

Here's how i proceeded : First i tried from the live cd but with no results, then i went back to the xdmcp window   and press ctrl+alt+f2 to sumon the console. 

Entered login/pw etc.. then

sudo nano /etc/gdm/gdm.conf-custom
i did not paste the your gdm.conf-custom (i still don't now how to do that or even how to open a text from my pendrive. not really..but anyway i was afraid to try too many things) instead i just backspace the template/command leaving the comments with # and type yours.

i saved with ctrl+x answered y and was back to the console, I re-read the comments where it specified to re-run gdm for the change to take place automatically. 
For that i used the command you gave me lastnight :

sudo /etc/init.d/gdm restart

and here i am! P4man you are my new king!!!

---

