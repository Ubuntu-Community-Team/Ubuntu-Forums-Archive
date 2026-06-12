---
title: "unkwon undeletable folder in pnedrive"
date: 2011-10-29
forum: General Help
---

### Post by shubham1 on 2011-10-29
hi
i brought a hp pen drive 8gb
when i copied sum data
after that the space used was more than the size of files
i veiewed hidden files
there were 2 i dont know where they come from
one deleted my me 
other is not deleted using ubuntu i opend folder using root it even did not
it even not windows its eating my space
help!

---

### Post by shubham1 on 2011-10-29
> **shubham1 said:**
> hi
i brought a hp pen drive 8gb
when i copied sum data
after that the space used was more than the size of files
i veiewed hidden files
there were 2 i dont know where they come from
one deleted my me 
other is not deleted using ubuntu i opend folder using root it even did not
it even not windows its eating my space
help!
file size is reduced but is atill indeletable

---

### Post by searchfgold6789 on 2011-10-29
The extra folder you see (probably includes the name "lost+found") should not be deleted; see [here]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html"). Let me know if you need any further explanation.
The reason that slightly more disk space appears to be used than is actually on the disk is that the filesystem stores additional information on the file so that the data can work. This behavior is always seen in most computing applications.
 - search

---

### Post by shubham1 on 2011-10-29
> **searchfgold6789 said:**
> The extra folder you see (probably includes the name "lost+found") should not be deleted; see [here]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html"). Let me know if you need any further explanation.
The reason that slightly more disk space appears to be used than is actually on the disk is that the filesystem stores additional information on the file so that the data can work. This behavior is always seen in most computing applications.
 - search
it was .trash and one more it was using 1gb and i some home how reduced it size to very low now i got it

---

