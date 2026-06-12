---
title: "Deleting files in root"
date: 2012-10-12
forum: General Help
---

### Post by Dark_Horizon on 2012-10-12
As it transpired not as easy as it would appear,

Firstly I had recovered a load of files from the HD since I rather cleverly deleted an entire folder after just having downloaded it from the server, I did this by using a Nautilus extension "Delete" this was to save time putting things in the Trash, not wishing to spent the next bejeebuz amount of time downloading it again I thought recovery would be the answer, so I used photorec unfortunately it found all the other files but the one I was searching for and left my harddrive moaning under the weight of recovered data.

Its amazing just how much Ubuntu 12.04 just flags as not there just like windows so I thought it might be good to delete these files so I could spend the bjeebuz time downloading it again, this is where the real trouble started. having deleted an entire 6gig file I thought getting rid of this would be a doddle unfortunately not because to recover the useless files requires root privileges.

"  gksudo nautilus ‘/root   "

so I went in and deleted the offending large file, then discovered that I could not access it  in the root trash. so I went in search of the .Trash file found the expunged files cut and paste into my home folder again. came out of root and discovered I didn’t have the necessary rights to delete it again Donald Duck he said loudly in the early hours of the morning, so back into root move the files back again then change their user rights in root by going to properties /permissions and changing it all there, then putting it back in my home folder coming out of root going to home and deleting the offending file.

Which worked, the moral of the story is don’t use nautilus extensions send things to the trash first so you can retrieve it later if need be. and you wont find yourself  off to download a gazillion files before anyone finds out.

I just thought I'd share this with you. deleting files by accident is bad enough but doing it in root is insanely complicated.

---

### Post by cjhabs on 2012-10-12
When I need to do something like that I do it from the command line, which skips the trash. You do need to be careful, particularly when using wild cards like * - so I tend to use the "-i" switch to the "rm" command so it prompts for each file it is about to delete. Of course you need to use sudo for this.

---

### Post by jerome1232 on 2012-10-12
shift+delete; it bypasses trash.

---

