---
title: "Lubuntu 11.10 - Can I add a Custom File Launcher to Panel?"
date: 2012-02-01
forum: General Help
---

### Post by 2CV67 on 2012-02-01
Hi!
Just today, I "downgraded" from Gnome Classic to Lubuntu (after previously "downgrading" from awful Unity) & am very pleased with both moves...
After only a couple of hours, I have nearly everything how I want it (took weeks in Classic & impossible in Unity).

Obviously, I don't expect "little" Lubuntu to do everything its big brothers can do (though experience to date suggests the opposite).
But I am still hoping that a couple of sticky points can be ironed out, with a little help.

One wish is to be able to pin FILE (document) Launchers to the top panel, which I could do easily in Gnome.
I added a top panel in Lubuntu & easily added all the APP launchers I wanted to it, with the very clear GUI for that.
I could easily make it autohide like a Unity Launcher, but don't want to.
I found this suggestion for creating custom APP launchers on desktop & that works very well:
[http://ubuntuforums.org/showpost.php?p=10134710&postcount=11](http://ubuntuforums.org/showpost.php?p=10134710&postcount=11)

But I can't figure out:
1. If/how it could launch a document (it only accepts executable files).
2. If/how it could be pinned to the panel.

I tried Googling, but Lubuntu does not figure much there (yet?), and this is a specific Lubuntu question.
I did read the whole of the astonishing Lubuntu - One Stop Thread ([http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)) & numerous links without finding an answer.

Thanks very much for any clues!

---

### Post by 2CV67 on 2012-02-02
I spent another several hours thrashing at this one - with no success so far.
I did find something encouraging here:
[http://wiki.lxde.org/en/LXShortCut](http://wiki.lxde.org/en/LXShortCut)
> LXShortcut is a small utility used to edit easily application shortcuts.
Opening files

You can create shortcuts that open specific files.

For example you can add the following in the "Command" box

xfw ./Documents/notes

This will open file "/home/user_name/Documents/notes", with the xfw text editor. Then you can add this shortcut on the panel, as well. 

That suggests:
1. You can use it to open files.
2. You can add it to panel.

I absolutely fail to see how to do either of those things.
All I can do with it is make a desktop shortcut for applications.

Is it possible to use LXShortcut to open, say a LibO Calc file?
Is it possible to pin a LXShortcut to a panel?
Is it possible to find any kind of help or manpage for LXShortcut?

Thanks!

---

### Post by 2CV67 on 2012-02-04
I made some progress on this, but would still not refuse any help offered!

I can now launch FILES from a desktop shortcut, under certain conditions.

1. I have to create the Shortcut with Terminal (or with Menu > Run) using "lxshortcut -o new.desktop".
2. Call it what I like, say "FO".
3. In "Command", put "xdg-open /<full path to file including extension>"
4. Drag & drop FO from home folder to desktop.
5. Double-click FO icon - and Voila! File opens.   :cool:

But it's not perfect yet.
Particularly it won't accept any spaces anywhere in the file path or file name.
Years ago, that would have been normal & I would not have had any spaces, but today I have spaces everywhere...

OK, I COULD replace all my spaces by dashes or whatever, but I don't really want to do that.

So I am now looking for suggestions on that problem (whilst searching diligently, of course).
And on methods for pinning to panel...

Thanks for any tips!

---

### Post by 2CV67 on 2012-02-04
OK! - I fixed the spaces problem.

Need to put quotes round <path to file>.

My example:
chris@Acer-desk:~$ xdg-open "/home/chris/Charts & Lists/Daily.ods"

Yipee!!

Now I just need to be able to pin it to the panel....

---

### Post by SteveDee on 2012-02-04
> **2CV67 said:**
> ...Now I just need to be able to pin it to the panel....

Well one way is to get it into the menu structure, because anything listed in menus can be added to the panel.

So you need a file called "Daily Charts.desktop" that looks something like this:-
[code]
[Desktop Entry]
Version=1.0
Name=Daily Charts
Comment=Chris's daily charts
Exec=xdg-open /home/chris/Charts & Lists/Daily.ods
Terminal=false
Type=Application
Categories=Utility;

[\code]
...and this needs to be saved in: /usr/share/applications
with Permissions:-
Owner = root
Group = root
Owner: read & write

Once you've establish that it is in your Accessories menu, you can right-click on the panel and add to the launch bar in the normal way.

---

### Post by 2CV67 on 2012-02-04
Thanks VERY much, SteveDee, for those instructions.
That looks very promising.

I made a file exactly as you suggested (copy/paste...) & I can see it sitting in /usr/share/applications, with permissions exactly as you said.

But so far, I can't get it to appear in the Accessories menu or any other menu...
Even after logout & reboot.

I tried Preferences > Main Menu > Applications > Accessories, but it does not show there yet.
From there, if I try "+New Item" I get an offer to Create a Launcher - is that the route? (I suspect not & have not tried that yet)

So I am sorry to have to admit I need another clue!

Thanks for your patience (I hope!).

---

### Post by SteveDee on 2012-02-04
> **2CV67 said:**
> ...I tried Preferences > Main Menu > Applications > Accessories, but it does not show there yet...

I don't recognise your menu path as Lubuntu. Did you convert from Ubuntu and end up with a Ubuntu/Lubuntu hybrid?

The standard Lubuntu menu structure is very flat with no menus nested within menus (see screen shot).

So the line:-
Categories=Utility;
...(yes, it does need the semi-colon) should automatically put this item within the Accessories menu.

---

### Post by 2CV67 on 2012-02-04
Yes, I "down graded" progressively from Unity to Gnome Classic to Lubuntu & I am happier & happier with that move.   :D

I have the same menu structure as you - see screenshot with:
1. Accessories menu (without Daily Charts...)
2. File Manager showing Daily Charts in /usr/share/applications
3. Content of Daily Charts.

The path I mentioned above is because in my Preferences Menu, I have an item called "Main Menu" which is a GUI for adjusting all the items in the main menu.
I didn't add it & don't know where it came from.
It works, except it doesn't see Daily Charts.

[ATTACH]212727[/ATTACH]

---

### Post by Theredbaron1834 on 2012-02-04
Lets see if I can help.

Fist off, LXpanel kinda sucks vs gnomepanel 2.x. Still better then 3.x, and a hella lot better then unity. I did the same thing you did when unity first came out. :)

So, when I needed to add a launcher to the panel, first  I "had" to use [lxmed]("http://sourceforge.net/projects/lxmed/"), as nothing else would work. It is a java based lxde menu editor. Just make your shortcut, and make sure the visible box is checked. Then it should show. 

So, did it help??? :)


