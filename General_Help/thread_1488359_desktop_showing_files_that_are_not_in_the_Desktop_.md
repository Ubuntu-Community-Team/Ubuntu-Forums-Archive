---
title: "desktop showing files that are not in the Desktop dir"
date: 2010-05-20
forum: General Help
---

### Post by holocene on 2010-05-20
Greetings,

I am on Lucid.

I accidentally deleted a system directory so I had to reinstall.

I reinstalled, and setup my users again in the same way.

When I tried to copy my user files from a saved source, they now appear on the desktop in mass. What I expect is that only files in the Desktop directory show on the desktop, instead all files in the home directory show on the desktop, less the dot files. 

I can not figure out how the system controls what files show up on the desktop. Comparing the problem user to a working user failed to disclose the difference. Searching help and the forum was unfruitful.

Any help appreciated.
steve.

---

### Post by ryan858 on 2010-05-20
Oops! Looks like you hit post before you meant to or something. You can click edit to finish your post.

But I'll take a guess at your problem; maybe you're looking in the desktop of the wrong user? For example, if you have multiple user accounts on your system, you may be looking in a different one than what you're logged in as, or you may be looking in /root/Desktop rather than /home/name/Desktop.

---

### Post by holocene on 2010-05-20
pls take a look again at the new message.

sorry for confusion.
steve.

---

### Post by ryan858 on 2010-05-20
Ah, ok, that helps.

Well, that is pretty bizarre.... Is it possible that you copied the files to the desktop instead of the intended directory? Maybe you were cd'd to the desktop and it just copied them to the current directory.

---

### Post by holocene on 2010-05-20
> **ryan858 said:**
> Ah, ok, that helps.

Well, that is pretty bizarre.... Is it possible that you copied the files to the desktop instead of the intended directory? Maybe you were cd'd to the desktop and it just copied them to the current directory.

Nope. Files and directories are NOT in the user's Desktop directory.

I am on gnome's website doing research. 

Any other ideas pls let me know.
steve.

---

### Post by ryan858 on 2010-05-20
I see, so it's like it's mirrored onto the desktop, but if you ls it from a shell then it's not actually there? Have you done an *ls -a*?

Also, I don't know why you marked it Solved... You probably ought to change that. I think you can edit the very first post of this thread and click the drop-down box next to the thread title box, to change it.

---

### Post by holocene on 2010-05-20
The problem of all the user files and directories showing up on the desktop, not just the files in Desktop was solved as follows:

Deleted these files:

on /home/baduser/


[LIST]
[*].config
[*].gconf
[*].gconfd
[*].gnome2
[*].gnome2_private
[/LIST]

Once  the user rebooted, the config files must have been regenerated, and now just the expected files (in Desktop) show on the desktop.

Looking at the sys admin doc on gnome's site may disclose which of these dirs is the culprit, but I could not find it within my time constraint so I just deleted them all and crossed my fingers. 

So far, no side effects have been noted from these deletions.

Regards
Steve.

---

### Post by ryan858 on 2010-05-20
I figure it was probably .config or .gconf.

I know that you can delete the entire .config directory with no ill effects, to effectively reset all of the user's settings.

Well, glad you got it solved! Sorry I wasn't more help to get it done quicker.

Good Luck in future endeavors!

---

