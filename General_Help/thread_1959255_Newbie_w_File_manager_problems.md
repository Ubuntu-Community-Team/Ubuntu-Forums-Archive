---
title: "Newbie w/ File manager problems"
date: 2012-04-15
forum: General Help
---

### Post by beelissa on 2012-04-15
Hi. I'm not a total newb, but some of the technical stuff is way over my head. I've been using Ubuntu for over a year, actually it's Xubuntu I guess, w/ the Xfce desktop version 4.8 and Ubuntu version 11.10.

Since I got Oneric, whenever I click on any of the folders it opens a window for it but the window is locked and I can't do anything. I have to close it because nothing responds to the cursor. This has been going on for quite a while.

I can save files and create folders from within other applications, such as Thunderbird or Firefox or the graphics programs and word processing and the unzipping utility. So when I download a file I can put it in the folder where I want it to go, or use Save As if I need to move a file I've created. But I can't open a folder/window to view the files on my USB thumb drive and drag those files onto my hard drive.

I don't know what's causing this or how to fix it, and every place I've looked has had info so far over my head that I don't even know what it means. If there is some simple answer to this, I'd love to hear it. Otherwise I'll have to take all of the files on my thumb drive, upload them to the Web and download them back to the hard drive.

I appreciate anyone's help! Thanks!

---

### Post by mike555 on 2012-04-15
Did you always safely eject your thumbdrive?  can you try the thumbdrive on another computer? then safely eject it ?

---

### Post by beelissa on 2012-04-15
I guess I wasn't very clear, sorry. I was using the thumb drive as an example, but this happens whenever I want to open any folder, folders on my hard drive included. I can save to and even create folders from within applications, but I can't open folders and manipulate their contents using the file manager. No matter where the folder is, the window locks up and is unresponsive (I even tried leaving it open overnight once to see if it just needed more time). I have to just close the window. I can't even re-size the window, it's completely locked up.

---

### Post by Toz on 2012-04-15
Is the file manager thunar? When the hang happens, is there anything being logged to the ~/.xsession-errors file?

---

### Post by beelissa on 2012-04-21
> **Toz said:**
> Is the file manager thunar? When the hang happens, is there anything being logged to the ~/.xsession-errors file?

I think the file manager is thunar. How can I check to be sure? 

Um, I'm still enough of a newb that I have no idea how to find the answer to the second question. All I know is, the window is unresponsive. Nothing happens no matter where I click and right-clicking doesn't do anything either. If I click to make another window active, when I go back to the File Manager window, it's blank. I click on the X in the top right and a message comes up: "This window might be busy and is not responding. Do you want to terminate the application?" and if I choose Yes, it closes it.

I want to move some files into the brush folder of GIMP and take some others out, any way I can do this without using the file manager, or is there a way to fix this? can I used another file manager program and if so, how do I load that? Thanks for your help!

---

### Post by Toz on 2012-04-21
> **beelissa said:**
> I think the file manager is thunar. How can I check to be sure?
Open a terminal window and type type in:
```
thunar
```
...and press Enter.
1. Does the same file manager come up and does it hang as per your original post?
2. Are any messages displayed on the terminal screen under where you just typed in "thunar"?

> Um, I'm still enough of a newb that I have no idea how to find the answer to the second question. All I know is, the window is unresponsive. Nothing happens no matter where I click and right-clicking doesn't do anything either. If I click to make another window active, when I go back to the File Manager window, it's blank. I click on the X in the top right and a message comes up: "This window might be busy and is not responding. Do you want to terminate the application?" and if I choose Yes, it closes it.

I want to move some files into the brush folder of GIMP and take some others out, any way I can do this without using the file manager, or is there a way to fix this? can I used another file manager program and if so, how do I load that? Thanks for your help!

In that same terminal window, type in:
```
cat ~/.xsession-errors
```
...and post back the last 10-15 lines that you see.

---

### Post by beelissa on 2012-04-21
The same file manager comes up and hangs in the same way. The Terminal window doesn't show any info until I click on the X to close it and then it says "Killed".

Session errors: this scrolled and scrolled. When it was done, I scrolled back to the top (or should I read from the bottom?).

Most of the lines say this:

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

but some of the lines (including the ones near the bottom, just before those I've typed further down) say:

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

The very last ones at the bottom say:

** (process:1491): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(gimp-2.6:24154): Gimp-Widgets-WARNING **: gimp_dialog_factory_dispose: stale non-toplevel entries in factory->open dialogs
** (process:1491): DEBUG: desktop-launch-listener.vala:118: ran with uri: http:/ubuntuforums.org/showthread.php?t=1959255&goto=newpost
** (process:1491) DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

I'm confused. I haven't had any problems, that I know of, using Thunderbird or Gimp. Does this mean anything to you?

Thanks again for your help. :-)

---

### Post by Toz on 2012-04-21
Can you post back the complete contents of the .xsession-errors file? Preferably right after you've tried to run thunar and it hangs.

Also, do you have alot of pictures in your Pictures folder? And, do you have alot of files in your Templates folder?

One final thing, is zeitgeist installed?
```
apt-cache policy zeitgeist
```

---

### Post by beelissa on 2012-04-21
To answer your questions in reverse order:

