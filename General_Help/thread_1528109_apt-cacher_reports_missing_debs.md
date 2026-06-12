---
title: "apt-cacher reports missing debs"
date: 2010-07-10
forum: General Help
---

### Post by imbjr on 2010-07-10
Twice now I've received mails from my server's apt-cacher indicating a potential problem. Here's one of them:

```

/etc/cron.daily/apt-cacher:
Unable to open file adduser_3.112ubuntu1_all.deb to verify checksum: No such file or directory at /usr/share/apt-cacher/apt-cacher-cleanup.pl line 685.
run-parts: /etc/cron.daily/apt-cacher exited with return code 2

```

I'm assuming that the existing cache of debs is incomplete, despite my running the script that populates the cache with the existing server deb packages. Apart from re-installing the named debs I'm not sure what else to do - or even if there is a real problem.

---

### Post by ErwanH on 2010-09-09
I had the same problem. Some of the DEB files were dead links.

[http://www.unix.com/shell-programming-scripting/112531-delete-dead-links.html](http://www.unix.com/shell-programming-scripting/112531-delete-dead-links.html)

To find how to delete all dead links I adapted that code:

> 
```
for FILE in *; do
  ls -dL $FILE >/dev/null 2>&1 || echo RM $FILE
done
 
```Or recursively...
 
```
for FILE in $(find .); do
  ls -dL $FILE >/dev/null 2>&1 || echo RM $FILE
done
 
```replace the echo RM with rm when you're happy!
This did the trick for me:

```

cd /var/cache/apt-cacher/packages/
sudo -s
for FILE in *.deb; do ls -dL $FILE >/dev/null 2>&1 || rm ../headers/$FILE; done
for FILE in *.deb; do ls -dL $FILE >/dev/null 2>&1 || rm $FILE; done
exit

```

---

### Post by imbjr on 2010-09-09
> **ErwanH said:**
> I had the same problem. Some of the DEB files were dead links.

[http://www.unix.com/shell-programming-scripting/112531-delete-dead-links.html](http://www.unix.com/shell-programming-scripting/112531-delete-dead-links.html)

To find how to delete all dead links I adapted that code:

This did the trick for me:

```

cd /var/cache/apt-cacher/packages/
sudo -s
for FILE in *.deb; do ls -dL $FILE >/dev/null 2>&1 || rm ../headers/$FILE; done
for FILE in *.deb; do ls -dL $FILE >/dev/null 2>&1 || rm $FILE; done
exit

```

Yes, they were all dead links. I kept pruning them away and eventually it stopped happening.

It's a nice piece of software. It's spared me having to wait yet again for a download I've already done elsewhere on the network.

---

### Post by Parasytic on 2010-10-19
I created a patch for this, but I don't think it's the Right Thing To Do:

```
--- apt-cacher-cleanup.pl~	2010-04-25 18:16:47.000000000 -0700
+++ apt-cacher-cleanup.pl	2010-10-19 11:17:58.492828845 -0700
@@ -672,9 +672,11 @@ if ($cfg->{checksum}) {
 for(<*.deb>, <*.udeb>, <*.bz2>, <*.gz>, <*.dsc>) {
     # should affect source packages but not index files which are added to the
     # valid list above
-    if(! defined($valid{$_})) {
+    if((! defined($valid{$_})) ||
+      ((-l $_) && (! -f $_))) {
 	unlink $_, "../headers/$_", "../private/$_.complete" unless $sim_mode;
 	printmsg "Removing file: $_ and company...\n";
+	$valid{$_} = undef;
     }
     else {
 	# Verify SHA1 checksum for uncompressed files only
```

This will check that it's a link, and then verify that the link is valid. Failing that, it deletes the [dead] link and associated metadata.

A better solution is to find out why there are any dead links, anyway.


[ EDIT: Fixed a bug where I was checking $valid{$_} instead of the filename: $_ ]

---

