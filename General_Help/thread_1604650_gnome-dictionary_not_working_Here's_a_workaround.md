---
title: "gnome-dictionary not working? Here's a workaround"
date: 2010-10-24
forum: General Help
---

### Post by Billsey on 2010-10-24
I recently discovered that I could not get gnome-dictionary to perform word look-up on ANY of my Ubuntu systems. Looking around on the web for help, I discovered that the problem is not with the app at all, but with the default source; dict.org has stopped functioning as gnome-dictionary expects (and trying to get to the web site just brings up a blank web page; page source is empty). One of the threads I saw in my search provided a different source that is working. It is not as extensive as dict.org's service, but it does work.

Open the Dictionary app, then open the Preferences dialog.

Go to the "Sources" Tab and click on the "Add" button.

In the dialog that opens, change the Description to "Chemnitz Server" (at least this is what I did).

Change the hostname to "dict.tu-chemnitz.de".

I did not mess with the other options.

Once you have done this you can click the "Close" button in that dialog.

In the remaining dialog, you will see a new option for "Chemnitz Server".

Select that, and you will have a working dictionary.



Hopefully, dict.org can soon be returned to its proper functionality.

---

### Post by rewyllys on 2010-10-24
> **Billsey said:**
> I recently discovered that I could not get gnome-dictionary to perform word look-up on ANY of my Ubuntu systems. . . .
Hopefully, dict.org can soon be returned to its proper functionality.
Many thanks for your solution.

I can add that installing Artha also provides a dictionary application, and it includes a nice thesaurus.  Artha is available via the Synaptic Package Manager.

---

### Post by wangsuda on 2010-10-24
Thanks for that - works like a charm!

---

### Post by banescusebi on 2010-10-24
It works, 10x :)

---

### Post by ninjasinloaf on 2010-10-24
Thank you!  It's not my favorite dictionary (and I already miss moby thesaurus), but it's doing the job.

---

### Post by rodolphoarruda on 2010-10-25
thanks! :)

---

### Post by ectospasm on 2010-10-25
You can also install your own dictd server on your local machine, and include whatever dictionaries (and thesauruses) you want:

```
# aptitude -y install dictd dict-moby-thesaurus dict-gcide
```

However, this isn't working for me right now, but YMMV.

EDIT:  I got it working by passing 127.0.0.1 instead of localhost as the server name.  Also, I had to install dict-gcide to get a comprehensive English dictionary

---

### Post by rjbl on 2010-10-26
@Billsey

Many thanks. it works fine. GBU

rjbl

---

### Post by Matt 6:27 on 2011-04-05
> **Billsey said:**
> I recently discovered that I could not get gnome-dictionary to perform word look-up on ANY of my Ubuntu systems. Looking around on the web for help, I discovered that the problem is not with the app at all, but with the default source; ...

Worked like a charm.  Thanks much!

---

