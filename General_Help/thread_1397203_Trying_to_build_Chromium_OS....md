---
title: "Trying to build Chromium OS..."
date: 2010-02-03
forum: General Help
---

### Post by myrules92 on 2010-02-03
Getting stuck on chroot. The enter_chroot.sh file is in /home/michael/[chromiumos]/chromiumos.git/src/scripts, but every time I try to enter chroot, I receive this message:

[email]michael@michael-desktop:~/[chromiumos]/chromiumos.git[/email]/src/scripts$ ./make_chroot.sh
./common.sh: line 78: /home/michael/[chromiumos]/chromiumos.git/src/third_party/shflags/files/src/shflags: No such file or directory
./make_chroot.sh: line 28: DEFINE_string: command not found
./make_chroot.sh: line 30: DEFINE_string: command not found
./make_chroot.sh: line 32: DEFINE_string: command not found
./make_chroot.sh: line 34: DEFINE_string: command not found
./make_chroot.sh: line 36: DEFINE_string: command not found
./make_chroot.sh: line 38: DEFINE_boolean: command not found
./make_chroot.sh: line 39: DEFINE_boolean: command not found
./make_chroot.sh: line 42: FLAGS: command not found

Help!

---

