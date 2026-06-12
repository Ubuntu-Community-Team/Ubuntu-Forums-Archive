---
title: "Accessing files"
date: 2010-07-29
forum: General Help
---

### Post by primetime34 on 2010-07-29
Fairly new to Ubuntu and I have a quick question. I have XP in virtual box and I just installed Office.  I now need to access the office files I have in my windows partition on the computer.  How can I do this?

---

### Post by primetime34 on 2010-07-29
A little more information.  I am able to see one partition in my windows drive however I can't see the others.  My HP machine has multiple partitions on my hard drive for the windows install (system reserved, c drive, and recovery drive).  The 'system reserved' drive is easily seen in Ubuntu but I can't see the 'C' drive.  I installed using wubi.  Any help?

---

### Post by -kg- on 2010-07-29
You have seriously confused me! :???:  Let me see if I've got this straight:

> I installed using wubi...

I have XP in virtual box and I just installed Office...

I now need to access the office files I have in my windows partition on the computer...

OK, I'm not sure I know what you're trying to do here.  If you installed using Wubi, then Ubuntu is installed in a folder on the Windows C: drive and is running under Windows.  I don't know how you would navigate to the rest of the folders on that drive, since I've never installed using Wubi, but I would assume that it would be a part of either root or /home.

Have you looked under "Removable Media"?  Have you pulled up "Computer" under "Places" and see what might be there?  You might be able to find the path that way and know where to look when accessing your files with Office.

What has me confused is why you would need to do that in the first place.  Can't you just boot into Windows and handle it?  Or are you experimenting with it?

If you're experimenting with it, it would be infinitely better to install Ubuntu regularly instead of with Wubi.  I don't know whether Office will run right under Wine, but using it under a Wubi installation might complicate that.  It might also complicate accessing files on the rest of the C: drive...you'd minimally have to go above the Ubuntu folder, and I don't know whether Ubuntu will recognize a "God" (i.e., go above the root directory it's running in). :p

<Edit>  Since Google is my friend, I found this from the [Wubi website]("http://wubi-installer.org/faq.php"):

> 
Can I access my Windows files from a Wubi installation?

Yes, the Windows partitions will be available within the directories /host and /media.


---

