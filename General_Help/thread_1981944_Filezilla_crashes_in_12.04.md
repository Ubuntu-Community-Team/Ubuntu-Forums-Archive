---
title: "Filezilla crashes in 12.04"
date: 2012-05-17
forum: General Help
---

### Post by doriad on 2012-05-17
I just upgraded to 12.04. Now when I run 'filezilla', the program loads fine. However, when I try to connect to one of my sites, it crashes and dumps the following error:

doriad@david-lab:~/temp$ filezilla 
The program 'filezilla' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 36989 error_code 3 request_code 152 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---------------
I did what the error said (run with --sync) but it crashes at exactly the same time.

Any ideas how to fix this?

Thanks,

David

---

### Post by doriad on 2012-05-24
According to the filezilla guys, it seems to be broken?

[http://forum.filezilla-project.org/viewtopic.php?f=2&t=24882&p=95859#p95859](http://forum.filezilla-project.org/viewtopic.php?f=2&t=24882&p=95859#p95859)

Is there any reason it is not removed from the software sources?

---

### Post by steve7777777 on 2012-05-24
You would think Filezilla would fix it -- fast!

---

### Post by jerome schatten on 2012-05-24
It appears to be a Ubuntu rather than a Filezilla problem, so it doesn't look like the FZ crew are going to fix it. It will be interesting to see how this plays out.
Best,
jerome

---

### Post by bulletxt on 2012-05-27
This is just crazy. I use Filezilla everyday, and now I upgraded to the so called "stable" Ubuntu and now it just crashes!!!

Let's see if Canonical is serious about such an important and well-known-used software.

---

