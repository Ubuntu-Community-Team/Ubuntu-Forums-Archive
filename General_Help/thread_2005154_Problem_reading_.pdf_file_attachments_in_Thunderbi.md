---
title: "Problem reading .pdf file attachments in Thunderbird [10.04 &amp; 12.04]"
date: 2012-06-17
forum: General Help
---

### Post by F W Adams on 2012-06-17
Normally with reading attachments to incoming emails one can just double left click the file name and all is well but with .pdf files this doesn't seem to work.

I am getting the message:
"/tmp/xxxx.pdf could not be opened, because the associated helper application does not exist. Change the association in your preferences."

All attachments seem to be moved to /tmp before reading. With other file types, .docx for example, there is no problem.

The system is of course set up to read .pdf files. The problem can be got round by right clicking the attachment and then selecting "save as" and then going to the saved file and reading it but this is annoying and not quite the point.

The error occurs in 10.04 & 12.04 but was working in earlier versions.

---

### Post by F W Adams on 2012-06-17
Solved my own problem, Thunderbird can use a variety of programs to read PDF documents and they don't all work?

In my case I had to first find the location of my .pdf reader, open a terminal and type in

> type name_of_pdf_reader

Make a note of the location given.

Then in Thunderbird go to "Edit/Preferences/Attachments" and highlight "PDF document"

Select your program, In my case it was "/usr/bin/acroread"

Problem fixed.

Thanks to, could also look at:
[http://groups.google.com/group/mozilla.support.thunderbird/browse_thread/thread/81413e5232bc15e0](http://groups.google.com/group/mozilla.support.thunderbird/browse_thread/thread/81413e5232bc15e0)

---

