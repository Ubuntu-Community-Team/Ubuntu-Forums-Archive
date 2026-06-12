---
title: "How do I delete a specific email in Evoution using Terminal?"
date: 2010-02-18
forum: General Help
---

### Post by sallymc on 2010-02-18
Hi

Somebody has sent me an email that crashes Evolution.  When I click on the email, that's it - I have to end the Evolution process and go back in again.  Definitely can't double click it, or right-click to delete or simply delete.   It just freezes.  I can't see any of the text of the email, but I can see that there is a .tiff attachment.

I've poked around in the .evolution/ folders and can't find the right thing to delete to get rid of this specific email.  Any ideas?

Using 9.10

Thanks!

---

### Post by gordintoronto on 2010-02-18
Each mail folder, such as "inbox" is a single file in Evolution.

Some people think Thunderbird is more robust, so you could consider switching to it.  Instructions to copy everything over are here:
[http://maketecheasier.com/how-to-migrate-from-evolution-to-thunderbird-in-ubuntu-intrepid/2008/12/04](http://maketecheasier.com/how-to-migrate-from-evolution-to-thunderbird-in-ubuntu-intrepid/2008/12/04)

---

### Post by sallymc on 2010-02-19
I posted another thread today, different caption, and solved the problem as follows :

Quote:
 	 	 		 			 				 					Originally Posted by **mechro** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8850721#post8850721") 				
 				[I]It looks like a bug...

[https://bugs.launchpad.net/ubuntu/+s....0/+bug/445435]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/445435")

Have you regularly installed updates?

A workaround mentioned is to change your desktop theme... strange, but that's what it says![/I]
 			 		 	 	 
Oh Mechro you are SO clever - you hit the nail on the head. I changed the Desktop theme, the email revealed itself and I then deleted it with ease. All back to normal.
Many thanks indeed.  
Sallymc   xx

---

