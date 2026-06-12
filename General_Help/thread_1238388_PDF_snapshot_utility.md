---
title: "PDF snapshot utility"
date: 2009-08-12
forum: General Help
---

### Post by cgonagu on 2009-08-12
Hi all!

This is my first post, so I am not really sure where it should be placed. I apologize for this temporary inconvenience. 

My question is related to Acrobat PDF. In the Professional version of this software, you can select some region of a PDF document, use the "Snapshot" tool and create a new PDF file from the region you have selected. 

I was wondering whether is there any software in Ubuntu that allows to do this. Obviously, I guess that the Profesional version of Acrobat could do it, but I was looking for something free!

Thanks in advance!

---

### Post by Tamlynmac on 2009-08-12
You might take a look at PDFedit. It's in the repositories "Synaptic Package Manager".

Hope this helps.

---

### Post by kaibob on 2009-08-12
I do not know of any PDF reader/editor with that ability. You can easily do it with the following command line, which can be assigned to a panel icon or keyboard key:

```
import -frame -compress zip filename.pdf
```

You can try this out by entering the above command line in a terminal window. Then, select the area of the screen that you want saved. I don't know if the import utility, which is a part of the Imagemagick suite, is installed by default. If not, it's in the repo's.

---

### Post by cgonagu on 2009-08-13
I didn't found out how to use PDFedit properly to solve my point.

But the thing from the command line with "import" works perfectly!! 
Thanks!!

---

