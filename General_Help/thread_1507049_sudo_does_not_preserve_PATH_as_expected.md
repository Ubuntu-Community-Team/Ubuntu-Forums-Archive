---
title: "sudo does not preserve PATH as expected"
date: 2010-06-11
forum: General Help
---

### Post by colonelmandrake on 2010-06-11
Hello,

I'm attempting to add a directory to PATH so it's available when I sudo. (I do not want to sudo -i), but it's not behaving as I expect.

I've added a line to add the directory to PATH in all of these files:

```

/etc/environment
/etc/bash.bashrc
/etc/profile
/root/.bashrc
/root/.profile
~/.bashrc
~/.profile

```

/etc/passwd looks like this (data is the user I'm sudo-ing as):

```

root:x:0:0:root:/root:/bin/bash
data:x:1000:1000:data,,,:/home/data:/bin/bash
<snip>

```

/etc/sudoers looks like this:

```

# /etc/sudoers
#
# Created by Chef for #

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL


# Members of the group 'admin' may gain root privileges without
# entering a password
%admin ALL=(ALL) NOPASSWD: ALL

```

Output from sudo sudo -V:

```

Sudo version 1.7.2p1

Sudoers path: /etc/sudoers
Authentication methods: 'pam'
Syslog facility if syslog is being used for logging: authpriv
Syslog priority to use when user authenticates successfully: notice
Syslog priority to use when user authenticates unsuccessfully: alert
Send mail if the user is not in sudoers
Use a separate timestamp for each user/tty combo
Lecture user the first time they run sudo
Require users to authenticate by default
Root may run sudo
Allow some information gathering to give useful error messages
Require fully-qualified hostnames in the sudoers file
Visudo will honor the EDITOR environment variable
Set the LOGNAME and USER environment variables
Length at which to wrap log file lines (0 for no wrap): 80
Authentication timestamp timeout: 15 minutes
Password prompt timeout: 0 minutes
Number of tries to enter a password: 3
Umask to use or 0777 to use user's: 022
Path to mail program: /usr/sbin/sendmail
Flags for mail program: -t
Address to send mail to: root
Subject line for mail messages: *** SECURITY information for %h ***
Incorrect password message: Sorry, try again.
Path to authentication timestamp dir: /var/run/sudo
Default password prompt: [sudo] password for %p: 
Default user to run commands as: root
Value to override user's $PATH with: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
Path to the editor for use by visudo: /usr/bin/editor
When to require a password for 'list' pseudocommand: any
When to require a password for 'verify' pseudocommand: all
File containing dummy exec functions: /usr/lib/sudo/sudo_noexec.so
File descriptors >= 3 will be closed before executing a command
Reset the environment to a default set of variables
Environment variables to check for sanity:
	TERM
	LINGUAS
	LC_*
	LANGUAGE
	LANG
	COLORTERM
Environment variables to remove:
	RUBYOPT
	RUBYLIB
	PYTHONINSPECT
	PYTHONPATH
	PYTHONHOME
	TMPPREFIX
	ZDOTDIR
	READNULLCMD
	NULLCMD
	FPATH
	PERL5DB
	PERL5OPT
	PERL5LIB
	PERLLIB
	PERLIO_DEBUG 
	JAVA_TOOL_OPTIONS
	SHELLOPTS
	GLOBIGNORE
	PS4
	BASH_ENV
	ENV
	TERMCAP
	TERMPATH
	TERMINFO_DIRS
	TERMINFO
	_RLD*
	LD_*
	PATH_LOCALE
	NLSPATH
	HOSTALIASES
	RES_OPTIONS
	LOCALDOMAIN
	PS4
	SHELLOPTS
	CDPATH
	IFS
Environment variables to preserve:
	XAUTHORIZATION
	XAUTHORITY
	TZ
	PS2
	PS1
	PATH
	MAIL
	LS_COLORS
	KRB5CCNAME
	HOSTNAME
	HOME
	DISPLAY
	COLORS
Locale to use while parsing sudoers: C
<snip>

```

So sudo claims to preserving PATH, but what PATH set where? And how can I change it?

Thanks for your help.

Col. Mandrake VC

---

### Post by sisco311 on 2010-06-11
You have to set the path in the sudoers file. e.g.:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset,secure_path=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin**:/your/path**

...

```

DON'T edit the file directly, use the **visudo** command!

Keep a sane PATH variable.

**Only root** should be able to write to the directory.

---

### Post by colonelmandrake on 2010-06-16
Thanks sisco311. That works for me. Out of interest, where is the default secure_path set?

---

### Post by sisco311 on 2010-06-16
> **colonelmandrake said:**
> Thanks sisco311. That works for me. Out of interest, where is the default secure_path set?

The path is hardcoded. Ubuntu's sudo is compiled with --with-secure-path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"

[http://www.gratisoft.us/sudo/install.html](http://www.gratisoft.us/sudo/install.html)

---

### Post by colonelmandrake on 2010-06-17
Oh yeah that makes sense, thanks very much.

---

