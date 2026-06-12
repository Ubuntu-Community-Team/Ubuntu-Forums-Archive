---
title: "folders don't show files"
date: 2009-11-13
forum: General Help
---

### Post by mattsegstro on 2009-11-13
Hey, I've been experiencing this problem and figured out that it's solved by a reboot but I thought I should maybe try and figure out what causes it rather than rebooting all the time.

When I open a folder through the Places menu and then like Documents or whatever, sometimes the cursor will show the spinning circle indicating that it's working, but it won't show any of the files and it just sits there spinning away until I reboot.  This happens sometimes at random but most often happens when I've opened just the Home directory, dragged a file into say the Video's folder, and then tried to open that Video's folder.  It has also happened with Downloads and Documents and like I said it most often happens after I drag a file into it.

Any suggestions?  It crossed my mind that it could be the fact that I frequently have things downloading, on a slow Internet connection, and also have Ubuntu One open so maybe that's causing it to load slowly because it can't pull information from the Internet but that doesn't make all that much sense... it's just all I could think of.

Matt

P.S. One other note on this, I just experienced this problem again and here's what happened.  I threw a video file into my video's folder, from the home folder.  Tried to open the video's folder and it showed the spinning working cursor and no files.  I waited for a few minutes, nothing.  I closed it and opened it again and only the new file showed.  I have a half dozen other videos in there that didn't show up but the new video I just dragged in appeared on this second time trying.

---

### Post by Giblet5 on 2009-11-13
I recommend opening a terminal window and running ```
top
```

That won't terminate until you stop it via Ctrl+C.


Now drag the files around and try to reproduce the behavior.

Look at the terminal window. It's showing you the top CPU hogs.

Is your CPU bogged down? By what?

---

### Post by finalfd on 2009-11-14
I've had the same issue, in folders containing a few images. Other then rebooting (which doesnt fix for long). The only way I can get all the files to show as to disable thumbnail view for the files.

---

### Post by mattsegstro on 2009-11-14
I haven't tried disabling thumbnails so I might try that, but what I have done is not clicked connect in Ubuntu One and left it disconnected after a reboot and surprisingly since I disconnected Ubuntu One I haven't had that issue.  It might be a coincidence but it could make sense as a reason why this happens.  Do you use Ubuntu One finalfd?

And I haven't had a chance to try the method Giblet5 suggested but I may have a chance today and I'll report back if I do.

---

### Post by shaviro on 2009-11-14
I have been having the same problem since I upgraded to Koala -- specifically with the Videos folder. It is resolved by turning off thumbnails.

---

### Post by finalfd on 2009-11-14
No its not something I use. Thumbnails disabling seems to be the only "fix" but I would prefer not having to disable it on the images.

---

