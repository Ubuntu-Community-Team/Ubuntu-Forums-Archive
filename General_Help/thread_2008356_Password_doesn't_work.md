---
title: "Password doesn't work"
date: 2012-06-22
forum: General Help
---

### Post by ganondorf29 on 2012-06-22
So I restarted my Ubuntu 12.04 LTS desktop after installing some software and when I get to the login screen, I type my password and the screen goes black like its loading and then comes back to the login in screen. I thought I must have misspelled the password, but if I purposely misspell it, it tells me in red (invalid password, please try again) at the login screen.  

So I decided to reset it via this [link]("http://www.psychocats.net/ubuntu/resetpassword") and according to the root director I did reset it properly.

However, when I get back to the login screen and type in the newly reset password, I get the black, loading like screen and then it takes me back to the login screen.

Any suggestions?

---

### Post by blackflame2996 on 2012-06-22
OK, lets see if your password works.
type:
```
CTL+ALT+F1
```
This will drop to console mode. see if your login works here. if it does, then you will get a welcome message, and a $> prompt.

---

### Post by steeldriver on 2012-06-22
... as above, then do

```
ls -l ~/.*authority
```If either of them has become owned by root then remove them

```
sudo rm ~/.Xauthority
```Then go back to the X virtual terminal (usually Ctrl-Alt-F7) and try again.

---

### Post by ganondorf29 on 2012-06-22
> **blackflame2996 said:**
> 
```
CTL+ALT+F1
```


I did this, typed my username/password and got to the :~$ 

 However, when I did the next step of

> **steeldriver said:**
> ... as above, then do

```
ls -l ~/.*authority
```



I get the following:

Command 'ls' is available in '/bin/ls'

The command could not be located because '/bin' in not included in the PATH environment variable.

ls: command not found



After that it returns to the :~$ prompt

---

### Post by jarro221 on 2012-06-22
You can try a direct path

```
/bin/ls -l ~/.*authority
```

---

### Post by ganondorf29 on 2012-06-22
> **jarro221 said:**
> You can try a direct path

```
/bin/ls -l ~/.*authority
```

So using this I got the following:


-rw----- 1 username username 21550 June 20 12:49 /home/username/.ICEauthority


-rw----- 1 username username 0 June 22 16:20 /home/username/.Xauthority



Now going back to steeldriver's post, should I use the following code to remove the .Xauthority:

```

sudo rm ~/.Xauthority

```

---

### Post by steeldriver on 2012-06-22
no... it seems like that is not your problem - your .Xauthority / .ICEauthority ownership and permissions look fine to me

it looks like there are more serious issues - starting with why your VT shell doesn't have a correctly set $PATH variable

you could check ~/.xsession-errors and/or your greeter log to see if there are any clues there

---

### Post by ganondorf29 on 2012-06-22
So do you think that this could be something more serious? I'm asking because I am by no means a Linux/Ubuntu expert and I don't really know where to go from there.

---

### Post by steeldriver on 2012-06-22
well I am running 11.10 but I think the lightdm bits should be the same - what does

```
sudo tail /var/log/lightdm/x-0-greeter.log
```give? in particular look for lines about "Loading user" and "Authentication"

---

### Post by ganondorf29 on 2012-06-26
> **steeldriver said:**
> well I am running 11.10 but I think the lightdm bits should be the same - what does

```
sudo tail /var/log/lightdm/x-0-greeter.log
```give? in particular look for lines about "Loading user" and "Authentication"

After Crtl-Alt-F1 I wrote the above code. Got the following:


Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable. 
sudo: command not found

---

### Post by steeldriver on 2012-06-26
OK well like I mentioned before maybe the fact that your $PATH environment variable is not getting set is a clue we should not ignore - maybe your home dir or login shell or .bashrc got corrupted? or your filesystem is full? what do you get if you try any or all of these

```
df -h
echo $PATH
echo $SHELL
source ~/.bashrc
```

---

### Post by ganondorf29 on 2012-06-28
> **steeldriver said:**
> 
```
df -h
echo $PATH
echo $SHELL
source ~/.bashrc
```


When I type:

df -h

**output:** 

Command 'df' is available in '/bin/df'
The command could not be located because '/bin' is not included in the PATH environment variable. 
df: command not found




**Input**:

echo $PATH

**output:** 

/usr/local/packages


**Input**:

echo $SHELL

**output:** 

/bin/bash



**Input**:

source ~/.bashrc

**output:** 


Command 'lesspipe' is available in the following places
* /bin/lesspipe
* /usr/bin/lesspipe

The command could not be located because '/usr/bin:/bin' is not included in the PATH environment variable.
lesspipe: command not found


Command 'dircolors' available in '/usr/bin/dircolors'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
dircolors: command not found
 

Command 'uname' available in '/bin/uname'
The command could not be located because '/bin' is not included in the PATH environment variable.
uname: command not found
 

-bash: [: =: unary operator expected

 
Command 'sed' available in '/bin/sed'
The command could not be located because '/bin' is not included in the PATH environment variable.
sed: command not found


Command 'ls' available in '/bin/ls'
The command could not be located because '/bin' is not included in the PATH environment variable.
ls: command not found

---

