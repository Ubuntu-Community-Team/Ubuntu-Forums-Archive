---
title: "Suggestions for online backup service please"
date: 2009-12-27
forum: General Help
---

### Post by mickeyjoe on 2009-12-27
I'm looking for suggestions for an online backup service please.  I don't mind paying for a service that gives some assurance either [for example, a service that also backs up my data at another site and doesn't put something in writing that they aren't responsible for losing my valuable photo data, etc...].

I have one other problem.  I am doing a transition from Mac os X to Ubuntu and all my folders and files on Mac os X have slashes.  For example, each and every date and month is neatly organized in such a way where last month is 11/09 and this month is 12/09.  Yesterdays photos would be 12/26/09 and todays photos would be 12/27/09 in the 12/09 folder.  I believe the Ubuntu system is going to have an issue with the slashes "/" when I bring the files and folders over to the Ubuntu box.  I have literally many many thousands of files and folders with slashes in them, is there any easy way to do a conversion from slashes [/] to dashes [-] on the fly?

---

### Post by junapp on 2009-12-27
> **mickeyjoe said:**
> 
I have one other problem.  I am doing a transition from Mac os X to Ubuntu and all my folders and files on Mac os X have slashes.  For example, each and every date and month is neatly organized in such a way where last month is 11/09 and this month is 12/09.  Yesterdays photos would be 12/26/09 and todays photos would be 12/27/09 in the 12/09 folder.  I believe the Ubuntu system is going to have an issue with the slashes "/" when I bring the files and folders over to the Ubuntu box.  I have literally many many thousands of files and folders with slashes in them, is there any easy way to do a conversion from slashes [/] to dashes [-] on the fly?
 
First thing that comes to mind for the photos is to use something that relies on the exif data. First link I found was:
[http://6v8.gamboni.org/Move-Rename-files-according-to.html](http://6v8.gamboni.org/Move-Rename-files-according-to.html)

Perhaps a similar sort of method on the create date could be used to recreate the file structure to a year/month/day setup. I suspect this would be something handled on the mac side of things, as you say, I agree that Ubuntu might have some issues. 

You might try to copy a couple over and see what happens, you may just end up with a folder structure like
/home/you/12/09/12/26/09
which you could then move to appropriate folders. I haven't tried this.

edit:
maybe rename them all in mac first with a tool like:
[http://www.publicspace.net/ABetterFinderRename/](http://www.publicspace.net/ABetterFinderRename/)
or this one which seems to get good reviews:
[http://wfco.de/applications/macosx/Renamer4Mac](http://wfco.de/applications/macosx/Renamer4Mac)

---

