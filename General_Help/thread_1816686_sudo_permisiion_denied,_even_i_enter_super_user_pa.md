---
title: "sudo permisiion denied, even i enter super user password"
date: 2011-08-02
forum: General Help
---

### Post by kotin76 on 2011-08-02
HI All,

I am new for ubuntu.

i trying to create file in /usr/local from below command

"sudo df | grep /dev > dev_string.txt"

First it asked for sudo password. I enterd sudo password. 

but I was not able to create the file dev_string.txt .

Next time onwards it not asking sudo password also.

Please see the below execution flow

##################################################
/usr/local/$ sudo df | grep /dev > dev_string.txt
bash: dev_string.txt: Permission denied
[sudo] password for vatf: 
/usr/local/$ ls | grep dev_
/usr/local/$ sudo df | grep /dev > dev_string.txt
bash: dev_string.txt: Permission denied
/usr/local/$ sudo df | grep /dev > dev_string.txt
bash: dev_string.txt: Permission denied
/usr/local/$ 
#####################################################

Regards
Kotin

---

### Post by sisco311 on 2011-08-02
Hi and welcome to the forums!

Please check out: [uhelp]community/RootSudo#Downsides of using sudo[/uhelp]

You can use tee to write the file as root:
```
df | grep /dev | sudo tee dev_string
```
or run the whole command as root in a sub-shell:
```
sudo bash -c "df | grep /dev > /usr/local/dev_string"
```

---

### Post by Wim Sturkenboom on 2011-08-02
sudo remembers your password for a while; that's fully normal

Alternative to *sisco311*'s solution is to write the result to your home directory and next use *_sudo mv_*

Or obtain permanent root privileges for a session using *_sudo su -_* (note the dash at the end)

---

### Post by dcstar on 2011-08-03
> **kotin76 said:**
> HI All,

I am new for ubuntu.

i trying to create file in /usr/local from below command

"sudo df | grep /dev > dev_string.txt"
.........

Make life easier for yourself - don't create files in System Folders, put it in something you have permissions to write in.

---

### Post by kotin76 on 2011-08-03
HI all,

I got solution now. Tx for your replys.

Regards
Kotin

---

### Post by Wim Sturkenboom on 2011-08-03
Please mark your thread as solved using the thread tools just above the first post.

Although it would be nice to know how it was solved (as future reference to others who have the same problem).

---

### Post by CatKiller on 2011-08-03
> **Wim Sturkenboom said:**
> 
Or obtain permanent root privileges for a session using *_sudo su -_* (note the dash at the end)

sudo -i 

would be a better choice.

---

### Post by Wim Sturkenboom on 2011-08-03
> **CatKiller said:**
> sudo -i 

would be a better choice.

I started a thread so one can explain to me why that would be the case.
[http://ubuntuforums.org/showthread.php?t=1817402](http://ubuntuforums.org/showthread.php?t=1817402)

---

### Post by CatKiller on 2011-08-03
I was going by the RootSudo Ubuntu Wiki page, which refers to [this post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4"). What does the - do?

---

### Post by Wim Sturkenboom on 2011-08-03
I've seen that post. It leaves out the option su with the dash.

From *man su* ;)
> 
The optional argument - may be used to provide an environment similar to what the user would expect had the user logged in directly.


---

### Post by gordintoronto on 2011-08-03
> **kotin76 said:**
> 
"sudo df | grep /dev > dev_string.txt"



Sudo was on the wrong command. The correction is:

df | sudo grep /dev > dev_string.txt

but, as noted, the proper solution is to CD to Documents before entering the command.

---

### Post by CatKiller on 2011-08-03
> **Wim Sturkenboom said:**
> I've seen that post. It leaves out the option su with the dash.

From *man su* ;)

Ah, OK, so they're pretty much identical then. Not been at a computer, otherwise I'd have read the man page myself.

---

