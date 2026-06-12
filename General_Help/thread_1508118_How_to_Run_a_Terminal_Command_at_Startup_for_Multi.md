---
title: "How to Run a Terminal Command at Startup for Multi-Touch Scrolling?"
date: 2010-06-12
forum: General Help
---

### Post by dvfrog on 2010-06-12
Hello,

I'm a day-1 Ubuntu user with a question about getting multi-touch scrolling enabled on my laptop automatically each time 10.04 loads.

I'm very green when it comes to all-things-Linux.  Basically, I'm just searching for help, following step-by-step guides, and copying-and-pasting commands.

I found the following website that helped me create a little script to enable multi-touch control:
[http://mixeduperic.com/Linux/Hacks/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html](http://mixeduperic.com/Linux/Hacks/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html)

But  I can't figure out the last step:
"All you need to do to have this run at startup [instead of typing ./2fsrl in terminal manually each time] is add it to you startup  programs."

I tried creating a file path to the 2fsrl file in Preferences -> Startup Applications program, but upon re-starting the laptop, the multi-touch isn't enabled anymore.

I'm sure I'm missing something simple.  Can anyone advise?  (Keep in mind my beginner's status!)

---

### Post by dcstar on 2010-06-13
> **dvfrog said:**
> Hello,

I'm a day-1 Ubuntu user with a question about getting multi-touch scrolling enabled on my laptop automatically each time 10.04 loads.

I'm very green when it comes to all-things-Linux.  Basically, I'm just searching for help, following step-by-step guides, and copying-and-pasting commands.

I found the following website that helped me create a little script to enable multi-touch control:
[http://mixeduperic.com/Linux/Hacks/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html](http://mixeduperic.com/Linux/Hacks/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html)

But  I can't figure out the last step:
"All you need to do to have this run at startup [instead of typing ./2fsrl in terminal manually each time] is add it to you startup  programs."

I tried creating a file path to the 2fsrl file in Preferences -> Startup Applications program, but upon re-starting the laptop, the multi-touch isn't enabled anymore.

I'm sure I'm missing something simple.  Can anyone advise?  (Keep in mind my beginner's status!)

Put the **full path** to the script in the launcher:
```

/home/your-account/2fsrl
```

Or launch the script in /etc/rc.local.

---

### Post by dvfrog on 2010-06-13
Forgive my ignorance, but would using Launcher require manually starting this script each time? (albeit, through a quicker method than typing a Terminal command)

Is there a simple way to run this multi-touch script automatically during the boot process?

Or are you saying that Launcher + Startup Programs, in combination, is the answer?

---

### Post by dgranillo on 2010-06-15
System > Preferences > Startup Applications > Add

Enter whatever you wish for name and comment. Browse to where you saved your 2fsrl script and click Open. Then Add

---

### Post by dvfrog on 2010-06-15
Hmmm...  I'm not sure what I'm doing wrong, but I follow those steps without any luck.  Here's a screen cap to show you my script, the location of the script (Home Folder), and the options within the Startup Applications program.

Those instructions were simple enough to follow.  Can you tell if I've missed a step anywhere?

[IMG]https://dl.dropbox.com/u/13118/Screenshot.png[/IMG]

---

### Post by dgranillo on 2010-06-17
Did you forget to make it executable?

chmod +x /home/jprice/2fsrl

---

### Post by dvfrog on 2010-06-17
> **dgranillo said:**
> Did you forget to make it executable?

chmod +x /home/jprice/2fsrl

Hmmm... not so much "forgot" as "didn't know"! :-)

I went to edit the Startup Application I'd created previously.  I added the text you mentioned.  Upon restarting the computer, however, it still didn't auto-enable multi-touch scrolling.

I created a "launcher" that can enable scrolling when manually clicked, but I'm still hoping I can figure out a way to auto-enable this command upon log-in.

Here's my screen shot from my latest Startup Application adjustment:

(note that the complete command reads: "chmod +x /home/jprice/2fsrl" even though it's cut off in the visible text field in the window below)

[IMG]http://dl.dropbox.com/u/13118/Screenshot2.png[/IMG]

Thoughts?

---

### Post by pitbullthe1st on 2010-06-18
Hi,

I'm looking for a fix like this lol but there is just one thing I can clarify for you. You have to use the 'chmod' command in command line to give your file permission to run as an executable file then you call the file in your start up programs list.

To do this open a terminal and type:

> chmod +x ~/2fsrl

This is assuming that you script is in your home directory and not where it should be witch is in your bin directory not that it matters lol.

Then in your startup apps menu just type in 
> /home/your-user-name/2fsrl

and that SHOULD work we hope lol good luck and I'm now going to try this on my vaio to see if it works for me.

---

### Post by pitbullthe1st on 2010-06-18
Nope it don't work for me but then nor dose the side scroll how annoying :-((

---

### Post by dvfrog on 2010-06-19
Rats.  It didn't work for me either.  Thank you very much for the suggestion, though.

Any other thoughts from anyone?

My "launcher" application (which I put in my menu bar, next to the Firefox and Help icons) starts this multi-touch capability with no problem when clicked.  Is it possible to put a specific "launcher" into the Startup Applications program?

---

### Post by dvfrog on 2010-06-19
> **dvfrog said:**
> 
My "launcher" application (which I put in my menu bar, next to the Firefox and Help icons) starts this multi-touch capability with no problem when clicked.  Is it possible to put a specific "launcher" into the Startup Applications program?

I created a new "launcher" on my desktop (Type:  "Application in Terminal") that pointed to the /2fsrl script in my Home folder.  Upon restarting my computer, I got the following pop-up window.

[IMG]http://dl.dropbox.com/u/13118/Screenshot3.png[/IMG]


Needless to say, this method didn't work either.

Any other ideas from anyone?

---

