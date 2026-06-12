---
title: "Trouble installing VMware Player"
date: 2006-03-13
forum: General Help
---

### Post by kaamos on 2006-03-13
When running vmware-install.pl
> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The kernel defined by this directory of header files does not have the same
address space size as your running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The kernel is 2.6.15 with the ck7 patch. And those are certainly this kernels headers since that source is where I just compiled the kernel from! :D

Whats the problem?

All ideas welcome. Thanks!

EDIT: For the next stumped up compiler: comment out these lines in vmware-config.pl
```


if ($header_page_offset =~ /[0-9a-fA-F]{8,}/) {
# We found a valid page offset
if (defined($gSystem{'page_offset'}) and
+not (lc($header_page_offset) eq lc($gSystem{'page_offset'}))) {
if ($source eq 'user') {
print wrap('The kernel defined by this directory of header files does '
. 'not have the same address space size as your running '
. 'kernel.' . "\n\n", 0);
}
return '';
}
} 
```
Problem solved.

---

