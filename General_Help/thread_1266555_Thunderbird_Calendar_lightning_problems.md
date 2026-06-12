---
title: "Thunderbird Calendar lightning problems"
date: 2009-09-14
forum: General Help
---

### Post by scrambledarthur on 2009-09-14
Hello all.

Does anyone know how to do anything with the calendar from Lightning?

I downloaded and installed Thunderbird no problem, transferred account setting from Kmail without a hitch, but the calendar setting is proving to be troublesome.

I can't create new events or import existing calendars from anywhwere. When I mouse over the option, the option is blacked out. I installed both the lightning app. and the thunderbird app from add/remove, so I don't see what could be the trouble. Help!

---

### Post by quixote on 2009-09-16
Installing Thunderbird from add-remove should be fine.  The way I usually install add-ons, though, is this:  

download the .xpi file to a directory, eg /home/arthur.
In Thunderbird, go to Tools > addons.
Click the Install button in the lower left under the Extensions tab.
A window opens that allows you to browse to the .xpi file you want to install.

I'd say uninstall Lightning in add-remove, and then try installing using this method, and see whether that works any better.

Also, adding new events: I usually right-click on the date, and a context menu pops up.  I take it that doesn't work for you?

---

### Post by scrambledarthur on 2009-09-16
No, it doesn't.

I want to uninstall Lightning from add/remove, but in order to do that I have to uninstall thunderbird, and I'm afraid that all my settings will be wiped out!

Does it carry over even if I uninstall the program?

---

### Post by quixote on 2009-09-16
I use Synaptic (System > Administration > Synaptic) instead of add/remove, so I'm not certain you get the same options in the latter.  In Synaptic you have two choices for removal: "mark for removal" and "mark for complete removal".  Complete removal gets rid of all your settings (which is useful if they're what's corrupted), and plain removal does not.

Your settings are stored in your home folder.  One way to be really sure nothing touches them is to copy the relevant folder to another name: ```
cp /home/your-home-name/.mozilla-thunderbird /home/your-home-name/thunderbird-settings-backup
```Then you can copy it back to .mozilla-thunderbird if it turns out your settings have been removed.

---

### Post by scrambledarthur on 2009-09-16
Update:

Thanks a bunch for helping, but the problem still arises.

I tried removing it via the synaptic package manager, downloading the .xpi, and installing it manually, but it's still the same problem: the "add new event" areas of the menu and right click menu are both grayed out.

Hmm. Any ideas?

---

