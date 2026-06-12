---
title: "Cannot read or write extracted Japanese files"
date: 2011-06-14
forum: General Help
---

### Post by selenir on 2011-06-14
I've extracted a few files through the archive manager through Ark (as well as through the command line) and some folders/files that were originally in Japanese are not properly displayed in the terminal or file browser. I can't delete them nor open them; I am informed that this file does not exist. 

I am running Kubuntu 11.04. I had a similar problem in Ubuntu 10.04 in that the text was not displayed properly, but the files were readable and writable.

---

### Post by ruffEdgz on 2011-06-14
Some more information about a file or files would be helpful. Please run the commands below and post them back on this topic with the results:
```

ll /path/to/file(s)

file /path/to/file(s)

```
Because I don't know where these files are, the code above is to help you use the command but point that command to the files.

---

### Post by selenir on 2011-06-14
Hm, it's odd, I wanted to test deleting the files again (I did this by rm -rf <folder containing incorrectly titled files>) and I accidentally removed it. Trying to extract it again reveals that it seems to have the proper filenames. Would you know the packages for Japanese fonts?

For reference, the name of the folder was "[&#65533;A&#65533;g&#65533;&#65533;&#65533;G&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;] &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#513;A&#65533;&#65533;&#65533;&#1922;&#65533;&#65533;C&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;&#65533;A&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;C&#65533;&#65533;&#65533;&#65533;&#65533;&#450;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;c&#65533;H&#65533;v&#65533;&#65533;&#65533;u&#65533;c&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;v/" as displayed by my terminal.

---

