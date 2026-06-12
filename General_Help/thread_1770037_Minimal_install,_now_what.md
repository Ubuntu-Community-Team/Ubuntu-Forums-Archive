---
title: "Minimal install, now what??"
date: 2011-05-28
forum: General Help
---

### Post by .psd on 2011-05-28
After the minimal install completed and I restarted at the prompt, the system restarted and I eventually wound up at what I can only call a frozen screen. So I hit alt+f2 and I guess I'm at a console now, I see this:

Ubuntu 11.04 mrt tty1
mrt login: _

Am I doing this right? I thought the first thing I'm supposed to do is sudo apt-get update, but that isn't an option as I think it wants me to log in...?

Anyways, once I get to where I'm supposed to be, and I do sudo apt-get update, how do I know what to do next? I've seen examples like

sudo apt-get install xorg xterm gdm icewm menu gksu synaptic --no-install-recommends
sudo service gdm start

and also like

sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install

but I don't know what each part is, and whether I can choose my own parts, and if I CAN then where do I go to learn the proper command for each part I want? Obviously I need a desktop environment, but how do I know which ones come with a window manager, and which window manager is compatible with which desktop environments?

I don't want to do ubuntu-desktop type commands because I don't want the bloat, that's why I did a minimal install. Also, is it pretty safe to use gnome 3 desktop by now?

---

### Post by .psd on 2011-05-28
Been stuck here for over an hour, don't even know where to start researching. Did a minimal install, it got to the part where it asks you to restart, I restart, and at the point where I would expect to see grub, the scree is clearly frozen, black with a blue line near the top. If I hit alt + f1 through f6 it will bring up a working console-like screens that says

Ubuntu 11.04 mrt tty1
mrt login: _

tty1 representing that I pressed alt+f1 to get to it, and so on.

Alt+f7 brings up a black screen with only a blinking underscore, and ctr+alt+delete says some stuff and then restarts the computer.

If you know about the install process maybe you'll know where it freezes or why it might freeze. Is this a big deal? Is there a way to recover? What can I do from here to get "the basics" (and I do mean basics) like a desktop environment and whatever other GUIs are important (synaptec etc).

I posted a similar question in the installation forums but it's not getting attention and I'm kinda stuck... feel free to delete that one if this goes anywhere mods.

---

### Post by mörgæs on 2011-05-28
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by .psd on 2011-05-28
Checking the links, meanwhile:

Well I can't do anything because of that frozen screen I mentioned. I think I read that it may be the bootloader... At the point of the minimal install where it asks you to restart, I restarted, and at the point where I would expect to see grub but the screen freezes. Someone else mentioned that maybe I need to install in graphical safe mode to begin with...

Ugh.......

I can get to the screens like I said, though, by hitting alt+ f1 through f6 at the frozen screen and there I can type there if I knew what to type. I can get a black screen with a blinking underscore where I can't type anything, by hitting alt+f7.

---

### Post by Rubi1200 on 2011-05-28
A few hints, tips, tricks:

yes, on 11.04 after reboot the screen goes blank and you need to use Alt+F2 first. Yes, the prompt is normal. Remember, at this point you have only a base system with no graphical environment.

Login with your user name and password. Now you can run sudo apt-get update and sudo apt-get upgrade.

Once that is done, if you want a graphical environment you need to install one. So, use this command: sudo apt-get install xorg.

At this point you could use startx to begin a graphical session, but it would be very basic.

What you need to decide now is what type of desktop environment you want to install. There are a number of options, as has already been pointed out in some of your other threads.

The decision as to what to install rests entirely on your needs and wants. Do some searching around and I am sure you will find things.

For example, if you want to know what packages are available you can use apt-cache search <name_of_package> or go here and search: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

At a minimum you need xorg, a desktop environment, and a terminal (if not included in the DE), and a web browser. After that, it is really a personal choice as to what to add.

---

### Post by .psd on 2011-05-28
OK That's really great news!

