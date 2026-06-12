---
title: "help me fix this"
date: 2009-11-23
forum: General Help
---

### Post by Cardale on 2009-11-23
This is sux!

---

### Post by fancypiper on 2009-11-23
You can use xpdf, Adobe and probably more to read pdf files.  If you haven't already, add the medibuntu sources

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Now:
sudo apt-get install acroread

will install the Adobe reader.  You can change the wine recommendation to your chosen reader by clicking System>Preferences>Preferred Applications

---

### Post by Prodigal Son on 2009-11-23
Are you talking about the multiple Wine entries or the ability to open PDF files ?

---

### Post by t0p on 2009-11-23
I don't know what's going on there.

Do you have the program **evince** installed?  That's the Ubuntu default PDF reader.  Find out by opening a terminal and typing:

```
which evince
```

If it's installed, you'll get output like:

```
/usr/bin/evince
```

If it's installed, go back to that "Open PDF document" window, click on "Open with custom command" and type in

```
/usr/bin/evince
```

If it's not installed, type into the terminal:

```
sudo apt-get install evince
```

Once it's installed, do as I said above.

---

### Post by Cardale on 2009-11-23
> **Prodigal Son said:**
> Are you talking about the multiple Wine entries or the ability to open PDF files ?

haha the multiple wine entries....cmon man!  :D

---

### Post by mechro on 2009-11-23
Right click any pdf file. Go to Properties > Open With. Remove all entries. Try Reset.

---

### Post by Cardale on 2009-11-23
THIS HAS NOTHING TO DO WITH PDF FILES.  :o  I want to remove the million wine entries.  Thanks.

---

### Post by wojox on 2009-11-23
Like this: [http://ubuntuforums.org/showthread.php?t=1273296](http://ubuntuforums.org/showthread.php?t=1273296)

---

### Post by mechro on 2009-11-23
> **Cardale said:**
> THIS HAS NOTHING TO DO WITH PDF FILES.  :o  I want to remove the million wine entries.  Thanks.

You were opening a pdf file. The Wine entries are associated with opening a pdf file. If your opening post's thumbnail has nothing to do with your problem then why post it?

---

### Post by Cardale on 2009-11-23
Don't worry I fixed it.  And no it has nothing to do with a PDF file.

---

### Post by mechro on 2009-11-24
You haven't marked the thread as Solved. Should I post a thumbnail to show you how to do it?

---

### Post by Cardale on 2009-11-24
Thanks love you big boy.

---

### Post by Cardale on 2009-11-24
> **mechro said:**
> You haven't marked the thread as Solved. Should I post a thumbnail to show you how to do it?

Your wrong and you get made...  :D

---

### Post by fancypiper on 2009-11-24
[Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

