---
title: "MS Office 2007 &quot;Open With...&quot;"
date: 2010-03-04
forum: General Help
---

### Post by phil13 on 2010-03-04
Hi

I've installed office2007 on ubuntu 9.10 by following this tutorial:
[http://www.mikesouthby.co.uk/2009/11/ubuntu-9-10-installing-microsoft-office-2007/](http://www.mikesouthby.co.uk/2009/11/ubuntu-9-10-installing-microsoft-office-2007/)

I've changed the default office program to MS word by right clicking on a .doc file, going to properties etc

My problem is that when I try to open a file through the ubuntu explorer (so actually clicking on the icon) it comes up with an error message "cannot find z:\home\desktop\my" and some other similar messages. My 'my documents' folder is currently saved on the desktop (copied from external hdd) and the program is obviously having problems with spaces in filenames (I tried making a document 'xyz.doc' and saving it to my desktop and it opened fine). I can currently open files by first launching word then going to file>>>open etc

Can anyone help me with this? Do I need to move the files to my virtual C drive create by wine?

Thanks very much in advance! I managed to format our hard disk only to discover that I'd lost our windows xp home product key = great time to try out ubuntu. Only thing is I've got to get my dad set up on it so ms office is something of a must.

Thanks again

---

### Post by cjhabs on 2010-03-04
> **phil13 said:**
> Hi

I've installed office2007 on ubuntu 9.10 by following this tutorial:
[http://www.mikesouthby.co.uk/2009/11/ubuntu-9-10-installing-microsoft-office-2007/](http://www.mikesouthby.co.uk/2009/11/ubuntu-9-10-installing-microsoft-office-2007/)

I've changed the default office program to MS word by right clicking on a .doc file, going to properties etc

My problem is that when I try to open a file through the ubuntu explorer (so actually clicking on the icon) it comes up with an error message "cannot find z:\home\desktop\my" and some other similar messages. My 'my documents' folder is currently saved on the desktop (copied from external hdd) and the program is obviously having problems with spaces in filenames (I tried making a document 'xyz.doc' and saving it to my desktop and it opened fine). I can currently open files by first launching word then going to file>>>open etc

Can anyone help me with this? Do I need to move the files to my virtual C drive create by wine?

Thanks very much in advance! I managed to format our hard disk only to discover that I'd lost our windows xp home product key = great time to try out ubuntu. Only thing is I've got to get my dad set up on it so ms office is something of a must.

Thanks again

I'm guessing that the space in the "My Documents" folder name is confusing things. Try renaming that folder to remove the space and try again.

---

### Post by phil13 on 2010-03-04
There is also a problem with the filenames - any filename with two words in it fails to open. Short of renaming *everything* and replacing the spaces with underscores I can't see a way round this problem. I guess I could just download a program to rename everything but it's kind of annoying!

---

### Post by cjhabs on 2010-03-04
> **phil13 said:**
> There is also a problem with the filenames - any filename with two words in it fails to open. Short of renaming *everything* and replacing the spaces with underscores I can't see a way round this problem. I guess I could just download a program to rename everything but it's kind of annoying!

I don't know why you have this problem, but to rename all the files should be easy. Go to the root folder of where your "spacey" files are stored and do:
find . -name '* *' -exec rename "s/ /_/g" {} \;

You should test this first. Also, it only handles a single space in a name. If you run it multiple times, it will get rid of a space at a time :-) replacing each space with an underscore.

---

