---
title: "emacs: opening stuff on startup"
date: 2010-08-08
forum: General Help
---

### Post by f1r3br4nd on 2010-08-08
Hi, I'm on my latest attempt to use emacs as my main text editor, and I've gotten further than before. The only snag is how to get emacs to open certain files whenever it starts up, and certain groups of files depending on what task I'm doing-- just like the sessions in the kate text editor.

After searching long and hard I still can't figure out the syntax for just hardcoding into ~/.emacs specific files to open. So as far as I can tell, what I need to do is put

```
(server-start)
```

into ~/.emacs and have an alias or small shell script that invokes it with the files I want open no matter what I'm doing...

```
emacs fileA.txt fileB.pdf fileC.html
```

And then, if I'm working on a specific task that needs a specific group of files to be opened at the same time, I would have another alias or shell script, this time to emacsclient...

```
emacsclient fileX.txt fileY.txt fileZ.txt
```

Because I have (server-start) in the .emacs file, any additional files that are opened via emacsclient get sent to the original instance instead of invoking emacs directly which would start a new instance. 

This works, but it seem so cumbersome! Is there really no way to specify all this in the .emacs configuration instead?

Also, is there a way to programatically close a list of named buffers if they happen to be open? The purpose of this is to get rid of the activity specific files when I am done with that activity without having to restart emacs.

Thanks.

---

