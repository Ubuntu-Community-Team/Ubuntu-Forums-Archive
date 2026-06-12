---
title: "Problem with xemacs over VNC"
date: 2009-08-14
forum: General Help
---

### Post by mindstorm23 on 2009-08-14
Starting with Intrepid (and now in Jaunty as well), I've been having problems running xemacs over VNC from a Windows machine. Xemacs works fine when using it directly on the computer, but if I try to run xemacs over VNC from a Windows machine, it crashes with the following output:

```
user@host:~$ xemacs &
[1] 10226
user@host:~$ Warning: Color name "Black" is not defined
Warning: Color name "Gray80" is not defined
Warning: Color name "Gray30" is not defined
Warning: Color name "Blue" is not defined
Warning: Color name "Red" is not defined
Warning: Color name "Maroon" is not defined
Warning: Color name "ForestGreen" is not defined

Fatal error (11).

Your files have been auto-saved.
Use `M-x recover-session' to recover them.

Your version of XEmacs was distributed with a PROBLEMS file that  may describe
your crash, and with luck a workaround.  Please check it first, but do report
the crash anyway.  Please report this bug by invoking M-x report-emacs-bug,
or by selecting `Send Bug Report' from the Help menu.  If necessary, send
ordinary email to `xemacs-beta@xemacs.org'.  *MAKE SURE* to include the XEmacs
configuration from M-x describe-installation, or equivalently the file
Installation in the top of the build tree.

*Please* try *hard* to obtain a C stack backtrace; without it, we are unlikely
to be able to analyze the problem.  Locate the core file produced as a result
of this crash (often called `core' or `core.<process-id>', and located in
the directory in which you started XEmacs or your home directory), and type

  gdb /usr/bin/xemacs core

then type `where' at the debugger prompt.  No GDB on your system?  You may
have DBX, or XDB, or SDB.  (Ask your system administrator if you need help.)
If no core file was produced, enable them (often with `ulimit -c unlimited'
in case of future recurrance of the crash.

Lisp backtrace follows:

  # bind (frame-being-created)
  make-frame(nil #<x-device on ":50.0" 0xb1d>)
  frame-initialize()
  # bind (debugger debug-on-error command-line-args-left)
  command-line()
  # (condition-case ... . ((t (byte-code "      ÂÃÂÂ§" ... 1))))
  # bind (error-data)
  normal-top-level()
  # (condition-case ... . error)
  # (catch top-level ...)
user@host:~$
```

I don't really know what this means or what to do about it. Any ideas?

Thanks!
Ben

---

### Post by mindstorm23 on 2009-08-14
I did some more digging and found the "PROBLEMS" file referred to in the error. It was in /usr/share/doc/xemacs21-support/PROBLEMS.gz.

There is a section in that file that reads:
```

** Linux
*** XEmacs crashes on startup, in make-frame.

Typically the Lisp backtrace includes

   make-frame(nil #<x-device on ":0.0" 0x2558>)

somewhere near the top.  The problem is due to an improvement in GNU
ld that sorts the ELF reloc sections in the executable, giving
dramatic speedups in startup for large executables.  It also confuses
the traditional unexec code in XEmacs, leading to the core dump.  The
solution is to use the --pdump or --ldflags='-z nocombreloc' options
to configure.  Recent 21.4 and 12.5 autodetect this in configure.

Red Hat and SuSE (at least) distributed a prerelease version of ld
(versions around 2.11.90.x.y) where autodetection is impossible.  The
recommended procedure is to upgrade to binutils >= 2.12 and rerun
configure.  Otherwise you must apply the flags by hand.  --pdump is
recommended.
```

Phooey. It looks like I'll need to compile it from source :-(

---

### Post by mindstorm23 on 2009-08-14
Sorry for replying to myself a bunch, but I had another thought.  According to that snippet from the PROBLEMS file, the problem was supposed to be autodetected when xemacs was configured before it was compiled. In that case, when the apt package was built, this should have been autodetected and I shouldn't be having this problem. Either the person who built the package specifically configured it to not support the option that would fix this problem, or the problem I'm having is not related to what the PROBLEMS file says.

I hope that made sense...any other ideas?

---

