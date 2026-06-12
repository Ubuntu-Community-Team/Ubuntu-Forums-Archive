---
title: "Import Vista .contact files into Thunderbird"
date: 2009-07-19
forum: General Help
---

### Post by shortylonglegs on 2009-07-19
I've finally convinced my family to ditch Vista and move to Ubuntu.  Pretty smooth transition so far, but I've hit a snag.  All the email contacts on Vista are stored individually in a .contact file in the users home directory.  Now that I'm using Ubuntu, and Thunderbird, I can't figure out to import the contacts.  Any one know how to do this?  I've been searching for a while now with no luck.

---

### Post by hibliss on 2009-07-19
Are these email contacts? From what email client in Vista. Generally you can export them as one file.

---

### Post by c0mput3r_n3rD on 2009-07-19
you can just go copy the file from Vista to the Ubuntu disk via pendrive or cd or what ever no?

---

### Post by shortylonglegs on 2009-07-20
Ehhh....
I kind of neglected to do any sort of backing up contacts before installing Ubuntu.  I have all the files from the Users directories, which is what I used to get everyone's firefox settings/bookmarks back to how they were, as well as all old emails.  The only problem is that I can't figure out to get these .contact files into anything.  I've done this type of thing before, and so didn't put as much thought into it as I should have.  I'm used to gmail accounts, with the contacts all automatically backed up online.  A bit of a major oversight on my part....
I used clonezilla to copy the hd before wiping Vista, so thats always an option, though it would take quite a bit more time that I would like to spend.
The email client they were using was Outlook, maybe Outlook Express.  The contacts files appear to be xml, though I know nothing about xml and am only guessing by how the raw text looks.  If need be I can post sample contents of one of the files, if that would help.

---

### Post by hibliss on 2009-07-20
Outlook stores all of the contact files in a .PST file (which is also where mail is kept, and calendar items). The .PST is the profile.

It is in C:/Documents and Settings/User/Local Settings/Application Data/Microsoft/Outlook

Check there and you should be able to find a tool for Ubuntu to read the PST.

---

### Post by stinger30au on 2009-07-20
> **shortylonglegs said:**
> 
The email client they were using was Outlook, maybe Outlook Express.  The contacts files appear to be xml, though I know nothing about xml and am only guessing by how the raw text looks.  If need be I can post sample contents of one of the files, if that would help.



we need to know for sure if it is outlook or outlook express

if it is outlook express, have a read thru this

[http://ubuntuforums.org/showthread.php?t=1195004&page=2](http://ubuntuforums.org/showthread.php?t=1195004&page=2)

---

### Post by cordoval on 2011-01-11
hi shortylonglegs

I have the same problem, did you find a solution please I would appreciate if you could post how you did it.

I have the exact same problem and no solution so far...

Please help

---

### Post by cordoval on 2011-01-11
for some reason vista is stupid, 

where should I look for possible contact or address books files on the directory structure besides the folder that says Contacts/ and is full of all a.contact b.contact c.contact ... and so on so forth for every contact one has... 

thanks

---

