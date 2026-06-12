---
title: "ssh x11 forwarding error"
date: 2010-07-02
forum: General Help
---

### Post by roxely on 2010-07-02
Hello!!

Every time I try to run a program over X11 and SSH, I receive these messages:

root@d1sweb:/# gedit
X11 connection rejected because of wrong authentication.

(gedit:6069): Gtk-WARNING **: cannot open display: localhost:14.0
root@d1sweb:/# firefox
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
Error: cannot open display: localhost:14.0

What can I do to fix this problem?

Thank you!

---

### Post by nmaster on 2010-07-02
i'm assuming that you used "ssh -X".  maybe try "ssh -Y".

---

### Post by jennyrule on 2010-07-02
i have same problem too, please help.

---

### Post by nmaster on 2010-07-02
> **jennyrule said:**
> i have same problem too, please help.
so you get the same error with the -Y option?  maybe you should talk to the sys admin of the system.  there could be a lot of things going on.

---

### Post by roxely on 2010-07-02
> **neal.m.master said:**
> i'm assuming that you used "ssh -X".  maybe try "ssh -Y".


Yes, I am using ssh -X, but actually I tried with ssh -Y and I obtained the same error.


roxely@dpack02-laptop:~$ ssh -Y [email]roxely@system.edu[/email]
[email]roxely@system.edu[/email]'s password: 
Linux system 2.6.32-22-server #36-Ubuntu SMP Thu Jun 3 20:38:33 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)
Last login: Fri Jul  2 17:53:47 2010 from dpack02
/usr/bin/xauth:  timeout in locking authority file /home/roxely/.Xauthority
$ firefox
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
Error: cannot open display: localhost:10.0
$ 


thank you

---

### Post by nmaster on 2010-07-02
well, like i mentioned.  there could be a lot of causes.  i'd suggest starting with these potential fixes: [http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/](http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/)

just so you know, that link was the first link listed by google when i searched:"X11 connection rejected because of wrong authentication." if you already tried these, you should let people know so that we don't waste time.  if you haven't tried the link, then you should try consulting google before starting a thread.

---

### Post by roxely on 2010-07-02
> **neal.m.master said:**
> well, like i mentioned.  there could be a lot of causes.  i'd suggest starting with these potential fixes: [http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/](http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/)

just so you know, that link was the first link listed by google when i searched:"X11 connection rejected because of wrong authentication." if you already tried these, you should let people know so that we don't waste time.  if you haven't tried the link, then you should try consulting google before starting a thread.

Neal.m.master:

If I post in this forum my problem is because I really need help. I am a beginner with Ubuntu.I tried all the solutions I found on google and none worked. So that's why I came to this forum.

Sorry If I made waste your time,

thank you! :)

---

### Post by bodhi.zazen on 2010-07-02
> **roxely said:**
> Neal.m.master:

If I post in this forum my problem is because I really need help. I am a beginner with Ubuntu.I tried all the solutions I found on google and none worked. So that's why I came to this forum.

Sorry If I made waste your time,

thank you! :)

Is it working now ?

---

### Post by nmaster on 2010-07-02
> **roxely said:**
> Neal.m.master:

If I post in this forum my problem is because I really need help. I am a beginner with Ubuntu.I tried all the solutions I found on google and none worked. So that's why I came to this forum.

Sorry If I made waste your time,

thank you! :)

i didn't mean to sound like a jerk.  you're not wasting my time.  sometimes people get a little bit flustered and immediately ask for help. sorry!

... and does the "thank you!" mean that it works now? what fixed it?

---

### Post by roxely on 2010-07-06
> **neal.m.master said:**
> i didn't mean to sound like a jerk.  you're not wasting my time.  sometimes people get a little bit flustered and immediately ask for help. sorry!

... and does the "thank you!" mean that it works now? what fixed it?


Ok, Don't worry Neal! Guys "Thank you!" it was just a thanks for your responses, but lamentably my problem continues. I am asking for help because I am a beginner computer engineering and now I am working in a summer internship project and this error that I don't know how to fix is making me delay.

So I have tried all of these commands:

1- Set forwardX11=yes

2- setenv DISPLAY host_name:0.0

3- DISPLAY = host_name:0.0;export DISPLAY

4-  rm.Xauthority
    touch.Xauthority
    chmod 600.xauthority

5- ls -l ~/.xauthority
    sudo chown roxely.xauthoriy
    ls -l .xauthority
    chmod 755 .xauthority

I think I have tried a lot of solutions but none worked to me. Do you guys have any idea?

---

### Post by bodhi.zazen on 2010-07-06
You should not need to do any of that to forward X applications.

