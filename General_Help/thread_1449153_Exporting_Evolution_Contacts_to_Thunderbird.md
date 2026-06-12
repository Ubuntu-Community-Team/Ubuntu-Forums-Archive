---
title: "Exporting Evolution Contacts to Thunderbird"
date: 2010-04-07
forum: General Help
---

### Post by HippieDave on 2010-04-07
I am trying to figure out how I can export my evolution contacts information into a Thunderbird application on my desktop (at work).  I back up the files onto a flashdrive into the evolution-backup.tar file which Evolution uses as the default backup file. But Thunderbird doesn't recognize the file type.  Anything I can do?

---

### Post by terrrorr on 2010-04-07
Hi,

I do not want to be mean, but do you know what kind of file tar is? If you don't then I recommend to see link below

[http://en.wikipedia.org/wiki/TAR_file_format]("http://en.wikipedia.org/wiki/TAR_file_format")

Here is how I would do it

1. Import all data back to Evolution mail (If you haven't done it already)
2. Export your contacts using **evolution-addressbook-export** tool (use your terminal)
3. Import your cvs file into your Thunderbird from Tools->Import...

Please let me know if you need more detailed instructions

---

### Post by dcstar on 2010-04-07
> **HippieDave said:**
> I am trying to figure out how I can export my evolution contacts information into a Thunderbird application on my desktop (at work).  I back up the files onto a flashdrive into the evolution-backup.tar file which Evolution uses as the default backup file. But Thunderbird doesn't recognize the file type.  Anything I can do?

You can save any/all of your Contacts as vCard files, that should be able to be used by just about anything.

---

### Post by winjeel on 2010-05-02
This doesn't work for me. Thunderbird wants to import from other Mozilla products. I've got my Evolution exported as tar.gz, so what do I do with it, now?

---

### Post by scouser73 on 2010-05-02
Check this website for help: [[COLOR="Red"]**Exporting Evolution Contacts To Thunderbird**[/COLOR]]("http://ryandaigle.com/articles/2006/5/16/exporting-evolution-contacts-to-thunderbird")

---

### Post by winjeel on 2010-05-02
Thanks, but I was hoping to be able to import the whole lock, stock, and barrel, not just the contacts. This is starting to be a bit of a miscommunication or mismanagement on the part of Canonical. I didn't have a problem with Evolution, it worked fine for me.

---

