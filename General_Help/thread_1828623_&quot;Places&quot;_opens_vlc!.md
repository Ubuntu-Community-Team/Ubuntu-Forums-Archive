---
title: "&quot;Places&quot; opens vlc!"
date: 2011-08-19
forum: General Help
---

### Post by peragrate72 on 2011-08-19
Hi all,

Having a weird problem here. When I try to open a location via places vlc opens and tells me it can't open the location.

If I try to open my home folder through places, this happens...

?

---

### Post by dino99 on 2011-08-19
either a custom symlink or nautilus prefs (open with)

sudo apt-get remove --purge vlc

then 

sudo apt-get install vlc

---

### Post by peragrate72 on 2011-08-19
OK. Trying it now...

- sudo apt-get remove --purge vlc -y
- sudo apt-get autoremove -y
- sudo apt-get update -y
- sudo apt-get install vlc -y

test of places: Failed.

OK. That didn't work. But it was good typing practice. :)

Update: I've gone through the entire control panel, but can't find anything. I used to have a config editor in my system tools, but I can't remember its name and it's not installed.  I also looked through Ubuntu Tweak.

---

### Post by plucky on 2011-08-19
It is probably File Association.

Type ALT+F2 and in the window that opens type **nautilus**.

When the File Browser opens,right click on any folder and select **Open with Other Application** and then select **File Browser** and select **Open**.

Test if the Places menu now works.

Good Luck

---

### Post by peragrate72 on 2011-08-19
I thought it was file association too, but I can't find anything. I got as far as:

> **plucky said:**
> ...and then select **File Browser**...

There's no file browser listed. Nautilus is listed, but it only opens the folder I right-clicked on that one time. It has no effect on the Places menu opening vlc.

I'm going to uninstall vlc, and then try Places again... see what happens.

---

### Post by peragrate72 on 2011-08-19
That fixed it. Completely and utterly removing vlc through synaptic did the job. Now to install it again and see what happens...

That's so weird. When VLC is not installed the Places menu functions normally.

As soon as I install VLC everything in the Places menu is opened with VLC.

---

### Post by dino99 on 2011-08-19
into /home, rename:

.local -> .localold
.gconf -> .gconfold
.config > .configold

then reboot

---

### Post by flipper T on 2011-08-19
Should be a simple enough fix~

Go to your "Places" menu, and open up "Computer"
Go into your "file system" , find the "Home" folder, 
and right click it,
then choose "Open with other application". 

