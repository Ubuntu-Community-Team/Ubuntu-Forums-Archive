---
title: "How do I undo the debuggingprogramcrash instructions"
date: 2010-04-14
forum: General Help
---

### Post by jatinps on 2010-04-14
Dear All - I am on lucid lynx beta 2.
While reporting for an evolution bug, I was asked to follow the debuggingprogramcrash instructions at [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash) and send some traces. Now that I am done, I wanted to know how do I get back to my original system and undo the changes (debug symbols, sources.list, etc?)

The wiki says "**How do we remove all this stuff after getting  the trace and get back to a normal system?** " but does not talk about how to do it. 'sudo apt-get update' takes really long now !

---

### Post by plucky on 2010-04-14
Just reverse the commands you used to install the programs.

For example ```
sudo apt-get install <name of package>
```

Use ```
sudo apt-get remove <name of package>
```

Also 

Open **System > Administration > Software Sources** and go the the **Other Software** tab and un-tick the debug repositories.

Then when you exit from Software Sources it will ask you to reload the index files.

Or use the CLI to remove them from the **/etc/apt/sources.list.d** directory and then run ```
sudo apt-get update
``` to reload the index files.

Good Luck

---

