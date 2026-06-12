---
title: "Undo &quot;make&quot;"
date: 2009-10-15
forum: General Help
---

### Post by adman4054 on 2009-10-15
Feel like I am in way over my head. Running 8.04 and I'm trying to fix an ffmpeg install that doesnt output the audio.  Working in putty I unistalled ffmpeg, and I am up to and including downloading the ffmpeg and dependices and running the "make" command. Thats as far as I have gotten. I need to start over again following some different instructions that I understand! My question is this, with just as far as the "make" command how can I undo and start over again. Sorry about the nob question, but da**it I'm going to learn this stuff :)

---

### Post by Giblet5 on 2009-10-15
It depends (heh, a pun) on whether your make project file provides for that.

There should be a file called "Makefile" in the project's top-level directory.

Go to that directory and type ```
make clean
```

If you get an error, then there is no "clean" target. Maybe it's called "tidy". You can look at the Makefile and find out. Look for something like: ```
cleanup:
  -cd src && rm -f *.o *.a *.so
```

That target would work with ```
make cleanup
```

It's not as cryptic as it looks.

---

### Post by adman4054 on 2009-10-15
> **Giblet5 said:**
> It depends (heh, a pun) on whether your make project file provides for that.

There should be a file called "Makefile" in the project's top-level directory.

Go to that directory and type ```
make clean
```

If you get an error, then there is no "clean" target. Maybe it's called "tidy". You can look at the Makefile and find out. Look for something like: ```
cleanup:
  -cd src && rm -f *.o *.a *.so
```

That target would work with ```
make cleanup
```

It's not as cryptic as it looks.

Thanks for the quick reply, "make clean" didnt show any errors but I do see that there are still items in the directory, is that ok when starting over?

Thanks again!

---

### Post by Giblet5 on 2009-10-15
> **adman4054 said:**
> Thanks for the quick reply, "make clean" didnt show any errors but I do see that there are still items in the directory, is that ok when starting over?

Thanks again!

Yeah, 'make clean' will only remove the compiled binaries that the build process creates. That returns the source package to its "clean" state...

When you do a manual build, it usually comes in a tarball (.tar.gz or .tar.bz2) and extracts into a directory eg, ffmpeg-1.0.1.2, and that's is where you go to type 'make' or './configure'.

Just roast that directory if you want it gone. ```
 rm -r ffmpeg-1.0.1.2
```

---

### Post by adman4054 on 2009-10-15
> **Giblet5 said:**
> Yeah, 'make clean' will only remove the compiled binaries that the build process creates. That returns the source package to its "clean" state...

When you do a manual build, it usually comes in a tarball (.tar.gz or .tar.bz2) and extracts into a directory eg, ffmpeg-1.0.1.2, and that's is where you go to type 'make' or './configure'.

Just roast that directory if you want it gone. ```
 rm -r ffmpeg-1.0.1.2
```


Thanks!!

---

### Post by shivaa on 2010-10-28
Please help
[http://ubuntuforums.org/showthread.php?p=10042073#post10042073](http://ubuntuforums.org/showthread.php?p=10042073#post10042073)
Thanks!!

---

