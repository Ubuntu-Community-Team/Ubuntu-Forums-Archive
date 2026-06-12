---
title: "mysqld and libstdc++.so.6"
date: 2012-04-25
forum: General Help
---

### Post by BenPope on 2012-04-25
So this morning my version of mysql-server-5.1 stopped working on two machines.  One has 10.04 LTS and the other 11.10.

On both machines I have previously installed GCC 4.7, added the requisite symbolic link to libstdc++.so.6.0.17 in the lib directory, and called ldconfig to set up the symbolic link of libstdc++.so.6 to to libstdc++.so.6.0.17 (overwriting the existing link to an older version).

Everything was running fine, until mysql-server decided to upgrade today, I'm guessing the upgrade triggered a restart that prompted the problem that has been a ticking time bomb since ldconfig was called.

Now I get:
mysqld: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

The file (actually a symbolic link to the file) is in the location pointed to by ldd.  The weird thing is, if I remove the links to libstdc++.so.6.0.17 and call ldconfig again, on Lucid I get libstdc++.so.6 -> libstdc++.so.6.0.13 and on Oneiric I get libstdc++.so.6 -> libstdc++.so.6.0.16, and mysqld works again in both cases.

In each case that's the libstdc++ that was supplied with the system.

Is there a problem with mysql-server-5.1 5.1.62-0ubuntu0-10.4.1 that somehow requires the exact version of libstdc++ it was built with?

Have I done something wrong when I installed GCC 4.7 and updated libstdc++.so.6?  (Of course, I left the original g++ intact and added the -4.7 suffix to the binaries, but various other runtime bits have been updated).

I think it's strange that it's coming up with "file not found".  The dependencies (from ldd) of libstdc++.so.6.13/16 are the same as .17.

Thanks for any help with this.

I guess the workaround is to set LD_CONFIG_PATH to include a path that has a symlink from libstdc++.so.6 to the "native" libstdc++ before launching mysqld, but it seems that I shouldn't have to do this and no other programs are having a problem (that I'm aware of).

Edit: The above workaround does not work.  I still get "file not found", even though ldd tells me it's looking in the new location specified by LD_CONFIG_PATH.  Now I'm really confused.  How do I find out which file it's looking for and can't find?

---

### Post by BenPope on 2012-04-25
Maybe this explains it more clearly:
```
ben@yyls03:~$ which mysqld
/usr/sbin/mysqld
ben@yyls03:~$ /usr/sbin/mysqld
/usr/sbin/mysqld: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
ben@yyls03:~$ ldd /usr/sbin/mysqld
	linux-vdso.so.1 =>  (0x00007fffd237c000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f18dad67000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f18dab4f000)
	libwrap.so.0 => /lib/x86_64-linux-gnu/libwrap.so.0 (0x00007f18da945000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f18da741000)
	libcrypt.so.1 => /lib/x86_64-linux-gnu/libcrypt.so.1 (0x00007f18da508000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f18da200000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f18d9f7c000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f18d9bdb000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f18dbb70000)
	libnsl.so.1 => /lib/x86_64-linux-gnu/libnsl.so.1 (0x00007f18d99c0000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f18d97aa000)
ben@yyls03:~$ ls -alH /usr/lib/x86_64-linux-gnu/libstdc++.so.6
-rwxr-xr-x 1 root root 6462357 2012-03-23 12:34 /usr/lib/x86_64-linux-gnu/libstdc++.so.6

```

---

### Post by BenPope on 2012-04-26
This is getting more and more weird.

If I copy /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.17 over the top of /usr/lib/x86_64-linux-gnu/libstdc++.so.6 it works, but a symlink does not.  So the problem seems to be that it doesn't want to follow the symlink.

The symlink was created by ldconfig.

And mysqld is now using /usr/lib/x86_64-linux-gnu/libstdc++.so.6 as confirmed by setting LD_DEBUG=all

---

