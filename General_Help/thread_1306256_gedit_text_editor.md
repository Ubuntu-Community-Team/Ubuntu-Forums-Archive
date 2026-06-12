---
title: "gedit text editor"
date: 2009-10-30
forum: General Help
---

### Post by cmcanulty on 2009-10-30
Is there  a way to set the gedit text editor to have a default option to display the .txt files?

---

### Post by Giblet5 on 2009-10-30
I'm not sure what you're asking.

Are you asking how to set preferences? That would be Edit -> Preferences.

---

### Post by alphaniner on 2009-10-30
What happens now when you double-click on a .txt file?  If it gives you the choice of executing or opening, that's because the file has execute permissions.

---

### Post by cmcanulty on 2009-10-30
I looked at all the preferences and see nothing about opening default. Every time I open a .txt file I have to say open to view, display, etc. I would like to just open txt files as that is all I ever do with them.

---

### Post by verv87 on 2009-10-30
May I ask why are you so inclined towards using gedit? Your dedication is not far away from being a lunatic obsession.

I recommend using [vim]("http://www.vim.com") instead.

Emacs (tm), gedit, vim -- they all have their plusses and their minusses but vim cuts the cheddar at the end of the day.

---

### Post by cmcanulty on 2009-10-30
I don't care what I use I just want to open .txt files quickly without having to tell it every time that I just want to view, not run in terminal

---

### Post by Giblet5 on 2009-10-30
Click Places -> Home Folder.

Right-click a .txt file and select Open With -> Other Application...

Select gedit.

Then click Edit -> Preferences...

Click the Behavior tab.

Select "View executable text files when opening them."

Done.

If that answered the question, click Thread Tools above and mark this SOLVED, please.

---

### Post by Gatemaze on 2009-10-30
Open nautilus... and then Edit/Preferences tab Behavior and make sure that under "Executable text files" you select "View executable text files when they are opened".

Again on nautilus right click on a .txt file Properties click on "Open with" tab and select gedit (This would be "Text editor") as the default... If you can't see Text Editor then click on add and add it.

---

### Post by cmcanulty on 2009-10-30
I tried that and still get run in terminal, display, cancel or run

---

### Post by jocko on 2009-10-30
Your question has already been answered several times. If you just make sure the text files are NOT set as executable, nautilus will treat them as simple text files and open them in gedit without asking you what to do.
Right-click the files in question, select properties and in the permissions tab make sure that "Allow running the file as a program" is NOT activated.
Or in a terminal:
```
chmod -x[COLOR=Blue] filename[/COLOR]
```But if the files are on a file system that can not handle linux permissions properly (like fat and fat32), I don't think there is any way to set the permissions properly...

---

### Post by alphaniner on 2009-10-30
gatemaze's solution worked for me.

---

### Post by Giblet5 on 2009-10-30
> **cmcanulty said:**
> I tried that and still get run in terminal, display, cancel or run

It sounds to me like you have completely messed up the permissions in your home folder and you can't save preferences in Nautilus.

Try setting the nautilus options again.

Close nautilus. Open another nautilus window. Check the setting. Did it go back to "Ask"?

If so, fix your folder permissions.

Here's a bulk way to do that (mostly) right:
```
sudo find $HOME -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
sudo find $HOME -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

Now, go set your nautilus preferences again and test it.

---

### Post by stchman on 2009-10-30
> **verv87 said:**
> May I ask why are you so inclined towards using gedit? Your dedication is not far away from being a lunatic obsession.

I recommend using [vim]("http://www.vim.com") instead.

Emacs (tm), gedit, vim -- they all have their plusses and their minusses but vim cuts the cheddar at the end of the day.

Vim or any variation of vi is a pretty lousy way to edit text files.

Vi is like some cult obsession.

---

### Post by Giblet5 on 2009-10-30
> **stchman said:**
> Vim or any variation of vi is a pretty lousy way to edit text files.

Vi is like some cult obsession.


Oh yeah? Try to spell "evil" without it...

Mmm?


PS: The reason it is so popular is that We Professionals know that any given Unix-like system will have it. Even systems where you're not allowed to install anything.

If all you know is Visual Studio, gedit, or emacs, working on a .gov Unix server will be a short-path to the unemployment line's "Losers Stand Here" section.

---

### Post by alphaniner on 2009-10-30
```
Vim or any variation of vi is a pretty lousy way to edit text files.
```

It's worse than lousy if you don't know how to use it.  But if you do it's \\:D/

---

### Post by verv87 on 2009-10-30
> **stchman said:**
> Vim or any variation of vi is a pretty lousy way to edit text files.

Vi is like some cult obsession.

First off watch the attitude.

Second lol emacs.

---

### Post by georgelenzer on 2009-10-30
I'm polyeditorous.  Started off loving Emacs, hated vi.  Then I started using Gedit because it was far easier than the other two.  Then I was forced to actually learn vi and now... I don't know how I lived without it.  But I've been known to use echo and cat too.  Now, I like them all and easily move between them.  But that doesn't help the original poster.

Regarding his problem, I concur that the permissions on the file he's trying to open are set for executable.  He should take care of that first.  If it still doesn't work for him, he should open a Nautilus window containing the file he wants to open.  Right click on the file and select "Properties".  Then in the dialog box, click on the "Opens With" tab.  There, it's pretty self explanatory to assign the default application for opening *.txt files.

> **alphaniner said:**
> ```
Vim or any variation of vi is a pretty lousy way to edit text files.
```It's worse than lousy if you don't know how to use it.  But if you do it's \\:D/

---

### Post by cmcanulty on 2009-10-31
Thanks all the key was to open Nautilus otherwise you never see a behavior tab.

---

