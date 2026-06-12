---
title: "Cuecat acting wierd (keyboard layout issue?)"
date: 2006-03-12
forum: General Help
---

### Post by eniacpx on 2006-03-12
This is odd. I have a cuecat, which plugs into the PS2 port. When you scan a barcode it is supposed to "type" the barcode number just like if you where typing it by hand, it just sends the keycodes. Here is the porblem. It works fine on a console not running in X. But whne I scan a barcode in X it spits out the ascii codes for each of the barcode numbers. For example a 5 would show as '053' but that is just ion the terminal. In an app like firefox or a text editor it just spits out nothing followed by a newline character. This really sounds like it has something to do with the keyboard map I am using or something, but I just can't figure out where to start. Any ideas?

---

### Post by Ahzwon on 2006-03-30
You're not the only one. A search of CueCat in the forum show two other instances, though not necessarily the same issue.

In your case, I'm guessing your using a modded CueCat. I'm using one, too. I see the same thing you see: Pure console = Ok. Xwindow = Not okay.

Here's something new to put in the mix. Run VMware and fire up a virtual XP machine. Then open up NotePad and voila! The CueCat's working fine.

Doesn't make sense why Xwindow is messing up the device...

---

### Post by Ahzwon on 2006-03-30
There are rumors (and dead links) to a linus driver. Did a search and found a live page with working download to a linux driver:

[http://www.beau.lib.la.us/~jmorris/linux/cuecat/](http://www.beau.lib.la.us/~jmorris/linux/cuecat/)

And the link claims to be to a CueCat driver version 0.1.4 but file you get seems to be 0.1.9.

Haven't tried it yet, but will let you know what kind of mileage I get. :)

Edit:
A quick read of the README reveals this:
[COLOR="Blue"]NOTE : read_cuecat does NOT work under X if you have a CueCat connected on your
       PS/2 port. Bad things may happen if you run read_cuecat as root under X.
       Instead, you should run read_cuecat in a plain text console.[/COLOR]

Which is useless if it's already working flawlessly in "a plain text console." Waaaa! I want it to work under X!

Edit, part II:
This page had some pretty good info:
[http://www.rtmark.com/f/get/funds/media/14/3/1.html](http://www.rtmark.com/f/get/funds/media/14/3/1.html)

[COLOR="Blue"]CueCat->decode uses a perl decode routine on raw scan data from the CueCat. This method is NOT recommended on linux or any system using X-Windows due to the initial Alt-F10 sequence sent by the CueCat. It will work on a regular text console however, provided you do not have a virtual terminal set up on tty10.[/COLOR]

---

### Post by tymanthius on 2006-03-30
Possibly a slightly easier method would be to try a different X term.  There are several available in synaptec.

Might work, might not.  :)

---

### Post by Linuturk on 2006-06-13
Do you have one to recommend?

I'm having the same problem. System specs are in my sig.

It seems the PS/2 Wedge version doesn't like Xserver, or visa versa. Is there a way to get this to work?

Is it confirmed that the USB version works ok in the default x term?

---

### Post by tiberius_k on 2007-02-22
Hi, 
This is my first post here. I have a cue cat and would like to set up an automation scheme for the linux system I just installed for my daughter(3yr's old.) I think that something like [[COLOR="blue"]Kittycontrol[/COLOR]]("http://sourceforge.net/projects/cjfeist/") would work, but frankly I'm amazed that there hasn't been more development in this area. What I envision is a barcode scanner or magnetic tape scanner and a set of cards. The cards would include (hopefully) explanatory pictures as to their functions, which would be things like: 
1. close all programs in the x-windows session, start gcompris, potato guy, etc. 
2. start xpenguins. 
3. sudo shutdown –p now. 
4. close all programs in the x-windows session, play video file xyz. 
Now, I can’t be the only one who can see the value in this. One doesn’t even need small children to appreciate how useful this could be. Your wife(partner, roommate, etc), calls you at work because she can’t check her email, or watch a show on mythtv, or whatever. So you tell her to go the safe(because physical security is key) and get the keyring with all the little plastic cards on it, and scan the one that says remote access, and then scan the one that says format floppy(the card with your root passwd on it,) and the next thing you know you are contacted by your home machine and bingo bango boingo, your back to work! There’s no “does it need to be caps?”  Just my thoughts about what a few short strings of keyboard data can do. Now I know that this will not teach my daughter the elegance of the command line, but she can’t even read for goodness sake, and I’ve got stuff to fix around the house. She recently said to me, “I’ll listen with I’m FOUR.”  Add to that that she’ll know how not to triple-click an icon when she’s six. 

  So, can anyone shed light on this idea. I just have to believe that like everything else I do on a computer, someone else has already done my work for me. Thank you for your time.

---

### Post by whein on 2007-05-22
> **Ahzwon said:**
> In your case, I'm guessing your using a modded CueCat. I'm using one, too. I see the same thing you see: Pure console = Ok. Xwindow = Not okay.
Quick question, when you refer to a modded CueCat, is this just removing the "encryption" or does this apply to the [hack to remove the serial number and other crap]("http://digilander.libero.it/electrons/CueKitty/68-1965.html#Clean")?
This morning I modified a couple of scanners at work and they appear to scan fine under Windows, but I would not be able to detect the Alt-F10 with the program I tested them with.  Anyone know if the above hack strips that out as well?  Does it then really behave like pressing keys on a keyboard, even under X?
-Will

---

### Post by whein on 2007-05-23
Well, got a chance to try it out last night and running it through the terminal program in Gnome and a text editor under Wine seemed to have no ill effects.  I was kind of annoyed that the reader sends a carriage return (or enter/return or whatever) after each scan, but I guess that makes sense for how it was designed.  Just makes it less useful for things it WASN'T designed to do.  :)
-Will

---

### Post by mimsmall on 2007-08-11
Here is a page with several cuecat linux drivers and others like Java and JavaScript.
[http://blort.org/cuecat/](http://blort.org/cuecat/)

---

