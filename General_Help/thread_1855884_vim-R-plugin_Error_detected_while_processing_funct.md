---
title: "vim-R-plugin: Error detected while processing function screen#ScreenShell..&lt;SNR&gt;31_Sc"
date: 2011-10-07
forum: General Help
---

### Post by CryptKeeper777 on 2011-10-07
I'm trying to get the vim-R-plugin to run which should integrate R (see [http://www.r-project.org](http://www.r-project.org)) in vim (see [http://www.vim.org/scripts/script.php?script_id=2628](http://www.vim.org/scripts/script.php?script_id=2628)). The installation seems to have worked. But when I try to start is using <LocalLeader>rf (which would be ;rf in my case), I get kicked out of vim (though it continues to run in the background; I'm returned to vim when I type exit) and get the following error message:
```

Error detected while processing function screen#ScreenShell..<SNR>31_ScreenInit:
line   85:
tmux: option requires an argument -- t^@usage: select-pane [-DLRU] [-t target-pane]^@
Press ENTER or type command to continue

```
followed by a horizontal green line dividing the terminal vertically, and the normal prompt beneath that. It looks like the screen plugin (see [http://www.vim.org/scripts/script.php?script_id=2711](http://www.vim.org/scripts/script.php?script_id=2711)) doesn't work properly. 

Any ideas?

---

### Post by diamrem on 2011-10-07
Exactly same problem here, error message is 
```
Error detected while processing function screen#ScreenShell..<SNR>51_ScreenInit:
line   85:
tmux: option requires an argument -- t^@usage: select-pane [-DLRU] [-t target-pane]^@
Press ENTER or type command to continue
```

I use the same vim configuration on my mac os, vim-r-plugin works fine.

Any thoughts?

---

### Post by jalvesaq on 2011-10-10
> **CryptKeeper777 said:**
> I'm trying to get the vim-R-plugin to run which should integrate R (see [http://www.r-project.org](http://www.r-project.org)) in vim (see [http://www.vim.org/scripts/script.php?script_id=2628](http://www.vim.org/scripts/script.php?script_id=2628)). The installation seems to have worked. But when I try to start is using <LocalLeader>rf (which would be ;rf in my case), I get kicked out of vim (though it continues to run in the background; I'm returned to vim when I type exit) and get the following error message:
```

Error detected while processing function screen#ScreenShell..<SNR>31_ScreenInit:
line   85:
tmux: option requires an argument -- t^@usage: select-pane [-DLRU] [-t target-pane]^@
Press ENTER or type command to continue

```
followed by a horizontal green line dividing the terminal vertically, and the normal prompt beneath that. It looks like the screen plugin (see [http://www.vim.org/scripts/script.php?script_id=2711](http://www.vim.org/scripts/script.php?script_id=2711)) doesn't work properly. 

Any ideas?

Tmux 1.3 is incompatible with screen plugin 1.5. You have to switch to either Tmux 1.5 or screen plugin 1.4.

---

### Post by CryptKeeper777 on 2011-10-11
> **jalvesaq said:**
> Tmux 1.3 is incompatible with screen plugin 1.5. You have to switch to either Tmux 1.5 or screen plugin 1.4.
I've updated Tmux to 1.5 and not it works, my vim window was divided and R started in the lower half. Now I only have to find out how to use it.

---

### Post by jalvesaq on 2011-10-11
> **CryptKeeper777 said:**
> I've updated Tmux to 1.5 and not it works, my vim window was divided and R started in the lower half. Now I only have to find out how to use it.

The plugin documentation has a subsection on Tmux:

  :h r-plugin-use

It should help you to get started.

---

