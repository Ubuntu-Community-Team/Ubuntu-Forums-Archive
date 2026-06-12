---
title: "Bash scripting problem ps: not found"
date: 2010-05-07
forum: General Help
---

### Post by johnnypeck on 2010-05-07
Ubuntu Server 9.10 fully updated.

I'm relatively new to shell scripting and am writing a script to start up and shutdown the tracd server which runs behind Nginx.  I can start it up just fine and have written a few scripts working with fast-cgi and nginx but for some reason, when tracd starts and I store the pid with the start-stop-daemon the pid that is stored does not match the one the process runs as.

Because of this I created a simple command to grok the pid with ps and the following runs just fine at the command line:

$ ps axo pid,comm | grep tracd | grep -v grep | awk '{print $1}'

But when I try to assign the return value to a variable in the stop part of my script I get:

ps: not found
grep: not found
grep: not found

In my shell script the relevant section follows:

stop)
  echo -n "Stopping Trac: "
  trac=`ps axo pid,comm | grep tracd | grep -v grep | awk '{print $1}'`
  ## kill $trac
  echo -n $trac
  ;;

I've also tried:
  trac=$(ps axo pid,comm | grep tracd | grep -v grep | awk '{print $1}')

I have no idea what's going on with this.  Any help would be greatly appreciated.

Thanks!

Johnny

---

### Post by jobix on 2010-05-07
It is a bit strange that it can't find "ps" and "grep" both of which are pretty basic commands. You can try specifying the full path, e.g., /bin/ps, etc.

Also, the "pidof" command does what you are doing but it's much cleaner.

> pidof tracd

would be all you need.

---

### Post by Portmanteaufu on 2010-05-07
There's an outside chance that since this is one of your first scripts, you're following a tutorial online that told you to use

```
#!/bin/sh
```

as your first line. In many systems this will work because '/bin/sh' is a soft-link to '/bin/bash'. However, in Ubuntu '/bin/sh' points to '/bin/**d**ash', which is similar to but not the same as bash.

If that's your problem, just change the first line to 
```
#!/bin/bash
```
and you should be set. If that's not the trouble, could you post a bit more of your code? I'm not sure what 'stop)' is part of. (Also, when you post code, if you put it in CODE /CODE tags (Using square brackets []) it will preserve the spacing and put it in a fancy box!)

---

### Post by johnnypeck on 2010-05-07
Thanks for the prompt replies!  Very grateful.

As it turns out, I had to specify the full paths to ps and grep as suggested by jobix.  I also found this strange.  

Re: Portmanteaufu - Thanks for the pointers.  I have been using 

```
#!/bin/bash
```

So my final call to find the pid of tracd is:

```

...
trac=`/bin/ps axo pid,comm | /bin/grep tracd | /bin/grep -v grep | awk '{print $1}'`
kill $trac
...

```

```

pidof tracd

```

would have been nice but unfortunately, for some reason the process is no longer recognized as being tracd.  I have to use

```

pidof python

```

which is rather annoying.  I have no idea why tracd (the trac server daemon) changes it's process to python.  Any thoughts regarding that funky bit would be well received.

Well, thanks for all the help!

---

### Post by Portmanteaufu on 2010-05-07
Another item that might simplify your script is a program in the repositories called "killall". It allows you to pass it a program name instead of having to track down the PID of what you'd like to kill.

e.g.```
killall tracd
```

---

### Post by johnnypeck on 2010-05-07
This is interesting.

```

pidof tracd

```

cannot find the process id, which is now somehow only recognized as python, but with your suggestion:

```

killall tracd

```

it works like a charm!  At least from the command line.  I'll try it in the script and see how it goes.  Is killall common on Ubuntu?  I mean, this script will only be used on a few of my own servers but can I get a little feisty and start using this in scripts I may distribute?

---

### Post by johnnypeck on 2010-05-07
Portmanteaufu,

Thank you for the note about killall.

Using killall in the stop() function replaced:

```

...
trac=`/bin/ps axo pid,comm | /bin/grep tracd | /bin/grep -v grep | awk '{print $1}'`
kill $trac
...

```

with 

```

...
killall tracd
...

```

So much shorter! Thanks for the pointer.

---

### Post by Portmanteaufu on 2010-05-07
> **johnnypeck said:**
> 
Is killall common on Ubuntu?  I mean, this script will only be used on a few of my own servers but can I get a little feisty and start using this in scripts I may distribute?

I'd say killall is pretty common, yup! Did you have to install it on Ubuntu or was it already there? Some distributions include it by default and others don't -- I can't remember which camp Ubuntu falls into.

If you *did* have to install it, though, that would be a good excuse to learn how to make a .deb package! Then you could distribute your scripts to people and their computers would install killall on their behalf during the un-bundling process. :D

---

### Post by johnnypeck on 2010-05-07
Okay, a few more thoughts on the situation.

Regarding not being able to find ps or grep:

I was placing the following at the top of my script:

```

...
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/usr/sbin:/usr/bin
...

```

which, when amended with /bin such as

```

...
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/usr/sbin:/usr/bin:/bin
...

```

fixes the issue of not being able to find the various programs.  I have not tried it without setting the PATH variable.

Second, I can use start-stop-daemon with the --name option to stop tracd as well such as the following:

```

...
start-stop-daemon --stop --quiet --name tracd
...

```

and that works as well!

---

### Post by johnnypeck on 2010-05-07
> If you *did* have to install it, though, that would be a good  excuse to learn how to make a .deb package! Then you could distribute  your scripts to people and their computers would install killall on  their behalf during the un-bundling process. :grin:

I have already been building .deb packages for my PHP and Nginx distributions for some time.  I have a few servers and I enjoy being able to manage my packages via dpkg and aptitude rather than having to do it on each machine separately.

---

### Post by Portmanteaufu on 2010-05-07
It's odd that your own $PATH isn't being carried into the script. Would you mind posting how you run the program? Also, could you look at your
```
~/.bashrc
```
file and let me know if you see
```
export PATH
```
anywhere? That line is what tells the shell to pass your environment on to child processes.

---

### Post by Portmanteaufu on 2010-05-07
> **johnnypeck said:**
> I have already been building .deb packages for my PHP and Nginx distributions for some time.  I have a few servers and I enjoy being able to manage my packages via dpkg and aptitude rather than having to do it on each machine separately.

Brilliant! Sadly, I have but a single Linux box to keep running, so I miss out on the joys of writing my own .debs. ;)

---

### Post by ck_linux on 2010-05-07
ps is found in /bin
I think you deleted your path ??

Check with:
echo $PATH   (command case sensitive)

the reply should be: 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

if NOT then add /bin to the path

---

### Post by johnnypeck on 2010-05-07
Ah!!  So I was placing a PATH variable at the top of my script and so it was over-writing the PATH that is automatically brought in to the script!

I comment it out and everything works without the full paths which is wonderful.


> Brilliant! Sadly, I have but a single Linux box to keep running, so I  miss out on the joys of writing my own .debs. :wink:Oh but it's so much fun!  Grab xen and build some IP fail-over setups to play with and you'll have good reason to build .deb's again!

Quick question: How do you grab a quote from a post without copy/paste/wrap in quote? Thanks!
-- nevermind: I just saw the 'quote' button. doh!

---

### Post by jobix on 2010-05-08
Usually when you want to add paths to the PATH variable, this is the way:

> export PATH=$PATH:/bin:/usr/bin:


In this example, I'm adding /bin and /usr/bin to my already existing PATH.

---