I guess zeitgeist is installed, here is what comes up when I type in the code you suggested:

zeitgeist:
  Installed: 0.8.2-1
  Candidate: 0.8.2-1
  Version table:
 *** 0.8.2-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages
        100 /var/lib/dpkg/status

Yes, I do have quite a lot of pictures and templates in those folders. Not that I could do anything about that without a file manager.

Here is the xsession result:

r plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found
** (process:1491): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(gimp-2.6:26725): Gtk-WARNING **: Unable to retrieve the file info for `file:///home/david/cliff/fbcover.jpg': Error stating file '/home/david/cliff/fbcover.jpg': No such file or directory

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

(gimp-2.6:26725): Gimp-Widgets-WARNING **: gimp_dialog_factory_dispose: stale non-toplevel entries in factory->open_dialogs

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found


** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found
** (process:1491): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found

** (process:1491): WARNING **: recent-manager-provider.vala:125: Desktop file for plugin-container was not found
** (process:1491): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1491): DEBUG: desktop-launch-listener.vala:118: ran with uri: [http://ubuntuforums.org/showthread.php?t=1959255&goto=newpost](http://ubuntuforums.org/showthread.php?t=1959255&goto=newpost)
** (process:1491): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

---

### Post by Toz on 2012-04-21
> **beelissa said:**
> Yes, I do have quite a lot of pictures and templates in those folders. Not that I could do anything about that without a file manager.

You might still have nautilus installed. Try running:
```
nautilus --no-desktop
```
...and this will give you a file manager to use. I would suggest moving the files out of ~/Pictures & ~/Templates and trying thunar again to see if that is the root of the problem.

As for all those warnings in your ~/.xsession-errors file, they are related to zeitgeist - which apparently is a core component of unity.

---

### Post by beelissa on 2012-04-22
Toz,

Thank you so much for your help.

Nautilus seems to work and I was able to re-arrange some of the files I wanted to move. I deleted lots of the templates and moved a bunch of pictures to a different folder. Thunar still doesn't work though (even after a reboot).

But at least I can use Nautilus if I need a file manager, I guess. 

Just curious -- what is zeitgeist and what is unity and, more importantly, should I be concerned about those session errors?

---

### Post by Toz on 2012-04-23
> Hi. I'm not a total newb, but some of the technical stuff is way over my head. I've been using Ubuntu for over a year, actually it's Xubuntu I guess, w/ the Xfce desktop version 4.8 and Ubuntu version 11.10.
I gathered from this quote that you installed the xubuntu desktop over an existing ubuntu install. The presence of nautilus (not part of the default xubuntu install) seems to confirm this.

Here is some information on unity: [http://unity.ubuntu.com/]("http://unity.ubuntu.com/")

And here is some information on zeitgeist: [http://wiki.zeitgeist-project.com/Getting_Started]("http://wiki.zeitgeist-project.com/Getting_Started")

As for thunar, does it hang if you open it with another account on your computer or with root privleges:
```
gksudo thunar
```

---

### Post by beelissa on 2012-04-24
> **Toz said:**
> I gathered from this quote that you installed the xubuntu desktop over an existing ubuntu install. The presence of nautilus (not part of the default xubuntu install) seems to confirm this.

Yes, this is correct.

> **Toz said:**
> As for thunar, does it hang if you open it with another account on your computer or with root privleges:


Yes, this seems to work. At least, I can open folders and click on things. I didn't try to move or copy anything. A pink banner across the top of the window warns me that I'm at the root account and "you may harm your system."

Thanks for the links. I'll check them out. I really appreciate your help! Thanks!

---

### Post by Toz on 2012-04-24
> **beelissa said:**
> Yes, this seems to work. At least, I can open folders and click on things. I didn't try to move or copy anything. A pink banner across the top of the window warns me that I'm at the root account and "you may harm your system."

Thanks for the links. I'll check them out. I really appreciate your help! Thanks!
Then it must be a problem with your profile, not thunar itself. What do the following commands return:
```
du -chs ~/Pictures
du -chs ~/Templates

```

Can you also try moving the thunar configuration files and running thunar again?
```
mv ~/.config/Thunar ~/.config/Thunar.BAK
thunar
```
Any difference?

(To restore the thunar config files: )
```
mv ~/.config/Thunar.BAK ~/.config/Thunar
```

---

### Post by beelissa on 2012-04-28
> **Toz said:**
> What do the following commands return:
```
du -chs ~/Pictures
du -chs ~/Templates

```
5.4G for Pictures, 16M for Templates

> Can you also try moving the thunar configuration files and running thunar again?
```
mv ~/.config/Thunar ~/.config/Thunar.BAK
thunar
```
Any difference?

Nope.

I have a question: will this problem cause a problem if I upgrade to version 12? or might it get fixed if I upgrade?

---

### Post by Toz on 2012-04-28
One more thing:

```
mv ~/Pictures ~/Pictures.BAK
mv ~/Templates ~/Templates.BAK
```

Any change?

Note: I think you're problem might be related to this bug: [https://bugzilla.xfce.org/show_bug.cgi?id=7834]("https://bugzilla.xfce.org/show_bug.cgi?id=7834"). Lets confirm whether it is.

---

