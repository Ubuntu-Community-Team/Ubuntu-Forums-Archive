---
title: "Convert old 'mbox' archives to a set of individual .eml files"
date: 2012-03-23
forum: General Help
---

### Post by Nickolai_Leschov on 2012-03-23
Hello,

I have an old mbox archive of a mailing list which is very valuable to  me. I need to convert it to a set of individual .eml files.

My "mbox" is a directory tree within each leaf of which is a small file. I believe such format was produced by Eudora.

I have installed Eudora OSE on Ubuntu to convert this archive. How should I go about it?

---

### Post by dcstar on 2012-03-24
> **Nickolai_Leschov said:**
> Hello,

I have an old mbox archive of a mailing list which is very valuable to  me. I need to convert it to a set of individual .eml files.

My "mbox" is a directory tree within each leaf of which is a small file. I believe such format was produced by Eudora.

I have installed Eudora OSE on Ubuntu to convert this archive. How should I go about it?

.EML is the ancient Microsoft Outlook Express format that no Linux program should have any need to Export, you'd be better looking for a Windows tool.

---

### Post by mike555 on 2012-03-24
This might do it;
[http://sourceforge.net/projects/ooconverter/?source=directory](http://sourceforge.net/projects/ooconverter/?source=directory)

---

### Post by SeijiSensei on 2012-03-24
> **Nickolai_Leschov said:**
> My "mbox" is a directory tree within each leaf of which is a small file. I believe such format was produced by Eudora.

I thought Eudora used the standard Unix mbox format where each "folder" consists of a single file with all the messages. Each message is delimited from the previous one by an extra return like this:

```

Return-Path: someone@example.com
[headers]

Message body


Return-Path: someone_else@example.com
etc.

```

If you open one of the Eudora files in a text editor, what do you see?

---

### Post by Nickolai_Leschov on 2012-03-24
Thank you for your replies.

I actually didn't want to specifically convert to .eml files, I wanted to convert to format that will be most likely understood by current and future mail programs and I thought .eml is that.

Here is the sample of my mailbox that I have taken.

When I open files in the editor, I see some HTML.

How do I go about converting it?

---

### Post by SeijiSensei on 2012-03-25
Those don't look at all like standard mbox files.  They must be a format unique to Eudora.

Here's what I'd suggest trying.  Create an account somewhere like gmail that uses IMAP, if you don't have an IMAP account already, and set up a connection to it in Eudora.  See if you can copy the individual messages from the Eudora folders to the IMAP account.  Then you can figure out what to do with them from there.  

.eml is, as far as I can tell, just a conventional ending used by clients like Thunderbird.  It simply contains a single message as a plain-text file.  There are really just two widely-used mailbox formats on Unix systems -- mbox and Maildir.  The first follows the format I described above, where all the messages are concatenated together in a single file delimited by an extra return.  Maildir uses directories to represent folders with the messages stored as individual files therein.

---

