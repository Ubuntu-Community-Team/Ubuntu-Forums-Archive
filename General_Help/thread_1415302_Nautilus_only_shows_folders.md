---
title: "Nautilus only shows folders"
date: 2010-02-24
forum: General Help
---

### Post by dtr1001 on 2010-02-24
Hello, often we need to add attachments to things, like adding a picture to a gmail when composing or to add a picture to a document. When I try to do this, nautilus shows only folders. It shows all the folders I would expect to see but none of these folders actually contain documents. If I navigate using places and open folders of course all my files are there, I just cant see them when trying to insert a file. Why might that be? Does anyone know?

I notice the "select which types of file to show" pulldown is empty - whats happened?

regards

David

---

### Post by quixote on 2010-02-26
That's bizarre.  It's lost some arcane setting somewhere.  I'd be curious to know the answer too.  Just adding a vote for that here.

---

### Post by dvlchd3 on 2010-02-26
Try reinstalling nautilus.

```

sudo apt-get update && sudo apt-get remove nautilus && sudo apt-get install nautilus

```

Then log off and back in so nautilus restarts.

If this does not resolve the issue, file a bug, that is extremely bizarre behavior!
```

ubuntu-bug nautilus

```

---

### Post by dcstar on 2010-02-26
> **dtr1001 said:**
> Hello, often we need to add attachments to things, like adding a picture to a gmail when composing or to add a picture to a document. When I try to do this, nautilus shows only folders. It shows all the folders I would expect to see but none of these folders actually contain documents. If I navigate using places and open folders of course all my files are there, I just cant see them when trying to insert a file. Why might that be? Does anyone know?
........

Nautilus does not do things like "adding a picture to a gmail when composing or to add a picture to a document", the actual application you are using does that.

"navigate using places" is actually using Nautilus, so if the files are there then Nautilus is actually working and something else is not.

---

### Post by robert shearer on 2010-02-26
> **dtr1001 said:**
> Hello, often we need to add attachments to things, like adding a picture to a gmail when composing or to add a picture to a document. When I try to do this, nautilus shows only folders. It shows all the folders I would expect to see but none of these folders actually contain documents. If I navigate using places and open folders of course all my files are there, I just cant see them when trying to insert a file. Why might that be? Does anyone know?

I notice the "select which types of file to show" pulldown is empty - whats happened?

regards

David

How do you know they don't contain files ?
Step us through what you do to find and attempt to add a file to a gmail email so we can try your method ourselves and troubleshoot.

Probably something simple like a step missing action.

Occam may help.

---

### Post by quixote on 2010-02-26
(No, app-specific file-open requests aren't using nautilus per se, but the fact that different apps have the same dir-only, file-blind behavior suggests to me it's not the apps.  It's something to do with gnome?  gdm?  the *screensaver*? (sarcasm alert! :)), I mean, what?  Something is malfunctioning across apps.)

---

