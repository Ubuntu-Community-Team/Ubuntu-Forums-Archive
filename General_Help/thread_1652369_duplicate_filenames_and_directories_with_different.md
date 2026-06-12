---
title: "duplicate filenames and directories with different case"
date: 2010-12-24
forum: General Help
---

### Post by angelofarina on 2010-12-24
I decided to post her after two hours of googling for searching a solution, and many searches here on Ubuntu Forums.
I have two Ubuntu Linux machines, one at home, one at the University. Both are used mostly as large file servers, where all our laptops are periodically backed up.
As some laptops run Windows, some are Mac, and some are various types of Linux, we always have problems with lowercase/uppercase compatibility.
It often occurs that on the Linux server duplicate directories are created, for example /papers/aes and /Papers/AES. Also duplicate file names appear, in the same directory or in the above different-case directories, such as Paper128.PDF and paper128.pdf.
This way, a lot of storage space is wasted, and also the older version of a file is maintained, instead of being superseded by the newer one, if the latter has different case.
I did not find the way to make the Ubuntu Server machines to be case-agnostic.
And now, after years of usage, these duplications are counting at approximately 10,000 files, for more than 100 Gbytes space, so I cannot ever attempt to manually re-merge the duplicate directories or manually remove the older files...
So the question is: does anyone know of an application or a script which takes care of this mess, reunificating the duplicate-name directories and destroying the older files with the same name? 
Please note that the lowercase or uppercase do not really have any meaning on my machines, they were used just for aesthetic reasons. So it is perfectly acceptable for me to loose this aesthetic effect: I will be happy if, after removing the duplications, I end up with file names and directory names all-lowercase...

---

### Post by dcstar on 2010-12-25
> **angelofarina said:**
> I decided to post her after two hours of googling for searching a solution, and many searches here on Ubuntu Forums.
I have two Ubuntu Linux machines, one at home, one at the University. Both are used mostly as large file servers, where all our laptops are periodically backed up.
**As some laptops run Windows, some are Mac, and some are various types of Linux, we always have problems with lowercase/uppercase compatibility**.
It often occurs that on the Linux server duplicate directories are created, for example /papers/aes and /Papers/AES. Also duplicate file names appear, in the same directory or in the above different-case directories, such as Paper128.PDF and paper128.pdf.
This way, a lot of storage space is wasted, and also the older version of a file is maintained, instead of being superseded by the newer one, if the latter has different case.
I did not find the way to make the Ubuntu Server machines to be case-agnostic.
.........

On the assumption that you are referring to Samba shares running on the Linux machines, then:

[http://oreilly.com/catalog/samba/chapter/book/ch05_04.html](http://oreilly.com/catalog/samba/chapter/book/ch05_04.html)

---

### Post by angelofarina on 2010-12-25
Ok, thanks, at least this page did finally explain what was the cause of the problem. I discovered that in my smb.conf file the setting was "preserve case = no", whilst the default value should be yes.
As some clients did connect sometimes through Samba for their backup, sometimes through FTP or SFTP (from home), the same filename on the client machine resulted in duplicate names on the server...
Now I restored the correct setting "preserve case = yes", so in the future this "name degeneration" should not increase further.

However, although this did explain the origin of the problem, it does not provide an evident solution for recomposing my degenerated filesystem...
Any other suggestion for removing as automatically as possible all these duplicates?

---

