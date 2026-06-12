---
title: "Terminal Shorthand"
date: 2009-12-02
forum: General Help
---

### Post by prem1er on 2009-12-02
I'm not exactly sure what you call it. I would like to take a command like 

```
ssh -p xxx user@hostname.com
```

and save it in script somewhere so no matter what directory I am in I can just do something like

```
sshlogin
```

and it will run the command in the saved file.

---

### Post by ManiacDan on 2009-12-02
```
[you@yours]# echo "ssh -p xxx user@hostname.com" > sshlogin
[you@yours]# chmod 744 sshlogin
[you@yours]# ./sshlogin
Magic!
```-Dan

---

### Post by Matt__ on 2009-12-02
try bashing this
```
alias [alias name]='[command]'
```
remove brackets :)
if it works ok it will be for that session only and you will need to edit your .bashrc or .bash_aliases to make it stick.

---

### Post by ManiacDan on 2009-12-02
Matt's answer is more correct, as it will allow you to do that from anywhere.  My answer creates a script file that holds that command for you, so you'll always have to execute it as if it were a program, starting from the proper directory.

-Dan

---

### Post by raktarok on 2009-12-02
Or you can add the script to one of the folders seen in the output of echo $PATH. 
Go with aliasing though, if you are using one line commands like that.

---

### Post by prem1er on 2009-12-02
Thank you both. Got it working.

---

### Post by prem1er on 2009-12-02
I thought I had this working, but it is not. I added this line to the file I created called bash_aliases. I added this line

```
#ssh to bubbles
alias login-bubbles=`ssh -p xxx user@hostname.com`
```

Wen I exited the terminal and restarted, it was immediately trying to login via ssh to the server without even using the alias. What am I doing wrong?

---

### Post by raktarok on 2009-12-02
The line should be like this, I think:
```
alias login-bubbles="ssh -p xxx user@hostname.com"
```
The use of **`** executes the command enclosed when the file bash_aliases is read. And you don't want that!

---

