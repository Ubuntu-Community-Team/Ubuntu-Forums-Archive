---
title: "upstart script"
date: 2012-05-30
forum: General Help
---

### Post by Homeservert on 2012-05-30
Hi,

I'm trying to use an upstart script for a program I want to run on start up and the program needs to respawn.

working on the script and trying to understand what to do, i've read several documents including the upstart cookbook .

But I can't get to work

I want to start /hs/bin/hs_main
the path for this program needs to have a path to its own directory: PATH="/hs/bin"

when I execute this command line in a terminal it works:
PATH=.:$PATH/hs/bin /hs/bin/hs_main

I have made the following script and places it into /etc/init

```
start on startup

script

PATH="/hs/bin"


exec su -c /hs/bin/hs_main
end script

```

this doesn't work

can anybody point me in a direction, upstart isn't really my cup of thea..

thanks.

---

### Post by Sivella on 2012-05-30
Hello,

The **exec** stanza is for a single-line command to run. I'm not sure it is correct to put it in the** script** part.

> start on startup
 
respawn

script[INDENT]       PATH="/hs/bin"
[/INDENT][INDENT]       /hs/bin/hs_main 
[/INDENT]end scriptcould be more "academic" ?

---

### Post by Homeservert on 2012-05-30
Hi Sivella

thanks for your reply. I've bin messing around with the script, but it seem that i am missing how it works.

it still doesn't work.

---

### Post by Sivella on 2012-05-31
I'm not an "expert" in Shell.

In Upstart the Script bloc is for **shell code** to be executed.

To my point of view, if your Upstart job doesn't work it is because the lines in the Script bloc don't comply with Shell syntax/rules.

Try in command line then put it in your Upstart job. Of course "sudo" or "su" are not needed because the Upstart job in running as Root.

Good luck.

---

