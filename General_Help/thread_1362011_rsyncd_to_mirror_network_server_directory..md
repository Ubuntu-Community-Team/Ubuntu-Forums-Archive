---
title: "rsyncd to mirror network server directory."
date: 2009-12-22
forum: General Help
---

### Post by junetwo on 2009-12-22
hey there.
so i have an idea, and that idea consists of the following:

step 1) buy a mac because i need it for design
step 2) install parallels with ubuntu 9.10
step 3) setup ub with apache2, php, extensions, etc
step 4) use it as a web server so i dont have to use osx to serve requests
step 5) use a program in osx to edit files
step 6) have an rsync daemon running on ub that mirrors the osx folder
step 7) ???
step 8) profit!

i'm stuck at step 6
i have my server up and running, configured, serving requests, yadda yadda, but i need to (for legacy purposes) edit any web files through an osx program. i want my ubuntu server to be running non stop, mirroring the folder on osx.

the reason i dont want to just mount ubuntu in osx and edit the files through the app, through ssh (eg. through macfuse?).

it's much slower (especially for searches through the app).

any thoughts or ideas or directions or links would be very much appreciated. i've been hacking on rsync for a bit but can't figure out how to do this.

thanks.

---

### Post by tad1073 on 2009-12-22
Not sure if this will help but it is worth a shot.

[http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

---

### Post by asmoore82 on 2009-12-22
steps 2 and 4 at the same time don't sound like a good idea to me.

---

### Post by StuartN on 2009-12-22
> **junetwo said:**
> step 4) use it as a web server so i dont have to use osx to serve requests

Out of curiosity, why do you not serve requests from apache2 installed in OS X? Seems like a lot of overhead for an application that runs natively anyway.

---

### Post by junetwo on 2009-12-22
@tad1073 will check it out.
@asmoore82 why not?
@StuartN consistency. my live server is a mirror image of my local, and it makes it easier. also, i'd much prefer working in a linux env for dev than osx, since installing extensions, modules etc. is a breeze. osx has a half-assed implementations of php imo.

any thoughts?

---

### Post by junetwo on 2009-12-22
@tad1073 no dice. i'm looking for more of a consistent mirroring effect. i was under the impression that i could setup rsync as a daemon that was constantly looking for changes to a certain directory (eg. the osx sites im working on).

not that i think about it, maybe that can't be done? i was hoping it could, but maybe i need to push the changes everytime?

---

### Post by junetwo on 2009-12-23
bump. (haha, find this on google, dunno how this is already on first page)

---

### Post by junetwo on 2009-12-27
bump.

---

