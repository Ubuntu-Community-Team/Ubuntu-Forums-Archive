---
title: "How do you change Xubuntu file manager and other program defaults?"
date: 2012-05-13
forum: General Help
---

### Post by Manmadegod on 2012-05-13
I want to replace the default file browser Thunar with Nautilus, but the  ability to change any program default (programs to launch by file type  as well) seems to be missing in the Settings Manager. I have already  downloaded Nautilus and it works in Xubuntu, and now I need a way to  make it the default so that when the system-installed Home and  file-system icons are clicked (as well as the launchers which I created  and was able to modify with "Nautilus Home" in the command line), files will be displayed through Nautilus, not Thunar.

When I went looking for a how-to, I found this, at 
[http://ubuntuforums.org/showthread.php?t=1081044](http://ubuntuforums.org/showthread.php?t=1081044)
**gksu gedit /usr/share/applications/nautilus-folder-handler.desktop**
Find the line that says: [B]Exec=thunar %U
[/B] change it to: [B]Exec=nautilus --no-desktop %U
[/B] 
The instructions which may have worked when this post went up in 2009 did not apparently apply when I tried it on current Xubuntu.  I cut and pasted that line into Terminal, just as it was called for, but there was no response to that command. 

Then I investigated, using gksu nautilus. I could not find under **/usr/share/applications**  any files by name similar to "folder-handler-desktop", and although I  have been using Nautilus, nothing of Nautilus could be seen in that  directory! I would be grateful if anyone can explain what happened here  with the Xubuntu file tree, as this seems like a relatively  straightforward tweak - if it can still be done in a different folder  somewhere, I'd like to have that option.

Upon taking a closer look at the items now contained in **/usr/share/applications**,  I saw what appears to be some of the items shown in "Settings Manager"  on the Xubuntu bottom panel, plus many which make me wonder why they  weren't included as part of this launcher. Very interesting, and I'd  like to know more about this too. Among these items I saw "Preferred  Applications", two of them actually, and one of them gave me the  opportunity to switch, under the Utilities tab, from Thunar to Nautilus  for the "Debian X Terminal Emulator". Problem is it doesn't work - the  default Place links on my Desktop (which are somehow differently set up  than the Launchers which I myself can make or delete) still use Thunar,  not Nautilus. Am I doing something wrong here?


Next, I found this idea, thought I would run it by you folks here:[URL="http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu"]
http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu[/URL]
Wow,  looks like I could really spin my wheels here, I could even install  more software just to get the right software to launch! What do the  gurus think of this?

Thanks.

---

### Post by Peripheral Visionary on 2012-05-13
I've got PCManFM set up as my default file manager in Xubu 12.04. Here's how:

First I installed PCManFM from Synaptic Package Manager.

Next I right-clicked my desktop, Applications -> Settings -> Settings Manager -> then clicked on Preferred Applications, then the Utilities tab (see screenshot) to select my new file manager default.

Done.

---

### Post by Manmadegod on 2012-05-13
> **Peripheral Visionary said:**
> I've got PCManFM set up as my default file manager in Xubu 12.04. Here's how:

First I installed PCManFM from Synaptic Package Manager.

Next I right-clicked my desktop, Applications -> Settings ->  Settings Manager -> then clicked on Preferred Applications, then the  Utilities tab (see screenshot) to select my new file manager default.

Done.


Well, thanks - it sort of worked, but not entirely. I did fail  to notice that the same launcher ("Settings Manager"), which I first  noticed under **/usr/share/applications**,is also installed on the  Xubuntu bottom panel by default, and is again accessible as you pointed  out by right-clicking the desktop. There's a mystery here that it didn't  work at all when I tried to use the launcher under the above path. When  accessed here, it knows that I have Nautilus and other file managers  installed, it allowed and saved the changes, but this had no impact on  my system behavior at all. When I tried your way (or the Xubuntu default  lanucher for these functions), this is where it gets weird - it changed  another type of launcher (blue folder icon, displays a menu for Home,  Documents, Downloads, etc) which was installed by the system on my  Xubuntu bar. A right click to Properties indicated that it is not  editable in the way ordinary launchers are, but there's a reference to a  "base directory". The popup window looks different from ordinary  launchers, but is also different from the two un-removable items  installed by the system on my desktop, for "File System" and "Home".  This menu launcher was changed so that it now launches with Nautilus  instead of Thunar, but the two unremovable desktop items remain the  same! What's up with this?

Another reason that I come back to the **/usr/shar/applications**  folder and the idea that it may contain or did contain editable files  for controlling links between files and applications is that most of  them are likely in the same folder, and the idea of substituting  "Nautilus" for Thunar references sounds like a straightforward failsafe.  Since I did not see the opportunity in "Preferred Applications" to  peruse file type associations, I may actually need to open up  application files if I want to change web browser, or change file type  associations for graphics, media and document files. Do you, or does  anybody know where these controlling files are now?

---

### Post by Bucky Ball on 2012-06-21
In a terminal:

```
locate nautilus
locate thunar
```

That should find editable files. The .desktop files can give a clue as to the where the rest are. 

/usr/share/applications doesn't really contain configurable files, just app launchers.

---

