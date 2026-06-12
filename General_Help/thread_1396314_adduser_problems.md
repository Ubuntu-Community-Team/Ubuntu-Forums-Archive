---
title: "adduser problems"
date: 2010-02-01
forum: General Help
---

### Post by dougHines on 2010-02-01
I am attempting to add a user via the adduser command.  However, I get an error/warning message after entering the following: (note I am following a HOWTO, and this is the line it says to enter)

```

adduser renderNode
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM] configuration variable.  Use the `--force-badname'
option to relax this check or reconfigure NAME_REGEX or NAME_REGEX_SYSTEM.

```

Any ideas what this means, or how I might fix it?  I'm still pretty new to Unix, and I don't quite understand how to check/configure locale settings or variables,

---

### Post by Ordes on 2010-02-02
usernames have to written in lowercase...

>> rendernote

---

### Post by rnerwein on 2010-02-02
hi
if you absolutely want the user named:renderNode
then use: adduser --force-badname renderNode
but i don't no how other commands like passwd ... will trade with this
ciao
if you absolutle want the user "

---

### Post by dougHines on 2010-02-02
Ah, no camel case.  This makes sense now that I think about it.  Thanks guys.

Doug

---

