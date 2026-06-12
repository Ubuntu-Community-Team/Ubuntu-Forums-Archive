---
title: "command to move multiple directories into one directory.."
date: 2009-11-28
forum: General Help
---

### Post by switch10 on 2009-11-28
```
mv -v /home/dave/Music/D/Dispatch/../Drive\ by\ Truckers/../Dusty\ Rhodes\ And\ The\ River\ Band-Palace\ And\ Stage-Advance-2009/ /media/disk/Music/D/

```

Why wont this work? Im getting this:

```
mv: inter-device move failed: `/home/dave/Music/D/Dispatch/../Drive by Truckers/../Dusty Rhodes And The River Band-Palace And Stage-Advance-2009/' to `/media/disk/Music/D/Dusty Rhodes And The River Band-Palace And Stage-Advance-2009'; unable to remove target: Is a directory
```

seems like the .. should work here right?  how else would i do it?  is there a way to mv it to 2 different directories?

---

### Post by audiomick on 2009-11-28
I think the answer is at the end of the error message. It is a directory.
I had a quick look at the man page for move

```
man mv
```

and that says it is for moving files.

I think you need a different command, but unfortunately, I don't know which one.

---

### Post by falconindy on 2009-11-28
What you want is command line substitution. You can't use .. in the way you're doing it.
```
mv /home/dave/Music/D/{Dispatch,Drive\ by\ Truckers,Dusty\ Rhodes\ And\ The\ River\ Band-Palace\ And\ Stage-Advance-2009} /media/disk/Music/D/
```

Command line substitution is probably the biggest saver of typing ever, particularly for long paths. You can do things like:
```
sudo cp /etc/ssh/sshd_config{,~}
```
And you'll instantly have a backup of your ssh config called sshd_config~. You can do crazy insane things like nesting {} inside each other for complex operations. If you're unsure of what the substitution will yield, just throw an echo in front of your command to test it.

edit: figured out your intention.

---

### Post by switch10 on 2009-11-29
> **falconindy said:**
> What you want is command line substitution. You can't use .. in the way you're doing it.
```
mv /home/dave/Music/D/{Dispatch,Drive\ by\ Truckers,Dusty\ Rhodes\ And\ The\ River\ Band-Palace\ And\ Stage-Advance-2009} /media/disk/Music/D/
```

Command line substitution is probably the biggest saver of typing ever, particularly for long paths. You can do things like:
```
sudo cp /etc/ssh/sshd_config{,~}
```
And you'll instantly have a backup of your ssh config called sshd_config~. You can do crazy insane things like nesting {} inside each other for complex operations. If you're unsure of what the substitution will yield, just throw an echo in front of your command to test it.

edit: figured out your intention.

Thanks I'll look that up.

---

### Post by switch10 on 2009-11-29
hmm.  seems I had to use the cp command instead on mv when moving to a different file system.  What could I add to this cp command to delete the original file after copying to my external drive?  I want to mimic the mv command in a sense..

---

### Post by falconindy on 2009-11-29
Check your syntax. It shouldn't matter if the destination is a different physical drive from the source. Furthermore, mv and cp can be substituted for one another if you're not specifying any options.

If you can't find the issue, you could do something like this:
```
dirs=(dir{1,2,3,4,5})
cp ${dirs[*]} destinationdir
rm -r ${dirs[*]}
```
However, this is bound to break on special characters if you're not careful with escapes.

---

### Post by SuperSonic4 on 2009-11-29
Don't single quotes work too?

```
mv -v 'dir 1' 'dir 2' /media/dir\ 3
```

also tab completion is your friend :D

---

