---
title: "Ubuntu lost my folder (Ubuntu needs a fix for this bug)"
date: 2011-09-21
forum: General Help
---

### Post by pretty_whistle on 2011-09-21
The mishap occurred twice yesterday till I figured out how to stop it-I can't permanently delete anything anymore.

I permanently deleted 2 folders and 2 other folders went with them.  How?  Because whenever you close a window it's icon is still highlighted so if you highlight *another* folder or file for deletion the previous one being highlighted means it gets deleted too.  The solution for a user is to not permanently delete anything so it'll end up in the trash can and thus you can go get it.

Ubuntu needs to be redone so when you close something it's not still highlighted.  This is a Ubuntu bug.

---

### Post by regala on 2011-09-21
> **pretty_whistle said:**
> The mishap occurred twice yesterday till I figured out how to stop it-I can't permanently delete anything anymore.

I permanently deleted 2 folders and 2 other folders went with them.  How?  Because whenever you close a window it's icon is still highlighted so if you highlight *another* folder or file for deletion the previous one being highlighted means it gets deleted too.  The solution for a user is to not permanently delete anything so it'll end up in the trash can and thus you can go get it.</quote>

Ubuntu needs to be redone so when you close something it's not still highlighted.  This is a Ubuntu bug.

no. This is not a bug. It's the spec of Gnome Desktop IHM or KDE IHM. And it has been deemed good for years. Because people can adapt (usually).

br,

-- 
Mathieu

---

### Post by rjbl on 2011-09-21
> **pretty_whistle said:**
> The mishap occurred twice yesterday till I figured out how to stop it-I can't permanently delete anything anymore.

I permanently deleted 2 folders and 2 other folders went with them.  How?  Because whenever you close a window it's icon is still highlighted so if you highlight *another* folder or file for deletion the previous one being highlighted means it gets deleted too.  The solution for a user is to not permanently delete anything so it'll end up in the trash can and thus you can go get it.

Ubuntu needs to be redone so when you close something it's not still highlighted.  This is a Ubuntu bug.

Interesting that you should spot this - I guess you must be using 10.04LTS - which permits a permanent 'Delete' on the dropdown in File manager. But, you do get a popup listing the files to be deleted beyond recall and a request to confirm or cancel the command. From the same drop down you* can* select 'Move to Rubbish Bin' - with later recovery still being possible.

In 11.04 you do* not* have a 'Delete' option on the File Manager drop down on the Classic / Gnome desktop - you *only* have the command to 'Move to Rubbish Bin' - from which of course it can later be recover, when you realize your mistake.

Does this help?

rjbl

---

### Post by pretty_whistle on 2011-09-21
> **rjbl said:**
> Interesting that you should spot this - I guess you must be using 10.04LTS - which permits a permanent 'Delete' on the dropdown in File manager. But, you do get a popup listing the files to be deleted beyond recall and a request to confirm or cancel the command. From the same drop down you* can* select 'Move to Rubbish Bin' - with later recovery still being possible.

In 11.04 you do* not* have a 'Delete' option on the File Manager drop down on the Classic / Gnome desktop - you *only* have the command to 'Move to Rubbish Bin' - from which of course it can later be recover, when you realize your mistake.

Does this help?

rjbl
This happened on 11.04 and it was on the desktop.  I used a keyboard shortcut for deleting: Shift+delete.  There's no confirm deletion option when I did it this way.

Edit :  And I have the classic/Gnome desktop.

---

### Post by sffvba[e0rt on 2011-09-22
I have myself never heard of this phenomenon... 

If it is indeed a bug I would suggest adding your input on Launchpad by marking yourself as being affected, and if no bug has been filed (which would be strange if this is something that is a bug) then you could file one and the devs can have a look at it.


Regards
404

---

### Post by 3rdalbum on 2011-09-22
I'm on 11.10 but I cannot reproduce the bug. Please tell us exactly how to reproduce the bug.

Are you sure you're not holding down Shift while clicking the other folder, which will select both? If so, that's not a bug, that's human error.

Also note that Ubuntu ships without the permanent delete option; instead you've got Move To Trash.

---

### Post by armandh on 2011-09-22
holding down the shift key selects all between two selections in a folder 
[light 1, hold shift, lite the second, all between light too]
lighting one and at another
right mouse while holding the shift key and
hitting delete, deletes them all between.
same for send to trash. 
combining 2 operations is not a bug.

select something such that is is the only thing lit B4 using the shift key as part of an operation.

---

### Post by pretty_whistle on 2011-09-22
> **3rdalbum said:**
> I'm on 11.10 but I cannot reproduce the bug. Please tell us exactly how to reproduce the bug.

Are you sure you're not holding down Shift while clicking the other folder, which will select both? If so, that's not a bug, that's human error.

Also note that Ubuntu ships without the permanent delete option; instead you've got Move To Trash.

I tested it a few times and was able to reproduce it.

Here's how to reproduce it:

Make 2 folders named "test 1" and "test 2".  Now open test 1 as if you were going to work in it.  Now close the folder like you're done with it-notice the folder is selected though you closed it.  (This is where the problem comes in)

Now pretend you wish to delete the folder test 2 because you don't need it-put the cursor over it and hit control to select it.  Look what you have now-2 folders are selected, test 1 AND test 2.  2 folders selected but you only wanted to delete test 2.

To permanently delete folder 2 hold shift and hit the delete key on the keyboard.  Viola!  Now both test 1 AND test 2 are gone-bypassing the trash.

In this example, the folder test 1 just got deleted though you didn't want it to and it happened because it was *still selected* after you closed it.  So, unless you unselected it 1st it got deleted as well.

Edit :   This may or may not play a role but I have the mouse set to single-click operation in Ubuntu, meaning I don't have to double click a folder/file to open them-I just single-click it.

---

### Post by pretty_whistle on 2011-09-22
> **armandh said:**
> holding down the shift key selects all between two selections in a folder 
[light 1, hold shift, lite the second, all between light too]
probably moving the pointer while holding the shift key
hitting delete deletes them all. combining 2 operations is not a bug
I didn't make myself clear.  This isn't happening *inside *folders.

It's happening to the folders themselves and lone files (meaning ones that aren't in folders) sitting on the desktop.

---

### Post by pretty_whistle on 2011-09-22
Wait a mminute...........

I see.  I was accidently using the control key for selection and thus did it to myself.  Ooops.
Nevermind it all then.
:eek::rolleyes:

---

### Post by Ms_Angel_D on 2011-09-23
OP I'm glad you got your issue sorted out. For future reference please remember that the Testimonials & Experiences forum is not for support but a place for users to share their *buntu experiences.

if indeed you do think you have a bug please note you can file bug reports on [launchpad]("https://launchpad.net/")

I've moved this thread to the General help forum.

---

