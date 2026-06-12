---
title: "Extracting incomplete rar files"
date: 2010-09-07
forum: General Help
---

### Post by unigee on 2010-09-07
Hi,

It is possible with winrar on windows to open up semi complete multipart rar files - only if the first rar file is not available.

For example

winrar would open up the file

myfile.part04.rar

only if myfile.part01.rar was not available (otherwise it shows an error)

It is then possible to extract the contents of myfile.part04.rar, without having to have the rest of the multipart rar files.

I am trying to have the same flexibility with my ubuntu box.

Archive Manager opens up myfile.part04.rar without errors but shows an empty file.
Ark brings up an error and fails after that.

however, the command line
```
rar e myfile.part04.rar
```

will sucessfully extract just the contents of part04.

I am wondering if there is a way to automatically run 
```
rar e selectedfile.partNN.rar
```

if I double click the rar file in the ubuntu gui?

Thanks

---

### Post by unigee on 2010-09-07
never mind, 
Xarchiver does exactly what I need

---

