---
title: "Opening Bash scripts"
date: 2009-10-29
forum: General Help
---

### Post by Living2007 on 2009-10-29
Like how Windows allows .cmd and .bat files to be opened and run in command prompt, what is the file type for nautilus to do this. I'm currently saving my bashes in .sh format and have to open it in Terminal instead of Nautilus!

---

### Post by mcduck on 2009-10-29
> **Living2007 said:**
> Like how Windows allows .cmd and .bat files to be opened and run in command prompt, what is the file type for nautilus to do this. I'm currently saving my bashes in .sh format and have to open it in Terminal instead of Nautilus!

If your script files are set to be executable, clicking them in Nautilus will by default ask you if you ant to open them or execute them.

If this is not happening to you, check these things:

1. Your script file has execute permission set for your current user/group.

2. The script has correct shebang in the first line "#!/bn/sh" or "#!/bin/bash", if you are writing normal shell scripts

3. The setting for how Nautilus handles executable files in in Nautilus Preferences (Edit-Preferences in any file manager window), under the Behavior-tab. You can set nautilus to open them, execute them, or ask every time what you want to do.

---

### Post by Living2007 on 2009-10-29
> **mcduck said:**
> If your script files are set to be executable, clicking them in Nautilus will by default ask you if you ant to open them or execute them.

If this is not happening to you, check these things:

1. Your script file has execute permission set for your current user/group.

2. The script has correct shebang in the first line "#!/bn/sh" or "#!/bin/bash", if you are writing normal shell scripts

3. The setting for how Nautilus handles executable files in in Nautilus Preferences (Edit-Preferences in any file manager window), under the Behavior-tab. You can set nautilus to open them, execute them, or ask every time what you want to do.

Thanks, but I would just like to know if their is a file type that nautilus will open natively into terminal?

---

### Post by mcduck on 2009-10-29
> **Living2007 said:**
> Thanks, but I would just like to know if their is a file type that nautilus will open natively into terminal?

There is no such thing. Linux doesn't really care a lot about file name extensions, executable files are defined simply by the file's execute permission, and file types by file's actual contents.

Text file is text file because it contains text, not because it might (or might not) have a .txt extension.

Executable script file is a script file because it contains a shell script (starting with the shebang specifying the shell to use to run the file) and executable because it's permissions are set to allow executing.

Like  I said, if your file is executable, nautilus will (by default) ask you if you want to execute it or open it. Regardless of the file's name.

---

