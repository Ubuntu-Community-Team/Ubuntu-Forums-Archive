---
title: "All files disappeared?!? Help?"
date: 2010-06-18
forum: General Help
---

### Post by MetapostAddict on 2010-06-18
I dual boot Ubunto 10.04 and windows 7.  I have a separate partition where I store all my documents, music, photos and videos, so that I can access them using windows or ubuntu.  

Now, all the files in the documents folder have disappeared.  The folder structure is still there, including all subfolders in the documents folder, but everything that was in the folders is gone.  The music, photos, and videos are all still there.

I recently tried to set up Ubuntu One.  Could it have somehow done this?

I greatly appreciate any help!

Postscript:
I'm glad to realize that a recent simple backup had saved my data.

---

### Post by teilnehmer on 2010-06-18
I never tried Ubuntu One, but your suspicion may be true... Maybe it's just a link that's missing, so your documents are still there, but the partition is not mounted. 

Do you see the files when in Windows? This would be a clue that the files have not been deleted. 

In Ubuntu, when you take a look at /etc/fstab (just look, don't change anything without knowing what you're doing :) ), where is you data partition mounted?

Also, I'm not sure if only the Documents folder is empty, or music, photos, videos as well. 

Best regards, 

Jan

---

