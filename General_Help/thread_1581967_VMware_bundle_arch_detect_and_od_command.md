---
title: "VMware bundle arch detect and od command"
date: 2010-09-25
forum: General Help
---

### Post by ericsonp on 2010-09-25
This is a two for one thread.

I'm trying to install VMware Player using their "bundle" file, which is really just a shell script.

The problem is that this script attempts to detect the system architecture using the 'od' command which on 64-bit Ubuntu 10.04 behaves rather oddly.

The od command should behave like a hex editor and output a file as hex or octal, instead is outputs:

    Sat Oct  9 18:22:23 EDT 2010

Of course the bundle file can't detect the arch and fails.

Question 1
How do I fix the bundle so that it will install?


Question 2
Why is od outputting a date instead of the content of a file in hex/octal?

Cheers,

Paul

---

### Post by ericsonp on 2010-09-25
So you can dork around with the script, but eventually it just fails.

You can modify get_arch() to return 2 (64 bit)

But the script makes such heavy use of the od command that there is no way to get the bundle to execute while it's currently outputting a date instead of heax/octal code.

Suppose I should go check if there is a bug report filed for od.

---

### Post by dcstar on 2010-09-26
[LIST=1]
[*]VM issues belong in the Virtualization forum
[*]Use the package and instructions VMware provide
[/LIST]

---

### Post by gmargo on 2010-09-26
> **ericsonp said:**
> 
Why is od outputting a date instead of the content of a file in hex/octal?

Probably you've overwritten your **od** command or you've copied the **date** command to another file named **od**.  I can't speak for 64-bit Lucid but I can say that in 64-bit Maverick beta, **od** is definitely what it's supposed to be.  See which **od** command you're finding, and see if it's a copy of **date** (here's what I get on Maverick beta):
```

$ ls -l $(which date od)
-rwxr-xr-x 1 root root 59992 Jun 11 00:24 /bin/date
-rwxr-xr-x 1 root root 59920 Jun 11 00:24 /usr/bin/od

```

---

