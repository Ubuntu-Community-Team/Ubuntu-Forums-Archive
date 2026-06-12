---
title: "Delete archives after extraction..."
date: 2010-08-21
forum: General Help
---

### Post by madmax.santana on 2010-08-21
I downloaded a file enclosed in 58 rar parts and extracted them. I was looking for a way which would enable autodelete of all rar-archives after the extraction so I don't have to clean the mess up later.
I hear there is some option in command line arguments but that doesn't work with split archives.
Is there a way in GUI? Some option maybe, which I could check to make all the future extractions in par with autodelete feature?

---

### Post by WorMzy on 2010-08-21
A simple rm command should work.

```
rm *.rar
```

Will remove all .rar files in the current working directory.

---

### Post by madmax.santana on 2010-08-23
And is there a way I can automate the process?

---

### Post by WorMzy on 2010-08-23
You mean if you're doing via GUI? It may be possible with nautilus-actions (sudo apt-get install nautilus-actions.

You can create an alias which runs the tar command followed by the rm command, e.g. add this to your ~/.bash_aliases file:

```
alias unrar-rm='unrar *.rar && rm *.rar'
```

with that in place, running unrar-rm in a terminal should unrar any rar files in the current directory, then remove the rars; but it's untested by me, and I'd recommend using the safer option of unraring, checking everything extracted OK, *then* deleting the rar files.

---

