---
title: "Opening PDF files from the Internet fails"
date: 2009-12-30
forum: General Help
---

### Post by DrScum on 2009-12-30
When I try to open PDF files from the internet, I get the following message:

"/tmp/MAT_Elektronenkonfiguration-1.pdf could not be opened, because the associated helper application does not exist. Change the association in your preferences".

The default helper app. for PDF's is evince document viewer. 
When I download the file I can open it with the evince document viewer.
The associacion in the mozilla preferences is set correctly. 

Does anyone have an idea what I could do?

---

### Post by s.fox on 2009-12-30
Hello,

[This]("http://kb.mozillazine.org/The_associated_helper_application_does_not_exist") page should help you solve the problem.  If you run into any more difficulties please post back :)

-Silver Fox

P.S.  I assume you are using Firefox,  the document should open if other browsers such as Opera just fine.

---

### Post by DrScum on 2009-12-30
Thanks for the help. I visited the page and did as instructed however, it didn't work the way described. Here are the problems I had to deal with (this is for people who visit this thread with the same problem I had):

On the mozillaZine page it says to locate the Firefox preferences under Tools > Options, which is not correct you find them under Edit > Preferences > Applications.

As default application for PDF files I had selected "Document Viewer" which is the default setting but didn't work.
 
I changed it to "evince" by using the "other" option and locating the evince program under usr/bin/ which still didn't help. 

I deleted the mimeTypes.rdf file in the profile folder (as described on the mozillaZine page) and restarted firefox. The newly generated mimeTypes.rdf didn't have any option for PDF files. To create one I had to attempt to download a PDF file, select evince as the application and check the box "do this automatically for files like this from now on"

Now it works.

---

### Post by Dangger on 2010-06-07
> **DrScum said:**
> To create one I had to attempt to download a PDF file, select evince as the application and check the box "do this automatically for files like this from now on"

Now it works.


The location for evince is ```
usr/bin/evince 
```just in case people are looking for it.

---

### Post by TheCat on 2010-07-26
A bug and patch have been filed at Mozilla.

[https://bugs.launchpad.net/firefox/+bug/239952?comments=all](https://bugs.launchpad.net/firefox/+bug/239952?comments=all)

I can confirm that this is still a problem with Ubuntu 10.04 and Firefox 3.6.7.

---

