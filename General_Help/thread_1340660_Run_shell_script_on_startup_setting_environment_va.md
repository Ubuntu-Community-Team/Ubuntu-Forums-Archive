---
title: "Run shell script on startup setting environment variables in gnome?"
date: 2009-11-28
forum: General Help
---

### Post by Jengu on 2009-11-28
Here's what I want to do:

-When I login, run a shell script
-The shell script sets environment variables through export VAR=/some/stuff. It may decide to set some of these conditionally, so the script has to actually run, it can't just be run through some parser looking for export's.
-Applications launched through the GUI (e.g. by the Applications menu) see the environment variables
-Do this in a way that is window manager neutral (works in KDE/Gnome/openbox/whatever)

Is there some file to edit that will meet all those goals? xsession, profile, and gnomerc haven't worked.

I can't find a way to do this to save my life and it's frustrating the hell out of me. Every method I try only affects terminals or applications launched from terminals, not from the GUI. There should be a straightforward easy answer to this question, but instead there's your bashrc, your bash login, your gnomerc, your xsession, your .profile... this is 10x worse than the windows startup hell (your startup programs folder, your HKEY registry key, etc.).

---

### Post by efflandt on 2009-11-28
.profile (hidden with dot prefix) runs whenever you login, so that should do what you want.  That works for most sh shells except maybe csh.  The default shell in Linux is bash.  Do **man bash** in a terminal or console to see which files bash uses for what.

When I needed to modprobe a module for wireless on live/install iso on bootable USB with persistent data, rather than playing with init scripts, I added some code to ubuntu's .profile to grep if the that wireless device was present (lspci), and if the module was not loaded (lsmod), then sudo modprobe it.  That way it would load the module on my company laptop, but not on other computers.

---

### Post by scorp123 on 2009-11-28
> **Jengu said:**
>  Is there some file to edit that will meet all those goals? xsession, profile, and gnomerc haven't worked. Because maybe the programs you want to use are ignoring those settings? Could that be possible?

> **Jengu said:**
>  I can't find a way to do this to save my life and it's frustrating the hell out of me.  You could manipulate the launcher command of the program you want to run and put the environment variable in front of it. Example:

Let's suppose I have a program called "Foo". The command to launch it is:
```
/usr/bin/foo
```

Now when I want to add a variable called "FOODIR" to this application I could do it in front of that command:
```
env FOODIR=/opt/foo/v2/data /usr/bin/foo
```

> **Jengu said:**
>  There should be a straightforward easy answer to this question Depends on what you're doing. :D

> **Jengu said:**
>  but instead there's your bashrc, your bash login, your gnomerc, your xsession, your .profile...  It's all about having choice and about having the possibility to be granular about what gets started when. Windows doesn't give you this choice. You eiher have something in the registry or you don't.

> **Jengu said:**
>  this is 10x worse than the windows startup hell (your startup programs folder, your HKEY registry key, etc.). You will get used to it :D

---

### Post by vontrapp on 2012-02-18
> **scorp123 said:**
> Because maybe the programs you want to use are ignoring those settings? Could that be possible?

No, it's not possible. Programs don't unset environment variables by simply ignoring them. If the environment variable is not set in the environment, it's because it's not in the environment, not because of whether some program cared about it.

> **scorp123 said:**
> 
 You could manipulate the launcher command of the program you want to run and put the environment variable in front of it. 


Which is really stupid if you want some general ENV variable to be set in any program you run, such as LD_PRELOAD or SSH_AUTH_SOCK, for example. How many .desktop files are you willing to edit by hand to do something that is dirt simple done the right way?

> **scorp123 said:**
> 
 Depends on what you're doing. :D


No, it doesn't! Because what he's doing is setting the environment for the *entire* desktop session. That is a well defined goal with a well defined success condition.

> **scorp123 said:**
> 
 It's all about having choice and about having the possibility to be granular about what gets started when. Windows doesn't give you this choice. You eiher have something in the registry or you don't.


It's all about having choice, sure. So where's the choice to set the ENV for the ancestor of (and therefore inherited in) all programs started from the desktop session?? It really is a simple problem.

---

