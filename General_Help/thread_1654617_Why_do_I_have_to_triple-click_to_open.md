---
title: "Why do I have to triple-click to open?"
date: 2010-12-28
forum: General Help
---

### Post by BuddyThirteen on 2010-12-28
I'm still a fairly recent convert, and I've been on Win for most of my computer life. So I hope you'll forgive me if my frame of reference is usually comparing to how things work in Windows. Yes, I know they're different, and not everything will be the same (that'd be pretty silly, wouldn't it).

One thing I really really liked when I switched over completely (as opposed to dual-boot, which I've done for years, but really just as a novelty, not to sit down and work), is that I can roll my mousewheel over any scrollable area and--guess what!--it scrolls. Ubuntu doesn't care if the particular area is selected. I love that. Windows is retarded when it comes to that. Even in the same file browser window, it won't scroll unless you first click in some empty space within the stupid file area of the window. How dumb is that?

Anyway, Ubuntu seems to go the opposite way for clicking, which I find rather annoying. What I mean is: When a file browser is open (or even the desktop) I have to triple-click to open most files and folders, because for some reason the first click activates the area, and then the double-click opens it. Why doesn't the double-click work as sensibly as scrolling? Sometimes it'll even do that when I swear I've already clicked within an area (which should activate it/focus it), and it won't open unless I triple-click.

Is this a bug? A feature? Just my computer? Everyone's computer? Is it supposed to be like that? Can I change this behavior?

---

### Post by SpadeIV on 2010-12-28
Forgive me if I sound rude, but maybe you're just clicking too slow? You could try to adjust your mouse-settings.

I tried what you said, and it worked for me to double click an unfocused object..

cheers

---

### Post by edhplus2 on 2010-12-28
In the file browser (nautilus), click on Edit, then Preferences. Choose the Behavior tab. In the first section, called Behavior, select the radio button for Single Click to Open Items. 

While you are there, you might also want to select the radio button for View executable text files when they are opened. Otherwise it will ask you every time. (nautilus seems to view most text files as executable, or at least the ones in dos format. Someone else might know more about this.)

Then click on Close to return to what you were doing.

You will need to do this if you do a fresh install of the next release  of Ubuntu, even if you back up and save your configuration files. Or  else I just haven't found where nautilus keeps its settings yet.

For some probably good reason, this will also change what happens when you click on a Desktop icon. I guess Gnome or Ubuntu or nautilus views the Desktop as a folder/directory in a file manager, which kind of makes sense.

(To start nautilus, click on your home folder on your desktop, or use Alt-F2 to run the application by name.)

I hope this is what you were asking about.

---

### Post by yetiman64 on 2010-12-28
> ....Is it supposed to be like that? Can I change this behavior? No its not supposed to be like that, I tend to agree with SpadeIV that you could have a timing issue. 

Go to System > Preferences > Mouse, and try adjusting the "Double-click timeout" setting to a longer timeout, hopefully this will help out.

My testing here is on 10.04 and I get the same result as SpadeIV on an unfocussed object (double click only required). I am assuming by user-profile details that SpadeIV tested on 10.10. Cheers and good luck.

---

### Post by tredegar on 2010-12-28
> I have to triple-click to open most files and folders, because for some reason the first click activates the area, and then the double-click opens it. Why doesn't the double-click work as sensibly as scrolling?
Scrolling un-raised windows is nice. It's a linux-thing.

As for triple-clicking, I think it is your mouse. I had a similar problem when the desktop wasn't responding correctly, and sometimes doing mad and very annoying things, but I have 3 (almost) identical installations of 10.04 and this fault was only on one, so I eventually tried swapping mice.

Problem solved.

Bad mouse > **/dev/recycling/bin** even though it was relatively "new".

Nothing wrong with linux, mouse was worn out.

---

