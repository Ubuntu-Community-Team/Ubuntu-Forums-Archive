---
title: "key is not available : NO_PUBKEY"
date: 2012-02-24
forum: General Help
---

### Post by YesGood on 2012-02-24
Hi

I have this error message
w GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couln't be verified because the public key is not available: NO_PUBKEY 29B940FC4EA8CBF6.

Then I run that
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4EA8CBF6
and the result is

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 4EA8CBF6
gpg: requesting key 4EA8CBF6 from hkp server keyserver.ubuntu.com
gpg: key 4EA8CBF6: "Launchpad PPA for Ubuntu FAI Developers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Why the result is unchanged?

---

### Post by matt_symes on 2012-02-24
Hi

It looks like you already may have the key in the keyring ?

What's the output of

```
sudo apt-key list | grep -A2 4EA8CBF6
``` 

Kind regards

---

### Post by YesGood on 2012-02-24
Thanks for reply

I run  
apt-key list | grep -A2 4EA8CBF6 

and the result is
pub   1024R/4EA8CBF6 2009-01-18
uid                  Launchpad PPA for Ubuntu FAI Developers

But I have the same error of  NO_PUBKEY 24B940FC4EA8CBF6

Why?

---

### Post by matt_symes on 2012-02-24
Hi

Maybe it's the wrong key. I have just managed to add that repository to my sources and it imported the key correctly.

Let's try to do it again for your PC. Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/fai-ppa-*
```

That will delete the repository reference.

then type

```
sudo apt-get update
```

Now let's re-add the repository.

```
sudo apt-add-repository ppa:fai/ppa
```

Hit enter when requested to import the key.

Then type

```
sudo apt-get update
```

What version of Ubuntu are you using ?

```
cat /etc/lsb-release
```

Kind regards

---

### Post by YesGood on 2012-02-24
Hi, thanks

I work with Ubuntu server 10.04 Lucid.

When I run the first command line
sudo rm /etc/apt/sources.list.d/fai-ppa-*

the result is
rm: cannot remove `/etc/apt/sources.list.d/fai-ppa-*': No such file or directory

And then with the
root@ubuntu:~# sudo apt-get-add-repository ppa:fai/ppa
sudo: apt-get-add-repository: command not found

Help me, what's wrong?

---

### Post by oldos2er on 2012-02-24
If you're root, you don't need 'sudo'. The correct command is **apt-add-repository ppa:fai/ppa** as matt_symes said.

---

### Post by matt_symes on 2012-02-24
Hi

> the result is
rm: cannot remove `/etc/apt/sources.list.d/fai-ppa-*': No such file or directory

This is interesting ! How did you add the repository ?

Is it in your sources.list file ?

```
grep -i "fai-ppa" /etc/apt/sources.list
```

Does that return anything ?

I think you may have had a problem adding the repository.

Kind regards

---

### Post by YesGood on 2012-02-24
Thanks, for yours helps

With this command  grep -i "fai-ppa" /etc/apt/sources.list  don't return anything.

in my /etc/apt/sources.list I add this line  for FAI

deb [http://ppa.launchpad.net/fai/ubuntu](http://ppa.launchpad.net/fai/ubuntu) lucid main

What's my error?

---

### Post by matt_symes on 2012-02-24
Hi

> **YesGood said:**
> Thanks, for yours helps

With this command  grep -i "fai-ppa" /etc/apt/sources.list  don't return anything.

in my /etc/apt/sources.list I add this line  for FAI

deb [http://ppa.launchpad.net/fai/ubuntu](http://ppa.launchpad.net/fai/ubuntu) lucid main

What's my error?

Remove that line from your sources.list files and follow the steps both Ann and I have suggested in posts #4 and #5.

Kind regards

---

### Post by YesGood on 2012-02-24
Hi

I erase the line of FAI in /etc/apt/sources.list with # begin of line.
 
Then I run apt-get update

Then that's the result
root@ubuntu:~#apt-add-repository ppa:fai/ppa 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 9129F9C36B552AE35EDE6F3E29B940FC4EA8CBF6
gpg: requesting key 4EA8CBF6 from hkp server keyserver.ubuntu.com
gpg: key 4EA8CBF6: "Launchpad PPA for Ubuntu FAI Developers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Apparently don't changed, because I have the same error

I run 
 apt-key list | grep -A2 4EA8CBF6

and I have the same result
pub   1024R/4EA8CBF6 2009-01-18
uid                  Launchpad PPA for Ubuntu FAI Developer

Help me. How can i follow?  
Thanks.

---

### Post by matt_symes on 2012-02-24
Hi

What version of Ubuntu are you using ? Post the output of this command.

```
cat /etc/lsb-release
```

I'm not quite sure what is happening on your system as i can install it correctly. 

Take a look at this. This is how i installed the ppa.

At the start ...

* The key is not imported. 
* The ppa is not installed. 
* There is no reference in sources.list.

```
matthew@matthew-Aspire-7540:~$ sudo apt-key list | grep -A2 4EA8CBF6
matthew@matthew-Aspire-7540:~$ grep fai /etc/apt/sources.list
matthew@matthew-Aspire-7540:~$ ls /etc/apt/sources.list.d/*fai*
ls: cannot access /etc/apt/sources.list.d/*fai*: No such file or directory
matthew@matthew-Aspire-7540:~$
```

I add the repository and it imports the key.

```
matthew@matthew-Aspire-7540:~$ sudo apt-add-repository ppa:fai/ppa
You are about to add the following PPA to your system:
 This ppa contains updated fai packages for earlier versions of ubuntu.

To use this PPA, add the following lines to your /etc/apt/sources.list and /etc/fai/apt/sources.list on the fai server
as described below in section 'Adding this PPA to your system'.

 More info: https://launchpad.net/~fai/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.EneaiToPoe --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 9129F9C36B552AE35EDE6F3E29B940FC4EA8CBF6
gpg: requesting key 4EA8CBF6 from hkp server keyserver.ubuntu.com
gpg: key 4EA8CBF6: public key "Launchpad PPA for Ubuntu FAI Developers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
matthew@matthew-Aspire-7540:~$ 
```

Proof the key is imported.

```
matthew@matthew-Aspire-7540:~/$ sudo apt-key list | grep -A2 4EA8CBF6
pub   1024R/4EA8CBF6 2009-01-18
uid                  Launchpad PPA for Ubuntu FAI Developers

matthew@matthew-Aspire-7540:~$ 
```

Proof the ppa has been added.

```
matthew@matthew-Aspire-7540:~$ ls /etc/apt/sources.list.d/*fai*
/etc/apt/sources.list.d/fai-ppa-oneiric.list
matthew@matthew-Aspire-7540:~$
``` 

I then update.

```
matthew@matthew-Aspire-7540:~$ sudo apt-get update
<snip>
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en          
Fetched 22.7 MB in 1min 17s (293 kB/s)
matthew@matthew-Aspire-7540:~$
```

There is no reference to a missing public key.

Did you add the ppa like this ?

Kind regards

---

### Post by YesGood on 2012-02-24
Hi 

thanks you matt_symes.

I decided to make all in the other new virtual machine, with your suggestions.

And so, the error disappeared.

---

