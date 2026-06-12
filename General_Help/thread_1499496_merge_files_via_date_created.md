---
title: "merge files via date created"
date: 2010-06-02
forum: General Help
---

### Post by rlb.contact on 2010-06-02
I am not entirely sure how to describe this, but I'll try.

I have several backups via grsync for several users on my machine.

The users are really just variants of "me"  that is, they were created at different times but are my user accounts. I wanted to play and learn more about the CLI, etc.

I had some omens that my HDD was about to die, and I made a series of hurried grsync's onto a USB HDD. (for the record, the HDD did shed its mortal coil)

***

My core problem is that I now have several accounts that are riddled with redundant information. Within this information there are some unique files, pdf's, etc.

We are talking about 50 or so top level folders full of files. It is a painfully slow and inefficient process by hand. I am willing to sacrifice some fidelity of data for speed.

So here's what I need to do:

Phase 1

[LIST=1]
[*]I want to automate a process in which a command/script/application dives into each folder and looks at the date of each file.
[*]The program identifies each file by its date.
[*]The program chooses the newest version of the file
[/LIST]
Phase 2:
All of the files are organized into the Ubuntu default folders (Documents, Videos, etc.) Some of the main folders have unique folders within them. 

For example:

user folder file

Bob/Documents A.txt  B.txt  
Mike/Documents  B.txt C.txt

would morph into

CombinedUsers/Documents  A.txt  B.txt  C.txt

There has to be some way to do this. Could someone please, please help?

Thanks,
Lee

---

### Post by PeEllAvaj on 2010-06-02
I can't give you the exact commands right now, but the way to start would be to do it in a few parts.

1. Construct a list of the files formatted as <filename> <date> <folder/filename>.  I would use "find" for this.
2. Sort this list alphabetically (this should give you a list of the files with their dates).
3. Iterate over this list, skipping the first entry of each filename, and deleting the rest (I recommend Python for this, since it makes scripting so easy).

I know this only gets you 5% of the way there, but hopefully that's a start.

---

### Post by rlb.contact on 2010-06-02
I see where you are going with this. The real headache is that there are so many files in so many folders. 

Many of the folders are identical. Some of them branch out more than others. Most of the files are identical except for date. It really comes down to mashing together the folders, tossing out the oldest versions of multiple files and leaving unique files behind.

I could at least start to do the rest manually, if need be.

I don't write scripts (I took C in college, and that was decades ago.) I was hoping that there was some sort of program or bash program that would do the trick.

I'm sure that there are system administrators who do this everyday.

Thanks for the ideas, and please keep them coming

---

