---
title: "Logging File Operations"
date: 2009-12-14
forum: General Help
---

### Post by Chazz56 on 2009-12-14
What is the best way to log file operations? I'm particularly interested in knowing which files are open for read/write and file create/delete. If this is not available under Ubuntu, are there any system where this is possible.

The reason I'm asking this is I would like to enable logging file read/write, trigger a build command then disable the logging and parse the logs manually. This would be helpful in understanding how the build command was executed and by looking at the log in each step to further understand dependencies. I know some of this information is in the build files already but looking at the log would give me some information that is not evident in the build file.

EDIT: One viable solution I have found is inotify. The only problem is I need to be able to associate the inotify event with the command.

---

