---
title: "How is the &quot;compression ratio&quot; calculated in the GUI"
date: 2010-02-15
forum: General Help
---

### Post by Broussard on 2010-02-15
I am creating tars and jars of some files from various floppy disks. (We are doing this at my job in the process of preserving some records from these old disks.) 

I am using Ubuntu 9.10

To create the tars and jars, I use the commands 

tar -cvf ouputfile.tar inputFolder

and 

jar cvf0 outputfile.jar inputFolder

My understanding is that neither of these commands compresses.

However, when I double click to view the tar or jar (or open it with Archive Manager) and select "properties," one line says, "compression ratio: #." Sometimes this number is 1, but sometimes it is .99, .97, or even .72. 
This occurs with both the tars and the jars. 
[B]
My question is: why is there a compression ratio for something I did not compress?

And/or: does anyone know how this number is calculated?[/B]

Notes:

If I view the properties directly from the tar or jar icon, no compression ratio shows.

We want to understand this because the integrity of these records over time is important to us. Even though lossless compression does not harm the files, we would like to understand what this number means. 

I run fixity checks using md5 and sha1, so I do know that none of the files have changed. On the tars, I also run a tar -c.

Thanks everyone!

---

### Post by ironclaw on 2010-02-16
In the Archive Manager, a compression ratio < 1 actually means that the archive file is larger than the total of the files inside the archive. I guess there is some overhead when you tar or jar files together. When you compress a text file with bzip2 the resulting file has a compression ratio > 1.

As for how it's calculated, it should be (size of uncompressed file)/(size of compressed file).

Looking at the [Wikipedia article]("http://en.wikipedia.org/wiki/Data_compression_ratio"), it seems like the inverse of the above number can also be called the compression ratio... :D

---

### Post by Broussard on 2010-02-16
Thanks! I get confused by little things. 

This is very comforting. We are probably the only institution that is happy that our container files are larger than the files we were containing.

---

