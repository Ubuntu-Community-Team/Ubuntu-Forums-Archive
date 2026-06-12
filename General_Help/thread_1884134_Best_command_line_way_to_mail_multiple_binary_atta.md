---
title: "Best command line way to mail multiple binary attachments (JPG files)"
date: 2011-11-20
forum: General Help
---

### Post by rocksockdoc on 2011-11-20
I often send batches of pictures to family & friends and would like an email command to add to a photo editing script I'm working on.

The script that I'm trying to improve is located here:

[LIST]
[*][Stringing commands together to manage typical digital photo operations]("http://ubuntuforums.org/showthread.php?t=1839153")
[/LIST]
The next task to improve is to encode (mime? uue? zip?) the dozen (or so) JPEG files in known specified directories (one for 'family', another for 'friends'), to send them as inline attachments so that the recipient, on most mail user agents, can simply view the files inline, separately (i.e., not combined into a hard-to-manage-for-most-people single zip or tgz file).

While I can easily manually attach multiple files in Thunderbird, I haven't found any Thunderbird command-line arguments that will do so.

What initially comes to mind is something like this:
% mail -s "Pics of the kids" family_alias < ./email/family/*.jpg

But, there are two problems with that approach to be solved:
a) The individual jpg files need to be encoded for mailing before mailing
b) The individual file names won't be known ahead of time (it will simply be all files in that directory)

Any suggestions?

---

### Post by rocksockdoc on 2011-11-20
I just installed "[mutt]("http://www.shelldorado.com/articles/mailattachments.html")" from the "Ubuntu Software Center" (mimencode and metamail didn't seem to be easily found options).

Mutt will probably do what I need with the "-a" attach option.

I will edit this with the current solution once I figure it out.

EDIT: So far, this is what I can insert into my bash script (which will only work for a single binary file so I need to improve it somehow to take EVERY JPG in the specified directory & to identify the content type accurately for the mail recipient's mail user agent to decode properly):

mutt -s "Photos of the kids" -a ./email/family/*.JPG family_alias < /tmp/family_email_body.txt

---

