---
title: "JezzBall for Gnome?"
date: 2006-01-20
forum: General Help
---

### Post by RoninGurl on 2006-01-20
Is there a well made JezzBall clone for Gnome? I totally miss JezzBall when I am not running Windows. I need my Windows Entertainment Pack, even if it's a clone of the games. :p I need it. So if anyone knows a good alternative to these, or maybe a proven way to run these games within Linux, please let me know. I know there is the WINE project for running windows applications in Linux but I am unsure if it will support JezzBall or the other windows entertainment pack games. And if so, will it support my custom InnoSetup installer for it. I still have the original install discs and the games directory, etc... but I was just curious if I could run my installer through WINE and if so, how.

Thank you ahead of time.

**Edit: ** I'm sorry. That's the second time I have put a game related topic here instead of Gnome gaming. I'll put it in Gaming next time. I just wanted to get the post out of my mind before I got sidetracked again by something that needed done.

---

### Post by Qrk on 2006-01-20
There is kbounce, its in the repositories. It isn't Gnome but runs fine in Gnome.

As for wine, I'd just try it to find out. Its hit and miss. I've run things I never thought I could and have had hang ups on things like notepad.

---

### Post by RoninGurl on 2006-01-21
[QUOTE=Qrk]There is kbounce, its in the repositories. It isn't Gnome but runs fine in Gnome.

As for wine, I'd just try it to find out. Its hit and miss. I've run things I never thought I could and have had hang ups on things like notepad.[/QUOTE]
I found a game called IceBreaker in the software system thingy. I cant remember the name off hand. I think it is Synaptic or something like that. I installed IceBreaker from that and it did not add an icon into the Applications --> Games menu. It was really a pain in the ass for a first time Linux user to try and locate the install directory and make a shortcut with the proper icon for IceBreaker. I wound up looking at the properties to an already installed game in the games menu and copied the location to Icebreaker and changed "Klotski" to "icebreaker" and it seems to have worked. But I dislike it not adding itself. It&#8217;s not cool.

I haven't tried KBounce. I have Gnome installed and I thought if I installed any KDE applications (and to my knowledge with their stupid naming scheme of adding that K to everything) you need KDE libraries, like all of them installed to even play KBounce. I never liked KDE. It&#8217;s unnecessarily complex. Gnome was always easier. I'd prefer not to install KDE if for no other reason than to keep the system as simple as possible and avoid conflicts. Besides, I doubt if I removed KBounce that it would remove KDE. 

I know nothing about WINE so I couldn't even begin to use it. That is why I was asking for help. If WINE is so unstable that it can't even run WordPad than I won't even bother with it. I doubt it would run classic applications like the Windows Entertainment pack build pre-windows 95 days if it cant even run WordPad. I'm new to Linux and anything that breaks Linux is bad. Bad. Bad. Bad. Bad. Bad. Bad. Have I said it was bad?

---

### Post by RoninGurl on 2006-01-21
Anyone?

---

### Post by ap0ll0 on 2006-01-21
[QUOTE=RoninGurl]I found a game called IceBreaker in the software system thingy. I cant remember the name off hand. I think it is Synaptic or something like that. I installed IceBreaker from that and it did not add an icon into the Applications --> Games menu. It was really a pain in the ass for a first time Linux user to try and locate the install directory and make a shortcut with the proper icon for IceBreaker. I wound up looking at the properties to an already installed game in the games menu and copied the location to Icebreaker and changed "Klotski" to "icebreaker" and it seems to have worked. But I dislike it not adding itself. It’s not cool.

I haven't tried KBounce. I have Gnome installed and I thought if I installed any KDE applications (and to my knowledge with their stupid naming scheme of adding that K to everything) you need KDE libraries, like all of them installed to even play KBounce. I never liked KDE. It’s unnecessarily complex. Gnome was always easier. I'd prefer not to install KDE if for no other reason than to keep the system as simple as possible and avoid conflicts. Besides, I doubt if I removed KBounce that it would remove KDE. 

I know nothing about WINE so I couldn't even begin to use it. That is why I was asking for help. If WINE is so unstable that it can't even run WordPad than I won't even bother with it. I doubt it would run classic applications like the Windows Entertainment pack build pre-windows 95 days if it cant even run WordPad. I'm new to Linux and anything that breaks Linux is bad. Bad. Bad. Bad. Bad. Bad. Bad. Have I said it was bad?[/QUOTE]

  First, most distros are bad about adding stuff. When I install stuff like Limewire, XMMS, or what have you it won't add an icon on the desktop, or menu. However when you open the terminal and type in the name of the binary of the program (usually the name of the program ex. Limewire is brought up by entering limewire) and it will run. I usually just right click the desktop and create an Icon that runs the command for the program, and if you really want to, there should be a program for editing the menus of the Kstart menu, and you can add it there. Some of this is complicated and I can't tell you alot more off hand. The libraries shouldn't be a problem unless you have to go out, find them on the net, and install each one, like I have done in the past with Mandrake. Synaptic should take care of it. Oh, yes, let me clear up the thing about wine. It isnt "unstable" for say, but some programs won't run quite right SOMETIMES. Older programs USUALLY have more success, but not always. I would try it, since its not real hard. Its not unstable as in the sense it will "harm" linux but emulation is bad. If wine fails you could buy cedega and atempt to use it to run "Windows Entertainment pack" or you could look for a clone. I am not an expert on this but I hope this helps.

---

### Post by NMUrugbysteve on 2006-01-21
If this windows entertainment pack is the one i'm thinking of, "Best of Entertainment". Then it should work with wine without any modifications. i've played jezzball on my computer with it.

---

### Post by NMUrugbysteve on 2006-01-21
sorry, double post.

---

### Post by RoninGurl on 2006-01-22
[QUOTE=NMUrugbysteve]If this windows entertainment pack is the one i'm thinking of, "Best of Entertainment". Then it should work with wine without any modifications. i've played jezzball on my computer with it.[/QUOTE]
Well, Wine runs the installer fine, but there is no indication of the installed files after the fact. I try to run "Wine Jezzball" and it doesn't work. I tried installing xwine for the GUI to see if maybe Jezzball was listed there and it wasn’t, plus xwine has a certain talent for crashing unexpectedly so I uninstalled xwine and left wine itself installed. It’s quite a pain in the ass. It really, truly is. As for the WEP edition -- no, it’s not Best of Windows Entertainment Pack, its Windows Entertainment Pack one through four wrapped into a custom InnoSetup install package. It installs itself perfectly under wine except for the aforementioned problems. Now, you say you’ve run Jezzball fine. Does that mean you simply have the executable to it in a folder and run it manually by going to it in command prompt and then doing “wine Jezzball?”

---

### Post by NMUrugbysteve on 2006-01-22
[QUOTE=RoninGurl] Does that mean you simply have the executable to it in a folder and run it manually by going to it in command prompt and then doing “wine Jezzball?”[/QUOTE]

Yeah, that's exactly what I did, I just made a folder and copied all the programs into it. It may work differently with the actual install disks, but I lost those years ago and have been transferring the files between my computers for a long time.

---

### Post by RoninGurl on 2006-01-23
Alright well I finally got it working but I am having issues with RAM leaks and slowness. The wine server is taking between 2.4 and 3 gigabytes of RAM and swap space at any given time when I am running say Chips Challenge or Jezzball. is there a way to make Wine run with a hard limit on the resources it is allowed to consume?

---

