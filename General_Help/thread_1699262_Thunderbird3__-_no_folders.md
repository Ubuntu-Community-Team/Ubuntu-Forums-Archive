---
title: "Thunderbird3  - no folders"
date: 2011-03-03
forum: General Help
---

### Post by col48 on 2011-03-03
I have just installed Thunderbird 3 in Lucid and after some struggles got the address books and accounts set up (although I haven't yet tried retrieving or sending mail) based on my Thunderbird 2 setup in Hardy.

I have also copied the 'Local Folders' folder across.

But when I fire up T3, no folders show in the LH pane.
The attached thumbnail shows the view.

As you see I have selected 'All Folders' but whatever I choose here nothing shows in the pane - not even Inbox, Drafts or Sent.

This thread appears to show the same problem being solved
[http://ubuntuforums.org/showthread.php?t=1489368]("http://ubuntuforums.org/showthread.php?t=1489368")
but it doesn't do it for me.

I have many (>30) local folders in the profile/Mail/Local Folders folder (including the above three).

If I compose an email and save it as a Draft, it gets saved in the correct Local Folder - I can see it is there using a text editor.  So at one level, T3 knows [some of] the folders are there.

I have tried deleting foldertree.json and session.json (when T3 is not running) and it makes no difference.  When T3 runs, foldertree is rebuilt as two characters, {}.  All the folders and files are read/write for me.

Since the prefs.js file is largely the T2 one from Hardy, could something be missing here? 

How can I persuade T3 to display the folders and therefore (presumably) the messages in them?

---

### Post by Habitual on 2011-03-03
I'd rename the ~/.thunderbird (T3 install) by 
```
mv ~/.thunderbird ~/.thunderbird.org
```
in terminal then re-copy the .thunderbird folder from the T2 install back over and then run ```
thunderbird
``` again.

"Since the prefs.js file is largely the T2 one from Hardy, could something be missing here? " You betchya it could be an issue.

You could compare the T2 version with the T3 version using diff at a command-line.
```
diff t2_file t3_file
``` to "see" the differences.

There is a possibility that your method may not work.

Good luck.

---

### Post by col48 on 2011-03-05
Thanks, Habitual.  That worked!

Being more explicit..
(1) rename .thunderbird (T3 install in Lucid) to serve as a backup, albeit a broken one
(2) rename .mozilla-thunderbird (T3 install) temporarily
(3) copy .mozilla-thunderbird (from T2 in Hardy) to Lucid
(4) rename file just copied from .mozilla-thunderbird to .thunderbird
(5) reverse step 2
I needed steps 2 and 5  because I was using drag/drop in Nautilus for step 3 and I can't combine this with a rename.

_Of course_ it should have worked, but I'm puzzled that it did, because that is what I thought I had done when I installed T3!

It could be that I hadn't taken into account what looks like a change in the way thunderbird operates. T2 expects to go to .mozilla-thunderbird for all its data (I have no .thunderbird in Hardy) whereas *perhaps* T3 goes direct to .thunderbird, since that is where all the data lives.  T3 does install a .mozilla-thunderbird as well, but this is purely a link to .thunderbird and could be a mechanism for compatability.

No point in trying to reconstruct what fails.  I'm just grateful for what works!

---

### Post by Habitual on 2011-03-05
Always glad to provide a working solution to those who appreciate it being given.

You are very welcome.

re: "No point in trying to reconstruct what fails. ..."
Even a broken watch is right twice a day!

---

