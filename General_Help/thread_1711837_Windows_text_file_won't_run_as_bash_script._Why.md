---
title: "Windows text file won't run as bash script. Why?"
date: 2011-03-21
forum: General Help
---

### Post by Gozu-san on 2011-03-21
I just learned that.  And I can deal with it.  Even so, I wonder why.  Anyone?

Basically, I created text for a bunch of "#!/bin/bash" scripts in MS SQL Server.  Being on a Windows machine, I used Ultraedit to create text files for a few examples.  After copying the files to a machine running Ubuntu 10.10, I changed group and owner, and made them executable.  However, they won't execute.  I get "file not found" errors.  But, if I paste the content into text files created in Ubuntu, it runs fine.

Why is that?

---

### Post by naudster on 2011-03-21
The windows files are no doubt formatted with CRLF newlines. My guess is your shebang line is being interpreted as

#!/bin/bash<CR>

which can't be found on the filesystem. Try converting the windows files with dos2unix (which nowadays is called fromdos, in the tofrodos package), or a simple command:

```

awk '{sub(/\r$/,"")};1' windowsfile > newfile

```

---

