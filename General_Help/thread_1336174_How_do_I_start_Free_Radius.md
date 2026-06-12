---
title: "How do I start Free Radius?"
date: 2009-11-24
forum: General Help
---

### Post by StarThorn1 on 2009-11-24
To start it I think I need to: login as root and type radiusd start

It does not give me an error. It doesn't really say anything after I type it in.

How do I tell if its running?

---

### Post by audiomick on 2009-11-24
In the menu
System > Administration 
there is a tool to look at the system resources. In German it is called "systemüberwachung"
One of the tabs in that shows you what is running and how much of the resources it is using. If the thing is running, it should show up there.

---

### Post by QLee on 2009-11-24
[QUOTE=StarThorn1]It does not give me an error. It doesn't really say anything after I type it in.

How do I tell if its running?[/QUOTE]

I mean you no disrepect but this is kind of a strange question from someone who has need of a radius server and is qualified to admin one.

May I ask what you are trying to accomplish? You might get better exposure to people who can help you if you post your queries in another sub forum where they are likely to see them. For example: Server Platforms or Networking.

---

### Post by StarThorn1 on 2009-11-24
This is for wireless authentication. I am sure I have my config files setup right in freeRadius but I am not familiar enough with linux to do much else.

---

### Post by 3rdalbum on 2009-11-24
```
ps aux | grep "radiusd"
```

If it's running, you should see two results: One is the actual radiusd process, and the other one is *grep "radiusd"*.

Quick explanation for you: "ps aux" gives you a list of all running processes, and *grep* allows you to search for strings. The *pipe* in the middle of the two commands will put the output from *ps aux* into the input of *grep*.

The "d" at the end of the program's name means that it's a daemon - it runs in the background. So it's normal that it will not print anything to your terminal.

Also, if the program is installed to a system-wide location, it probably sets itself up to start on boot. Try running the above command before starting the program to see if this is the case.

---

### Post by StarThorn1 on 2009-11-24
This is what came on the command prompt when I tried your command.


```



# ps aux | grep "radiusd"
root      4142  0.0  0.2   3232   736 pts/1    S+   06:43   0:00 grep radiusd

# radiusd start

# ps aux | grep "radiusd"
root      4158  0.0  0.2   3232   740 pts/1    S+   06:45   0:00 grep radiusd

# ps aux | grep "radiusd"
root      4167  0.0  0.2   3232   740 pts/1    S+   06:45   0:00 grep radiusd

# ps aux | grep "radiusd"
root      4169  0.0  0.2   3232   740 pts/1    S+   06:45   0:00 grep radiusd



```

Because it said grep radiusd it means its running right?

---

### Post by Darael on 2009-11-24
No.  It's picking up itself, you see.
And by the way, rather than logging in as root, it's advisable to log in as a normal user (in the sudoers group, the first account created always will be) and prefix the command with "sudo".  This means that you can disable the root password, which increases security.  Also, you may find that either "start radiusd" or "service radiusd start" (only one will have any effect, if either) works.

---

### Post by StarThorn1 on 2009-11-24
I tried service radiusd start and it told me to no such service radiusd

---

### Post by StarThorn1 on 2009-11-26
so what does this mean? Why wont it start?

---

### Post by blueridgedog on 2009-11-26
You are asking about a complex server process in a general help Ubuntu forum.  I doubt you will get the best reply here and suggest you use the free radius mailing list as outlined on their website.

Also, you should work to debug the process to produce more information.  Have you checked for errors in the various log files in play after attempting to start the service?  From my years of being a sysadmin, I have gotten the dance down pat whereby you attempt to run a program, "tail" the system or application log, adjust the config and try again....

---

### Post by pretendiamaterminal on 2009-12-31
Has anyone ever got freeradius to work on ubuntu?

---