So what do I type at the login prompt?

then

sudo apt-get update
sudo apt-get upgrade

sudo apt-get install xorg xterm menu firefox gksu synaptec --no-install-recommends

Am I missing anything besides a desktop environment (assuming the desktop environment I choose comes with a windows manager and file manager)? If I want the gnome environment, what all would I have to throw in there? And I mean the gnome gnome, not the bloated ubuntu-desktop gnome. What about gnome 3 instead? Is it even safe to install gnome 3 yet with ubuntu 11.04? Does gnome come with a window manager and file manager or will I have to throw something in there to get those too?

---

### Post by .psd on 2011-05-28
I'm stuck at the login prompt because I don't know what to put.

mrt is one of the names it asked me to put in at one point, but i dont know which one it is or which one i need at this point.

What do I type so I can start the update and stuff?

---

### Post by Elfy on 2011-05-28
Thread closed. Please do not post duplicates, it dilutes community effort.

Please stop opening threads asking the same thing in different words.

---

### Post by cariboo on 2011-05-28
Sorry forestpiskie, I guess we were both moderating this thread at the same time, I merged it with the other one, and then reopened it.

---

### Post by .psd on 2011-05-28
Or you could just answer the question I don't think this thread was hurting anyone it's getting me closer to installing I've been stuck forever nobody needs you to close the thread go away.

EDIT: thanks for merging, that's what I was asking a mod to do in the other thread.

EDIT2: stressing lol. How has nobody asked this question before...

---

### Post by lmn. on 2011-05-28
It's hard to tell what the problem is, probably because I'm no ubuntu expert.

change your sata connections, try a different hd, download the ISO again, keep trying ;)

---

### Post by Rubi1200 on 2011-05-28
> **.psd said:**
> Or you could just answer the question I don't think this thread was hurting anyone it's getting me closer to installing I've been stuck forever nobody needs you to close the thread go away.

EDIT: thanks for merging, that's what I was asking a mod to do in the other thread.
Okay, when you installed from the CD you set up a user name and password otherwise you would not have been able to install. That is what you need to enter at the prompt now.

For example,

login: john
password: (whatever you set during the installation) 

Remember, you won't see any visual feedback when typing the password but just press Enter when done and you should then be logged in.

> **linuxinstalledfromhdd said:**
> I have never seen someone get banned from the Ubuntu help group before. This should be fun to watch. :)
That is not an especially helpful comment. With all due respect, .psd is struggling to get going here and we need to try and be patient and exhibit some understanding.

---

### Post by .psd on 2011-05-28
@linuxfromhdd, wanna just tell me what to type at the login prompt instead of heckling so I can get this show on the road?

---

### Post by .psd on 2011-05-28
Thanks Rubi.

The prompt doesn't just say "login:" is that OK? It says

mrt login: _

mrt is one of the names it asked me to input during install. Is there a way to list the users or do I have to reinstall? Because it asked me to enter names like 3 or 4 times during install and I forgot all of them! I really didn't know what to expect. I know the password, though...

---

### Post by linuxinstalledfromhdd on 2011-05-28
It is on one of the pages that users have posted for you during the last few days. Honestly you have posted so many of the same questions over and over again, I can't really remember which one it is now. You mean to say you didn't keep track of all the responses you have been receiving from everyone here?  I guess that's our fault too perhaps.

---

### Post by Thewhistlingwind on 2011-05-28
Please don't insult the mods. 

Anyway, at the login prompt, root, there should be no need for a password.

Then you just install what you need.

Also, use thread tools at the top to subscribe to and keep track of your own threads.

---

### Post by el_koraco on 2011-05-28
> **.psd said:**
> 
Am I missing anything besides a desktop environment (assuming the desktop environment I choose comes with a windows manager and file manager)?

