---
title: "Bash: Executing in Tabs"
date: 2009-09-02
forum: General Help
---

### Post by umeboshi80 on 2009-09-02
Hi

I have been trying to find info on how to write a shell script which opens multiple tabs each in which an executable will be run. By now, I have something which looks like: 

#!/bin/bash 

gnome-terminal --tab exec ./executable1 variables_executable1 \  
--tab exec ./executable2 variables_executable2

But this seems not to work. Also, the shell file is in a different directory as the executable (I tried to include --working-directory=... but it did not make a difference).

Thanks for any comments.

---

### Post by Johnny B on 2009-09-02
theres some bug reports on this.
> the issue where "gnome-terminal --tab" doesn't work is apparently a long-standing known bug, and it doesn't look like the developers upstream want it fixed. The response, basically, was that the feature is there in case you want to open a new window with more than one tab. It is not intended to open a new tab in an existing window (even though the "--help" docs say so).

[https://answers.launchpad.net/ubuntu/+question/32515]("https://answers.launchpad.net/ubuntu/+question/32515")

> gnome-terminal --tab-with-profile=Default --tab-with-profile=Foo

gives you a window with two tabs with profiles Default and Foo.


---

