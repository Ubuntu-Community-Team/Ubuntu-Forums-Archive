---
title: "deleted using &quot;rm&quot; need help!"
date: 2011-06-24
forum: General Help
---

### Post by garyed on 2011-06-24
I just deleted a bunch of important files using:
 ```
rm -r *.*
```
Is there any way to get them back?

---

### Post by trizrK on 2011-06-24
rm is dangerous if you dont know what you are doing. There is no way of getting them back if you didn't copy them.

---

### Post by idoitprone on 2011-06-24
> **garyed said:**
> I just deleted a bunch of important files using:
 ```
rm -r *.*
```
Is there any way to get them back?

it depends on you file system and etc. If you have ext 4 your out of luck

i will just say just restart your profile from scratch

check the /etc/skel and copy over some files to y
our home

---

### Post by nothingspecial on 2011-06-24
> **garyed said:**
> I just deleted a bunch of important files using:
 ```
rm -r *.*
```
Is there any way to get them back?

What did you delete?

---

### Post by garyed on 2011-06-24
Of course it would be ext4.
I know all about the dangers of using rm but I've been using it for years & am very comfortable with it. Obviously too comfortable. The funny thing is this all happened because I was trying to back up the directory in question & I was in a hurry. I wrote a simple bash script to back it all up to a separate drive on the same computer but I made a mistake in the script & I put the directory & its subdirectories in the wrong place. So I changed the script to the correct directory & instead of running the backup script first I decided to delete the stuff I put in the wrong place first. I deleted everything fine but by habit I must have hit ```
cd
```& went back to my home directory on the original drive. When I checked & found the directory wasn't empty I then issued the ```
rm -r *.*
```command again without realizing where I was. As soon as I hit the enter button I realized what I had done but it was too late. It looks like I got myself good. I can't believe there's no way to recover deleted files from ext4. I guess you live & learn.

---

### Post by Thewhistlingwind on 2011-06-24
photorec and testdisk? 

rm is a very powerful utility, to the point where many users want it's power nerfed. (To stop this sort of thing from happening.)

---

### Post by idoitprone on 2011-06-24
> **Thewhistlingwind said:**
> photorec and testdisk? 

rm is a very powerful utility, to the point where many users want it's power nerfed. (To stop this sort of thing from happening.)

ah hell no, i love destroying my system

[QUOTE="Doug Gwyn"]"UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things."[/QUOTE]

---

### Post by nothingspecial on 2011-06-24
Well, the obvious answer is to restore from your backups.

You do have them?

If not photorec - test disk -

---

### Post by FormatSeize on 2011-06-24
> **Thewhistlingwind said:**
> rm is a very powerful utility, to the point where many users want it's power nerfed. (To stop this sort of thing from happening.)
Hm. That's interesting. I do agree that it's pretty powerful, but I can't say that I'd like to see it toned down. It would, though, be interesting how that would be implemented if it were to happen. 
 
I guess there could be a /trash directory where everything deleted with rm would go, but what happens when you accidently input the command to delete a filesystem, and everything tries to go into a /trash directory that is being recursively deleted? A black hole? Yeah, probably a black hole, formed right in front of you inside your computer.

---

### Post by idoitprone on 2011-06-24
> **FormatSeize said:**
> Hm. That's interesting. I do agree that it's pretty powerful, but I can't say that I'd like to see it toned down. It would, though, be interesting how that would be implemented if it were to happen. 
 
I guess there could be a /trash directory where everything deleted with rm would go, but what happens when you accidently input the command to delete a filesystem, and everything tries to go into a /trash directory that is being recursively deleted? A black hole? Yeah, probably a black hole, formed right in front of you inside your computer.

if the command had that behavior, then i cannot call the rm command removing files. I call it moving. Moving files within the same partition is an instant process.

---

### Post by garyed on 2011-06-24
> **nothingspecial said:**
> What did you delete?
I deleted a directory called "bills_paid" that had subdirectories with every bill that I've paid in the last few years.

---

### Post by jmszr on 2011-06-24
There is "safe-rm".

The description in Synaptic:

This package provides a tool intended to prevent the accidental deletion
of important files by replacing rm with a wrapper, which checks the
given arguments against a configurable blacklist of files and directories
that should never be removed.

Users who attempt to delete one of these protected files or directories will
not be able to do so and will be shown a warning message instead.

Protected paths can be set both at the site and user levels.

@garyed:  Ouch!!

---

### Post by garyed on 2011-06-24
I like the "rm" command. Sure I wish there was an undelete command that would fix things when you do something stupid like I did but thats part of the power that comes with using Linux. Had I slowed down & heeded the warnings I would have been fine. I already executed the "rm" command correctly & should have known when I got the "directory not empty" prompt when I tried to delete it that I moved back into my home directory. 
Live & learn.

---

### Post by Gyokuro on 2011-06-25
> **garyed said:**
> I just deleted a bunch of important files using:
 ```
rm -r *.*
```Is there any way to get them back?

try the extundelete command: [http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

---

### Post by 3rdalbum on 2011-06-25
I'm not sure if this works for Ext3/4, but in the olden days as soon as you realised that you were deleting files you didn't want to delete, the conventional wisdom was to immediately unplug the power and hope that the changes hadn't sync'ed to disk.

---

### Post by garyed on 2011-06-25
> **Gyokuro said:**
> try the extundelete command: [http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

I tried it but couldn't get the syntax right. You would think if someone could write something like that then they could also show an example of the syntax how to undelete a directory. I just kept getting errors. I worked on it all night & gave up. I did have most of the stuff on another computer so I only ended up losing a couple months of bills. I copied over a few gig of files so its probably gone now.

---