When you install the xorg package, you will install the Xserver, the foundation for a desktop environment. The Xserver is the "primitive" part of the GUI, which needs a window manager to do the actual drawing of windows of the screen. the xorg package comes with twm, the most basic and first window manager for the X Windows system (xserver and a window manager). Whe you install it, you can run the command startx from the command line to get into a "desktop environment" that you will want to forget as soon as possible. Thereafter, you need to make some decisions. i'm not sure how people can be a lot more helpful if you don't give them further instructions as to your wishes.

---

### Post by .psd on 2011-05-28
@linuxfromhdd, they are all different questions and yes I'm subscribed to all of them. I read or at least skimmed every link people have offered since I started here, I don't know what link you're talking about and it doesn't sound like you do either.

@whistlingwind, at the prompt if I type "root" (no quotes) it asks for a password, then says login incorrect. Note, the prompt isn't

login: _

its

Ubuntu 11.04 mrt tty1
mrt login: _

Is that normal? Again, mrt is one of the names it asked me to input during install, but is there a way to list the users?

---

### Post by bobbob1016 on 2011-05-28
> **.psd said:**
> Or you could just answer the question I don't think this thread was hurting anyone it's getting me closer to installing I've been stuck forever nobody needs you to close the thread go away.

EDIT: thanks for merging, that's what I was asking a mod to do in the other thread.

EDIT2: stressing lol. How has nobody asked this question before...

(I think I solved your login issue at the bottom, but you should read these paragraphs too)

I would say to be patient, this is all happening within an hour, so people are helping.  I am also curious as to why you chose the minimal install when you seem to be starting out with Ubuntu/Linux.  That's like expecting to fly a 747 on your first day in pilot school (not exactly a perfect analogy, but still).

"@linuxfromhdd, wanna just tell me what to type at the login prompt instead of heckling so I can get this show on the road?", I'm just going to say this as an outside observer, no offense intended or meant, you, .psd, seem to be heckling the people who are offering you help.  Just keep in mind, that everyone here is taking time to help you, absolutely free, they don't have to, but they are choosing to.  Most people here are friendly, but don't like being treated like they *owe* you the help.  Again, I am stating this objectively, not to cause more problems.


The screen you seem to be getting immediately seems to be a login screen to me.  Enter your username and password and you'll be able to login.  If you don't remember it, which a refresh of the page told me, the easier option is to reinstall and remember the usernames and passwords.  That part where you typed in "mrt" or whatever is your computer's name.  So when it says "mrt login:" it's saying your're going to login to the computer named mrt.

---

### Post by Thewhistlingwind on 2011-05-28
> **.psd said:**
> 
Is that normal? Again, mrt is one of the names it asked me to input during install, but is there a way to list the users?

Use a live cd and look in the file /etc/passwd

From commandline it would be less /etc/passwd

---

### Post by lmn. on 2011-05-28
updates & upgrades are done after login, a frozen screen means something is wrong and it's unlikely there'l be a magic command to fix it.

reinstall, try the normal version instead of minimal. if your ISO is OK and there haven't been any changes to your system hardware-wise (mines buggered and won't reinstall regardless of ISO, version of linux, whatever), you'l have a normal install which, with a pinch of salt & a fair wind, will take you into your OS without any problems

---

### Post by linuxinstalledfromhdd on 2011-05-28
[QUOTE=bobbob1016;10874931

"@linuxfromhdd, wanna just tell me what to type at the login prompt instead of heckling so I can get this show on the road?", I'm just going to say this as an outside observer, no offense intended or meant, you, .psd, seem to be heckling the people who are offering you help.  Just keep in mind, that everyone here is taking time to help you, absolutely free, they don't have to, but they are choosing to.  Most people here are friendly, but don't like being treated like they *owe* you the help.  Again, I am stating this objectively, not to cause more problems..[/QUOTE]

Thanks. :)

---

### Post by .psd on 2011-05-28
Thanks bobbo. I apologize for my impatience everyone, and I'm honestly super thankful for all the legit responses.