When the list of applications comes up, 
Scroll down to "Open Folder", Select it, 
and at the bottom of the window, you'll see a check box, that says "remember this application for file folders".
(make sure it's checked)

Then simply click the "open" button at the bottom right,
and now whenever you open a folder..
it should open correctly. 

[courtesy of Rasa 1111]

---

### Post by peragrate72 on 2011-08-21
That's Tipper T, but that didn't work. I've tried that a few times, but I tried again to make sure. And dino99, thank you, but I can't find those files in my file system and they're definitely not in my home folder...

Thanks for the idea's everyone... keep thinking because I have absolutely no idea...

---

### Post by peragrate72 on 2011-08-21
That's Tipper T, but that didn't work. I've tried that a few times, but I tried again to make sure. And dino99, thank you, but I can't find those files in my file system and they're definitely not in my home folder...

Thanks for the idea's everyone... keep thinking because I have absolutely no idea...

...I'm going to reinstall nautilus and see if that helps...

---

### Post by mc4man on 2011-08-21
Open up your home folder > view - show hidden files
Browse to .local > share > applications and delete mimeapps.list

---

### Post by spiky001 on 2011-08-21
The folders Dino mention are hidden, Press Ctrl+H

---

### Post by peragrate72 on 2011-08-21
That's Tipper T, but that didn't work. I've tried that a few times, but I tried again to make sure. And dino99, thank you, but I can't find those files in my file system and they're definitely not in my home folder...

Thanks for the idea's everyone... keep thinking because I have absolutely no idea...

...I'm going to reinstall nautilus and see if that helps... nope...

---

### Post by mc4man on 2011-08-21
> **peragrate72 said:**
> That's Tipper T, but that didn't work. I've tried that a few times, but I tried again to make sure. And dino99, thank you, but I can't find those files in my file system and they're definitely not in my home folder...

Thanks for the idea's everyone... keep thinking because I have absolutely no idea...

...I'm going to reinstall nautilus and see if that helps... nope...
The issue you're having is almost always from having the wrong default set for inode/directory= in mimeapp.list
What does this show (if blank then close without saving
And what release of ubuntu are you using?
```

gedit ~/.local/share/applications/mimeapps.list
```

---

### Post by coffeecat on 2011-08-21
> **peragrate72 said:**
> That's Tipper T, but that didn't work.

@peragrate72, flipper T's instructions should work with one correction:

> **flipper T said:**
> Go to your "Places" menu, and open up "Computer"
Go into your "file system" , find the "Home" folder, 
and right click it,
then choose "Open with other application". 

When the list of applications comes up, 
Scroll down to "[COLOR="Red"]Open Folder[/COLOR]", Select it, 
and at the bottom of the window, you'll see a check box, that says "remember this application for file folders".
(make sure it's checked)

Then simply click the "open" button at the bottom right,
and now whenever you open a folder..
it should open correctly. 

Substitute "File Browser" when you scroll down for "Open Folder". That will re-associate folders with Nautilus.

---

### Post by mc4man on 2011-08-21
> **coffeecat said:**
> @peragrate72, flipper T's instructions should work with one correction:

Substitute "File Browser" when you scroll down for "Open Folder". That will re-associate folders with Nautilus.

If the OP is using 10.04 there is a possibility that vlc.desktop is at the front of the inode/directory= line and consequently is the default
Due to an ill-advised update to nautilus in 10.04 that can only be changed directly by editing (or by removing the line itself, editing is preferred in the long run


No sense going thru here - bug on this
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/805753](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/805753)

---

### Post by peragrate72 on 2011-08-23
The saga continues...

In additon to VLC opening up locations as if it were a file manager, a bunch of file associates have disappeared in the last few days.

For example, when I right click on a folder to zip it file roller isn't used. If I click on a pdf Adobe Reader is no longer available as a selection (I can get to it by selecting other application - but the change isn't permanent even if I check the always use box).

A few times I've had to restart because all of a sudden all applications would not open. The menus kept working, but nothing would start.

There's a ghost in my machine... can anyone help me find it?

Thanks

---

### Post by jonnyboysmithy on 2011-09-27
Hi guys,
 I'm having exactly the same issue here, I'm using ubuntu 11.10 atm
Do I just mark the bug as 'this affects me too' and confirm it?? 
Im rather new you see..

---

### Post by peragrate72 on 2011-09-28
Well. I gave up finding a solution and reinstalled. My data is on a seperate partition, so aside from setting up my apps again, that's the only way I could fix this problem.

Sorry for the long delay.

---

### Post by rockney on 2011-10-17
SOLUTION -- Do this:

 1) Goto Applications, Accessories, Text Editor.

 2) Then File, Open and click the pencil so you see the Location line.

 3) In the Location line type:
        .local/share/applications/mimeapps.list
    And don't miss the leading period.

 4) Under  [Added Associations]  make sure it looks like this:
        inode/directory=nautilus-folder-handler.desktop

 5) Under  [Default Applications] make sure it looks like this:
        inode/directory=nautilus-folder-handler.desktop

 6) File, Save

You shouldn't even need to logout or reboot. It should just work.

Note 22 Oct 2011 - It seems this solution is working for others.

---

### Post by jonnyboysmithy on 2011-10-18
Thanks! 
Your workaround is very helpful:D

---

### Post by ah pook on 2011-10-22
thankyouthankyouthankyou! I've been stuck for three days trying to fix that by myself. 

I get stubborn sometimes....

---

