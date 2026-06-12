---
title: "Bluefish Fails to save files"
date: 2005-02-25
forum: General Help
---

### Post by ions on 2005-02-25
If I am in a directory and I try and create a new file in Bluefish it fails to save.  I get an error dialogue popping up saying:

```
**File Save Error**
Could not write file:
"/home/user/Desktop/Web%20Sites/Project/index.htm"

```

I do have permissions to write in this directory.  In fact if I go to the directory in a terminal and 'touch index.htm' the file gets created just fine and Bluefish will even save to it!  Any idea why Bluefish is being so colosally stupid?  :(

HUGE pita to have to create each file manually in a terminal first then work on it in Bluefish.

This is in Warty with - 
$ bluefish -v
bluefish 1.0 HTML editor

---

### Post by ions on 2005-02-25
Ok I can save just not to a directory with a space in the name - such as 'Web Sites'.  Stupid.  Colosally stupid.  I never had this problem with Bluefish in Gentoo where I had an identical directory structure.

/me is very frustrated.

Oh well I've now renamed all my directories so none have spaces.  :(

---

