---
title: "How do you reinstall Mono and Mono Basic?"
date: 2010-06-13
forum: General Help
---

### Post by 28_SNaKeS on 2010-06-13
Hello there. I was told posting this in the general forum would get more results so I will paste some from my previous thread:

"Before upgrading to 10.04 (from 9.10) I had already installed and had been using yWriter5, a novel writing software. I am using it to organize an adventure game I am writing. It's great software and is very helpful.

After the upgrade to 10.04, yWriter DOES NOT start anymore.

I get this following messege:
-------------------------------------
snake@snakepit:~/yWriter5/bin$ mono yWriter5.exe

** (yWriter5.exe:4171): WARNING **: The following assembly referenced from /home/snake/yWriter5/bin/yWriter5.exe could not be loaded:
Assembly: Microsoft.VisualBasic (assemblyref_index=1)
Version: 8.0.0.0
Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/snake/yWriter5/bin/).


** (yWriter5.exe:4171): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded
--------------------------------------
"

I have tried uninstalling the VB Libraries and installing them fresh. No change. I have tried removing yWriter and installing it again. No change.

Now I am getting suggestions to reinstall Mono and Mono Basic. The creator of yWriter thinks that Mono may be causing the problems and needs to be freshly installed.

Being fairly new to Linux, I do not know how to uninstall Mono and Mono Basic. I have looked in the Package Manager but it confuses the hell out of me. There's 101 Mono things in there.

Please, I've googled and googled and googled some more and CANNOT for the life of me find out how to REINSTALL MONO and MONO BASIC.

Thanks in advance!

---

### Post by MCVenom on 2010-06-13
Try this:

```
sudo apt-get purge libmono* libgdiplus cli-common libglitz-glx1 libglitz1 && sudo apt-get install libmono* libgdiplus cli-common libglitz-glx1 libglitz1
```

That should uninstall, then reinstall Mono on your system.

---

### Post by 28_SNaKeS on 2010-06-14
GAH!

That didn't work either. I've uninstalled Mono, reinstalled and the problem still persists.

I am giving up.

Thank you for the help, Black Otaku.

---

