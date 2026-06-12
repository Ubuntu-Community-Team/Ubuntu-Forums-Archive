---
title: "Copying and pasting multiple lines from a file into a new emacs file"
date: 2012-05-16
forum: General Help
---

### Post by GammaPoint on 2012-05-16
Hi, I've got lots of text files that I need to copy and paste select regions into a new file (using emacs). If I simply open the original files with 'more', and then highlight the text and then drop it into a new file (opened with emacs) I get line breaks in the middle of my lines (the size of my terminal window determines how many linebreaks I have of course). Is there a good way around this, using a similar method as I'm using? Of course I can simply cat files together and then delete what I don't want, but I'm putting new information in the middle of a file and not necessarily building it from the beginning to the end. Any suggestions?

---

### Post by sjuranic on 2012-05-16
Is there any reason you can't open the files you want to copy from in Emacs as well?  Then you just copy and paste within Emacs.  Emacs should ignore the "soft" line breaks that the terminal would otherwise insert.

---

### Post by GammaPoint on 2012-05-16
> **sjuranic said:**
> Is there any reason you can't open the files you want to copy from in Emacs as well?  Then you just copy and paste within Emacs.  Emacs should ignore the "soft" line breaks that the terminal would otherwise insert.

Well okay, I did not know that would work. Figured it was just a copy and paste problem. Thanks, I'm good now :)

---

### Post by sjuranic on 2012-05-16
Emacs is an extremely powerful tool (it's basically a LISP interpreter with file editing functions built in).  I run my terminal inside Emacs itself so I don't have to worry about ever using my mouse unless I'm browsing the web.

You can use Emacs as a web browser as well, but I personally think that those guys are just a little crazy. :-)

---