O, and  the main menu editor you have is prob alacarte. It is the gnome menu editor. You can remove it if you don't use gnome.

---

### Post by 2CV67 on 2012-02-05
Thanks Guys - IT WORKS!   :D

This was the last hurdle to pass before finally deciding that Lubuntu was for me, so I feel happy now with my snappy clean new desktop & won't need to go back to Gnome, let alone Unity...

Actually, it still took me several hours of messing about before I got these launchers to work, but now it's easy, so I will write it down as a HOW TO: in case that can help anybody else (or in case I need to refer to it next time...).

I try to avoid downloading & installing stuff as I am such an admirer of Synapt, but I have not found any way to do this job without lxmed, so resorted to that & was pleased with the results.
It would be nice to see lxmed available via Synapt.
If anybody can show me a decent way without lxmed, I am still interested.

To repeat Theredbaron1834, you need to down load lxmed from
[http://sourceforge.net/projects/lxmed/](http://sourceforge.net/projects/lxmed/) 
& Unpack & install it.
I always get in a mess with that, so I won't try to explain how - you probably know better than me.

After that  :::::::>>>>>>>>>

**HOW TO: Add FILE Launchers to Lubuntu Top/Bottom Panel.**

1. Download & install lxmed (see above).
2. Look in Menu > Preferences for "Main Menu Editor" & click to open. You will need your admin password.
3. In MME, select "Accessories" if not already selected, then "+ New Item".
4. Add Name (this is what will show in Menus & when you mouse-over your icon).
5. For "Command:" Click "Browse" then navigate to the file you want to open. DON'T STOP YET.
6. At the beginning of the new Command line you just created, add "xdg-open " without quotes but with final space.
7. If the path you just created includes any other spaces, you will need to put quotes round the file path, after the space after xdg-open. (example: xdg-open "/home/chris/Charts & Lists/Daily.ods")
7. In Comment, whatever you might like, or nothing.
8. Icon: Browse to whatever icon you want, including any special ones you might have created. Note that this is a long & miserable business unless you know what you want. It it significantly easier if you also have Nautilus, where you can see a preview af all the icons in each folder, without having to click through them all... (better suggestions accepted!)
9. "OK" & Close.
10. Look in Menu  >  Accessories. You should find your new icon there. Click it to check it works OK there.
11. Right-click on Top or Bottom Panel  >  "Add/Remove Panel Items"  -  opens Panel Preferences.
12. Select Panel Applets tab.
13. If "Application Launch Bar" not present  >  "+ Add" > "Application Launch Bar"  >  "+ Add".
14. Application Launch Bar  >  Edit.
15. Available Applications  >  Expand "Accessories".
16. Select your new item by Name/Icon  >  "+ Add".
17. Look for your new item on the Panel.
18. Click it to check it works OK.
19. If you want to move it within the other Panel items  >  Select it  >  Use Up & Down Arrows to move left/right.
20. Close Panel windows & you are all done!
21. You have actually just created a new .desktop file which you can find in /usr/local/share/applications, unlike others which are in /usr/share/applications.

If anybody wants to correct/improve/simplify/elaborate this HowTo  -  feel free!

Thanks again for all the help, much appreciated!

---

### Post by 2CV67 on 2012-02-05
I marked this thread as [SOLVED] but then it lost the Lubuntu prefix, so I am marking it UNSOLVED to get Lubuntu back...

---

### Post by 2CV67 on 2013-01-16
I occasionally need to revise my Top/Bottom Panel File Launchers, to launch a different file (Accounts 2012 > Accounts 2013 in this case).

I somehow expected to be able to do that by right-clicking on the Icon & modifying 'Properties' or something.
But there does not seem to be a simple GUI method (is there?).
What I found to work was:
- Navigate to "/usr/local/share/applications"
- Open "Acounts 2012" in Leafpad AS ROOT.
- Change the line:   Exec=xdg-open "/home/chris/Finance/Accounts 2012.ods"  to "...2013.ods"
- Reboot

As ever, I would be only too pleased to hear of any better (GUI?) method!

---

