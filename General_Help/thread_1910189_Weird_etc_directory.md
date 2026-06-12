---
title: "Weird /etc directory"
date: 2012-01-16
forum: General Help
---

### Post by Diametric on 2012-01-16
Hello,

I'm pretty sure there should not be the following in my /etc directory:  /etc/etc/bash_completion.d

Correct?

I was mucking about and may have exported something I didn't mean to.  But, I'd like to make sure before I delete the extra /etc dir.

Thanks!

---

### Post by CharlesA on 2012-01-16
That's right. bash_completion.d should be in /etc/. Is there one there as well?

---

### Post by Diametric on 2012-01-16
Yes, there is.  I was following the following command in a book:

```
DIR_STACK=""
export DIR_STACK
```

SO, I don't know how that caused the extra directory, but I noticed it and was pretty sure it shouldn't be there

Thank you for your reply!

---

### Post by Diametric on 2012-01-16
Interestingly, there are two files in the extra etc dir.  In /etc/etc/bash_completion.d  are the following files, which are NOT in the main /etc/bash_copmpletion.d directory:

gdbus-bash-completion.sh  gsettings-bash-completion.sh

Can anyone shed some light on these files?  They appear to be legit bash files and I do not want to delete them if they're needed, but not sure what to do if they're in the faux /etc directory.

Thank you.

---

### Post by CharlesA on 2012-01-16
I'm not sure. I didn't look at my /etc directory that closely.

---

### Post by |{urse on 2012-01-16
Odd, yeah /etc/etc is not normal

---

### Post by Diametric on 2012-01-16
Anyone...Bueller?

---

### Post by WorMzy on 2012-01-16
Looks like a bug in Oneiric's libglib2.0-bin package. I'd [file a bug report]("https://help.ubuntu.com/community/ReportingBugs") if I were you.

---

### Post by Diametric on 2012-01-16
Fair enough - but I can't be sure it wasn't caused by me exporting the command I mentioned above. And I'd hate to submit it as a bug when I'm unsure.  I'm hoping that someone can confirm the where the two files I mention are supposed to reside - that way I can move them, then delete the incorrect etc directory.

---

### Post by CharlesA on 2012-01-16
You just cleared a variable, which shouldn't create anything.

Sounds like the bug that WorMzy mentioned.

---

### Post by WorMzy on 2012-01-17
> **Diametric said:**
> Fair enough - but I can't be sure it wasn't caused by me exporting the command I mentioned above.


Don't worry, it wasn't. Everyone with that package installed (and up-to-date?) on Oneiric has that strange directory set up: [http://packages.ubuntu.com/oneiric/amd64/libglib2.0-bin/filelist](http://packages.ubuntu.com/oneiric/amd64/libglib2.0-bin/filelist)

---

### Post by Diametric on 2012-01-17
Ah - thanks for the replies.  I guess I'll leave it alone until a fix is suggested.  

Cheers!

---

