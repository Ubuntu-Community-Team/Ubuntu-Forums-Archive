---
title: "synchronizing texts"
date: 2011-09-13
forum: General Help
---

### Post by bofak on 2011-09-13
I've been using grsynch to keep folders and files in sync between two computers, but is there anything that will synchronize the actual content of text files?

---

### Post by haqking on 2011-09-13
> **bofak said:**
> I've been using grsynch to keep folders and files in sync between two computers, but is there anything that will synchronize the actual content of text files?

rsync and grsync will.

i dont understand ?

if you have filea and copy of filea in a location  and you rsync filea to location of copid filea, the content changes will be synced ?

or am i not understanding you ?

becasue i rysnc daily changes in docs and the like

---

### Post by bofak on 2011-09-13
> **haqking said:**
> rsync and grsync will.

i dont understand ?

if you have filea and copy of filea in a location  and you rsync filea to location of copid filea, the content changes will be synced ?

or am i not understanding you ?

becasue i rysnc daily changes in docs and the like
It isn't working that way for me, using Gedit.  The changes simply don't appear.

---

### Post by haqking on 2011-09-13
> **bofak said:**
> It isn't working that way for me, using Gedit.  The changes simply don't appear.

so you are making a change to filea in gedit then running sync and the change is not occuring in the copy of filea ?

i just

rsync -av /path/filename /path filename

obviously adjust to suit path and options if needed for recursion etc

---

### Post by aeiah on 2011-09-13
are you expecting that you could change the file in two places at once, and the changes would be merged or something?

---

### Post by haqking on 2011-09-13
> **aeiah said:**
> are you expecting that you could change the file in two places at once, and the changes would be merged or something?

yes i think he is.

or if its to do with grsync

then see here for rsync and grync to make sure you are using it correctly 
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by donaldsmith on 2011-09-13
Content of the document is displayed in the main central window. If there are questions related to documents as they appear on the left side. Questions can be grouped into different columns in order to avoid duplication

---

### Post by bofak on 2011-09-13
I would like to be able to make changes to one version of a text, then designate that version as "source" in Grsync and have the changes appear in the "destination" version.

On a later occasion I might reverse source and destination, depending on which machine I'm working on (in my case, desktop or netbook).

---

### Post by haqking on 2011-09-13
> **bofak said:**
> I would like to be able to make changes to one version of a text, then designate that version as "source" in Grsync and have the changes appear in the "destination" version.

On a later occasion I might reverse source and destination, depending on which machine I'm working on (in my case, desktop or netbook).

ok did you read the guide i posted ?

are you using gsync to sync at a given time ?

using a cronjob to schedule the sync ?

how are you doing it ?

---

### Post by bofak on 2011-09-13
> **haqking said:**
> ok did you read the guide i posted ?

are you using gsync to sync at a given time ?

using a cronjob to schedule the sync ?

how are you doing it ?
Thx Haqking for the lead to that guide, which I had never seen before.  I'll study it when I find time (which I don't have right now!)

---

### Post by haqking on 2011-09-13
> **bofak said:**
> Thx Haqking for the lead to that guide, which I had never seen before.  I'll study it when I find time (which I don't have right now!)


ok no problem, have a good read then post back if you still have issues.

peace

---

