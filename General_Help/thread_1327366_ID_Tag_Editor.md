---
title: "ID Tag Editor"
date: 2009-11-15
forum: General Help
---

### Post by joeyknuccione on 2009-11-15
I'm trying to get an ID3 tag editor that will override the tags from Windoze Media Player.

Whenever I change tags, Rhythmbox doesn't always accept the changes, so I've tried the following:

Easytag, Ex Falso, neither of which work.

PyRename, where I change from mp3 to ape, edit, and back to mp3, doesn't work.

Several command line tools - I attempt to install either as me, or as root - and permission is denied as me or as root. (No biggie really coz I prefer not to hafta use command line)

Question:
Is there an ID3 Tag Editor for Ubuntu that actually works?

Is Windoze more powerful than Ubuntu? Please say not!

I'll settle for some way to strip all tags and hafta redo a couple thousand tags just to get these dang Windoze tags removed.

---

### Post by fluffman86 on 2009-11-15
1. Remove all of your files from Rhythmbox.
2. Use Ex Falso to edit the tags.
3. Reimport into Rhythmbox.

or...

1. Install Banshee
2. Edit > Preferences
3. Check "update file and folder names" and "write metadata to files"
4. Import your current files and update them.

---

### Post by baggins on 2009-11-15
> **joeyknuccione said:**
> 
Whenever I change tags, Rhythmbox doesn't always accept the changes

Do you mean that you can change the tags for some files and not for others?
If so I am guessing that you don't have write permissions for the files. Don't know why, but most files I have gotten from Windows Media Player seems to be write protected when opened in linux.
Also if the files are on a NTFS filesystem sometimes strange things happen to file permissions when seen in linux.

For one of the files where you can't change the tags, could you please post the commandline output of:
ls -lh /path/to/file.mp3
(and yes the /path/to/file.mp3 are to be replaced by the actual path of a file :) )

> **joeyknuccione said:**
> 
Several command line tools - I attempt to install either as me, or as root - and permission is denied as me or as root. (No biggie really coz I prefer not to hafta use command line)

I'm a bit unclear here did the install of the tool fail, or did the tool fail to work?
If it's the latter did it give any error message?

-- Jon

---

### Post by joeyknuccione on 2009-11-15
> **fluffman86 said:**
> 1. Remove all of your files from Rhythmbox.
2. Use Ex Falso to edit the tags.
3. Reimport into Rhythmbox.

or...

1. Install Banshee
2. Edit > Preferences
3. Check "update file and folder names" and "write metadata to files"
4. Import your current files and update them.
Thank you very much. I will try these methods and report back in a day or so.

---

### Post by motorcity909 on 2009-11-15
I've experimented with a few ID taggers since moving to Ubuntu and am currently using Kid3-qt, which seems okay.

Songbird (an iTunes lookalike) is also okay for amending the odd tag.

Sad to say, I haven't found anything quite as good as [MP3Tag]("http://www.mp3tag.de/en/") which is sadly Windows only.

Kid3-qt is working pretty good though.

---

### Post by joeyknuccione on 2009-11-15
These files are stored on an NTFS filesystem.

> 
For one of the files where you can't change the tags, could you please post the commandline output of:
ls -lh /path/to/file.mp3
(and yes the /path/to/file.mp3 are to be replaced by the actual path of a file )

Returns:
```

-rwxrwxrwx 1 root root 4.6m 2009-11-15 10:55 test.mp3

```
^test.mp3 is in green letters

Does seem to be a permission problem, eh?

> 
Several command line tools - I attempt to install either as me, or as root - and permission is denied as me or as root. (No biggie really coz I prefer not to hafta use command line)

> 
I'm a bit unclear here did the install of the tool fail, or did the tool fail to work?
If it's the latter did it give any error message?

Permission errors, even in a root terminal. Installed onto an ext3 hard drive.

Thanks for your help.

---

### Post by joeyknuccione on 2009-11-15
Tried all of the above, to no avail.

Even tried cut/paste into ext3 Music folder, and edit there. Couldn't even see the tags that Windoze is forcing onto Rhythmbox. Rhythmbox/Ubuntu is beholden to what Windoze says.

Windoze wins another round :(

Please tell me again why I prefer Ubuntu.

---

### Post by arnab_das on 2009-11-15
install kid3.

```
sudo apt-get install kid3
```

---

### Post by joeyknuccione on 2009-11-15
> **arnab_das said:**
> install kid3.

```
sudo apt-get install kid3
```
Got it, c/p file to ext3 for my permissions, edited, c/p back to ntfs folder.

No Go.

Thanks anyway.

---

### Post by fluffman86 on 2009-11-15
Aha...the problem is that "root" owns those files, instead of your username.  I don't think linux permissions stick around very long on ntfs drives--especially removable/usb drives--but we only need them for a little while.

So now you have 2 options.

1) Change the permissions on the files before editing with:
```
sudo chown -R username:username /media/disk/musicfolder
```
Just change username to your name and remember than you can use TAB to help complete the location of your files...it's almost necessary with spaces!

2) Have root edit the files himself.  Do this by pressing alt+f2, then type
```
gksu exfalso
```
replacing exfalso with easytag or whatever.  I wouldn't recommend using gksu on banshee or rhythmbox because the database probably won't stick around once you launch it as a normal user later.

And as for why you like Ubuntu better than Windows--well, because it's easier, safer, and makes more sense...at least once you understand it. :)

Imagine the opposite case in Windows.  First of all, you wouldn't be able to open an ext3 or 4 partition to view the files at all.  And if you could, the permission changes are MUCH harder to do or undo.  

Or, more likely, you would already be running as "root" which makes your whole system less secure to begin with.  

And finally, if you had a problem, who would you ask?  A windows help forum?  And where did they get their information?  By trial and error, and they may even offer some random exe to help you, which could kill your whole system.  That's scary.  

On the other hand, I got my information about chown and gksu (the commands you issue) straight from Linux/Ubuntu developers, and I read about it in the open source documentation.  If you think that my commands listed above could be harmful, you can read the documentation yourself with "man chown" or "man gksu"  :D

---

### Post by joeyknuccione on 2009-11-15
Ubuntu Wins! Ubuntu Wins! Ubuntu Wins!

First, thanks for all the help.

Heres my deal:

Install MP3 Diags from Software Center

C/P file(s) to ext3 drive

Edit offending ID tag

C/P back to ntfs drive 

WIN!

---

### Post by joeyknuccione on 2009-11-15
Update:

For giggles I tried the MP3 Diag on the ntfs with root as owner anyway.

It worked!

Also, it's a bit tricky to figure out how, but do know that when editing (I was just removing) a given tag, you seem to need to push delete to get that ball rolling.

Your mileage may vary, and always, always backup before editing.

---

### Post by nortexoid on 2009-11-15
I've noticed editing tags in both Banshee and Rythmbox don't always work as expected. I've tried EasyTAG with limited success, at least concerning cover art. Songbird has always worked for me, though obviously if you just want to edit metadata, creating a library and editing them in Songbird isn't ideal.

If you like a particular piece of Windows software for editing tags you might try to run it under Wine or in VirtualBox.

---

### Post by jocheem67 on 2009-11-15
I'm actually using Foobar2000 exactly for it's tagging capabilities. It's very good, using wine on an Arch-install.

I do like easytag though.

---

