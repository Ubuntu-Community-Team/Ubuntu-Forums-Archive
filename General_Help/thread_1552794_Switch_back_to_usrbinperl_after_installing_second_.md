---
title: "Switch back to /usr/bin/perl after installing second perl?"
date: 2010-08-14
forum: General Help
---

### Post by Puzzled Guy on 2010-08-14
Hi,

I recently reinstalled the B module for perl. Now I found out it didn't just do that, it installed a whole new copy of perl into /usr/local/bin/perl. When I type 'which perl' at the terminal, it says '/usr/local/bin/perl' instead of '/usr/bin/perl'. Normally, this wouldn't bother me. But I installed the one in local/bin *without* threading support. The one that comes with the system already is build with threading support, which is why I want to switch back to the system perl, and possibly remove the one in /usr/local/bin.

So how do I change it so that the result of 'which perl' returns as '/usr/bin/perl'?
And what do I have to do to remove /usr/local/bin/perl?

The reason I need threading support is because I'm designing a file copier that copies several chunks of a file simultaneously to speed up the copying process. Guaranteed a useful script if it works. :D

---

### Post by robsoles on 2010-08-14
Please tell us how you installed the second copy of perl to your system - knowing that may help someone help you reverse it.

---

### Post by amauk on 2010-08-14
if you compiled from source
just cd to the source directory
and do
```
sudo make uninstall
```

This will uninstall everything previously installed by "make install"

You can also just delete the files under /usr/local/bin & /usr/local/lib related to perl
but it's more convenient to use make's uninstall feature

---

### Post by Puzzled Guy on 2010-08-15
Here's how I installed the second perl:
```
sudo cpan
install B
(got an error message saying I should use 'force install B')
**force install B**
```
The line in bold is what caused it to install a second perl in /usr/local/bin.
Somewhere in the installation questions, there was one asking where perl should be installed, I chose the default: /usr/local/bin/perl.

The source was most likely compiled in the CPAN temporary directory. Unfortunately, I don't know where that is. And, the source might have automatically been removed after installation.

Just deleting /usr/local/bin/perl and /usr/local/lib/perl won't change the output of "which perl" back to /usr/bin/perl, or will it?

---

### Post by Puzzled Guy on 2010-08-15
By the way, the /usr/local/bin directory is empty except for perl files. There are no other files there that belong to different software. Does that mean that I can delete the contents of /usr/local/bin? Will this automatically set the default perl as the one in /usr/bin?

Or do I have to manually re-link it somehow?

---

### Post by amauk on 2010-08-15
> **Puzzled Guy said:**
> Just deleting /usr/local/bin/perl and /usr/local/lib/perl won't change the output of "which perl" back to /usr/bin/perl, or will it?Yes, it will

---

### Post by Puzzled Guy on 2010-08-19
I'll try it out. I'll back up the /usr/local/bin folder and then delete the original. If it works, I'll post the output of 'which perl'. If it doesn't, I'll can just restore the backup and then think of another aproach.

I can't do it now, no time. Tomorrow is Friday so I'll do it then. Until then, wait for another 24 hours.

---

### Post by Puzzled Guy on 2010-08-20
```
me@ubuntu-laptop:~$ which perl
/usr/bin/perl

```

Yes! Thanks! It worked. I never realized how simple the solution could be!

Thanks again.:KS

---

