---
title: "Building Image"
date: 2010-08-17
forum: General Help
---

### Post by siteregsam on 2010-08-17
Hi,

I had currently installed LucidLynx(10.04 Ultimate Edition) in my laptop and tried to create an image for uploading it to Eucalyptus. But while creating image i got the following error....

[COLOR=Blue][COLOR=Black]sam@sam-laptop:~$[/COLOR] sudo ubuntu-vm-builder kvm lucid --addpkg vim
[COLOR=Black][sudo] password for sam:[/COLOR] 
2010-08-17 10:46:30,075 INFO    : Calling hook: preflight_check
2010-08-17 10:46:30,089 INFO    : Calling hook: set_defaults
2010-08-17 10:46:30,092 INFO    : Calling hook: bootstrap
2010-08-17 11:16:37,695 ERROR   : Process (['/usr/sbin/debootstrap', '--arch=i386', 'lucid', '/tmp/tmpq1F7Gk', 'http://archive.ubuntu.com/ubuntu']) returned 1. stdout: I: Retrieving Release
E: Failed getting release file [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)
, stderr: 
Traceback (most recent call last):
  File "/usr/bin/ubuntu-vm-builder", line 24, in <module>
    uvb.main()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/contrib/cli.py", line 110, in main
    distro.build_chroot()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/distro.py", line 82, in build_chroot
    self.call_hooks('bootstrap')
  File "/usr/lib/python2.6/dist-packages/VMBuilder/distro.py", line 66, in call_hooks
    call_hooks(self, *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/util.py", line 165, in call_hooks
    getattr(context, func, log_no_such_method)(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/ubuntu/distro.py", line 142, in bootstrap
    self.suite.debootstrap()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/ubuntu/dapper.py", line 269, in debootstrap
    run_cmd(*cmd, **kwargs)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/util.py", line 120, in run_cmd
    raise VMBuilderException, "Process (%s) returned %d. stdout: %s, stderr: %s" % (args.__repr__(), status, mystdout.buf, mystderr.buf)
VMBuilder.exception.VMBuilderException: Process (['/usr/sbin/debootstrap', '--arch=i386', 'lucid', '/tmp/tmpq1F7Gk', 'http://archive.ubuntu.com/ubuntu']) returned 1. stdout: I: Retrieving Release
E: Failed getting release file [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)
, stderr: [/COLOR]

Any idea as how to overcome this problem and create an image?

---

