---
title: "installing image with dd"
date: 2009-10-04
forum: General Help
---

### Post by Adina on 2009-10-04
I have successfully installed both these images using the commands below, but I don't understand the difference between them. They both seem to accomplish the same thing. 

```
gunzip -c net45xx-xxx.img | dd of=/dev/sdc bs=16k
```


```
dd < ZeroShell-1.0.x-CompactFlash512.img > /dev/sdc
```


Is there any difference between the 2 commands? Is it just two ways of doing the same thing? Is one way better than the other?

---

### Post by falconindy on 2009-10-04
I believe redirecting the STDOUT of a program to the STDIN of another will actually create a temporary file in between, which would mean you're better off piping output.

Why not skip the piping and redirection all together?

```
dd if=ZeroShell-1.0.x-CompactFlash512.img of=/dev/sdc bs=16k
```
The above is functionally equivalent to your second example (aside from the additional specified block size).

---

### Post by fela on 2009-10-04
Limitless possibilities to accomplish the same goal.

You'll find it alot with Linux.

---

### Post by Adina on 2009-10-04
Thanks for your replies! I actually tried falconidys example first:

```
dd if=ZeroShell-1.0.x-CompactFlash512.img of=/dev/sdc bs=16k
```

but it seems to simply copy the image file to /dev/sdc and not "install" it.
I get the message "no bootable device". With the other commands the cf card boots up no problem. So does anyone know what the difference is?

---

### Post by falconindy on 2009-10-04
Wild -- not at all what I expected. dd's man page says:
```
       if=FILE
              read from FILE instead of stdin
```
Which, you'd think, would mean the same results. So something is strange in the way the data is being written when an input file is used.

Perhaps try doing the write without specifying a block size? I'm not convinced that will make a difference, though.

---

