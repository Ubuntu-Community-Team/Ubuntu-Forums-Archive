---
title: "what Executable File in ubuntu and how to run ?"
date: 2011-04-29
forum: General Help
---

### Post by dabyv on 2011-04-29
Executable File in windows is exe
and  ubuntu ever have any format like that?
how to run that? double click?

---

### Post by sikander3786 on 2011-04-29
To be exact, .exe equal in Ubuntu is .deb and you can install it by simply double clicking and then follow on-screen instructions.

But, Ubuntu uses repositories, software sources and you can install almost any software without going to different websites and downloading multiple .deb packages. All you need to do is to search for your software in 'Software Center' under the Applications menu.

---

### Post by sj1410 on 2011-04-29
On Linux, executables don't have an extension. The files simply have a flag in their attributes to say whether they are executable or not. These files tend not to have an extension, but it doesn't mean that files with an extension aren't executable

for example you create a file myexec.sh 

```

#!/usr/bin/sh

echo "Hello Word!"


```

now make it executable

```

chmod +x myexec.sh

```

and run it

```

$ ./myexec.sh

```

---

### Post by mcduck on 2011-04-29
The closest equivalent of a Windows .EXE file in Linux would be an [ELF file]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format").

But the others are correct in that the only thing that defines an executable file in Linux is the execute permission, and of course if the file has some content that can be executed, be it ELF file or some script that can be executed in some shell (like shell scripts) or interpreter (python scripts, for example).

The file name extensions are mostly just for user's convenience in Linux, the system itself doesn't care much about them and instead detects file types by the file's actual contents, using [magic numbers]("http://en.wikipedia.org/wiki/File_format#Magic_number").

---

### Post by dabyv on 2011-05-01
> **mcduck said:**
> The closest equivalent of a Windows .EXE file in Linux would be an [ELF file]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format").
 
But the others are correct in that the only thing that defines an executable file in Linux is the execute permission, and of course if the file has some content that can be executed, be it ELF file or some script that can be executed in some shell (like shell scripts) or interpreter (python scripts, for example).
 
The file name extensions are mostly just for user's convenience in Linux, the system itself doesn't care much about them and instead detects file types by the file's actual contents, using [magic numbers]("http://en.wikipedia.org/wiki/File_format#Magic_number").
 
 
so i have 2 files compiled by my self whit a [guid]("http://www.trinitycore.org/w/How-to:Linux") and they dosent any format just 2 file name! and i want to run them and i duoble click on them and nothing changed any idead?

---

### Post by FlekkeN on 2011-05-04
Try to start them from the console.
eg:
```

$ ./programname

```

---

