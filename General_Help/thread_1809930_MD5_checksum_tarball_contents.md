---
title: "MD5 checksum tarball contents"
date: 2011-07-22
forum: General Help
---

### Post by roomey on 2011-07-22
Hi All,
I have a large tarball which is bz2 compressed, and I would like to get a md5 sum of the files contained in it, as I have a separate directory on another server containing what I think are the same files.
I want to check to see if the tarballs files are the same as the uncompressed files on the remote server. 
The files are big 10gb+ so I was wondering if there was a quick way without having to uncompress them all and then md5 them.

---

### Post by gmargo on 2011-07-22
Not an MD5 solution, but you might try the "-d" option on tar to compare the archive to the filesystem.
From the **tar(1)** man page:
```

     -d, --diff, --compare
           find differences between archive and file system

```

---

### Post by roomey on 2011-07-22
> **gmargo said:**
> Not an MD5 solution, but you might try the "-d" option on tar to compare the archive to the filesystem.


Thanks, problem is the files on the remote server were not tarred! I just did it the normal way, untarred the archive and then compared md5sums. 
Thanks for your help!

---

### Post by gmargo on 2011-07-22
Just for fun I whipped up a perl script that will generate MD5SUMs of all the files in a compressed tar archive:
```

#!/usr/bin/perl -w
# vim: ts=8 sts=4 sw=4 et :
use strict;
use warnings;

# Generate MD5SUMS for files within a compressed tar archive.
# G. Margo 2011-07-22
#
# Usage: tar_sum.pl tarfilename

use Archive::Tar;
use Digest::MD5 qw(md5_hex);

my $filename = $ARGV[0];
die("File not found") unless -f $filename;

my $iter = Archive::Tar->iter($filename, 1, {limit => 1});

while(my $f = $iter->())
{
    next unless $f->is_file;
    print md5_hex($f->get_content)." *".$f->name."\n";
}

exit 0;

```

---

### Post by roomey on 2011-07-25
Hi G. Marco,
That works really well! I thought scripting may be the way to do it, but I didn't have time to figure out how to! either way the remote server was disconnected so we didn't even get the chance to md5sum the originals! thanks for your help.
Ronan

---