To answer your question I'm doing minimal install because A) I thought it would be easier and B) strictly preference. It's actually pretty easy, I got through it without a tutorial I just don't know like the 5 magic words to type in at the end hahaha.

And Thanks Koraco that's really helpful. So if I'm getting gnome, is that a full package (desktop environment, window manager, file manager, terminal)?

@TheWhistlingWind, how?

---

### Post by Thewhistlingwind on 2011-05-28
> **.psd said:**
> 
@TheWhistlingWind, how?

Boot a live CD (If you don't have one I'm not sure how you determined ubuntu is bloated)

Mount your minimal install file system

From that root directory, go to etc, then open the passwd file and read it, thats a list of all users on the system.

Or, reinstall and remember the names.

---

### Post by bobbob1016 on 2011-05-28
> **.psd said:**
> To answer your question I'm doing minimal install because A) I thought it would be easier and B) strictly preference. It's actually pretty easy, I got through it without a tutorial I just don't know like the 5 magic words to type in at the end hahaha.

I'd say that the full install is *much* easier.  More so if you are just starting out and installing gnome anyways.  If you want to learn how to build a car, buy the frame, and add parts to learn.  If you want to just drive the car, buy from a dealer.  Minimal is building, normal install is the dealer.

Minimal lets you install only what you need, but until you find just what you need, you are probably going to be installing a lot of things by hand.  Just a warning.

---

### Post by .psd on 2011-05-28
@bobbo Oops I didn't mean I thought it would be easier than the regular install, just easier than it has proven to be (which isn't hard to be honest, forgetting my user name was my "fault" I guess).

Minimal install doesn't seem complicated at all, the tough part is finding the 5 or 6 magic words after the end of the install.

As for regular Ubuntu I used it for a week, hung out in the forums and learned a bit, got a lot of opinions, and like many new users I want to customize my experience. That's what Linux seems to be about, user choice.

Anyways it looks like I'm stranded until I know my login name so I'm going to re-minimal-install and take notes, and post back here. Sorry everyone :( and sincere thanks!

---

### Post by linuxinstalledfromhdd on 2011-05-28
One of my very favourite guides that worked for me was:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Or wouldn't this be the same thing? It's Ubuntu.. 

[http://www.techdrivein.com/2011/02/madbox-1010-review-ubuntu-based-openbox.html](http://www.techdrivein.com/2011/02/madbox-1010-review-ubuntu-based-openbox.html)

It's only 338.2Mb ISO in size. It doesn't get much smaller than that.
 [URL="http://download.tuxfamily.org/madbox/madbox-10.10/madbox-10.10.01-i386.iso"] 
[/URL]

---

### Post by Elfy on 2011-05-28
> **cariboo907 said:**
> Sorry forestpiskie, I guess we were both moderating this thread at the same time, I merged it with the other one, and then reopened it.

Your thread now - I'll be back next week :)

---

### Post by Elfy on 2011-05-28
> **.psd said:**
> Or you could just answer the question I don't think this thread was hurting anyone it's getting me closer to installing I've been stuck forever nobody needs you to close the thread go away.

EDIT: thanks for merging, that's what I was asking a mod to do in the other thread.

EDIT2: stressing lol. How has nobody asked this question before...

If you need staff help - then you need to use the report button - there's 40 so of us - 50000 or so of you and we do not read all the threads/posts 

> EDIT: thanks for merging, that's what I was asking a mod to do in the other thread.Report it.


> EDIT2: stressing lol. How has nobody asked this question before...I suspect they have - you;ve just not found it.

The search function here is not so good, once upon a time I used to point people tp uboontu, gone now - try googlubuntu - a great tool. My link I think. See you next week

---

### Post by Miljet on 2011-05-28
In the "mrt login: _" prompt that you seem so worried about, the mrt is simply the name that you gave to the computer during install and is not important at this point. All you need to do is enter your username, then your password. If you don't remember what username and/or password you assigned, it will be easier to start the install over from scratch. And this time, write down what names and passwords you assign.

---

