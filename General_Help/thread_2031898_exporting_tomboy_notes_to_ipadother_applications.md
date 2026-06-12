---
title: "exporting tomboy notes to ipad/other applications"
date: 2012-07-22
forum: General Help
---

### Post by edfromballarat on 2012-07-22
hi all,

i have been using tomboy notes for my studies over the last 2 years and have ended up with many thousands of notes that i regularly consult using the search function.

i am looking for a way to export these notes for viewing and searching across platforms.  In particular, migration to an ipad friendly program/app.  It does not seem as if there is a tomboy ipad app planned for any time soon.

exporting to HTML using the tomboy plugin has been problematic.  In particular, hotlinks appear twice, a big problem when there are multiple links in each note.

the tomboy windows build is also quite cumbersome, with long load times

i think i am really looking for a way to export all my data from tomboy while keeping the formatting and links.

any ideas?

thanks

---

### Post by aardvark4 on 2012-07-24
I don't know if this is exactly what you need, but as luck would have it, I actually (finally) jumped through all of the hoops necessary to get a Tomboy-compatible notes client in the app store today. 

You can use it to sync to Ubuntu One, and you can have Tomboy do the same, so you could get your notes that way. The markup that it supports isn't exactly the same as Tomboy's internal HTML tags, because to actually view the results of the markup, I show it in a web view, but you can at least get all of your notes onto your phone.  

The original thread
[http://ubuntuforums.org/showthread.php?t=1716106](http://ubuntuforums.org/showthread.php?t=1716106)

Link to the app
[http://itunes.apple.com/us/app/webnotes-powered-by-ubuntu/id519580240?ls=1&mt=8](http://itunes.apple.com/us/app/webnotes-powered-by-ubuntu/id519580240?ls=1&mt=8)

---

### Post by edfromballarat on 2012-07-27
that looks like exactly the sort of thing I am interested in.  I have installed the iphone version.  The client is working fine, unfortunately I am having difficulty syncing my tomboy notes to ubuntu one, a recognised problem with version 1.10.1.  This has been addressed in 1.10.2, but unfortunately this is a development release that is not in the repos yet.  Tried to install it from the source files, but no luck there, so i'll just have to wait until the next release to the repos to give it a go.  I will let you know how I get on when that happens.

good work on your app though (any chance of an iPad version:) )

---

### Post by aardvark4 on 2012-07-31
Thanks for the feedback! I'm glad you think it will be useful. If and when you (or anyone else for that matter) get a chance to actually use it together with Tomboy, I'd appreciate it if you could let me know of any issues you run into or suggestions for improvements. This is the first iPhone app that I've written, and I'm sure it's far from perfect.

As far as an iPad specific version, that is definitely something worth looking into. I haven't written anything for the iPad yet, but I would think much of the core would remain the same and mostly the iPad UI would need to be added, but I'm not sure. I'll look into it, though.

---

### Post by edfromballarat on 2012-08-31
just letting you know that i finally got my notes across.  I found out that they were not transferring from the backup to ubuntu one that i had already made.  i had to make a small change to each note (just changed a letter in the category) for it to update, THEN your app would recognize them and sync them across.  I have about 3000 notes, so there is a short lag between opening the notes section and being able to interact with it (iphone 4s, ios 5), which is  mildly annoying.   The only feature that I would like to see that is absent is preservation of the links to other notes within each note.  But otherwise, great job!

---

