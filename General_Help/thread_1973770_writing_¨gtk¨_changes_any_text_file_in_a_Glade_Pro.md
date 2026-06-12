---
title: "writing ¨gtk¨ changes any text file in a Glade Project"
date: 2012-05-05
forum: General Help
---

### Post by grossogrossum on 2012-05-05
Excuse my bad,bad,bad english, please. I hope you can understand me.

My problem is simple: if I write ¨gtk¨ (or sdfslkjsdifj**gtk**sfsfkls) in a text file it automatically changes to a Glade Project in XML format, and I can't change to sh or simple text. My scripts don't work because this. 
This happens after  a clean installation using 12.04, with no previous configuration.

Somebody can help me? 

Thank you.

---

### Post by mc4man on 2012-05-05
I noticed that also during 12.04 dev, was wondering why some text files changed their icon, mimetype  ect. Eventually traced to gtk
Never did file a bug on, probably because couldn't figure out what package to file against, guess I will now (will start against nautilus 
Also If I remember not all files change, though most do..?


[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/995067](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/995067)

As far as your curent issue - not sure, here I just set the default from Firefox to gedit 
 application/x-glade=gedit.desktop

---

### Post by grossogrossum on 2012-05-05
Thanks for your answer and for open a new bug. 

I'm running Ubunt 12.04 3.2.0-24-generic x86_64

I was beginning to think that this happens just with me. I'm not alone at least :razz:

---

### Post by vasa1 on 2012-05-05
> **mc4man said:**
> ...

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/995067](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/995067)
...

Thanks! Marked "it affects me too".

---

### Post by mc4man on 2012-05-05
So this is caused by shared-mime-info, specifically if "gtk" is the 1st. 256 bytes then it's a glade file

So if needed you could pad the file so the 1st gtk is 257/8 in, wait to see if adjusted in a new package release or
it's likely you could adjust the value in 
/usr/share/mime/packages/freedesktop.org.xml (lines 10804,10805
Then update the mime-database

---

### Post by flemur13013 on 2012-05-05
I had a text file containing "##" - a pretty common string! - and it became a "MATLAB script/function".

The culprit again is /usr/share/mime/packages/freedesktop.org.xml:

<match value="##" type="string" offset="0"/>

---

### Post by grossogrossum on 2012-05-07
> it's likely you could adjust the value in 
/usr/share/mime/packages/freedesktop.org.xml (lines 10804,10805
Then update the mime-database     This solved the problem with my scripts.

thanks.

---

