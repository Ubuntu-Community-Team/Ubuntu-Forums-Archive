---
title: "PATH problems"
date: 2010-01-29
forum: General Help
---

### Post by Dfr0st on 2010-01-29
I'm trying to run a script in /usr/lib/gmt/bin/ but I always get the respsonse "command not found".
If I type echo $PATH I get 

"dan-desktop:/etc> echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/dan:/usr/lib/gmt:/usr/lib/gmt/bin:/home/dan/Documents:"

Any ideas how to get this into my PATH file?
I am using tcsh in case that makes a difference.
Thanks,
Dan

---

### Post by sandkernel on 2010-01-29
I see this in your Path variable:
/usr/lib/gmt/bin

It should find the script. Is it executable?

---

### Post by cjhabs on 2010-01-29
Try:
cd /usr/lib/gmt/bin
./progname
where progname is the prgram you wish to execute.
I have seen this where you are running a script and the script calls another program that doesn't exist.
Your path looks ok.

---

### Post by doas777 on 2010-01-29
I usually put scripts in sbin, but shoudl work either way

---

### Post by Dfr0st on 2010-01-29
I can run the script if I type "usr/lib/bin/gmt/scriptname" or "cd usr/lib/bin/gmt; ./scriptname"
This isn't calling the path though is it if I'm giving it the full directory?
Dan

---

### Post by doas777 on 2010-01-29
> **Dfr0st said:**
> I can run the script if I type "usr/lib/bin/gmt/scriptname" or "cd usr/lib/bin/gmt; ./scriptname"
This isn't calling the path though is it if I'm giving it the full directory?
Dan

no it isn't. the request is just testing the script itself. 

who owns your script, and what are it's permissions?

---

### Post by Dfr0st on 2010-01-29
The permissions are set as executable for all. It's a collection of downloadable scripts called GMT.
Also I can never run anything in "gv" unless I give it the full directory.

---

### Post by cjhabs on 2010-01-29
cd to your home directory and do:
which scriptname

if it finds it then it is something that the script is calling that is the issue.
if doesn't find it, then it is a $path issue

---

### Post by raktarok on 2010-01-29
By any chance, are you using sudo before the script? sudo resets the PATH by default,and maybe that's why it is showing command not found.

---

### Post by doas777 on 2010-01-29
you have a bang line, right?

---

