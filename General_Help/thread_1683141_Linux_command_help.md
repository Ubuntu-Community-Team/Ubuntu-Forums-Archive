---
title: "Linux command help"
date: 2011-02-07
forum: General Help
---

### Post by Menace97 on 2011-02-07
I would like to know how to logoff using terminal.
I'm pretty sure it's not logout cause i tried that even as root.

Another is how to change directory to make a directory for an example, i know it's something to do with cd but i dont get it. Can anyone tell me how to set the location to my desktop?

I know that mkdir makes the directory and rmdir deletes them.

Thanks, and yeah i've only been using linux for 3 days and i like the transparency you can add to the bars and themes you can use. Looks much better than my windows partition.

EDIT: Can linux like take shortcuts and assignthem manually like CTRL-U for ubuntu software centre?

---

### Post by slooksterpsv on 2011-02-07
> **Menace97 said:**
> I would like to know how to logoff using terminal.
I'm pretty sure it's not logout cause i tried that even as root.

Another is how to change directory to make a directory for an example, i know it's something to do with cd but i dont get it. Can anyone tell me how to set the location to my desktop?

I know that mkdir makes the directory and rmdir deletes them.

Thanks, and yeah i've only been using linux for 3 days and i like the transparency you can add to the bars and themes you can use. Looks much better than my windows partition.

Logoff the computer using Terminal? I don't know on that one exactly.

How to change Directories. Open up a Terminal:
You should see something like:
```

johndoe@johndoe-computer:~$ 

```
And type in the following:
```

ls

```
and press enter after.

It should give you something like:
```

Desktop
Documents
Downloads
Music
Pictures
Templates
Videos

```

Maybe more, let's say we wanted to go to the directory Desktop, we'd type in the following (and yes, case does matter)
```

cd Desktop

```

Now we should see:
```

johndoe@johndoe-computer:~/Desktop$
[code]

Let's make a directory on the Desktop called Examples:
[code]
mkdir Examples

```

If all went well, we can now cd into Examples:
```

cd Examples

johndoe@johndoe-computer:~/Desktop/Examples$

```

If when you open terminal you want the Desktop to be the directory you start in, type in the following:

```

pico ~/.bashrc

```

Type the following in at the very end (use the arrow keys to go up and down):
```

cd ~/Desktop

```

Now press ctrl+o then press enter, then ctrl+x, now open a new terminal. You'll start at ~/Desktop instead of ~

~ denotes /home/<your_username>

---

### Post by whatthefunk on 2011-02-07
Do you want to logout or shutdown?

Shutdown:
```
sudo shutdown -h now
```

To change directory:
```
cd nameofdirectory/
```

To see available directories and files:
```
ls
```

To see all directories, even those starting with a . :
```
ls -a
```

To make a directory:
```
mkdir nameofdirectory/
```

Heres a command list:
[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)

And heres a decent tutorial about the command line:
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by Menace97 on 2011-02-07
Thanks, this really helped.

---

### Post by Menace97 on 2011-02-07
and i want to logout and switch user.

---

### Post by mörgæs on 2011-02-07
The links in my signature give a good introduction to general Linux/Ubuntu usage, also navigating in the directories.

I am not on a Linux machine right now so I can not give an exact answer to the log-off question. Have you tried 'exit'?

---

### Post by stoneage on 2011-02-07
```
gnome-session-save --logout
```


[http://askubuntu.com/questions/15795/how-can-you-log-out-via-the-terminal](http://askubuntu.com/questions/15795/how-can-you-log-out-via-the-terminal)

---

### Post by Menace97 on 2011-02-08
thanks stoneage, who thought the command for logout was so long, on some websites it only says logout.
Exit just closes Terminal. (use it all the time) :)
Halt turns off computer. (My fav without timer)

---

