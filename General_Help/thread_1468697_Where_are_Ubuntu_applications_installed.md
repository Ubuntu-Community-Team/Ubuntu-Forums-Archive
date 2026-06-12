---
title: "Where are Ubuntu applications installed?"
date: 2010-05-01
forum: General Help
---

### Post by sgsawant on 2010-05-01
I tried to download a .pdf file from a website. Then I wanted to open it not with the default document viewer but using "Okular" (just a personal preference).

So in Firefox, I clicked the"Open with>(Drop down)>Other". Now had I been operating Windows, I would have headed to something like "C:\Program Files\Okular\Okular.exe". But in Ubuntu I don't know where to go. Can someone help?

Regards,

-sgsawant

---

### Post by Kilz on 2010-05-01
That depends on what else you have installed to read pdf's, but if you are using kde okular will be the default application.

---

### Post by Rasa1111 on 2010-05-01
can you open "Okular" first..
and simply 'drag' the PDF file into it? 

 I think that should work.

---

### Post by todak on 2010-05-01
Most programs are stored in */usr/bin*. However, you do not need to hunt for the location of the app. Simply type the word *okular* into the space. That will only be for that instance. If you want to use okular to open all of you PDFs, then right-click on a PDF that you have saved, choose *Properties* then click on the *Open With* tab and choose okular. Okular will then be the default PDF viewer for you.

---

### Post by sgsawant on 2010-05-01
@todak:

Thanks! 

I browsed through to: "/usr/bin/okular". That did it!

Regards.

---

