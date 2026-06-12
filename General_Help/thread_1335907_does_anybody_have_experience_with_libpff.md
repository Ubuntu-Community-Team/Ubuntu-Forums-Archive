---
title: "does anybody have experience with libpff?"
date: 2009-11-23
forum: General Help
---

### Post by DouglasAWh on 2009-11-23
I need to recover a PST file (the Great Satan is opening that spec up, right?)

I've run ./configure on the latest version of libpff found at [http://sourceforge.net/projects/libpff/files/](http://sourceforge.net/projects/libpff/files/) .

However, the tools listed at [http://www.forensicswiki.org/wiki/Libpff](http://www.forensicswiki.org/wiki/Libpff) aren't in my path.  I looked through the configure output and it wasn't particularly helpful.  I started looking at the configure file itself for some clues, but it's bedtime and I thought maybe someone else would understand it better.  

I'd upload the configure file, but UF doesn't take files without extensions and you can get it from the sourceforge link at the top.  if someone wants me to put .txt on the end and upload, I will.  Also, I was going to do the ./configure output, but seems that history is already gone out of bash.  If someone wants that, I can re-run it but for the time being, I need to go to bed.

Thanks in advance for the help!

---

### Post by DouglasAWh on 2009-11-24
So, there was a little PEBKAC here, but now I've got it compiled and working but I still don't have pffrecover, which is what I think I want.  pffexport definitely works on files that are not corrupt but have yet to see it work on a corrupt file.

---

### Post by DouglasAWh on 2009-11-25
So, got things compiled and spoke briefly with one of the developers.  However, I am still getting an error

```

Opening file.
Error opening file: archive.pst.
libpff_index_read_node: mismatch in crc ( 253233616 != 1670426924 ).
libpff_index_read_tree: unable to read index root node.
libpff_io_handle_read_offset_index: unable to read offset index.
libpff_file_open_read: unable to read offset index.
libpff_file_open_file_io_handle: unable to read from file handle.
libpff_file_open: unable to open file: archive.pst.

```

---

### Post by heartbeat348 on 2009-12-28
I have just compiled on Jaunty without any problems. I have had a quick look at the pdf docs provided on sourceforge. If you compile with the verbose and debug options switched **on** pffexport generates what appear to be quite comprehensive log files. It might be worth your while recompiling with switches on (if you haven't already done so) then check the log files to see if it has detected where the corruption has occurred. BTW I recommend the pdf docs as an interesting read.

Good Luck
Dave
[Blackdog Forensics]("http://www.blackdogforensics.co.cc")

---

