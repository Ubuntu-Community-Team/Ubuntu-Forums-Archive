---
title: "How do I patch a kernel?"
date: 2012-03-01
forum: General Help
---

### Post by ClientAlive on 2012-03-01
I'm interested in this thing called efi_stub but it's slated to appear in a kernel that isn't even released yet (3.3-rc5 as of this writing). I'm not keen on using a kernel that bleeding edge but I was wondering if I can get just that part as a patch and compile it into the latest stable kernel.

I've compiled a kernel once before (probably not the greatest job of it but it worked in the end). I don't have any experience with patching a kernel though and was wondering what I need to learn about, what commands or utilities are involved maybe. Also, this would be on a 64 bit system so I'd need to be sure it would work with that.

I guess there's three parts to my question:

1) Will it work for a 64 bit system and/ or is there something I need to do in the process to make it to work?

2) How can I identify the patch or patches I need (Because I think there may be more than one for this thing).

3) How do I apply the patch or patches?

If anybody knows about these things I'd sure appreciate a shove in the right direction.

Links for efi_stub:

[http://felipec.wordpress.com/2012/01/18/efi-adventures/](http://felipec.wordpress.com/2012/01/18/efi-adventures/)
[http://lwn.net/Articles/463330/](http://lwn.net/Articles/463330/)

Thanks
--------------------

I found something on kernel.org that may answer my questions about whether it would work for 64 bit and where I can get it but I want to be sure my assumptions are correct before I go throw a party or anything.

I saw a link where you can view a list of patches in a particular kernel. It also looked like you can click through and have an opportunity to download a bz2 archive of it. There were two listed next to each other. One ends with "...32.s" and the other ends "...64.s". I wonder if that stands for 32 bit or 64 bit. Also, the page you get when you click that item on the list contains some other information I'm not sure what you do with. Hash include ("#include<//stuff>").

---

### Post by Khayyam on 2012-03-01
> **ClientAlive said:**
> [...] I guess there's three parts to my question:

1) Will it work for a 64 bit system and/ or is there something I need to do in the process to make it to work?

Thats hard to tell, I don't imagine there will be problems with EFI on 64bit.

> **ClientAlive said:**
> 2) How can I identify the patch or patches I need (Because I think there may be more than one for this thing).

From the link it looks like there is one unified "diff" (the patch format), generally a "diff" will be "unified" to patch all required files under a source tree.

> **ClientAlive said:**
> 3) How do I apply the patch or patches?

patch -p0 --dry-run -d /usr/src/linux < patch.diff 

