---
title: "View Script Output Using SSH?"
date: 2010-12-13
forum: General Help
---

### Post by csharpplus on 2010-12-13
I have a python script, called **test.py**, that does the following:

  > 
while (1):
    ....print "hello world"
(this script simply prints 'hello world' continuously).
    
Now, I am using two machines (machine A and machine B). Same user is used for both machines. I would like to do the following:
  (1)   **[working with machine A]**   run **test.py** *programatically* on machine A {  meaning, a local python script will be running **test.py** using say os.system(....)  }        ( at this point, the script **test.py** is printing "hello world" to the screen of machine A )
  (2)   **[working with machine B]**   I now want to log in into machine A using ssh and 'view' the output of the script that we ran in (1)

  How do I achieve this?  I know how to write the script that will be running and starting **test.py** on machine A. I also know how to ssh from machine B to machine A.

  What I don't know is:
  (*)    What command should I use in (1) in order to run the python  script so that its output can be easily viewed while logging from a  different machine (machine B) to machine A?
  (*)    Following the ssh from machine B to machine A, how do I 'navigate' to the screen that shows the output of **test.py**?

---

### Post by papibe on 2010-12-21
You can accomplish what you want using the program screen. The simplest case is when both users are the same (the one ssh-ing and the local user wanting to "see" the content).

The remote user can connect to machine A normally, then run screen, and finally the python script.
First:
```
$ ssh machineA
user@machineA.local's password:
$ screen
<there's info here, press enter until you get a prompt>
$ TEST_AREA/justprint.py
```
also, you can call screen with the script at the same time:
```
$ ssh machineA
user@machineA.local's password:
$ screen TEST_AREA/justprint.py
```
and finally, the shorter way would be passing screen on the ssh command:

```
$ ssh machineA 'screen TEST_AREA/justprint.py'
user@machineA.local's password:

```
In any case, you have created a virtual terminal that can be attach/detach/share in many ways. screen is a VERY interesting and powerful command, so I advice you to read more about it (start with 'man screen', then google 'screen tutorial').

Now, the user in the local session can see what's going on on the virtual terminal also by running screen:
```
$ screen -x
```
Note that you not only will see what's going on, but you'll be there. For example, if you press control-C you'll stop the script. To get out (detach) from the screen press C-a d (control a, and then d)

I hope that helps.

OBS: it is possible to make this work for two different users. In that case you'll need to configure more stuff (it rise a security concern though). Let me know if you need help with that.

---