You connect via ssh

```
ssh -X user@server
```

This gives you a command line interface.

You then start an application from the command line:

```
xeyes
```

You do not need to set the display or mess with xauthority.

---

### Post by roxely on 2010-07-06
> **bodhi.zazen said:**
> You should not need to do any of that to forward X applications.

You connect via ssh

```
ssh -X user@server
```This gives you a command line interface.

You then start an application from the command line:

```
xeyes
```You do not need to set the display or mess with xauthority.


Bodhi.zazen,
I did it and I received this:

Last login: Tue Jul  6 19:03:02 2010 from dpack03-laptop
Could not chdir to home directory /home/roxely: Not a directory
/usr/bin/xauth:  error in locking authority file /home/roxely/.Xauthority
$ xeyes
X11 connection rejected because of wrong authentication.
Error: Can't open display: localhost:10.0
$

---

### Post by bodhi.zazen on 2010-07-06
See if any of this helps you :

[http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/](http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/)

---

### Post by roxely on 2010-07-07
> **bodhi.zazen said:**
> See if any of this helps you :

[http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/](http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/)



Bodhi.zazen, I tried these commands but the error appear again. I think the problem is due to the missing .Xauthority file in my home directory, look: 

root@d1sweb:/# find / -name '.Xauthority'
/home/Paul/.Xauthority
/home/Maria/.Xauthority

when I type:   find / -name '.Xauthority', the file .Xauthority is located in the home directory of my partners and I do not have the .Xauthority file. Do you think also that this missing file is causing the error? Really I do not know I am just assuming.

---

### Post by bodhi.zazen on 2010-07-07
Well, in your previous post you indicated you removed .Xauthority

See this thread to create a new one (although it should be automatic):

[http://ubuntuforums.org/showthread.php?t=1386329](http://ubuntuforums.org/showthread.php?t=1386329)

---

### Post by roxely on 2010-07-08
> **bodhi.zazen said:**
> Well, in your previous post you indicated you removed .Xauthority

See this thread to create a new one (although it should be automatic):

[http://ubuntuforums.org/showthread.php?t=1386329](http://ubuntuforums.org/showthread.php?t=1386329)



Thank you bodhi.zazen! I have created a new .Xauthority file and now is working.

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)
Last login: Wed Jul  7 16:01:06 2010 from dpack03-laptop
/usr/bin/xauth:  creating new authority file /home/roxely/.Xauthority
$ firefox
$ nautilus


Thank you!!!  :D

---

### Post by bodhi.zazen on 2010-07-08
> **roxely said:**
> Thank you bodhi.zazen! I have created a new .Xauthority file and now is working.

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)
Last login: Wed Jul  7 16:01:06 2010 from dpack03-laptop
/usr/bin/xauth:  creating new authority file /home/roxely/.Xauthority
$ firefox
$ nautilus


Thank you!!!  :D

You are welcome. Firefox is tricky , you should probably tunnel your traffic over ssh rather then forward firefox.

[Proxy Firefox through a SSH tunnel "how to" @ Calomel.org - Open Source Research and Reference]("https://calomel.org/firefox_ssh_proxy.html") 

If you forward firefox, it runs locally, unless you give the --no-remote option.

```
firefox --no-remote &
```

You may also want to look at using screen and/or nohup.

---

### Post by gr0ck on 2013-04-02
> **roxely said:**
> Hello!!

Every time I try to run a program over X11 and SSH, I receive these messages:

root@d1sweb:/# gedit
X11 connection rejected because of wrong authentication.

(gedit:6069): Gtk-WARNING **: cannot open display: localhost:14.0
root@d1sweb:/# firefox
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
Error: cannot open display: localhost:14.0

What can I do to fix this problem?

Thank you!

whenever I get there error its caused by the account I'm trying to access using keys. 

check on the server in the account you are trying to access for files located in ~/.ssh
files are:[INDENT]id_dsa
id_dsa.pub
[/INDENT]

copy those files to the client system .ssh directory by using sftp user@host
on client do the following[INDENT]cd .ssh
sftp user@host
get id_dsa
get id_dsa.pub
bye
[/INDENT]

now ssh -Xl user [host or ip]
you will be prompted to supply your key passphrase

as long as you are logged in to your current session on the client and your keys are unlocked you will be able to access any ssh server with the current setup without supply key passphrase again. 


Let me know if that fixed it.

---

### Post by cariboo on 2013-04-02
@gr0ck , thanks for providing the op with an answer, but he hasn't been back to the forum since he created this thread in 2010. Thread closed.

---

