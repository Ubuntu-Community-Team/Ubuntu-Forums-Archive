---
title: "Unity Broken"
date: 2011-05-11
forum: General Help
---

### Post by nexoncore on 2011-05-11
I enabled the desktop cube using Compiz Manager and now unity wont work, I changes the settings back using the classic envoroment but it still work work. How can I fix is?

---

### Post by Hedgehog1 on 2011-05-11
Please do a **<ctrl> + <alt> + t** to get the terminal.

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

Logout and reboot...

***The Hedge***

:KS

---

### Post by matth1j on 2011-05-11
> **Hedgehog1 said:**
> 
```
unity --reset
```


Just tried that:

```
johnm@ubuntu:~$ unity --reset
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'

```
:?:

---

### Post by wildmanne39 on 2011-05-11
> **matth1j said:**
> Just tried that:

```
johnm@ubuntu:~$ unity --reset
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'

```
:?:

Hi, when you run that command you will get a lot of errors do not worry about them, but it takes a while to complete if that is all the out put you got it probably did not complete give it a few minutes before logging out and restarting.

---

### Post by matth1j on 2011-05-12
> **wildmanne39 said:**
> Hi, when you run that command you will get a lot of errors do not worry about them, but it takes a while to complete if that is all the out put you got it probably did not complete give it a few minutes before logging out and restarting.

Thanks, but it doesn't continue running - it just outputs the error message and stops:

```
johnm@ubuntu:~$ time unity --reset
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'

real	0m0.207s
user	0m0.040s
sys	0m0.112s
johnm@ubuntu:~$ 

```

---

### Post by wildmanne39 on 2011-05-12
> **matth1j said:**
> Thanks, but it doesn't continue running - it just outputs the error message and stops:

```
johnm@ubuntu:~$ time unity --reset
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'

real	0m0.207s
user	0m0.040s
sys	0m0.112s
johnm@ubuntu:~$ 

```

Hi, have you restarted the computer after you ran that command, it has worked for everyone else including me.:)

---

### Post by matth1j on 2011-05-12
> **wildmanne39 said:**
> Hi, have you restarted the computer after you ran that command, it has worked for everyone else including me.:)

Just tried it - no difference :(

I'm going to try another installation (in VMplayer), but not install the VMplayer tools in case they've got something to do with it.

---

### Post by garvinrick4 on 2011-05-12
> **matth1j said:**
> Just tried it - no difference :(

I'm going to try another installation (in VMplayer), but not install the VMplayer tools in case they've got something to do with it.
Compiz does not work to good at all in VMplayer use classic ubuntu. If you want to use Unity in 11.04 then make a partition install.

---

### Post by matth1j on 2011-05-12
> **garvinrick4 said:**
> Compiz does not work to good at all in VMplayer use classic ubuntu. If you want to use Unity in 11.04 then make a partition install.

:(

---

### Post by Allavona on 2011-05-12
Compiz and Unity = oil and water

---

### Post by matth1j on 2011-05-12
> **garvinrick4 said:**
> Compiz does not work to good at all in VMplayer use classic ubuntu. If you want to use Unity in 11.04 then make a partition install.

Hah - just installed another ubuntu under VMplayer and at the first login I get a warning message:

"It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment."

That rings a bell now... :oops:

---

### Post by wildmanne39 on 2011-05-12
> **matth1j said:**
> Hah - just installed another ubuntu under VMplayer and at the first login I get a warning message:

"It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment."

That rings a bell now... :oops:

Thats most likely because it is only reading what the vm has available to it if you did not install vm tools I would do it you should save your vm first just in case. Good luck

---

### Post by ucracker on 2011-10-16
Solved [here]("http://ubuntuforums.org/showthread.php?p=11351590").

---

