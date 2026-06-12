---
title: "files not showing in a network share"
date: 2009-11-24
forum: General Help
---

### Post by brian873 on 2009-11-24
Hi :)

I just setup an ubuntu box with boxee and wanted to copy some movie files to it.

Inside the videos folder I created a folder Movies and shared it on my network.  I then copied the files to it from my mac book.  They copied over ok but I can't find them on the ubuntu machine and I cant see them on my mac book.  

I have never seens this before anyone got any clues?

thanks

---

### Post by jamesisin on 2009-11-24
So you didn't COPY them, you MOVED them?

What type of file sharing are you employing?

Is it possible that the files are hidden for any reason?  (Show hidden files.)

---

### Post by brian873 on 2009-11-24
hey jamesisin, thanks for the reply.

To answer your questions...

> So you didn't COPY them, you MOVED them?

What type of file sharing are you employing?

Is it possible that the files are hidden for any reason? (Show hidden files.) 

1. I copied them, still have a copy on my macbook
2. I just right clicked the folder and used sharing options.
3. I am not sure, in preferences, show hidden and backup files is checked.

---

### Post by jamesisin on 2009-11-24
Ah, so when you say "I cant see them on my mac book" you mean through the share (as a copy still resides in the original location).

If you just used the Sharing Options dialog or the Share tab from the Properties dialog, then I believe this is a Samba share (an implementation of Windows sharing).

If you try to send one of the succeeded files to the share again, do you get an error (file already exists) or does it silently fail again?

Also, if it silently fails again, what is the exact name of the file (including the extension) you are trying to copy over?

---

### Post by brian873 on 2009-11-25
[QUOTE=jamesisin;8380878]Ah, so when you say "I cant see them on my mac book" you mean through the share (as a copy still resides in the original location).

If you just used the Sharing Options dialog or the Share tab from the Properties dialog, then I believe this is a Samba share (an implementation of Windows sharing).

If you try to send one of the succeeded files to the share again, do you get an error (file already exists) or does it silently fail again?


Hey Thanks again for the reply...

1. Yes, they are not visible through the share.
2. No, it appears to cop over again without an overwrite error/prompt
3. filename = restles-natives.avi

I have tried with a couple of different file types (txt,iso,jpgs) and all the same.  I have also copied over 10gig worth of data and this does not sho up if I check the disk usage, were I would expect to see less free space.

thanks

brian

---

### Post by jamesisin on 2009-11-25
Are you attaching to the Samba share using guest access or using authenticated credentials (username/password)?

I'm having trouble with Samba using guest access.

Another test you can try is to attempt to create a folder directly on the share (usually right-click --> new folder).  See if that doesn't generate an error (or a folder!).

---

### Post by brian873 on 2009-11-25
hey jamesisin,

I am using an acocunt on the ubuntu machine, with username and password.

I can create a folder and it appears OK.  But again when I copy files to the folder they do not appear. :(

I might go for a fresh install without boxee and see how it goes! apart from updates I have only install lir,ssh and boxee.

thanks

---

### Post by jamesisin on 2009-11-25
Sorry, I had a few theories but they haven't panned out.  You are able to write to the share (creating a folder proves that).  The file names are Windows friendly (as evidenced by the file you presented above).  And this is not related to my guest access issue (aside from it being Samba that's at fault).

You may try renaming some file a.avi (or something equally simple) to see if that helps, but the issue is probably deeper in Samba than I am able to understand.

---

### Post by brian873 on 2009-11-25
thanks anyway :)

will try a fresh install when i get home tonight :)

---

### Post by jamesisin on 2009-11-25
Hope it works out for you.

---

