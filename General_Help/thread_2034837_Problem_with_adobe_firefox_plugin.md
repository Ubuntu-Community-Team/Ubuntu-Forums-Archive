---
title: "Problem with adobe firefox plugin"
date: 2012-07-29
forum: General Help
---

### Post by Azrael84 on 2012-07-29
Hi,

Since I upgraded to 12.04 every time I try to open a PDF through firefox (which I like to do quite often as I read a lot of PDF documents and downloading each then deleting is tiresome) I get the error message:

"Could not launch Adobe Reader 9.5.1. Please make sure it exists in PATH variable in the environment. If the problem persists, please reinstall the application."

How can I fix this?

thanks

---

### Post by Azrael84 on 2012-07-31
Anyone?

---

### Post by Azrael84 on 2012-08-07
If I launch firefox from the terminal the message it gives when attempting to open a PDF is:

"/usr/bin/acroread: 23: exec: /opt/Adobe/Reader9/Reader/intellinux/bin/acroread: Permission denied"

---

### Post by arrrghhh on 2012-09-26
Did you ever solve this?

I seemingly found one other reference to it, [here](http://www.tinyguru.com/unix/qid45011.html) and it did not seem to work.

On the machine that had the issue, I do notice quite a few updates are missing - one of them is a Firefox update.

Did you ever fix the issue?  Was it a Firefox update?

I checked permissions, and I can run acroread no problem... so I don't understand what the issue is.  In the link above, the guy seems *convinced* it's an apparmor issue.  I've never really dealt with apparmor, but I added the line and did a reload on the apparmor service - and no dice.

I'm waiting to hear back if the updates fixed it, but curious if anyone still has this problem.  Thanks!

---

### Post by arrrghhh on 2012-11-22
I am ***still*** struggling with this issue...

I found out more information.  If I run 'acroread' from the command line, no problems.  If I run /opt/Adobe/Reader9/bin/acroread from the command line, it works.  However, if I run /opt/Adobe/Reader9/Reader/intellinux/bin/acroread, it fails!!

```
/opt/Adobe/Reader9/Reader/intellinux/bin$ ./acroread 
./acroread: error while loading shared libraries: libBIB.so: cannot open shared object file: No such file or directory
```

This is really strange, as the other two executables are really just symlinks back to that executable that refused to run...

So what gives?  I get a permission denied in FF if I try to run acroread from within FF, so I definitely have a permissions issue somewhere - but where?  And why am I allowed to run acroread from cli yet FireFox fails to run it from the same locations?  Further more, why does that one fail when the others work!?!

Maddness.  Please, if someone has a suggestion I'm all ears.  I need Adobe Reader - envice doesn't cut it unfortunately...

---

### Post by arrrghhh on 2012-11-22
I ended up using [this addon](https://addons.mozilla.org/en-US/firefox/addon/pdfjs/) for Firefox...

Not the best solution, but I beat this thing up as much as I could today, and was not able to resolve it.  I installed from the Partner repo, from the Adobe site... didn't matter.

So the issue is still outstanding, but at least I have a workaround.  The user was very against Chrome, which has been suggested several times for having this type of feature built-in... Oh well.

---

