---
title: "Perl error running findimagedupes"
date: 2010-10-31
forum: General Help
---

### Post by jordon on 2010-10-31
I'm using Ubuntu 10.10, and I just installed findimagedupes (plus dependencies) from the repositories. I get the same error message no matter how I invoke it:

```
$ findimagedupes -R -- images/
Can't locate findimagedupes/C.pm in @INC (@INC contains: /usr/lib/findimagedupes/lib /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/bin/findimagedupes line 41.
BEGIN failed--compilation aborted at /usr/bin/findimagedupes line 41.
```

This seems to be a problem with Perl, which I don't have any experience with. I noticed that the file /usr/lib/findimagedupes/lib/i486-linux-gnu-thread-multi/findimagedupes/C.pm does exist, so I made a link to it at /usr/lib/findimagedupes/lib/findimagedupes/C.pm. Now I get the following error:

```
$ findimagedupes -R -- images/
The extension 'findimagedupes::C' is not properly installed in path:
  '/usr/lib/findimagedupes/lib'

If this is a CPAN/distributed module, you may need to reinstall it on your
system.

To allow Inline to compile the module in a temporary cache, simply remove the
Inline config option 'VERSION=' from the findimagedupes::C module.

 at /usr/bin/findimagedupes line 0
```

This was probably the wrong thing to do, but I figured it couldn't hurt. If I delete the link, the previous error reappears.

Can anyone help?

---

### Post by gmargo on 2010-10-31
It works fine for me on 64-bit 10.10 Maverick.  I suggest you remove and reinstall the package.  You should see that file under /usr/lib/findimagedupes/lib/x86_64-linux-gnu-thread-multi/findimagedupes/C.pm

---

### Post by jordon on 2010-10-31
> **gmargo said:**
> It works fine for me on 64-bit 10.10 Maverick.  I suggest you remove and reinstall the package.  You should see that file under /usr/lib/findimagedupes/lib/x86_64-linux-gnu-thread-multi/findimagedupes/C.pm

I completely removed and reinstalled the package and some of its dependencies (libgraphics-magick-perl, libfile-mimeinfo-perl, libinline-perl), but I'm getting the same error. The file is still at /usr/lib/findimagedupes/lib/i486-linux-gnu-thread-multi/findimagedupes/C.pm (I'm using 32-bit Maverick).

---

### Post by gmargo on 2010-10-31
I confirm: I get the same error as you under 32-bit 10.10 Maverick.  Will investigate a bit further.

```

$ findimagedupes 
Can't locate findimagedupes/C.pm in @INC (@INC contains: /usr/lib/findimagedupes/lib /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/bin/findimagedupes line 41.
BEGIN failed--compilation aborted at /usr/bin/findimagedupes line 41.

```

---

### Post by gmargo on 2010-10-31
**strace** tells me that perl is looking for an **i686** directory, not **i486**.  Here's how to make **findimagedupes** work:
```

$ cd /usr/lib/findimagedupes/lib
$ sudo ln -s i486-linux-gnu-thread-multi i686-linux-gnu-thread-multi
$ ls -lgG
total 4
drwxr-xr-x 4 4096 Oct 31 14:28 i486-linux-gnu-thread-multi
lrwxrwxrwx 1   27 Oct 31 15:26 i686-linux-gnu-thread-multi -> i486-linux-gnu-thread-multi

```

---

### Post by jordon on 2010-10-31
Thanks! That did the trick. Should a bug report be filed for findimagedupes?

---

### Post by gmargo on 2010-11-01
Bug report filed:
[https://bugs.launchpad.net/ubuntu/+source/findimagedupes/+bug/669661](https://bugs.launchpad.net/ubuntu/+source/findimagedupes/+bug/669661)

---

