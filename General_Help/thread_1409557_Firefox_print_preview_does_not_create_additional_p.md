---
title: "Firefox print preview does not create additional pages when needed"
date: 2010-02-17
forum: General Help
---

### Post by alecz20 on 2010-02-17
I need to print the tax forms from our University.

There is the option to select a "printable form", but the form is much larger than any paper the printer supports. 

If I use "Print Preview" in Firefox, it creates only one page that contains the beginning of the form, and ignores the rest of the form.

If I do the exact same thing on a Windows machine, Firefox creates as many pages as necessary when I click "Print Preview"

I feel that this problem is not because of Firefox, but because of how "Print Preview" works on Ubuntu.


How can I get the print preview to create additional pages to include the entire text when I click "Print Preview" ?

---

### Post by dcstar on 2010-02-18
> **alecz20 said:**
> I need to print the tax forms from out University.

There is the option to select a "printable form", but the form is much larger than any paper the printer supports. 

If I use "Print Preview" in Firefox, it creates only one page that contains the beginning of the form, and ignores the rest of the form.

If I do the exact same thing on a Windows machine, Firefox creates as many pages as necessary when I click "Print Preview"

I feel that this problem is not because of Firefox, but because of how "Print Preview" works on Ubuntu.


How can I get the print preview to create additional pages to include the entire text when I click "Print Preview" ?

Sometimes the Firefox profile gets corrupted. Look in the (hidden) .mozilla folder and rename the existing profile so Firefox creates a fresh one when it starts and see if that fixes it.

---

### Post by alecz20 on 2010-02-18
Thanks, that fixed the problem.

But now all my settings, add-ons, extensions, bookmarks, and passwords are gone.

If only I knew what the bad file was.

---

### Post by dcstar on 2010-02-18
> **alecz20 said:**
> Thanks, that fixed the problem.

But now all my settings, add-ons, extensions, bookmarks, and passwords are gone.

If only I knew what the bad file was.

You can move/copy those files back from the renamed profile. The folders for some are obvious, you can also use the Bookmark import/restore function on the old folder.

You should be able to get 99% of it back using a bit of trial and error file copying.

---

