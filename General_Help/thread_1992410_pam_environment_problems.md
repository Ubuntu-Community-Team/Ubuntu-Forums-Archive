---
title: "pam_environment problems"
date: 2012-05-31
forum: General Help
---

### Post by kupaka on 2012-05-31
According to [https://help.ubuntu.com/community/EnvironmentVariables]("https://help.ubuntu.com/community/EnvironmentVariables"), I should place my environment variables in ~/.pam_environment. I've done so (code below):
```

LANGUAGE=en_CA:en
LANG=en_CA.UTF-8
EDITOR=vim
SURF_USERAGENT="Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/536.6 (KHTML, like Gecko) Chrome/20.0.1092.0 Safari/536.6"

```

This works if I'm in a terminal session (like ctrl+alt+f1 and the like) but doesn't work in an X session. I'd like for this to work because the file browser that I use (Ranger) uses the environment variables to open things like text files, and the editor environment variable isn't defined for me, making it use nano (instead of vim, which is what I use). I don't want to put my variables in .bashrc or .bash_profile because I use zsh for my shell, and I don't want to use .zprofile for it because the way I launch some programs bypasses the shell, so it wouldn't be read in that way. 

What am I doing wrong?

---

### Post by gordintoronto on 2012-05-31
From the same wiki you referenced:
[https://help.ubuntu.com/community/EnvironmentVariables#System-wide_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#System-wide_environment_variables)

"Environment variable settings that affect the system as a whole (rather then just a particular user) should not be placed in any of the many system-level scripts that get executed when the system or the desktop session are loaded, but into

/etc/environment - This file is specifically meant for system-wide environment variable settings. It is not a script file, but rather consists of assignment expressions, one per line. Specifically, this file stores the system-wide locale and path settings.

---

### Post by kupaka on 2012-05-31
> **gordintoronto said:**
> From the same wiki you referenced:
[https://help.ubuntu.com/community/EnvironmentVariables#System-wide_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#System-wide_environment_variables)

"Environment variable settings that affect the system as a whole (rather then just a particular user) should not be placed in any of the many system-level scripts that get executed when the system or the desktop session are loaded, but into

/etc/environment - This file is specifically meant for system-wide environment variable settings. It is not a script file, but rather consists of assignment expressions, one per line. Specifically, this file stores the system-wide locale and path settings.

Am I missing something here?
I would like the variables to apply only for my session, thus they are put in .pam_environment, right?

---

### Post by kupaka on 2012-06-03
Bump.

---

### Post by tau-lepton on 2012-08-27
I had the same issues and just used .profile instead of the .pam_environment.  That is a horrible wiki page.

---

