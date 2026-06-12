---
title: "floppy permission problem"
date: 2006-02-12
forum: General Help
---

### Post by jchristian on 2006-02-12
I've been using Ubuntu since Warty, just upgraded from Hoary to Breezy yesterday and love it!

But I've run into a very peculiar problem: I set up an account for my girlfriend this morning and it refuses to let her use the floppy drive. 

At first, the prompt was "you don't have permission, blah, blah" I checked permissions, and "ls -l /dev/fd0" showed permissions to be "brw-rw-rw", just like they're supposed to be...

So I added her to the floppy group, on the theory of "when in doubt, do _something_" Now the error prompt is " cannot process, (or initialize, or somesuch) pmount.

Now bear in mind that the floppy works perfectly fine from my account. 

Anybody got any ideas about what in the world is going on??

---

### Post by dcstar on 2006-02-13
[QUOTE=jchristian]
.......
So I added her to the floppy group, on the theory of "when in doubt, do _something_" Now the error prompt is " cannot process, (or initialize, or somesuch) pmount.

Now bear in mind that the floppy works perfectly fine from my account. 

Anybody got any ideas about what in the world is going on??[/QUOTE]

All pmount users need to be in the plugdev group.

---

### Post by jchristian on 2006-02-13
That seems to have done the trick! Thanks, Dave

---

### Post by dcstar on 2006-02-13
[QUOTE=jchristian]That seems to have done the trick! Thanks, Dave[/QUOTE]
No worries, it is just another little "gotcha" that is buried deep enough in the documentation to catch people out!       :(

---

