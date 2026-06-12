---
title: "Simple question for someone who knows anything about zip"
date: 2010-04-08
forum: General Help
---

### Post by yaroto98 on 2010-04-08
I'm writing a script that unzips an archive, edits it, and zips it back up.

That being said, I've got it all figured out except for the zipping it back up.

```
unzip file.zip -d /tmp/foobar
```
##regexes###

Now when i get to zipping the files back up, I don't want to include the /tmp/foobar directory I created. I want it to have the same tree as before.

I've gotten two commands to come close, but not what I want.

```
zip -r /tmp/file.zip /tmp/foobar/*
```
 - this zips up the folders and files within /tmp/foobar/ however, it includes the /tmp/foobar tree.
```

zip -rj /tmp/file/zip /tmp/foobar/*
```
 - this gets rid of the directories, however, it gets rid of ALL the directories, and doesn't preserve any within /tmp/foobar.

Now, by default zip will ignore /tmp/foobar if you're in that directory and running zip from there. But since this is a script I don't want to be limited to where I can run the script, or lower my standards to including changedirectory lines in my script. It seems to me like I should be able to 1-liner it, and it's frustrating me.

Anyone use zip enough to be able to help me?

---

### Post by yaroto98 on 2010-04-08
bump?

---

### Post by Tilex on 2010-04-08
Bumping after 30 minutes is a bit excessive there ...

Your command "zip -r /tmp/file.zip /tmp/foobar/*"
tells to zip everything in the /tmp/foobar/ directory into /tmp/file.zip.

You want to *exclude* that folder, so you must specify it with the -x (see man pages).

It would thus look like :
zip -r /tmp/file.zip /what-you/want-to-zip/* -x /tmp/foobar/*

If there are many directories you wish to exclude, you could create a file named "exclude.lst", include all the directories to be excluded, and write :
zip -r /tmp/file.zip /what-you/want-to-zip/* [email]-x@exclude.lst[/email]

---

### Post by diesch on 2010-04-08
> **yaroto98 said:**
> I'm writing a script that unzips an archive, edits it, and zips it back up.

Now, by default zip will ignore /tmp/foobar if you're in that directory and running zip from there. But since this is a script I don't want to be limited to where I can run the script, or lower my standards to including changedirectory lines in my script.


Why you don't want to use *cd* in a script?

---

### Post by yaroto98 on 2010-04-09
I did look at the man page, several times. However after trying every combination using -x I looked at the man page again looking for examples, and -x only excludes files, not directories.

Any other ideas?

---

### Post by smartidiot on 2010-04-09
```
zip -r /tmp/file.zip /tmp/foobar/*
```
 - this zips up the folders and files within /tmp/foobar/ however, it includes the /tmp/foobar tree.

Have you tried running the command from the /tmp/foobar directory?

For example:
```

cd /tmp/foobar
zip -r /tmp/file.zip *

```

I would think that should fix your problem.

By including the path in your zip command it will include the path in the zip file.

---

### Post by Hikayu on 2010-04-09
Sry, didn't see first post. My answer was stupid. How do you delete a post?

---

### Post by aeiah on 2010-04-09
> **smartidiot said:**
> ```
zip -r /tmp/file.zip /tmp/foobar/*
```
 - this zips up the folders and files within /tmp/foobar/ however, it includes the /tmp/foobar tree.

Have you tried running the command from the /tmp/foobar directory?

For example:
```

cd /tmp/foobar
zip -r /tmp/file.zip *

```

I would think that should fix your problem.

By including the path in your zip command it will include the path in the zip file.

this seems like the best solution. set your path as a variable then you can use it when you unzip, and then again to change directory before zipping back up. if its always gonna be in /tmp/ then you dont even need to do that.

---

### Post by Paddy Landau on 2010-04-09
The above posters are correct; you need to change directory first.

I don't know how changing a directory would "lower standards". You may find the commands pushd and popd useful, as they let you remember where you were before changing directory.

---

### Post by yaroto98 on 2010-04-09
I guess cd-ing isn't "lowering my standards", it just seems like I should be able to just say in one command "zip this directory and everything underneath it, and nothing above it". That doesn't seem like it's asking too much does it?

More than anything it's become personal between me, my coworkers and zip....

---

### Post by Paddy Landau on 2010-04-09
> **yaroto98 said:**
> I should be able to just say in one command "zip this directory and everything underneath it, and nothing above it". That doesn't seem like it's asking too much does it?
Well, there's no "should" or "shouldn't" about it, it's just the way it is.

The manual for zip says, "... paths stored in zip archives are always relative." Zip actually is deliberately programmed that way.

You could get the zip source code and modify it to add a new option to specify the starting directory. But that would be an awful lot of work!

Do you have to use zip? Would tar + bzip2 do? If so, you can do it in one command with tar's --directory and --bzip2 options.

---

### Post by yaroto98 on 2010-04-09
Yea, unfortunately I do have to use zip, unless another program can use the same zip algorithm.

---

### Post by Paddy Landau on 2010-04-09
In that case, you're stuck with pushd, zip, popd.

---

