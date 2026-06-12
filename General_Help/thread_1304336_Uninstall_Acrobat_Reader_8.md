---
title: "Uninstall Acrobat Reader 8"
date: 2009-10-29
forum: General Help
---

### Post by frs89 on 2009-10-29
Hi

I downloaded Acrobat Reader 8 and I installed through: 
dpkg -i AdobeReader_ptb-8.1.7-1.i386.deb
How do I uninstall it?

Thanks

---

### Post by henryjack on 2009-10-29
[FONT=&quot]Hi.. it is very easy to uninstall the Acrobat Reader 8,
first click on start menu>Control panel>add/remove programs,
there  u can find acrobat reader, select that and click on remove option[/FONT]

---

### Post by philinux on 2009-10-29
```
sudo aptitude purge acroread
```

---

### Post by frs89 on 2009-10-29
nope
Acrobat Reader doesn't appear in add/remove

and purge Acroread does nothing

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "acroread"
Couldn't find any package whose name or description matched "acroread"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by philinux on 2009-10-29
Try 

sudo apt-get remove acroread

The other guy was referring to a windows install. Not funny either.

Other than that look through synaptic and see if you can find it. Mark it for removal.

---

### Post by dibenedette on 2009-12-25
Talvez vc já tenha resolvido isso, mas...

Para desinstalar o Adobe Reader, basta excluir o diretório no qual ele foi instalado (ou seja /opt/Adobe/Reader8 ).

Eu passei pelo mesmo problema. See it in /opt/Adobe/Reader8/ReadMe.htm

Sorry for using portuguese,

Regards! :)

---

### Post by Ian Eales on 2010-08-17
From Applications > Unbuntu Software Center, select Get software and enter acrobat in the search box.

Acrobat reader shows and it can be removed.
Once removed "Sorry, 'adoboreader-enu' is not available for this type of computer (ui386).' is displayed.

Gotta say the new Software Center SUX !!!

---

### Post by luigi_mb on 2010-08-17
How about

```

sudo dpkg -r AdobeReader_ptb

```

or maybe

```

sudo dpkg -r AdobeReader

```


/luigi

---

### Post by AGentGreenland on 2013-02-18
This thread says it is solved... But which reply made it work...??

---

### Post by oldos2er on 2013-02-18
Old thread closed.

When the 'Solved' tag isn't used properly, it is frustrating. Best thing would be to start a new thread.

---

