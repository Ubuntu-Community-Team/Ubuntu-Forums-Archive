---
title: "Home Folder filled with new unrecognized folders"
date: 2011-09-22
forum: General Help
---

### Post by dr1094 on 2011-09-22
Hi, I created a new account on ubuntu 11.04. In the home folder there are the regular 9 or 10 folders i.e. documents, pics, vids ,downloads, etc... 

I was using the computer and had to take a break, so I put the computer in suspend mode, came back after a while to find the home folder has many other folders in it with names like ".adobe" , ".cache" , and ".local" There are now 27 folders like this and a few files in the home folder (not including the original 9 folders). THese folders take up about 60 MB of space.

What are they? why are they there? Can I delete them? How do I ensure it won't happen again? and/or Can someone just make some sense of this to me, thanks

---

### Post by papibe on 2011-09-22
Most probably those files have been there the whole time. Most of the files and directories that start with a dot, and are located in your Home are configuration files. They hold important data so don't remove them!

To hide them again just press Ctrl+H.

Hope it helps,
Regards.

---

### Post by raja.genupula on 2011-09-22
> **papibe said:**
> Most probably those files have been there the whole time. Most of the files and directories that start with a dot, and are located in your Home are configuration files. They hold important data so don't remove them!

To hide them again just press Ctrl+H.

Hope it helps,
Regards.

+1
Hey papibe , its nice to see you .

hey man , dont delete them all are your application configurations files . what are the customization made by you to your application all going to stored in that file . How the application going to behave for the current user that will be there in that file and all important data about your application .

---

### Post by bodhi.zazen on 2011-09-22
> **dr1094 said:**
> Hi, I created a new account on ubuntu 11.04. In the home folder there are the regular 9 or 10 folders i.e. documents, pics, vids ,downloads, etc... 

I was using the computer and had to take a break, so I put the computer in suspend mode, came back after a while to find the home folder has many other folders in it with names like ".adobe" , ".cache" , and ".local" There are now 27 folders like this and a few files in the home folder (not including the original 9 folders). THese folders take up about 60 MB of space.

What are they? why are they there? Can I delete them? How do I ensure it won't happen again? and/or Can someone just make some sense of this to me, thanks

Some you can delete, thumbs for example, others you can not.

Actually most of them if you delete them you will loose any customization you made to your desktop or application options. Usually you will not break anything, you will simply reset them to the defaults , and the . or configuration files will re-appear when you next start an application or make a customization.

---

### Post by dr1094 on 2011-09-29
thank you all for replying, and a follow up question. Which folder/file is not to be deleted i.e. will cause serious harm to the operating system if deleted.

---

### Post by jocko on 2011-09-29
> **dr1094 said:**
> thank you all for replying, and a follow up question. Which folder/file is not to be deleted i.e. will cause serious harm to the operating system if deleted.
If you're still talking about the files and folders in your home directory, you can delete any of them without harming the operating system (but there are some files that are read-only so you can't delete them).
As others have already said, you'll just loose your personal settings for some applications, and the deleted file will be regenerated with the default settings the next time you start the application that uses that file...
If you as an example delete the ~/.mozilla folder you'll loose all your firefox settings (including bookmarks and saved passwords), but the folder itself will reappear the next time you start firefox (which now will have a completely new profile without any of your old settings).


If you're talking about files anywhere else in the file system: Unless you know **exactly** what you're doing, don't delete anything. Every single file is put there for a reason during the install of the operating system or an application, and removing a file will very likely break something.

---

### Post by dr1094 on 2011-09-29
thanks for the answers everyone.

---

