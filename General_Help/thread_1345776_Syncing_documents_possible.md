---
title: "Syncing documents possible?"
date: 2009-12-04
forum: General Help
---

### Post by drakvakt on 2009-12-04
When I installed Ubuntu 9.10 I had it to copy my documents from Vista, making the transition almost seamless. But now I find myself wanting to keep these folders synced. Seeming as it was possible to do during install, I see no reason why it shouldn't be possible to do when installed. Preferably i'd like a sync-on-bootup.

Is there a way to accomplish this?

Thank you in advance for all your help.

//Drakvakt

---

### Post by fluffman86 on 2009-12-04
Instead of syncing them, and having 2 copies, you can simply leave them stored on Vista and access them with ubuntu.  First, make sure all of your latest documents are synced to your Users folder: Open your Documents folder in Ubuntu, CTRL+A to highlight, CTRL + C to copy, then go to Places, navigate to your Vista Users directory, right click on Documents, and click Paste into Folder.  Now right-click again, and click "Make Link" and drag that link into your Ubuntu home folder.  Delete Documents, and rename the "Link to Documents" to "Documents" and you're done!   Now everything that you put into Documents is automatically stored in Vista.

---

### Post by drakvakt on 2009-12-04
Well, that does work pretty well. I hadn't used that option before since I thought it was impossible to see the Vista documents folder in ubuntu (been trying to go through C:\documents and settings). Now that you mentioned it, I managed to find the folder through a different route. 
Having two copies would still serve a good purpose as a backup though, especially considering each system is on separate harddrive.

I've set up the folders as you suggested for now though. Thanks for your help.

---

### Post by juliobahar on 2009-12-04
> **drakvakt said:**
> Well, that does work pretty well. I hadn't used that option before since I thought it was impossible to see the Vista documents folder in ubuntu (been trying to go through C:\documents and settings). Now that you mentioned it, I managed to find the folder through a different route. 
Having two copies would still serve a good purpose as a backup though, especially considering each system is on separate harddrive.

I've set up the folders as you suggested for now though. Thanks for your help.

Having two copies on a single computer would defy the reason behind syncin'

I guess having a link to vista's documents in ubuntu as mentioned above would be the the best solution. But there would be one drawback... if you delete a file on the vista partition from inside ubuntu, it is gone. No trash nor recycle bin. Retrieval would be impossible, right?

---

### Post by gslug79 on 2009-12-04
For keeping two folders in sync, you can use Unison: [//http://www.cis.upenn.edu/~bcpierce/unison/]("//http://www.cis.upenn.edu/~bcpierce/unison/"), which can be found in the repos.

I use this to sync between various machines over ssh, but it can also be used for folders on the same machine. It workos very well and will default to coping the newest version of a file, though if a file has been changed in both folders since the last sync, it will ask you what to do. The only thing to watch out for is the way diferent OSs treat case sensitivity in file names: You can quite happily have two different files called [FONT="Book Antiqua"][FONT="Georgia"]File1[/FONT][/FONT] and [FONT="Georgia"]file1[/FONT] in Linux, but Windows won't like that and will only allow one.

---

### Post by falconindy on 2009-12-04
> **juliobahar said:**
> Having two copies on a single computer would defy the reason behind syncin'
Actually, synchronization doesn't exist **without** 2 entities. Although its typical that the entities are physically separated.

---

### Post by drakvakt on 2009-12-06
Thanks, Unison does appear  to be exactly what I was looking for. The Vista drive doesn't automatically mount on startup, but it should still work out well.

I always permanently delete files when in Windows, so no change there. 

I do believe that two different harddrives would qualify the files as physically seperated. The point of syncing was that if one drive/OS fails i'll still have a copy of all my stuff. The most important documents will also be backed up in Ubuntu One, giving impressive redundancy.

Thanks for all your help and knowledge.

//drakvakt

---

### Post by karamu on 2009-12-08
> **gslug79 said:**
> For keeping two folders in sync, you can use Unison: [//http://www.cis.upenn.edu/~bcpierce/unison/]("//http://www.cis.upenn.edu/~bcpierce/unison/"), which can be found in the repos.

Will this work for an external USB drive that is not always plugged into the machine? I use one to keep backups of some of my Home folders (Pictures, Documents etc) but I often lose track of what I have updated and haven't. I'd like something I could run maybe once a week when I plug in the backup drive to ensure it is up to date with the Home folder on my computer.

I remember using "Windows Briefcase" on XP which did what I'm describing perfectly- is there a good equivalent on Linux?

---