-p = path, and 0 means strip no part of the path ... sometime you may need to use '-p1' or '-p2' or 'p3' (etc) dependent on how the patch was created (sometimes there are paths to strip off if say the patcher has made the diff against a non-standardly named tree i.e: "/usr/src/linux-3.2.32-linus-efi"

--dry-run ... this means not to apply the patch but meerly show what would be done. This is a good method of checking '-p0' is correct, and seeing if the patch will apply cleanly before removing the '--dry-run' and actually modifying the source.

> **ClientAlive said:**
> If anybody knows about these things I'd sure appreciate a shove in the right direction.

Hopefully the above gives you some idea of whats involved. The only other advice I'd give you is **not** to copy diff's from webpages/emails/etc ... use diff files only ... every char in the diff is important. Also, if the patch fails it'll give you some idea of where (these are called "failed hunks"), so you can then use an editor and try and merge in these "failed hunks" by hand, its best however to use the kernel version for which the patch is intended (though they can often work with both older and newer kernel sources of the same general release, 2.x, 3.2.x, etc ).

HTH ... khay

---

### Post by ClientAlive on 2012-03-02
> **Khayyam said:**
> Thats hard to tell, I don't imagine there will be problems with EFI on 64bit.



From the link it looks like there is one unified "diff" (the patch format), generally a "diff" will be "unified" to patch all required files under a source tree.



patch -p0 --dry-run -d /usr/src/linux < patch.diff 

-p = path, and 0 means strip no part of the path ... sometime you may need to use '-p1' or '-p2' or 'p3' (etc) dependent on how the patch was created (sometimes there are paths to strip off if say the patcher has made the diff against a non-standardly named tree i.e: "/usr/src/linux-3.2.32-linus-efi"

--dry-run ... this means not to apply the patch but meerly show what would be done. This is a good method of checking '-p0' is correct, and seeing if the patch will apply cleanly before removing the '--dry-run' and actually modifying the source.



Hopefully the above gives you some idea of whats involved. The only other advice I'd give you is **not** to copy diff's from webpages/emails/etc ... use diff files only ... every char in the diff is important. Also, if the patch fails it'll give you some idea of where (these are called "failed hunks"), so you can then use an editor and try and merge in these "failed hunks" by hand, its best however to use the kernel version for which the patch is intended (though they can often work with both older and newer kernel sources of the same general release, 2.x, 3.2.x, etc ).

HTH ... khay


Wow, awesome! That gives me a good start. In fact, I think I'll give this thing a shot, maybe this weekend. Fortunatly, the machine I'll be working on is, well was, a bare/ new machine - so no personal data to worry about losing or backing up or anything like that. I can just go for it and if something doesn't work out I can just start over and try again till I get it right.

Thanks a bunch.

;)

---

### Post by Khayyam on 2012-03-02
> **ClientAlive said:**
> [...] Fortunatly, the machine I'll be working on is, well was, a bare/ new machine - so no personal data to worry about losing or backing up or anything like that. I can just go for it and if something doesn't work out I can just start over and try again till I get it right.

The only two things you'll possible screw up is the kernel sources, which can easily be replaced, and perhaps your ability to boot (so make sure you add a seperate entry into /boot/grub/grub.conf). Otherwise you shouldn't have any issues, EFI is not like a disk driver, or filesystem, its very unlikely to destroy the install.

> **ClientAlive said:**
> Thanks a bunch

Your welcome ... best ... khay

---

### Post by ClientAlive on 2012-03-08
Well, it isn't what I expected. Turns out it's a bz2 archive

```

patch-3.3-rc6.bz2

```I tried running:

```

patch -p0 --dry-run -d /usr/src/linux < patch-3.3-rc6.bz2

```I get:

```

patch unexpectedly ends in middle of line
patch: **** Only garbage was found in the patch input.

```I also tried on the uncompressed file and got a similar result. I guess I'm unfamiliar with patch but I'm gonna look at the man page and see what I can learn about it.

So the result I get on the uncompressed file (using -p0) is:

```

can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/CREDITS b/CREDITS
|index 44fce988eaac..370b4c7da39b 100644
|--- a/CREDITS
|+++ b/CREDITS
--------------------------
File to patch: linux-3.2.2-hardened-r1
linux-3.2.2-hardened-r1: No such file or directory
Skip this patch? [y] 

```The patch is located in /usr/src  right next to the physical kernel source (my full kernel source that I'm trying to patch).

```

(chroot) sysresccd src # pwd
/usr/src
(chroot) sysresccd src # ls
linux  linux-3.2.2-hardened-r1  patch-3.3-rc6  patch-3.3-rc6.bz2
(chroot) sysresccd src # 

```What I have as my kernel source is

```

linux-3.2.2-hardened-r1

```-------------

[B]Edit:

running the command with "-p1" seems to yield a result but I'm not certain what I'm looking at.[/B] [B]

It would keep outputting:[/B] ```
 [B]
Reversed (or previously applied) patch detected!  Assume -R? [n] n
Apply anyway? [n] y
[/B]
```[B]and I would answer it "n" then "y" then every once in a while it would tell me some, specified, hunk failed.

What am I doing wrong here?
-----------------

Edit:

Here's the thing, and I probably should share this:

The full kernel source that I'm trying to patch is not a normal, vanilla kernel you would get from kernel.org. It's a hardened kernel source. So the idea is that when adding this patch to it I want to avoid it removing stuff to do with the hardening. Add not remove stuff - so to say. Maybe a better approach for me would be to obtain a vanilla kernel (the latest stable one) and see if I can get the patch that makes it hardened. Then add both the patch for 3.3-rc6, that has efi_stub in it, and the patch for hardening. I'm not sure. If there is a way to add the 3.3-rc6 patch w/o it screwing up the hardened stuff that would certainly be more straightforward I think.
[/B]

---

