---
title: "circular symlink problem"
date: 2010-03-31
forum: General Help
---

### Post by floobit on 2010-03-31
I just started doing regular backups to an off-site server and used scp this first time to copy my entire ~/ and let it think for a few hours while I did other things.  When I came back, I found that wine uses a symlink to point to the ~/ directory, creating a circular loop for scp.  I killed the task, but now have a directory tree on the server that is many folders deep.  I tried to remove it, but bash does not allow rm to descend to the lowest level of the tree to remove things because of the maximum folder depth (error message: permission denied).  Is there a way to just delete this folder another way?

---

### Post by dcstar on 2010-03-31
> **floobit said:**
> I just started doing regular backups to an off-site server and used scp this first time to copy my entire ~/ and let it think for a few hours while I did other things.  When I came back, I found that wine uses a symlink to point to the ~/ directory, creating a circular loop for scp.  I killed the task, but now have a directory tree on the server that is many folders deep.  I tried to remove it, but bash does not allow rm to descend to the lowest level of the tree to remove things because of the maximum folder depth (error message: permission denied).  Is there a way to just delete this folder another way?

There are scripts to find and delete big quantities of object names that exceed the shell expansion limits, you should be able to find them with a web search.

---

### Post by Johnny B on 2010-03-31
Use below command that will do what you want

> find data-dir-path ! -type l ! -type d | tar -zcvf fillename.tgz -T-


from: [http://osdir.com/ml/misc.lost/2004-05/msg00027.html]("http://osdir.com/ml/misc.lost/2004-05/msg00027.html")

---

### Post by floobit on 2010-04-01
Wow.  Thank you for your prompt replies.  My google searching skills must be lacking.  I cannot find any such scripts.  There are many to delete empty directory trees, but I suspect I have several files at the bottom of each branch.  Regardless, the command does not work.  There are also scripts that delete many files, getting around the "too many arguments" issue.  These solutions did not work either.  @dcstart: Could you direct me to such a script?  

@Johnny B: I tried that (exact command shown): 
```
 find /scratch1/lauren/wine/ ! -type l ! -type d ! tar -zcvf fillename.tgz -T-
``` 

I am trying to delete the directory /scratch1/lauren/wine/ and all its contents.
I got the following:

```
find: paths must precede expression
Usage: find [path...] [expression]

```

When typing ```
find /scratch1/lauren/ wine
```

I get the expected, found output.  
Furthermore, this solution seems to be targeted at someone hoping to tar the output.  I do not wish to do so, I want to delete it.  Do you know how to modify this command to delete everything instead?  

Thank you.

---

### Post by Johnny B on 2010-04-01
I'm sorry i completly misunderstood your question.


if you can't remove the directory with 'sudo rm -rf'
i would make a script to get to the bottom of the directory structure, then delete the single directories on its way up. for exapmle:

if your directory repeats, like: /home/floobit/.wine/home/floobit/.wine/home/floobit/.wine
then you can do: while [ -d "./home/floobit/.wine" ] ;do cd ./home/floobit/.wine ;done

once that stops, we can cd up through the directory structure and remove sub-directories on the way, but that could be dangerous, because we have to know how to make it stop without going all the way up to the root dir.

Because of the danger, and since i misunderstood you once already, Please tell me more about the directory structure. is it like my first example: /home/floobit/.wine/home or is it floobit/.wine/floobit/.wine/floobit/.wine/

---

### Post by floobit on 2010-04-01
It is not strictly a linear tree.  For some reason, when it got 
18 levels deep, it started branching.  Here is the result from tab expansion from typing cd 
```
wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/c\:/windows/profiles/lauren/My\ Documents/.wine/dosdevices/z\:/

```
At this point, it decided to copy several folders:
```
home  proc  usr  var
```

./proc contains the expected empty files and extensive folder system of empty files, but I cannot delete them, getting the same permission denied issue.  This could be an independent issue.  They are all write-protected.  I am the owner, but chmod 777 says permission-denied as well.  

./usr I cannot cd into (permission denied) however a find * usr yields a directory tree of /home/lauren/.wine/dosdevices/z:/ which then repeats the structure in the last quoted section, except lacks the home folder.  There are extensive copied files in proc, as before.  

./var has one folder structure, ./cache/system-tools-backends/backup/ which I can tab-complete but not descend into.  

./home contains ./lauren/, which contains 
Desktop  .wine    yohoho

.Desktop contains ./home/yohoho/java, which contains 
bin      include  lib64    sbin     src      
games    lib      local    share    

each of which cannot be deleted (permission denied).

.yohoho contains java as above. 

.wine contains home/lauren/.wine/dosdevices/z:/ which contains 
proc usr
./proc contains the mess as before, but I think that's the lowest level.  

Ideas?

Thanks.

---

### Post by Johnny B on 2010-04-01
18 is not even close to the maximum folder depth (assuming there is one).
so I think this is a permissions problem. is there any indication of why you're getting the 'permission denied' error?
is it 'no such file or directory'?

try this and post errors please
(assuming top folder is /scratch1/lauren/wine)
```
sudo chmod 777 -R /scratch1/lauren/wine
sudo chown -R $USER /scratch1/lauren/wine

```

is wine a hidden folder?   /scratch1/lauren/**.**wine

---

### Post by floobit on 2010-04-01
Wow.  that did it.  I didn't think of chown because I was clearly shown as the owner in an ls -l, but in my diligence for following your suggestion to the letter, I reset the owner and then tried a chmod 777, and it worked that time.  with recursive options on chown and chmod 777, followed by a rm -r *, I was able to delete everything.  

Thank you so much.  I was pretty worried that I would have to call the sysadmins to do it, which they would not have been happy about.

---

