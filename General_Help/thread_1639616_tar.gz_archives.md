---
title: "tar.gz archives"
date: 2010-12-06
forum: General Help
---

### Post by COKEDUDE on 2010-12-06
Is the point of tar.gz archives to keep the execute permission? I was quite surprised this already had the execute permission after I extracted the file. 

[http://dl.dropbox.com/u/2886083/w8/launchpad-update.tar.gz](http://dl.dropbox.com/u/2886083/w8/launchpad-update.tar.gz)

---

### Post by Brandon Williams on 2010-12-08
Yes. By default, tar will keep all permissions that are allowed by the user's umask. When run by root, it doesn't even apply the umask by default.

---

### Post by COKEDUDE on 2010-12-10
> **Brandon Williams said:**
> Yes. By default, tar will keep all permissions that are allowed by the user's umask. When run by root, it doesn't even apply the **umask by default**.

What do you mean by umask by default? My man pages are very vague.

---

### Post by Brandon Williams on 2010-12-10
Your umask is your "file mode creation mask". It prevents some permission bits from being set when a file is created using the default permission setting. For example, I want any files I create to be readable only by me unless I explicitly state otherwise, so my umask is 0077, since the two 7s prevent any permission bits from being set for my group and the world. View 'man umask' to get more information about this.

By default, when tar is run by a user other than root, it will only restore permissions that are allowed by the user's umask. So when I extract a tarfile, a file in the tarball that has 0755 permissions (a.k.a. rwxr-xr-x) permissions, tar will only give it 0700 permissions because the 0055 bits are disallowed by my umask.

When root uses tar to extract files, the default behavior is different. root's umask will not be applied unless a command line flag is used to explicitly ask for the umask to be applied. Thus, by default, a file with 0755 permissions will have 0755 permissions when extracted by root, even if root's umask disallows some of the bits.

---

### Post by COKEDUDE on 2010-12-11
> **Brandon Williams said:**
> Your umask is your "file mode creation mask". It prevents some permission bits from being set when a file is created using the default permission setting. For example, I want any files I create to be readable only by me unless I explicitly state otherwise, so my umask is 0077, since the two 7s prevent any permission bits from being set for my group and the world. [B]View 'man umask' to get more information about this.
[/B]
By default, when tar is run by a user other than root, it will only restore permissions that are allowed by the user's umask. So when I extract a tarfile, a file in the tarball that has 0755 permissions (a.k.a. rwxr-xr-x) permissions, tar will only give it 0700 permissions because the 0055 bits are disallowed by my umask.

When root uses tar to extract files, the default behavior is different. root's umask will not be applied unless a command line flag is used to explicitly ask for the umask to be applied. Thus, by default, a file with 0755 permissions will have 0755 permissions when extracted by root, even if root's umask disallows some of the bits.


Isn't umask the opposite of chmod's octal numbers? 

My man pages are very vague.

---

### Post by AlphaLexman on 2010-12-11
'umask' is like 'umount' .. it really means u(n)mask or u(n)mount, the letter 'n' is left out to save keystrokes (I'm guessing).

The default 'mask' for files is 666 and 777 for directories. Your 'umask' setting/value will subtract from the default value for files or directories.

---

### Post by COKEDUDE on 2010-12-11
> **AlphaLexman said:**
> 'umask' is like 'umount' .. it really means u(n)mask or u(n)mount, the letter 'n' is left out to save keystrokes (I'm guessing).

The default 'mask' for files is 666 and 777 for directories. Your 'umask' setting/value will subtract from the default value for files or directories.

I don't have any man pages on mask. Are you sure mask exists?

---

### Post by AlphaLexman on 2010-12-11
> **COKEDUDE said:**
> I don't have any man pages on mask. Are you sure mask exists?
'mask' is not a command, but 'umask' is... see:
```
man umask
```

---

### Post by Brandon Williams on 2010-12-13
> **COKEDUDE said:**
> Isn't umask the opposite of chmod's octal numbers? 

My man pages are very vague.

Yes, I suppose that the umask value could be considered the opposite of chmod's octal numbers ... a bit that's on in the umask is not allowed to be on in the file permissions unless you do something to explicitly turn it on. As my previous post indicates, the bits that are on in the umask "prevent" bits from being turned on in the default file permissions.

If you understand how bitwise notation, application of the umask value works like this:```
applied_mask = default_mask & ~umask
```

---

