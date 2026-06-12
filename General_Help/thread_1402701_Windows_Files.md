---
title: "Windows Files"
date: 2010-02-09
forum: General Help
---

### Post by Lordofsraam on 2010-02-09
I'm running Ubuntu 9.1 as a Wubi installation from Windows 7. All my music, vids, etc. are still in my hard drive and I can access them from Windows, but Ubuntu won't let me see them. 
I have installed the NTFS congfig tool but it can't find the the original windows drive. I have also tried setting my C: drive to "shared" in windows but that's not working either. Can someone please tell me what to do?

---

### Post by unmole on 2010-02-09
Open your 'Home' folder (or any other folder for that matter). Just below the 'Back' button, there is a button with an icon which looks  like a pen over a piece of paper, click it. You should now see a text based location of where you are. Replace the contents of this "Location bar" with ```
/host
```. This will now show you the windows files on the partition on which you installed wubi.

Hope that helps.

---

### Post by sailthesea on 2010-02-09
Whilst in Ubuntu browse the system files (enable see hidden files just to be sure) and look for a folder called "Host" open it and your windows stuff is in there! Unless Wubi has changed a lot since I used it last you can access NTFS and even save stuff to there as well
 Hope this helps 
 And Welcome!
:)

---

