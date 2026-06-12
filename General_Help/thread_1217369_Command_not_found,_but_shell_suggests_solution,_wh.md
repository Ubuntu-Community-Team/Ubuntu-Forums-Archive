---
title: "Command not found, but shell suggests solution, why don't help further?"
date: 2009-07-19
forum: General Help
---

### Post by UranUtan on 2009-07-19
Hi,

I ran the command wipe and got the following response from the shell
> The program 'wipe' is currently not installed.  You can install it by typing:
sudo apt-get install wipe
bash: wipe: command not found

I guess that the shell has been customized to supply this kind of hint for a certain number of programs which are considered not essential. If so could it go a little further by proposing, "Do you want to run sudo apt-get install XXX" (Y/n)"?

I don't mind typing the sudo cmd actually. But I am puzzled by the implementation. Is it because it is for security reason or is it a temporary solution?

---

### Post by unutbu on 2009-07-19
I like your idea. You might want to suggest it on brainstorm:
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

The behavior you are talking about is controlled by the command-not-found package,
and in particular, /usr/share/pyshared/CommandNotFound/CommandNotFound.py

You can effect the change yourself by editing CommandNotFound.py:

Change
[PHP]
            elif self.user_can_sudo:
                print >>sys.stderr, _("You can install it by typing:")
                print >>sys.stderr, "sudo apt-get install %s" %  packages[0][0][/PHP]

to
[PHP]
            elif self.user_can_sudo:
                print >>sys.stderr, _("You can install it by typing:")
                print >>sys.stderr, "sudo apt-get install %s" %  packages[0][0]
                print 'Install it for you now? ([Y]/n) ',
                resp=raw_input().upper()
                if resp.startswith('Y') or resp=='':
                    os.system("sudo apt-get install %s" %  packages[0][0])
[/PHP]
This is what it looks like:

```
% wipe
The program 'wipe' is currently not installed.  You can install it by typing:
sudo apt-get install wipe
Install it for you now? ([Y]/n)  
[sudo] password for user: 
...
Processing triggers for man-db ...
Setting up wipe (0.21-5) ...
```

Unfortunately, after wipe is installed, bash still reports
```

bash: wipe: command not found
```
But if you run the command again, wipe will be there.

Below I've attached the modified CommandNotFound.py.

---

### Post by UranUtan on 2009-07-25
Thank you very much for your time to provide such an expert answer and with a solution! I am now happy to understand the underlying mechanism. 

Will try your solution and I hope your idea will be adopted somewhere upstream. Also thanks for suggesting [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) that I discover today. 

Idea submitted to Ubuntu Brainstorm, with your solution as suggestion:
[http://brainstorm.ubuntu.com/idea/20790/](http://brainstorm.ubuntu.com/idea/20790/)

---

### Post by castrojo on 2009-07-26
Please file a bug here: [https://bugs.edge.launchpad.net/ubuntu/+source/command-not-found](https://bugs.edge.launchpad.net/ubuntu/+source/command-not-found)

and attach the patch so it doesn't get lost somewhere, thanks!

---

