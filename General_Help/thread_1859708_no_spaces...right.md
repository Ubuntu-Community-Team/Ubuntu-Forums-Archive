---
title: "no spaces...right?"
date: 2011-10-14
forum: General Help
---

### Post by liquidmonkey on 2011-10-14
i've read a few places that when naming a directory or file, u should not include spaces, instead capital the next word or add a '-' etc.

so why does the Ubuntu One folder have a space in it?
anyway to change this so that it still syncs etc.

---

### Post by mikejonesey on 2011-10-14
you can have spaces no prob, the uppercase thing is called camel case and can make life easyer, would you rather;

cd new\ dir
cd "new dir"

or

cd newDir

however i'm sure you will find standards or at least recommendations to not include spaces in web projects... this is to keep urls user firendly... (%20 is not nice...)

---

### Post by WorMzy on 2011-10-14
Wherever you read that, it was wrong.

You can use practically anything in a file/folder name*. The only character that I can remember you're not allowed to us is "/", for obvious reasons.


*on a Linux filesystem

---

### Post by IWantFroyo on 2011-10-14
You can perfectly have spaces. I don't do it, because in my opinion it breaks up the name and looks messy, but if you like it, there's really no problem with it.

Maybe the guide you read was for Windows? I don't remember W7 very well, but I think it might have flipped at me once for doing that...

---

### Post by liquidmonkey on 2011-10-14
ok, thanks for the responses but can we get past the first line in my post please.

i'm using the Ubuntu One folder to keep some programs and am having problems with the fact that that THERE IS a space in that directory name.

specifically, the problem is in my .bashrc file and the space seems to cause the problem.

---

### Post by WorMzy on 2011-10-14
Escape the space with a backslash, or put quotes around the path.

e.g.

~/Ubuntu\ One
"~/Ubuntu One"

---

### Post by liquidmonkey on 2011-10-14
i'm sorry, none of those solutions works for the .bashrc file.

even more specific i'm using ROS and roscd but the line that points to the directory where ros is stored keeps removing the space in the Ubuntu\ One part.
i also tried renaming the Ubuntu One folder to ubuntuOne but that was no good either.

i can link another directory to Ubuntu One as a go around but it defeats the purpose IMHO.

any other suggestions are welcome.
thanks!

---

### Post by mikejonesey on 2011-10-14
escape should work... but to get the job done sym link...

ln -s /folder\ with\ spaces/ /folderCamelCase/

then ur prog can use a path with no space...

---

### Post by liquidmonkey on 2011-10-14
thanks for the help.
i moved the folder to dropbox instead.

---

### Post by sisco311 on 2011-10-14
> **WorMzy said:**
> Wherever you read that, it was wrong.

You can use practically anything in a file/folder name*. The only character that I can remember you're not allowed to us is "/", for obvious reasons.


*on a Linux filesystem

A file name can contain any character but a forward slash, which is the name of the root directory and the path separator, and the NULL (\0) character, which is the end of text indicator.

---

### Post by liquidmonkey on 2011-10-14
well my whole point is that by adding a space in a sync folder like ubuntu one, it causes problems for programmers who want to use it as a reference or keep their stuff secure in the cloud.

but everyone here is so focused on what characters can be used or not.

---

### Post by WorMzy on 2011-10-14
If you're a programmer, I'd suggest you use something purpose built for handling code. Like launchpad, or github.

---

