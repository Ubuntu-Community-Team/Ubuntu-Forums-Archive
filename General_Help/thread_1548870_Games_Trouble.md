---
title: "Games Trouble"
date: 2010-08-09
forum: General Help
---

### Post by Gamewiz on 2010-08-09
Okay, so I've downloaded some games from the Ubuntu Software Center and after the first time I play the game I'll leave, go do whatever on the internet and come back. But when I try to get back into the game it won't open.. I mean I'll click for it to open and nothing happens.. 

Any Ideas?

Also I'm running Ubuntu 10.04.

---

### Post by bergfly on 2010-08-09
Gamewiz

Gonna need a bit more info than that to go on. What game is the issue? Does the screensaver come on? Does the system monitor show the game as up and running? What happens if you try to close the game? Any additional info will be great to help isolate the problem.

---

### Post by Gamewiz on 2010-08-09
The games that don't work are pretty much any of the full screen games, such as gl-117 and Freedroid RPG. These games work right after I download them, but after I quit, they won't open again. I can't really give much more information other than that because when I click on the game nothing happens, my prossesors don't start using more power, nothing, its like I click on a blank space on my desktop.

---

### Post by bergfly on 2010-08-09
Gamewiz

When you say you click on the game, do you mean that you try to launch the game from a shortcut on your desktop and the game does not load.

Is there an instance of the game running on the machine already. You can check this under the system monitor

[IMG]http://www.liberiangeek.net/wp-content/uploads/2010/07/command_gui_ubuntu_9.png[/IMG]

Once you have th monitor running, look for the name of the game under the list of processes.

---

### Post by Gamewiz on 2010-08-09
When I say I click on the game I mean I'm in the applications menu and clicking on it within the games section, also, I've tried restarting my computer, and the game still will not work.

---

### Post by bergfly on 2010-08-09
Ok, the best way forward now is to run the game from the command line and then troubleshoot the output from that. 

Click on Applications, then accessories and then terminal. This opens the command line. Once you have this open type the first three or four letters of the name of  the game and hit tab. This will give you a list of the actual name similar to the game. Select the one that is the game you want (sorry, don't know the actual bin file names so can't help on that)

More than likely a whole pile of text will appear in the window even i the game does not run. Cut and paste the text so we can see it

thanks

---

### Post by Gamewiz on 2010-08-09
This is the text that came up when I tried to open in like you said in the terminal..

Hello, this is FreedroidRPG, version 0.12.1.
This seems to be a 'stable' release, so no exit on floating point exceptions.
-Signal Handling------------------------------------------------------
Setting up signal handlers for internal backtrace:
Now catching SIGSEGV: YES
Now catching FPE (if raised, that is!): YES


Video system type: x11.
Using screen resolution 1280 x 960.
----------------------------------------------------------------------
Freedroid has encountered a problem:
In Function: set_video_mode_for_open_gl.
FreedroidRPG package and version number: freedroidrpg 0.12.1.
SDL reported, that the video mode mentioned above is not supported
Breaking off...If you encounter this message, please inform the Freedroid developers
about the problem, by sending e-mail to 

[email]freedroid-discussion@lists.sourceforge.net[/email]

Or you can mention it to someone of the developers on our
IRC channel.  The channel is:

channel: #freedroid on irc.freenode.net

Thanks a lot!

Freedroid will terminate now to draw attention to the problems it could
not resolve.  Sorry if that interrupts a major game of yours...

----------------------------------------------------------------------
Termination of freedroidRPG initiated...Thank you for playing freedroidRPG.



Also, I've E-mailed the E-mail address that is quoted in the error message.

---

### Post by bergfly on 2010-08-09
Ok, the issue we have here is the game is trying to use Open-gl to the screen that is not seen as supported by the hardware. This may be because you don't have the right drivers for the card, or set the wrong resolution in the game (you mentioned it ran once) Many different roads to go down here, but lets start with what type of graphics card you have. Do you have any idea what you have for a graphics card on the machine you are using?

---

### Post by Gamewiz on 2010-08-09
Crap, I think I was screwing with my resolution settings... How can I change that now without going in game?

---

### Post by bergfly on 2010-08-09
All is not lost necessarily. Most games store their settings in a hidden file in the home directory. If you delete this hidden file or folder, the game goes back to defaults when you start it. Now if you had a whole lot of saved games, you would loose these, but assuming you don't...

Go to Home in Places. 

At the top of the window, you will see view, Choose this menu and then check the box marked Show hidden files. 

As you can now see there a whole bunch more files in the view, many starting with a .   If you put a dot in front of a file in linux this indicates it is hidden.

Anyway, find either the folder with the game name  ( so if you are deleting freedroidrpg, look for .freedroidrpg ), or the file, or both if there are both, and simply delete them. Then try running the game again. 

hope that works...

---

### Post by Gamewiz on 2010-08-09
Awesome! Thank you so much! It worked, good thing I didn't do anything other than a tutorial in those games.

Anyway Thank you again!

---

### Post by Eddison on 2010-10-24
I had the same problem with gl-117 not working it just quit. I clicked on the game, and nothing would happen. failed completely. But the above post really helped to get it working again, except that I navigated to the .gl-117 folder, and the file was called conf, I opened it, and it said this at the top

# Configuration

# Some possible width x height values for fullscreen mode:
#  640x480, 800x600, 1024x768, 1152x864, 1280x768, 1280x960, 1280x1024
 width = 1280
 height = 1024

I realised i had changed the resolution, so i changed it back to 
width = 1024
height = 768
And now the program is working fine.

Eddison

---

