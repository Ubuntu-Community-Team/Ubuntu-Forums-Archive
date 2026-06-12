---
title: "How to change default 'open-with' for .jar to openjdk ?"
date: 2012-07-11
forum: General Help
---

### Post by ubnewbie2 on 2012-07-11
I have looked under properties on the open with tab, but openjdk (or any form of java) doesn't show up as a choice.  It is installed, and I am using it, but I have to manually choose open with on the context menu each time.  I just want to make it the default (instead of archive manager).

---

### Post by OM55 on 2012-07-11
Hello ubnewbie2,

> **ubnewbie2 said:**
> I have looked under properties on the open with tab, but openjdk (or any form of java) doesn't show up as a choice.  It is installed, and I am using it, but I have to manually choose open with on the context menu each time.  I just want to make it the default (instead of archive manager).

The easy way would be to instal Ubuntu-Tweak and change the setting there. 

1. To accomplish that go to: [http://ubuntu-tweak.com](http://ubuntu-tweak.com) and download the latest Ubuntu Tweak version (currently 0.7.2). To install just double click on the downloaded '.deb' file.

2. You can launch it from the menu (if not using Unity) or from the command line by typing:
```
ubuntu-tweak
```3. While in Ubuntu Tweak click on the "Admin" tab (at the top) and then on "File Type Manager" (at the lower left). Then in categories select "All" - After this last step it may seem as if Ubuntu Tweak froze, but be patient, it is just collecting the data on all different file types associations in your system. 

4. When the process is done you will see all file types sorted alphabetically. Scroll down to find your specific file type. It may be listed by the name of the association, not necessarily the file type.

5. Highlight the selection and click on the 'Edit' button (lower-right). Then simply select from the list. Notice that there is no 'OK' button, once you select the new file association the change has been made. 

6. If the desired application is not listed, click on the 'Add' button. If the desired application is yet not listed in the list of available additional applications, just select 'Command Line' and either type in the file name of the desired application (it has to be in the search list) or the full path to the binary file of the application. 

One way or the other, Ubuntu Tweak makes it very easy to change file type associations, as well as other little tweaks.

Hope that helps!

---

### Post by ubnewbie2 on 2012-07-11
Brilliant.

Thanks for taking the time to explain that.  I already had Ubuntu Tweak, but haven't discovered everything it can do yet.

All fixed.

---

### Post by OM55 on 2012-07-11
Glad I was able to help!

---

