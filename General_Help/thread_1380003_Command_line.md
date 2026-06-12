---
title: "Command line"
date: 2010-01-13
forum: General Help
---

### Post by Monolith1200 on 2010-01-13
can anyone point me a good direction to learn command line in linux? a good long list of commands as well as tutorials would be appreciated. Google is my best friend buy i dont want to chase my tail. Im sure that a few of you on here know particularly good ways to learn, and id like to know. thanks much.



                  <H3artW0rm>

---

### Post by audiomick on 2010-01-13
Hi.
you could have a look here
[http://www.linux.org/](http://www.linux.org/)
at their course "linux 101"
There is a link on the page on the right hand side.
They start getting into the shell and commands in lesson 6

---

### Post by x33a on 2010-01-13
[http://linuxcommand.org/](http://linuxcommand.org/)

[http://tuxradar.com/content/master-linux-command-line](http://tuxradar.com/content/master-linux-command-line)

[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

also, whenever you get to know a new command, always refer to the man page for extra information.

---

### Post by SoftPops on 2010-01-13
I tend to use [http://ss64.com/bash/](http://ss64.com/bash/) to find commands. No tutorial but it does give a description of each command and the syntax. Also has links to other Linux references.
 
Another good list of commands can be found at [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/).

---

### Post by cong06 on 2010-01-13
Basically ever singe application installed in linux is a command. For a COMPLETE list, just open up a terminal and press "tab" twice. Though that should be more than anyone would want to see.
Still the auto-complete feature can help you find some interesting tools.

But as x33a points out, when you find a command, such as "echo" or "wget"
type:
```

man wget

```
to learn more about how "wget" actually works.

---

### Post by Grenage on 2010-01-13
Run a distro in a VM so that you can 'fearlessly' hack away; then you can roll back the image when it all goes wrong (assuming you can't fix it).

---

### Post by John Bean on 2010-01-13
If you want a manageable summary list of all the commands available on your installation use "apropos" to generate the list and view the result in "less":```
apropos * | less
```
PS: "less" is a replacement for "more" that is generally more friendly, allowing you to use cursor keys to navigate. As always, "man less" and "man apropos" will give you the full story on these two commands, and don't forget "man man" to find out the capabilities of "man" itself.

---

