---
title: "Change or delete obsolete system file type"
date: 2010-05-23
forum: General Help
---

### Post by davejacobs on 2010-05-23
I use Markdown to store all of my source documents. Unfortunately, the .md extension maps to application/x-genesis-rom under Ubuntu. I'm not sure why that would be a system default MIME type, but I'd like to change it.

I've tried using:

```
gksu assogiate
```

to modify my file type cache. Unfortunately, even as the SU, I can't modify the entry for this file type. The "Remove" button is inactivated for the entry. (**See attachment**.)

How can I get rid of this (obsolete?) file association? Alternatively, how can I make my new one (text/x-markdown) take precedence?

---

### Post by bobcollard on 2010-05-23
> **davejacobs said:**
> I use Markdown to store all of my source documents. Unfortunately, the .md extension maps to application/x-genesis-rom under Ubuntu. I'm not sure why that would be a system default MIME type, but I'd like to change it.

I've tried using:

```
gksu assogiate
```to modify my file type cache. Unfortunately, even as the SU, I can't modify the entry for this file type. The "Remove" button is inactivated for the entry. (**See attachment**.)

How can I get rid of this (obsolete?) file association? Alternatively, how can I make my new one (text/x-markdown) take precedence?
You might try using your File Manager in terminal.  Mine is Thunar so the access in Terminal via root is :
```
gksu thunar
```
In the File manager you should be able to delete or rename any file at the root level.

---

### Post by davejacobs on 2010-05-24
> **bobcollard said:**
> You might try using your File Manager in terminal.  Mine is Thunar so the access in Terminal via root is :
```
gksu thunar
```
In the File manager you should be able to delete or rename any file at the root level.

Bob, thanks for the advice.

I ended up reading more about the MIME system specifically and found a solution to my problem.

So, for the record:

The easiest way to change a MIME type is by adding your own entry under /usr/share/mime/packages. (Requires super-user access.) After adding an XML entry for your MIME type (use one of the other XML files in the packages folder as a reference), you simply update the database, making your MIME type take precedence:

```
sudo update-mime-database /usr/share/mime
```

For more information on customizing a MIME type, see [the Gnome MIME database introduction]("http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-database.html.en") and [the discussion about source files]("http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-source-xml.html.en").

---

### Post by zhemao on 2011-06-05
I haven't been able to create a new mime type for markdown, but I've figured out how to stop *.md from being associated with genesis ROM. Open /usr/share/mime/packages/freedesktop.org.xml for editing with superuser privileges. Find the line <glob pattern="*.md"/> and remove it. Then run sudo update-mime-database /usr/share/mime. After doing this, *.md is recognized as text/plain instead of application/x-genesis-rom.

---

### Post by davejacobs on 2011-06-05
Following the directions above should let you create a MIME type. What seems to be the problem?

---

### Post by sergio91pt on 2011-09-10
I was checking [https://bugs.launchpad.net/shared-mime-info/+bug/611763](https://bugs.launchpad.net/shared-mime-info/+bug/611763) when I saw a link to this thread and why not share my recipe for this?

• Choose $LOC:
&#8728; export LOC=/usr/local/share/mime
&#8728; export LOC=~/.local/share/mime
&#8728; export LOC=/usr/share/mime
• mkdir -p $LOC/packages
• wget -P $LOC/packages [http://dl.dropbox.com/u/3790279/dl/markdown.xml](http://dl.dropbox.com/u/3790279/dl/markdown.xml)
• update-mime-database $LOC
• unset LOC

I actually read part of the specification #-o

---

