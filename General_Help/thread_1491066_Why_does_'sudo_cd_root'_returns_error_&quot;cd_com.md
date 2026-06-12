---
title: "Why does 'sudo cd /root' returns error: &quot;cd commad not found&quot;?"
date: 2010-05-23
forum: General Help
---

### Post by abcuser on 2010-05-23
I use Ubuntu 10.04. With sudo command I can execute root users commands.
But why the following command:
```
sudo cd /root
```
returns error: "sudo: cd: command not found"?

---

### Post by lisati on 2010-05-23
You shouldn't need "sudo" to run "cd". Try the command again without "sudo".

---

### Post by gmargo on 2010-05-23
> **abcuser said:**
> returns error: "sudo: cd: command not found"?

"cd" is a shell built-in command, so it cannot be the sudo target.

You can get around this with something like (right from the sudo man page):
```

sudo sh -c "cd /home ; du -s * | sort -rn > USAGE"

```

---

### Post by cbecker78 on 2010-05-23
no need for anything fancy really, you just need admin priveledges/prompt to change to /root.  I won't go into the warnings much, but make sure you know what you are doing if you want to fool with anything in root.  You can kill your system.  for the sake of this, I'll assume you just want to look around...

the way to go is the following:
```
sudo -i
cd /root
```the first command gives you a superuser prompt at "/" (i.e., the true root) the second does what you want and changes to the /root directory.

Be cautious.  Someone will probably chime in soon and tell you not to do it.  don't forget to type "exit" to return to your normal user prompt when you are done looking around.

Edit: oh, and you'll need to use ```
 ls -a 
``` to actually see the hidden files there...

---

### Post by abcuser on 2010-05-24
> **lisati said:**
> You shouldn't need "sudo" to run "cd". Try the command again without "sudo".
I don't agree with you. If I execute cd /root I get error of not having enough permissions, which is quite logical. If executing command "ls -l /" I get:
drwx------ root root /root
To make it possible that ordinary (non-root) user to access /root directory, directory should have execute permissions for others, that is what x means on directory, so it should be:
drwx-----x root root /root


> **cbecker78 said:**
> the way to go is the following:
```
sudo -i
cd /root
```
Thanks for this info, but I was not asking how to do this, but why I can't do it my was "sudo cd /root". Just trying to understand why something can't be done using sudo command.

> **gmargo said:**
> "cd" is a shell built-in command, so it cannot be the sudo target.

You can get around this with something like (right from the sudo man page):
```

sudo sh -c "cd /home ; du -s * | sort -rn > USAGE"

```
OK, this makes sense of output error: "sudo: cd: command not found", so cd is shell-build in command and not actually a program that sudo is searching to execute.

I tried to use:
sudo sh -c "cd /root; ls -l" > /home/myuserid/output.txt
But I am still getting permissions denied error.

---

### Post by philinux on 2010-05-24
The only thing in /root is it's Desktop folder.

---

### Post by jamesisin on 2010-05-24
My user account can cd into /root and there run ls -a without any elevation.  (And there is definitely more in there than a Desktop folder.)

---

### Post by philinux on 2010-05-24
I'm running a clean instal lucid.

---

### Post by mc4man on 2010-05-24
/root is the root 'HOME' (~#), everything but Desktop is hidden
(don't see much good going into it..

---

### Post by jamesisin on 2010-05-24
Interesting.  They must have changed things between 8.10 and 9.10 because my 8.10 machine behaves as per above, but my 9.10 and 10.04 machine don't allow my user account access to /root.  (The 9.10 and 10.04 machines don't have a /root/Desktop but there are several other items in /root.)

---

