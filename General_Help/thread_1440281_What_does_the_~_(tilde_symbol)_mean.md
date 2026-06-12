---
title: "What does the ~ (tilde symbol) mean?"
date: 2010-03-27
forum: General Help
---

### Post by leesiulung on 2010-03-27
I'm absolute beginner to Linux for the most part. What does the tilde mean in this situation?

```
mkdir ~/.somedir
```I know the / means root directory and the dot means from here. Does the tilde mean hidden?

---

### Post by Redundant Username on 2010-03-27
It means the home directory of the logged on user.

---

### Post by nothingspecial on 2010-03-27
It means your home directory
```

/home/username/.somedirectory
~/.somedirectory
```

Are the same thing

---

### Post by leesiulung on 2010-03-27
Thanks guys! 

Can you confirm this:

"I know the / means root directory and the dot means from here. Does the tilde mean hidden?"

---

### Post by nothingspecial on 2010-03-27
In your case the dot means hidden directory
```

./somedir
/.somedir
```

Are different

---

### Post by Ayuthia on 2010-03-27
Actually / is the topmost directory.  There is the possibility that /root can be the root directory.

. is the current directory and .. is the directory above it.

~ is the same as $HOME which is /home/username.

---

### Post by Vaphell on 2010-03-27
and ~username is an equivalent of /home/username that works also for users other than the current one

~ sometimes means 'hidden', for example gedit creates backup files with ~ at the end, but when ~ is at the beginning it definitely means home dir.

---

### Post by leesiulung on 2010-03-27
Dang! Could they make it consistent?

> **nothingspecial said:**
> In your case the dot means hidden directory
```

./somedir
/.somedir
```Are different

So the latter means hidden directory, what does the former mean in your example?

> **Vaphell said:**
> and ~username is an equivalent of /home/username that works also for users other than the current one

~ sometimes means 'hidden', for example gedit creates backup files with ~ at the end, but when ~ is at the beginning it definitely means home dir.

Is this inconsistency something I should just learn to accept as that is the way Linux is or is this just an anomaly?

Either way, I really like the community so far though.

---

### Post by nothingspecial on 2010-03-27
> **leesiulung said:**
> Dang! Could they make it consistent?



So the latter means hidden directory, what does the former mean in your example?



Is this inconsistency something I should just learn to accept as that is the way Linux is or is this just an anomaly?

Either way, I really like the community so far though.

The second example means dir_you_are_in/somedir

It`s not really an inconsistency because it is different, once you get used to it, the 2 don`t look similar at all.

---

### Post by sisco311 on 2010-03-27
> **leesiulung said:**
> 
So the latter means hidden directory, what does the former mean in your example?


. is a (hard) link to the current working directory and .. is a link to the parent directory. So ./dirname means that dirname is in the current working directory. *ls .* means list the crrent working directory. 

> **leesiulung said:**
> 
Is this inconsistency something I should just learn to accept as that is the way Linux is or is this just an anomaly?


Most editors use a ~ to denote backup files.

---

### Post by rahilm on 2010-03-27
```
./somedir
/.somedir
```isn't inconsistent. lets say thet you have a file named 'ls' that you want to execute. Now, typing "ls" won't help, since it is a system command. It will certainly display the list of files. To overcome this, and to make more options available, you can use the first line.... "." signifies the current directory. It tells the shell to look for the file in the current directory rather that in bin folders.


"/." is a hidden file.

---

### Post by leesiulung on 2010-03-27
Thank you, it makes much more sense now.

I'll mark this as solved as soon as I can figure out how....

---

### Post by sisco311 on 2010-03-27
Go to Thread tools -> Mark my thread as solved, for more details see the (red) link in my signature...

---

