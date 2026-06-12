---
title: "NetBook Remix -- Can I use multiple desktops?"
date: 2009-10-08
forum: General Help
---

### Post by ohiomoto on 2009-10-08
Edit:  This thread is relevant to 9.04.

There is another thread for 9.10:
[http://ubuntuforums.org/showthread.php?t=1345974](http://ubuntuforums.org/showthread.php?t=1345974)

---------------------------------------------------------------------------------------------------------------------

I've been using Ubuntu Netbook Remix on my Acer AS1410 and Dell Vostro 1400 and love it.  I'm not one to keep a bunch of junk on my desktop so I think using that space as a menu is great.  Plus it's a nice change of pace from the standard desktop.

So far, the only thing I feel like I'm missing is the ability to use multiple desktops.  I like to keep my workspaces separate.  I might use one space for personal web browsing and my music player, another for development and maybe another for some course work I'm doing.  I often have multiple browsers open and maybe two different Eclipse IDEs running at the same time and I would like to be able to do that with remix mainly as a way to keep the programs separated.  

Anyone else out there try this? Any ideas?

Thanks

EDIT:  My solution is in post #4.

---

### Post by Chronon on 2009-10-08
You can.  I use two desktops with my Eee PC 1000HEB.  I find it a convenient way to switch between maximized programs.

---

### Post by ohiomoto on 2009-10-08
Great...how do you do it?

---

### Post by ohiomoto on 2009-10-09
Alright, found a way to do it.  

From UNR:
1) Preferences> Switch Desktop Mode>
2) Select "Classic Desktop" > Apply
From Classic Desktop:
3) Right click the Workspace Switcher in the lower right corner and open the Preferences.  
4) Set the desired "Number of workspaces" to whatever you like.
5) System> Preferences> Switch Desktop Mode>
6) Select "Ubuntu Remix Desktop" > Apply
Now your back in UNR.

Here's how it works.  It's a little different than the classic desktop in the sense that a) there is no Workspace Switcher and b) all of your open applications are still listed in the Window Picker in the upper left corner. 

For example, if you have two instances of FireFox open on two different workspaces, they will both be displayed in the Window Picker and you can click on either one to display that instance.  But if you press Alt+Tab, it will only cycle through the applications in that particular workspace.  

To switch workspaces, you can either click on an application in that resides in that workspace or use Ctrl+Alt+ Right or Left Arrow.  Once in that workspace, you can cycle through the applications in the workspace using Alt+Tab.

This is pretty cool because you can organize your workspaces.  I like this because I might be working on a project and want to Alt+Tab between my IDE, a command line terminal, and Firefox for testing.  I don't want my music player, Solitaire and the Firefox that I opened to get email getting in my way, so I keep those on another workspace.  

Being able to do this in Remix makes me very happy. :)

---

### Post by ohiomoto on 2009-10-09
Also, please feel free to add any other ideas or solutions to this thread.

---

### Post by Chronon on 2009-10-09
Sorry, I was away for a bit.  I'm glad you got it figured out.

I use the classic desktop with only the top panel.  I have taken to launching most things with the Alt+F2 dialog and switch desktops with the key combo you mentioned.

---

### Post by ohiomoto on 2009-10-09
> **Chronon said:**
> I have taken to launching most things with the Alt+F2 dialog...
Nice, I didn't know about that one.

---

### Post by fyo on 2010-02-22
The multiple-desktops solution no longer works as described for the 9.10 version of Ubuntu Notebook Remix.

If you want multiple desktops without changing anything else, the easiest way is to start gconf-editor and change the value for /apps/metacity/general/num_workspaces to however many you want. ctrl-alt-right/left works to switch between them, as usual.

If you don't want to have icons for windows on other desktops shown in the panel, uncheck /apps/panel/applets/applet_1/prefs/show_all_windows.

Both changes can also be made from the command line using:

gconftool -s -t TYPE PATH VALUE

(type is boolean and value false for the second one)

---

### Post by ohiomoto on 2010-02-22
> **fyo said:**
> The multiple-desktops solution no longer works as described for the 9.10 version of Ubuntu Notebook Remix.

If you want multiple desktops without changing anything else, the easiest way is to start gconf-editor and change the value for /apps/metacity/general/num_workspaces to however many you want. ctrl-alt-right/left works to switch between them, as usual.

If you don't want to have icons for windows on other desktops shown in the panel, uncheck /apps/panel/applets/applet_1/prefs/show_all_windows.

Both changes can also be made from the command line using:

gconftool -s -t TYPE PATH VALUE

(type is boolean and value false for the second one)Yes, this thread is relevant to 9.04.

There is another thread for 9.10:
[http://ubuntuforums.org/showthread.php?t=1345974](http://ubuntuforums.org/showthread.php?t=1345974)

---

### Post by fyo on 2010-02-23
> **ohiomoto said:**
> Yes, this thread is relevant to 9.04.

There is another thread for 9.10:
[http://ubuntuforums.org/showthread.php?t=1345974](http://ubuntuforums.org/showthread.php?t=1345974)

Which is nice -- especially now that there's a link to it from this thread. When a solution is depreciated, it's useful to have a link to the new one.

The problem is one of search engines. Even including "9.10" in the search terms returns THIS thread (or at least did at the time of my original posting) and not the other thread. Hopefully, the link from this thread to the other will boost the other's google ranking...

Just tried googling again and the other thread isn't in the top 30 (at which point I gave up). A solution isn't worth much if it cannot be (or isn't) found.

The problem is that the forum encourages people to indicate in their profile what Ubuntu version they are running and updates to this are propagated to all their messages thus leading search engines to "believe" that they are about 9.10.

---

### Post by ohiomoto on 2010-02-24
I actually forgot this thread even existed, but you raise a good point.  I'll put the link in the OP in case anyone else runs across this thread.

---

