---
title: "wget download of multple files"
date: 2012-04-11
forum: General Help
---

### Post by Methodize on 2012-04-11
I'm using wget to download a bunch of pics off a website directory with more directories inside. i also used -nd so the end result is a bunch of files with .1,.2,.3 extensions after the .jpg extention. 

It does this i suppose because i used the "-A jpg" option and it recognized the .1,.2,.3, as unaccepted file types therefore deleting them right before finishing the task.

I found a work around but that required me to do this to the accepted list option: '-A jpg,1,2,3,4,5...'

i was hoping there was some other type of workaround because this becomes quite a task if you have upwards of 50 duplicate file names.

thanks, mike

---

### Post by Dngrsone on 2012-04-11
Why not use a for/next loop?

---

### Post by Methodize on 2012-04-11
Please excuse my noobishness. i am learning shell commands as i go. i've tried googling the 'for/next/ loop' to find a way to implement this in my current situation but i haven't had any breakthroughs. would anybody mind enlightening me on this subject?

---

### Post by Dngrsone on 2012-04-11
Write a bash script, use the for command.

[bash for loop examples](http://www.cyberciti.biz/faq/bash-for-loop/)

---

