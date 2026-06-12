---
title: "Application Launcher: Redirect STDOUT?"
date: 2010-08-16
forum: General Help
---

### Post by rhp997 on 2010-08-16
I am trying to get an application launcher to run a custom rsync app (which generates pages of stdout data) to redirect stdout to a file.  My test launcher is set to run as a command in terminal.  Common options - which work fine from the console - fail when run from the launcher.  I suspect the launcher requires additional quotes or escape characters - but I can't figure it out!  In testing, I've tried several variations (with quotes, without, etc...) of the following:

ls -al ~/ > ~/testFile
ls -al ~/ 2>&1 > ~/testFile
ls -al ~/ | tee ~/testFile
ls -al ~/ | cat > ~/testFile

All of the above examples create the "testFile" from the console - but none from the launcher.  What am I missing?

I've tested this on Ubuntu v9.4 and v9.10

---

### Post by maclenin on 2011-06-23
Exactly the same question, here!

---

### Post by maclenin on 2011-06-23
The [answer]("http://ubuntuforums.org/showpost.php?p=7913252&postcount=9")!

---

### Post by rhp997 on 2011-06-23
> **maclenin said:**
> The [answer]("http://ubuntuforums.org/showpost.php?p=7913252&postcount=9")!

I had forgotten this thread was still open (sorry); I also ran across the answer [here]("https://help.ubuntu.com/community/HowToAddaLauncher") ("An Alternative to Bash Scripting")...

---

