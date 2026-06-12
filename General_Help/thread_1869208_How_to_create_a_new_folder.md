---
title: "How to create a new folder?"
date: 2011-10-25
forum: General Help
---

### Post by WB0HYQ on 2011-10-25
I am sure this had been brought up many times, but since all my multi-word search queries keep getting broken up into individual words, I have been unsuccessful in finding an answer.

I have a USB HDD that I use on my Windows 7 machine.  I now have a Ubuntu (11.10) machine also.  When I plug the drive into the Ubuntu mahcine, I can see every one of the directories just fine, but when I try to create a new directory (by right-clicking) there is NO 'create folder' option.  Whenever I try to change permissions of ANY directory (or the whole drive) The drop-down selections will appear, but when I select "read/write" it will appear for a brief instant and then revert back to an empty field.

The drive is formatted NTFS and I am the Administrator on both machines (actually, the ONLY user).

Attempts to "find" the drive in a terminal have also failed as I am not sure where the drive is mounted so I cann't "cd" to it.  I am fairly sure that even if I did find it, any attempt to 'mkdir' would also fail.

So, what is the secret?

Bill

---

### Post by satanselbow on 2011-10-25
What do you see if you open nautilus and then plug the USB drive in?

Does the drive appear in the left hand column? (devices) 
Are you asked to supply your sudo password? 
Is the NTFS drive encrypted by windows (bitlocker) ?

---

### Post by WB0HYQ on 2011-10-25
Further info:  I have now found the drive under /media.  I kept forgetting to enclose the drive name (It had a space in it) with quotes.  Sorry. :redface:

Now, for some reason, using a terminal I am able to create a new directory.  Why can't I do this using the GUI?  Shouldn't the same overlying permissions structure apply?

Bill

---

### Post by WB0HYQ on 2011-10-25
When I plug the drive in, there is a short (5 second) delay and then the drive appears in the left-hand launch column.

Using the terminal, when I create a new directory i simply use 'mkdir' with no "sudo" prefix.

The NTFS drive is not encrypted in any way.

Bill

---

### Post by WB0HYQ on 2011-10-25
Now my question is narrowed further.  I did find that IF the list of directories/files did NOT extend the whole length of the Nautilus window I could right-click and create a new folder.  BUT, if the list (even at full-screen) fills the window, then there is nowhere inside that window I can click that will allow folder creation.

Some of my directories have as many as 50 or 60 photos (for example) in them.  If I wish to break those photos down into smaller groups by putting them into sub-directories, then I must navigate a terminal window down to that top-level and 'mkdir' the extra folders because of the above problem - no room to right-click and get the context menu.

Is this the normal way it is done? If so, then I'll shut up and accept it.

Bill

---

### Post by in·ter·punct on 2011-10-25
File > Create New Folder
Holding Alt reveals the menu bar. From there you can tap the letter on your keyboard that is underlined to bring up the corresponding drop-down. Try it. ;)

The shortcut to create a new folder is Shift+Ctrl+N.

---

### Post by WB0HYQ on 2011-10-25
Oh.  In the two weeks I've been running Ubuntu, this is the first I've noticed that the very top menu level menubar changes depending on what window you are viewing.  I never knew that.  I can see it now.  I've been so used to each window having it's own menubar right ON the window that I never thought to look way up at the top.

I can also see that ctrl-1/2/3 which changes the view of the folders/files in the window.  Once the view changes, and lets me see some whitespace in the window, the right-click context menu will then have 'Create a new Folder' available.

This is definitely NOT Windows (thank goodness).

Thanks for your input.

Bill

---

