---
title: "prevent file from being deleted"
date: 2010-12-31
forum: General Help
---

### Post by v923z on 2010-12-31
Hi All,

I would like to ask if there is a way of preventing a file from being deleted, but still retaining the option of editing it. I know that I can set write access off with chmod, but that would also mean that I can't edit the file any more. What I would like to achieve is to make it impossible to remove a file on which I am working. 
Cheers,
Zoltán

---

### Post by r_s on 2010-12-31
use  *chattr* to manage special attributes of a file in ext3
[I]man lsattr
man chattr[/I]
[http://yonitg.com/chattr-lsattr-linux-files-permissions/](http://yonitg.com/chattr-lsattr-linux-files-permissions/)

---

### Post by v923z on 2011-01-01
Thanks for the hint! I haven't yet been able to find out, whether this would also work on ext4. All my partitions are ext4 at the moment, and I don't really want to "downgrade" them to ext3. I have seen that there are some problems with chattr and ext4. 
Cheers,
Zoltán

---

### Post by v923z on 2011-01-01
> **r_s said:**
> use  *chattr* to manage special attributes of a file in ext3

I have tried this, and this doesn't work at all. The undeletable flag (u) of chattr is not respected. Even if I set it, I can remove the file without any problems, in fact, the OS doesn't even ask for confirmation. Rather frustrating. I just can't imagine that I am the only person with this problem. Of course, I can create a custom command, saferm, or something, which would check the attributes, and if 'u' is there, it wouldn't attempt to remove the file, but the problem with that is that any script that contains rm would just wipe out the file. Can I, then, make an alias like this
```

alias rm = 'saferm'

```where saferm contains a call to rm? Won't it become an infinite loop?
Zoltán

---

### Post by melander on 2011-01-01
Without putting words in his or her mount, I believe r_s might have been suggesting you set the "i" (immutable) attribute, unset it while you edit and reset it once you're done.

'u' if it were implemented would mean the file was capable of being undeleted, not that it would be incapable of being deleted in the first place.

However, as can be learned from reading [man chattr]("http://linux.die.net/man/1/chattr"), "[t]he 'c', 's', and 'u' attributes are not honored by the ext2 and ext3 filesystems as implemented in the current mainline Linux kernels."

[According to kernel.org]("https://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions#Can_I_undelete_files_in_Ext4.3F"), who ought to know, ext4 also doesn't implement undelete (and thus presumably the "u" attribute).

Your alias idea might be interesting. I believe you can call the original command by escaping it, so that may be a way out of your loop. You may want to research the point: the Wikipedia alias article seems very good.

It may be hard to make bulletproof:

```
mv zoltans_pet_file /dev/null
```

Regards,

---

### Post by v923z on 2011-01-01
Hi Melander,

Thanks for the comments! 
> **melander said:**
> Without putting words in his or her mount, I believe r_s might have been suggesting you set the "i" (immutable) attribute, unset it while you edit and reset it once you're done.

Yes, this is clear, but then, it wouldn't be too much different to
```

chmod a-w foo

```or something similar, in fact, it would even be worse, for you couldn't even create a link to a file. Besides, it would make scripting a bit awkward. 

> 
I believe you can call the original command by escaping it, so that may be a way out of your loop. 
It seems that the alias simply expands the content of the right hand side to the command line, therefore, it won't lead to infinitely loops. By the way, if it did, then one would have problems with the simple construct 
```

alias ls='ls -a'

```> 
It may be hard to make bulletproof:

```
mv zoltans_pet_file /dev/null
```True, although it wouldn't be hard to guard against this particular case: if the second argument is a pseudo-file, one can just skip the command. 

The bigger problem is that I don't know how to evaluate the attribute tags effectively. I could do something like this
```

x = `lsattr foo | gawk '{ if($1~/u/) print 1; else print 0}'' 
if [ $x -eq 0 ]
then 
   rm foo
fi

```but that calls gawk, and thus, it is not going to be very fast. As you pointed out, the 'u' tag is not used at the moment, so it seems rather harmless to use it in this way. Any ideas as to how to learn the value of the attribute flag?
Cheers,
Zoltán

---

### Post by sisco311 on 2011-01-01
> **v923z said:**
> Hi All,

I would like to ask if there is a way of preventing a file from being deleted, but still retaining the option of editing it. I know that I can set write access off with chmod, but that would also mean that I can't edit the file any more. What I would like to achieve is to make it impossible to remove a file on which I am working. 
Cheers,
Zoltán

Check out: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

Write permission on a file doesn't means you can delete it.

If you have write permission on some **directory**, you can add files to it, rename and delete files from it. 

So if you don't have write permission on a directory, you can't delete files from it. Try it out:
```
sisco@acme:~$ mkdir ~/foo
sisco@acme:~$ > ~/foo/bar
sisco@acme:~$ chmod -w ~/foo
sisco@acme:~$ echo 'Boldog Uj Evet!' >> ~/foo/bar
sisco@acme:~$ cat ~/foo/bar
Boldog Uj Evet!
sisco@acme:~$ rm ~/foo/bar
rm: cannot remove `/home/sisco/foo/bar': Permission denied

```

---

### Post by v923z on 2011-01-01
> **sisco311 said:**
> 
Write permission on a file doesn't means you can delete it.

Very true, my bad! However, this still doesn't bring us closer to a viable solution. 
```

v923z@penguin: joe zoltans_pet_file
La Multi Ani si Un An Nou Fericit!

```
If you set the i flag with chattr, 
```

v923z@penguin: sudo chattr +i zoltans_pet_file

```
you won't be able to delete the file (as required), but at the same time, you can't do anything with it. You can't change its content, or even create a link to it.
Cheers,
Zoltán

---

### Post by melander on 2011-01-01
> **v923z said:**
> The bigger problem is that I don't know how to evaluate the attribute tags effectively. I could do something like this
```

x = `lsattr foo | gawk '{ if($1~/u/) print 1; else print 0}'' 
if [ $x -eq 0 ]
then 
   rm foo
fi

```but that calls gawk, and thus, it is not going to be very fast.

It appears that lsattr has u as the second character in the line if 'u' is set. Could you do something like:

```
lsattr foo | grep -c -e ^.u
```

Regards,

---

### Post by v923z on 2011-01-01
> **melander said:**
> It appears that lsattr has u as the second character in the line if 'u' is set. Could you do something like:

```
lsattr foo | grep -c -e ^.u
```Regards,

This looks cool! Unfortunately, it doesn't work with wildcards :(
But let me pose the question in a different fashion: what is the reason for the attribute tags not being fully implemented? I have looked into the source code of cp, and it shouldn't be too difficult. In fact, cp already checks the standard attribute tags (rwx).
Zoltán

---