### Post by winotree on 2009-09-16
Is it also downloading a *googleizer*?  If so, would this remedy it?  [http://forums.mozillazine.org/viewtopic.php?f=46&t=1372035](http://forums.mozillazine.org/viewtopic.php?f=46&t=1372035)  ;)

---

### Post by scrambledarthur on 2009-09-16
> **winotree said:**
> Is it also downloading a *googleizer*?  If so, would this remedy it?  [http://forums.mozillazine.org/viewtopic.php?f=46&t=1372035](http://forums.mozillazine.org/viewtopic.php?f=46&t=1372035)  ;)

Thanks for your reply. Well, the problem is that I can't get ANY kind of event going, not one from a yahoo calendar, not one from a google calendar, and not even one from Lightning. All the events are just grayed out.

---

### Post by winotree on 2009-09-16
Sorry.  :(

---

### Post by The Recorder on 2009-09-16
On the left hand side of the screen, right-click on your calendar (default, Google, whatever...), and go to properties.  If the calendar is checked for "read-only", uncheck it...  Hope this solves your problem.

---

### Post by scrambledarthur on 2009-09-16
> **The Recorder said:**
> On the left hand side of the screen, right-click on your calendar (default, Google, whatever...), and go to properties.  If the calendar is checked for "read-only", uncheck it...  Hope this solves your problem.

I tried it, but there's not even a default calendar to click. When I click on the empty space, the "New calendar" option is predictably grayed out.

Thanks, but any other ideas?

---

### Post by The Recorder on 2009-09-16
Still seems like a permission problem - Things are working, but you are not permitted to access or change things.  Try looking at the permissions of the files themselves, in your home directory.  Make sure that you have "write" permission on all the files in your "mozilla-thunderbird" directry.

---

### Post by scrambledarthur on 2009-09-21
> **The Recorder said:**
> Still seems like a permission problem - Things are working, but you are not permitted to access or change things.  Try looking at the permissions of the files themselves, in your home directory.  Make sure that you have "write" permission on all the files in your "mozilla-thunderbird" directry.

And how would I do that?

---

### Post by The Recorder on 2009-09-21
I will assume that you are using ubuntu, so open up nautilus as root (Alt-F2 - gksu nautilus).  Go to your home directory, and then right-click on your mozilla-thunderbird directory and click on "Properties, and then on "Permissions".  Make sure that "Owner" and Group" are you, the three (3) "Folder access" entries are "Create and delete files", and that the three (3) "File access" entries are "Read and write". (If someone else uses your computer, and you don't want to take the chance that he, she or they might change things in this directory, only change the three (3) "Owner" entries, and the "Group" "name".)  Then (at the bottom of this tab) click on "Apply Permissions to Enclosed Files", and then close.  Then go into the mozilla-thunderbird directory and make sure that the changes have been made to all contained file folders and their file and folders - If not, you will have to make the necessary changes on an individual basis.

Good luck!

---

### Post by scrambledarthur on 2009-09-21
> **The Recorder said:**
> I will assume that you are using ubuntu, so open up nautilus as root (Alt-F2 - gksu nautilus).  Go to your home directory, and then right-click on your mozilla-thunderbird directory and click on "Properties, and then on "Permissions".  Make sure that "Owner" and Group" are you, the three (3) "Folder access" entries are "Create and delete files", and that the three (3) "File access" entries are "Read and write". (If someone else uses your computer, and you don't want to take the chance that he, she or they might change things in this directory, only change the three (3) "Owner" entries, and the "Group" "name".)  Then (at the bottom of this tab) click on "Apply Permissions to Enclosed Files", and then close.  Then go into the mozilla-thunderbird directory and make sure that the changes have been made to all contained file folders and their file and folders - If not, you will have to make the necessary changes on an individual basis.

Good luck!
Yeah, I am using ubuntu.

WhenI type in gksu nautilus, I just see a blank window with the desktop icon. In the desktop icon, however, there's nothing. I tried going to the folder labeled "home", but it just showed personal docs, like music, pictures, etc...

am I doing something wrong?

---

### Post by The Recorder on 2009-09-21
There should be a folder under /home that was set up when you installed ubuntu; usually named whatever your user name is.  This is where the "mozilla-thunderbird" directory should be.

However, if you did an Alt-F2, typed in "gksu nautilus" in the "Run program" box. and got a "blank window" after you clicked on "Run", then perhaps there is something wrong with your installation.

---

### Post by quixote on 2009-09-21
The files in question are hidden, so when you have that window with nothing but the desktop icon, try hitting ctrl-h to show hidden files.  A whole mass of directories and files that start with "." should show up.  (The . is what makes them hidden.)  (If there's still nothing, then there's a big problem with the install, and the smartest thing would be to get the data you need and then reinstall.)

.mozilla-thunderbird is what you're looking for.  Under that will be a directory with some random letters and numbers followed by (probably) .default.  Unless you specifically made another profile, that'll be where your mail, extensions, and suchlike should be. 

To see permissions, it's easier to go to "list" view, and under View > visible columns, make sure Permissions is checked.  Possibly move them up the list to make them easier to see.  Then you can just scan down the whole lot.  The other way is to right-click an individual entry and go to the "properties" tab.

It may be that somehow the directories lost their "execute" permission, which makes them inaccessible.  Most directory permissions will look more or less like this: -rwxr-x-r-x.  The X's show that there is execute permission, and the directories for lightning should have that.  Lightning itself may be hard to find because I believe it's under extensions but the name is just one of those long strings of gobbledygook.  You have to look inside the dirs, maybe look at files in a text editor, and try to find something that says "lightning".  Or maybe someone else has a more elegant method? :)

---

### Post by jmkemp on 2009-09-24
I've got the same problem, Mozilla Thunderbird version 2.0.0.23 (20090817); Lightning 0.9; Provider for Google 0.5.4 running on the UNR 9.04 on an Acer Aspire One D150. 

Read a few threads and tried several things, including setting all the files in the extension folder to be executable (on the command line with the following code:
```
chmod -vR +x *
```
(obviously you don't need the 'v' but if gives the confidence that permissions have been changed without needing to do ```
ls -all
```

The problem as it manifests itself for me is that the extension is obviously installed, but there is no default calendar created as part of the installation, nor can I create a new calendar. On the File > New >.. menu the 'Calendar' option is there but greyed out. On the toolbar when I click on the 'Calendar' tab button in the bottom left pane all the 'New X' options are also greyed out. 

Anyone else got ideas, even if to say which versions you are on if it works.

---

### Post by quixote on 2009-09-24
I have the same versions of Tbird, GProvider & Lightning, and they work.  I'm running on regular Jaunty, though, not Netbook Remix.  There's no logical reason, though, why that should make a difference.  It's got to be something about the way it installed.  ??

---

### Post by ld.4lpha on 2009-09-30
Forgive me if I missed this already in the thread...didn't read EVERY post.

Try this:

1) Uninstall Lightning
2) ```
sudo apt-get install libstdc++5
```3) Install Lightning

Hope that helps.

LD

---

### Post by scrambledarthur on 2009-10-01
> **ld.4lpha said:**
> Forgive me if I missed this already in the thread...didn't read EVERY post.

Try this:

1) Uninstall Lightning
2) ```
sudo apt-get install libstdc++5
```3) Install Lightning

Hope that helps.

LD
Good gravy, it works!

Consider this fixed! Thanks a million!

---

### Post by quixote on 2009-10-03
(scrambledarthur, under "Thread Tools" at the top you, as the original poster, can mark this thread "solved."  Which is a good and neighborly thing to do, because then people know without reading the whole thread :D.)  Glad to see it is, by the way!  Very useful tip, about the libstdc++5.

---

### Post by jmkemp on 2009-10-09
> **quixote said:**
> I have the same versions of Tbird, GProvider & Lightning, and they work.  I'm running on regular Jaunty, though, not Netbook Remix.  There's no logical reason, though, why that should make a difference.  It's got to be something about the way it installed.  ??

Yes, something to do with the way it was installed. I had downloaded the .xpi from the mozilla website and installed that. When I zapped the contents of the extension folder in my profile and then installed the extensions from the ubuntu repositories then it sort of worked. I say sort of because I still can't open any network calendars, I get an error message. Tried installing the libstdc++5 library but that isn't available on the karmic beta I'm now using. Installing lidstdc++6 doesn't seem to help.

---

### Post by dunbrokin on 2009-11-11
That does not work anymore as you cannot install libstdc++5 anymore.


I have the same problem.....TB Calendar just will not work!!

---

### Post by Ebuntor on 2009-11-14
Hi,

I found a solution, at least it worked on my system. Simple uninstall Lightning from the add-ons list. After that go the Software Center and install the Lightning extension from there. The info in your calender, todo list etc isn't lost when you remove the extension.

Hope it works for you.

---

### Post by scrambledarthur on 2009-11-14
D'arghh!

Still the same problem! The "New event"/"New Task" buttons are grayed out!


hmmmm

---

### Post by kolinab on 2009-11-14
I had this same problem. Solved it with the following instructions:

[http://ubuntuforums.org/showthread.php?t=1310196](http://ubuntuforums.org/showthread.php?t=1310196)

---

### Post by scrambledarthur on 2009-11-14
Gooder gravy, it works again!


linus for life!

---

