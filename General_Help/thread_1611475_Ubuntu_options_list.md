---
title: "Ubuntu options list?"
date: 2010-11-01
forum: General Help
---

### Post by SimpleMan49004 on 2010-11-01
I am new to Ubuntu and I have a lot to learn. I have searched these forums and the net and for the life of me I cannot find a list of of all the options (ie. -a -b -c)

I also have some interest in knowing what certain symbols do such as {} \  ; 

If anybody can help this newbie out, I would greatly appreciate it.

---

### Post by Boondoklife on 2010-11-01
That would be because each command has different switches and the meanings can vary. You need to know the commands to know what the switches are. I suggest you start with `man`.

Google a bash tutorial and it will tell you what those mean.

---

### Post by SimpleMan49004 on 2010-11-01
Thanks for the quick response. 

I tried searching man, but I dont know the full name of the commands. Thats the tricky part. For example, I have no idea what the name is for -f, or even if there is an -f. To search man don't I need to at least know the command name? 
I just want these lists for reference so I know what Im looking at. 

Someone wanted me to type in a command in my terminal: 
find /home/(my username) -name "*.o" -exec rm {} \;

Before I do this, I need to know what all this means and why they want me to type this in. What does it do? I understand some of it, but those characters are throwing me for a loop as well as -name

-n= numeric uid gid     -a= list all files   -m= format  -e= encrypt files    ???????

---

### Post by Boondoklife on 2010-11-01
the command you have there will delete all your files matching *.o so do us all a favor and dont run it.

---

### Post by uRock on 2010-11-01
If you are wanting to learn the command line and want to be able to mess things up, then you may want to install ubuntu in a virtual machine to test commends before running them on the actual system.

To learn the options of a command you can open a terminal and type **man** then **make** to get a listing of all of the options for the **make** command. The **man** command tells bash that you want the manual for the following command.

```
man make
```

I also recommend finding some literature on the UNIX/Linux command line.

---

### Post by SimpleMan49004 on 2010-11-01
Ahh, thanks for the heads up. I have Ubuntu on my external drive. I have books galore on Ubuntu, but most of them just talk about navagating through Ubuntu, no actual meaningful information for Terminal. Im actually pretty comfortable with it, but I still have lots to learn. Ive been playing with it for a couple months now. 


The only way to really learn is to play with it, right? I did find a decent link for some of what I was looking for:

[http://www.oreillynet.com/linux/cmd/cmd.csp?path=l/ls](http://www.oreillynet.com/linux/cmd/cmd.csp?path=l/ls)

Its the best information I have found so far on this topic. Still looking for what all the symbols mean. Im the type of person who likes to know the meaning of everything before I even get into it, so that way when I am ready to step up from the mundane user I will be well prepared. Reading on how to write shell scripts wont help much as I have no idea what half of the commands mean. 

If you have any links to push at me, please feel free.

---

### Post by tredegar on 2010-11-02
If you are not even sure which command to use (let alone the options) then the command you need is **apropos**
Try **apropos file**
It'll give you a (long) list of commands relevant to files, and (briefly) what they do.

You can use **man** to find out more about each command:


Here's a simple script that will reformat the output of **man *commandname*** to a PDF file which is easier to read:
[http://www.linuxquestions.org/questions/linux-general-1/how-to-make-shell-script-wait-for-key-press-to-proceed-687491/#post3360877](http://www.linuxquestions.org/questions/linux-general-1/how-to-make-shell-script-wait-for-key-press-to-proceed-687491/#post3360877)

Here's a good guide to bash:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

Have fun.

---

