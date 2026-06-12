---
title: "Banshee moves the physical locations of directories when rescanning library"
date: 2011-10-08
forum: General Help
---

### Post by switch10 on 2011-10-08
The title says it all.  When Banshee rescans my library, it moves around the physical locations of the directories that my music files are located in.  

My ~/Music directory is organized like this:  Music/"A-Z"/Artist/Album/.mp3

So Music/ just has directories named "A-Z", no artists or albums.  After I rescan my library with Banshee, *some* (its always the same ones) albums and artist directories have moved to Music/ (see screenshot).

I should mention that ~/Music is actually a soft link to a directory in /media.

Why does this happen?  How can I fix it?

Thanks,
Dave

---

### Post by vajorie on 2011-10-09
Not sure, but you didn't get replies for a day, so I'll try :)

In Banshee: Edit > Preferences > General > File Policies: are all four options there unchecked? They should be, if you want it to just read the thing. 

Alternatively, I would temporarily change read-write permissions of the directory (make it read only) and launch banshee from the command line with a dbg thingy so it gives output... At the worst, leaving the directory read-only until Banshee creates the database should solve your problem until the next time you hit "sync database" or whatever it was called :) Anyway, the command was

```
banshee --debug
```

These not working, I'd try mounting the drive under ~/Music rather than having it symlinked and see if that makes a difference.

If all fails, mount it read-only and have banshee sync the database?.. A temporary workaround, at least...

PS. I assume it's a drive bc it's under /media

---

### Post by switch10 on 2011-10-10
I assume that this was happening due to the fact that my ~/Music was a symlink.  I never had a chance to test it though because I installed arch linux over my ubuntu install.  

I have been pointing banshee to the music dir located in /media, and I have not had a problem.  

Banshee (and everything else) runs much smoother under Arch btw!!  I'm sticking with it.

---

### Post by vajorie on 2011-10-10
> **switch10 said:**
> 
Banshee (and everything else) runs much smoother under Arch btw!!  I'm sticking with it.

Give a try to gogglesmm --no mono dependencies and very lightweight. 

(A symlink shouldn't have created any problems though...)

---

### Post by switch10 on 2011-10-10
> **vajorie said:**
> Give a try to gogglesmm --no mono dependencies and very lightweight. 

(A symlink shouldn't have created any problems though...)

Yeah!  gogglesmm is really nice!  Thanks!

---

### Post by switch10 on 2011-10-11
What is really interesting is Banshee running under Ubuntu let me choose the symlinked ~/Music dir as the location of all my music, but running banshee under Arch, the option is grayed out.

---

### Post by vajorie on 2011-10-11
Quick question --why do you use a symlink instead of pointing banshee to your actual music library?

---

### Post by switch10 on 2011-10-12
Just because ~/Music is the default location that Banshee reads from.  I didn't think it could cause issues.

---

### Post by directhex on 2011-10-12
> **switch10 said:**
> Just because ~/Music is the default location that Banshee reads from.  I didn't think it could cause issues.

To confirm, you definitely don't have Banshee configured to do what you reported, right? The four tickboxes in the preferences window?

---

### Post by switch10 on 2011-10-12
All of the preferences were default.  I no longer use Banshee, or Ubuntu, so I cannot confirm.

---

