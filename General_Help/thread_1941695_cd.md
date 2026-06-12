---
title: "cd"
date: 2012-03-16
forum: General Help
---

### Post by Miykel on 2012-03-16
G'Day;  I'm trying to cd a folder in my Home folder; I can cd any other folder in Home, i.e. Downloads, Documents etc. btu the folder I want to cd comes back "no such directory", the folder is Called Note Book which I created myself to house the help I get here, is it that I created the folder ???
Regards Miykel

---

### Post by papibe on 2012-03-16
Hi Miykel.

Does it have an space on it?

Try this:
```
cd 'Note Book'
```
Or this:
```
cd Note\ Book
```
That should work. Now, one of the best tools of the command line is autocompletion. The shell tries to guess the parameters of your command by filling in what is missing. Use tab to active it.

For instance, if you write (don't press enter):
```
cd Note
```
and then you press tab, it should complete the name of the directory.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by codemaniac on 2012-03-16
If your folder name contains special character or spaces , you need to escape them so that it is not interpreted by shell .Wrep quotes around them as mentioned above .

```
cd "Called Note Book"
```

You can also tab complete it by
```
cd Calle+tab
```

---

### Post by winh8r on 2012-03-16
Always try to name your self created  directories using lowercase letters and avoid empty spaces.

papibe and codemaniac have explained how to get around having spaces and getting the directories to be recognised, but you can save yourself a whole lot of hassle if you get into the habit of doing things like:

notebook
note-book
miykels-notes
notes


Hope this helps.

---

### Post by Miykel on 2012-03-16
Thanks guys, so much....  the tab deal worked a treat plus.. I'll have a play with the label deal, lower case and no spaces.
Kind Regards Miykel

---

