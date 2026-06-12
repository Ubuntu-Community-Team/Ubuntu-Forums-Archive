---
title: "Perl C Libraries not in Standard Location?"
date: 2011-12-16
forum: General Help
---

### Post by scorchgeek on 2011-12-16
I'm trying to do something very unusual just for fun: get my computer to respond to whistle control. I have this tutorial page: [http://www.mostlymaths.net/2009/09/whistle-control-your-computer.html](http://www.mostlymaths.net/2009/09/whistle-control-your-computer.html).

Everything works fine and I've had no trouble installing (though I had to manually edit a few source files) until I try to actually run the script, at which point I get:
```

$ perl cmdWhistle.pl
Can't locate asm/unistd.ph in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/lib/perl/5.10.1/sys/syscall.ph line 7.

```

I was told that I probably just need to recompile the perl C interface libraries (or whatever the technical term is).
```
sudo cd /usr/include
sudo h2ph *.h */*.h
```

There are no errors, but the problem is still just the same. A bit of research tells me that this seems to be a Ubuntu-specific problem, because some of Ubuntu's files are stored in a different location or with different names.

I don't know much about Perl, but I also tried installing the file via CPAN, but that failed because (I think) the missing file is not a perl module.

Has anyone seen anything like this problem? If you need more information, I'd be happy to give it.

---

### Post by c.cobb on 2011-12-17
Written a lot of Perl code, but this is new to me. Looks like you're [on the right track]("https://bugs.launchpad.net/ubuntu/+source/perl/+bug/838649"), though.

Where did the resulting *.ph files get put? And no, they aren't Perl modules but C header files. To see the default location:

```
perl -e 'use Config; print "$Config{installsitearch}\n";'
```On my system, this shows '/usr/local/lib/perl/5.10.1' which would not be the right place, as your error indicates that it's looking for an 'asm' subdirectory. Try creating an 'asm' subdir such as /usr/include/asm (if it doesn't already exist) and using the '-d' option to the h2ph command.

BTW, if /usr/include/asm already exists, confirm that unistd.ph is not there, and then just run h2ph just for that one header file.

---

### Post by scorchgeek on 2011-12-17
Thank you, that works. For future reference, the steps I took were:
```

$ cd /usr/include/
$ sudo mkdir asm
$ sudo h2ph -d asm unistd.h
unistd.h -> unistd.ph
$ sudo cp -r asm /etc/perl

```

Now I'm having a problem where I can't set the microphone source, and it only accepts input from whatever's playing on my speakers, which is really strange, but the original perl problem is solved. Thanks c.cobb!

---

