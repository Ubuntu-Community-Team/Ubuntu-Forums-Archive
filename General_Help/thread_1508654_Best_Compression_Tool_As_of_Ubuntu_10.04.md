---
title: "Best Compression Tool As of Ubuntu 10.04"
date: 2010-06-13
forum: General Help
---

### Post by Gias Kay on 2010-06-13
I used to use PeaZip for the job, but it's not a very good application. It doesn't depend on other compression libs in the repository but maintains its own; it's more like a program for Windows got ported to Linux.

I just had a fresh install of Lucid and would like to find a better tool handling the job. What I'm looking for is an application that can handle .7z, .rar formats, has a not-so-bad GUI, and depends on compression libs in the repository. Any recommendations?

---

### Post by Kulshrax on 2010-06-14
If you would like a GUI compression program that doesn't act like a Windows program, you should use the default compression application that comes with Ubuntu, [File Roller]("http://en.wikipedia.org/wiki/File_Roller"). While File Roller is not listed in the applications menu, it is the default app that pops up whenever you double-click an archive. However, it does not support formats such as .rar, .7z, .xz, etc by default, which is why many users end up using apps like PeaZip.

However, there is an easy fix for this. File Roller will support any compression format installed in Ubuntu. Install the package **p7zip-full**, and presto! Now Ubuntu will have support for .7z, rar, etc. You can open/make archives right in the file manager. Additionally, if you would like support for the up-and-coming [.xz format]("http://en.wikipedia.org/wiki/XZ_Utils") (basically a more modern version of .lzma), install **xz-utils**, and you'll be able to open .tar.xz files.

While p7zip-full won't handle things like PEA, *PAQ, Arc, and some other formats PeaZip supports, it will handle rar, 7z, and other common formats easily. Coupled with p7zip-full and 
xz-utils, Ubuntu will support all the archive formats you're likely to stumble upon.

**EDIT:** To correct the above, if you want rar support in File Roller, you'll need to install **unrar** as well.

---

### Post by jheis on 2010-06-15
I have 7zip installed, but every time I try to open a rar file the archive manager tells me:

Could not create the archive
Archive type not supported.

What am I doing wrong?

James

---

### Post by ks07 on 2010-06-15
In synaptic, make sure you have unrar installed. Click here to install: [apt:unrar](apt:unrar)

---

### Post by Kulshrax on 2010-06-15
Oops, I forgot to mention that in my original post. By default, p7zip does not support rar files because rar is a non-free format. However, support can be added by installing either **p7zip-rar** or **unrar**.

If you're using File Roller to open archives, you have to install unrar to get rar support in the GUI.

However, if you're using p7zip on the command line, you'll need to install p7zip-rar to get rar support. Note than installing p7zip-rar does NOT give File Roller rar support. For that, you need unrar. p7zip-rar is for the command line only.

---

### Post by Gias Kay on 2010-07-29
Thanks for your very helpful info Kulshrax! =)

---

### Post by abdusamed on 2010-11-19
Can you please a tool which actually compresses?? The tools I tried, pzip and fileroller, all they do is compress pictures from 11.8mb to 11.7!!

---

### Post by Kulshrax on 2010-11-19
> **abdusamed said:**
> Can you please a tool which actually compresses?? The tools I tried, pzip and fileroller, all they do is compress pictures from 11.8mb to 11.7!!

While you have not provided any specifics on your specific circumstances, I will try to answer your question.

You said you are trying to compress pictures. However, you are getting very poor compression ratios. This is because the pictures are in all likelihood ALREADY COMPRESSED!

Most digital photographs are stored in the JPEG format. This format already employs lossy compression algorithms to compress the image, producing a small filesize. This means that each JPEG file is already compressed. *No compression utility will be able to compress it any further.*

The same holds true with PNG images, GIF images, or any image in a compressed format. If the image is already in a compressed format, it cannot be compressed further.

---

### Post by linux18 on 2010-11-19
> **abdusamed said:**
> Can you please a tool which actually compresses?? The tools I tried, pzip and fileroller, all they do is compress pictures from 11.8mb to 11.7!!
pictures, music, and movies dont't compress very well (8% at the most)

---

### Post by abdusamed on 2011-03-07
well.. i doubt it cause recently during my data backup using winzip to create zipx archives, it was able to in some causes compress data with 2.5 gb less than original folder size!!!! Picture too were relatively compress very well. Also, I have came across with some tar archives which are kb in size but extract to serveral mbs! I was never able compress anything like that in ubuntu. Does pzip really compress?

---

### Post by Kulshrax on 2011-03-07
> **abdusamed said:**
> well.. i doubt it cause recently during my data backup using winzip to create zipx archives, it was able to in some causes compress data with 2.5 gb less than original folder size!!!! Picture too were relatively compress very well. Also, I have came across with some tar archives which are kb in size but extract to serveral mbs! I was never able compress anything like that in ubuntu. Does pzip really compress?

Yes, p7zip does compress files, and should be able to achieve similar results to ZIPX.

The size of the files is not the issue. The issue is how much redundancy there is in the data. For example, a WAV audio file or a BMP image will compress very well, as these types of files are not already compressed, and therefore contain much redundant information. However, an MP3 audio file or a JPEG image would NOT compress well, because these formats already employ their own compression, and the resulting files contain little redundancy.

With regards to ZIPX, ZIPX is essentially a .zip file that uses more modern compression algorithms. Instead of using the DEFLATE algorithm (which is used by .zip and tar.gz), it uses either bzip (as in tar.bz files) or LZMA (used by 7-zip, xz-utils, etc). As a result, ZIPX should perform no better than what 7-zip or xz-utils is able to do.

Again, the degree of compression you achieve is dependent on both the compression algorithm used and the redundancy in the data being compressed. If you believe that your files should be able to compress well, experiment with different compression formats, like tar.gz, tar.bz2, tar.xz, .7z, etc, and see which one works best. But remember that even the best compression algorithm cannot compress data that contains no redundancy.

---

### Post by abdusamed on 2011-03-08
Thanks for the information. I guess, I'm going install pzip again. 

Whats sucks right now is there is no gui for 7zip.

---

### Post by Sazhen86 on 2011-03-08
7zip archives are supported by File Roller.

---

