---
title: "running a root command whn system starts"
date: 2011-01-05
forum: General Help
---

### Post by mahmoodn on 2011-01-05
I want to run some commands with sudo when the system starts. I have created a file in /etc/init.d/myfile
```
#!/bin/bash
command1
command2
```
Normally, I have to use "sudo command1" and "sudo command2". I then run:
```
sudo update-rc.d -f /etc/init.d/myfile defaults
```
After restart, that file has not been executed. How can I fix that?

---

### Post by tredegar on 2011-01-05
> After restart, that file has not been executed. How can I fix that? 

You could put some error-reporting in your script, and redirect the stderr to ~/errors.log Then you could see what was going wrong.

But you are trying to do this the complicated way.

I like an uncomplicated life.

So I'd just put the **/full/path/to/each_command** in the file **/etc/rc.local** on the lines before the final **exit 0**

That file is executed by root, so you should not use **sudo**

---

### Post by mahmoodn on 2011-01-05
Really thanks for your help. I did that and it no works :)

---

### Post by seawolf167 on 2011-01-05
Make sure the script it executable, if it isn't already, otherwise see if this helps you out

[UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto")

---

### Post by mahmoodn on 2011-01-05
thanks it was useful

---

