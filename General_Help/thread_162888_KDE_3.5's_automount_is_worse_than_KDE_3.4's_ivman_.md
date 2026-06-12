---
title: "KDE 3.5's automount is worse than KDE 3.4's ivman implementation"
date: 2006-04-19
forum: General Help
---

### Post by aysiu on 2006-04-19
So in KDE 3.4 on Breezy, *ivman* had this annoying behavior where you would pop in a CD and it would not only start playing but also open in Konqueror. [This tutorial](http://ubuntuforums.org/showthread.php?t=90457) made that a simple fix.

Now that I'm using Dapper Drake, it's KDE 3.5 (I think), and it isn't using *ivman* any more.

Thing is: how do I get it to do what I want--open a CD with *goobox* instead of *kaudiocreator*, for example?

Someone suggested

The file or folder / does not exist this > Don't you need to select > audio cd > add > audio cd then edit command to what ever you want to use and name it and pick a picto?

And then ti will give the window with a new option that you can use always our not if you select it. which appeared to work, but when I actually tried it, I got this error when I popped in a CD ```
The file or folder / does not exist
```

Is there some config file that I can edit? Why is this so weird and difficult? I love KDE, but this is one of the things Gnome has over it--easy configuration of removable media.

---

### Post by ComplexNumber on 2006-04-19
when you slip a cd into the drive, don't you get that dialogue that i told you about in the other thraed?

---

### Post by aysiu on 2006-04-19
[QUOTE=ComplexNumber]when you slip a cd into the drive, don't you get that dialogue that i told you about in the other thraed?[/QUOTE] Yes, it's in the left part of the first screenshot of my post.

Unfortunately, it gives you only so many options. When I use the most appropriate predefined option, it uses KAudioCreator. I want to use Goobox. When I try to make Goobox an option and actually use the option, it gives me that weird error.

---

### Post by ComplexNumber on 2006-04-19
>  Yes, it's in the left part of the first screenshot of my post. i wasn't referring to that. what i'm referring to looks nothing like that. when you pop in a cd, it bring up a dialogue that gives you the option to cancel, open, or configure. clicking on 'configure' brings up another dialogue which lists such things as 'audio cd', 'dvd', 'data cd', 'usb', etc totgether with the application thats used to open them (eg 'kscd <command>'). i've just tried it now on suse both in root and user. kde being the temperamental so'n'so that it is, it refused to respond. sometimes it does and sometimes it doesn't. it seems to have a mind of its own :confused:. anyway, thats what should happen. and that seem to be the only way to associate a command/application to a particular media. i've just had a look around kcontrol centre and the menu, and there isn't anything that allows me to do this manually. i'll try rebooting in a minute and see if it decides to work for me.

---

### Post by aysiu on 2006-04-19
[QUOTE=ComplexNumber]when you pop in a cd, it bring up a dialogue that gives you the option to cancel, open, or configure. clicking on 'configure' brings up another dialogue which lists such things as 'audio cd', 'dvd', 'data cd', 'usb', etc totgether with the application thats used to open them (eg 'kscd <command>').[/QUOTE] That's what I get. I have two screenshots attached to my first post.

The first screenshot has two images in it. The left image is the dialogue that pops up when I insert the CD. The right image is the dialogue that pops up when I click "configure."

If I use *goobox* as the command, I get the error in the second screenshot.

What you're describing is just what I get--only problem is that it doesn't appear to be working...

By the way, I appreciate your trying to help out.

---

### Post by ComplexNumber on 2006-04-19
it doesn't look anything like that in suse kde and fedora kde. i'll reboot and try and get the damn thing to work. then i'll get a screenshot to show you. i've never had those dialogues that you show on my kde.

---

### Post by ComplexNumber on 2006-04-19
*ok, i'm not in favour of double posting, but you'll probobly not know that i've updated my reply otherwise.*



EDIT: still doesn't work as it should. however, a possible workaround is to go to /media directory in konqueror. right click on 'dvd' (or 'cd'), then 'open with' -> 'other'. tick the 'remember application association for this type of file'. when you next slip a cd in, it will use that selected other application.

---

### Post by aysiu on 2006-04-19
So are you saying you're using Fedora and SuSE's KDE? Maybe it's a weird Kubuntu thing.

---

### Post by ComplexNumber on 2006-04-19
[quote=aysiu]So are you saying you're using Fedora and SuSE's KDE? Maybe it's a weird Kubuntu thing.[/quote] yes. i've never had kubuntu on my HD. i've had ubuntu just to see what all the fuss is about a few months back. because i have no internet conenction to my linux pc, ubuntu isn't much good for me becausde its so minimal with regards to the number of applications. i liked it, though. when i get wifi, maybe then. until then, fedora and suse are the best for me.

maybe it is a kubuntu thing because that functionality is on all the kde's that i've tried. i think i even remember it being on mandrake 2005 LE.
the workaround that i've given above will work for you.

---

### Post by claydoh on 2006-04-19
These steps worked for me:

I did this with no cd in my drive
go to  System Settings - Storage media

then, under Media Types, select "Audio CD", then click "Add'

You then type in your description in the dox under "Edit Service". and you can change the icon by clicking on the big red 'X', click "other icons" and scroll down to "goobox".
You also will need to move "Audio CD" from the left column over to the right, and enter "goobox %u" in the command box., click OK, then Apply. I did get an error about kded crashing but nothing visibly was wrong.

Now I have the goobox option working for me, though I do not see how to get it to automatically rip the tracks as there don't seem to be any cli options for that in the man pages

---

### Post by aysiu on 2006-04-19
[QUOTE=claydoh]
You then type in your description in the dox under "Edit Service". and you can change the icon by clicking on the big red 'X', click "other icons" and scroll down to "goobox".
You also will need to move "Audio CD" from the left column over to the right, and enter "goobox %u" in the command box., click OK, then Apply. I did get an error about kded crashing but nothing visibly was wrong.[/QUOTE] That did it! I did that before and got the error with just ```
goobox
``` but when I did ```
goobox %u
``` it worked. How would I have known to put the %u there? What does %u mean, anyway?

---

### Post by ComplexNumber on 2006-04-19
the u% means load the media into it, effectively. 'kscd' on its own (ie without %u) would just bring up the kscd player and it would just sit there not doing anything. the u% would pass the media as an argument to the application.
btw did you try the workaround that i suggested? just curious.

---

### Post by aysiu on 2006-04-19
[QUOTE=ComplexNumber]the u% means load the media into it, effectively. 'kscd' on its own (ie without %u) would just bring up the kscd player and it would just sit there not doing anything. the u% would pass the media as an argument to the application.[/quote] Thanks. So, basically any player I associate with an action should have the %u attached to it, then. > btw did you try the workaround that i suggested? just curious. I'll try that workaround, too, if I run into further problems. If it works, I'll post back in this thread.

---

### Post by ComplexNumber on 2006-04-19
> So, basically any player I associate with an action should have the %u attached to it, then.well,  the application almost always has a "u%" after it. if the u% is omitted, the player just sits there and does nothing when a cd/dvd is inserted

---

### Post by awakatanka on 2006-04-20
If you open system settings with sudo our root, you can edit the standard entry's our delete them.( I'm in mepis didn't check in kubuntu atm). only 2 options that stay are open window and do nothing.

Audio cd entry with play cd gives the following entry in command : kscd -s -caption "%c" %i %m %u 

It looks like you need %command for somethings. But it solved i see.

---

### Post by Jose Catre-Vandis on 2006-06-03
Can anyone advise how you do this adjustment for Ubuntu. I need a player application, e.g. Xmms or VLC to play my audio CD's as opposed to Sound Juicer! The KDE solution just doesn't seem to be here in Dapper?

---

