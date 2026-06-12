---
title: "GLIBCXX_3.4.11 not found, add-apt-repository not working"
date: 2012-08-13
forum: General Help
---

### Post by 1stuffy1 on 2012-08-13
Im trying to run a server (the latest release of the arma2-server) on my 8.04 Ubuntu server .  If I try to run it the following error comes up: 

```
./server: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./server)
./server: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by ./server)
```however, I've read a post somewhere that you can fix that with the following command: 

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test 
sudo apt-get update
 sudo apt-get install gcc-4.7
```But I cant get the command "add-apt-repository" to work. I know that I need "python-software-properties", but I already got these and the command is still not working. I've run out of ideas and all the searches I did never brought up a good result. So I hope someone is these forums is able to help me.

---

### Post by cortman on 2012-08-13
> **1stuffy1 said:**
> on my 8.04 Ubuntu server

Likely this is the problem- it's a rather outdated version- no security updates and likely no packages for it in newer PPA's.
You may want to upgrade to 12.04.

---

### Post by 1stuffy1 on 2012-08-13
Thanks for the reply!

Update you say. I'm renting the server from a hosting company. Should I execute the update myself, or contact my hoster to do it? Also, how do I perform an upgrade? Do I have to reinstall everything afterwards or will my files/configurations be kept?

---

### Post by cortman on 2012-08-13
I should clarify- 8.04 server LTS is still supported till April of 2013- the desktop support reached EOL last year.
What is the output of the add-apt-repository command?

---

### Post by 1stuffy1 on 2012-08-13
add-apt-repository gives me:

```
bash: add-apt-repository: command not found
```

---

### Post by cortman on 2012-08-13
> **1stuffy1 said:**
> add-apt-repository gives me:

```
bash: add-apt-repository: command not found
```

What's the output of

```
sudo apt-get install python-software-properties
```

? (I know you said it's installed already; I'd just like to check). You can reinstall it with

```
sudo apt-get install python-software-properties --reinstall
```

---

### Post by 1stuffy1 on 2012-08-13
Yeah, I already installed it. But I'll post the output for you:

```
sudo apt-get install python-software-properties
Reading package lists... Done
Building dependency tree
Reading state information... Done
python-software-properties is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by cortman on 2012-08-13
> **1stuffy1 said:**
> Yeah, I already installed it. But I'll post the output for you:

```
sudo apt-get install python-software-properties
Reading package lists... Done
Building dependency tree
Reading state information... Done
python-software-properties is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

This may sound like a Windows fix, but have you logged out/back in since you installed python-software-properties, or rebooted? Believe it or not I've had problems similar to that with Linux myself.

---

### Post by 1stuffy1 on 2012-08-14
Rebooted it, but still isn't working. Also tried to reinstall it with the command you posted, but it just doesn't want to work.

---

### Post by cortman on 2012-08-14
You can see if all it needs is to be upgraded:

```
sudo apt-get upgrade
```

But beyond that I'm out of ideas- no idea why add-apt-repository isn't working...

---

### Post by 1stuffy1 on 2012-08-14
First off, thanks for your time and help.

I've got all recent upgrades, the command says there arent any more to download.
Maybe you or anybody else here knows a way to fix the GLIBCXX_3.4.11-problem on another way. If not, I'll do a complete reinstallment of my server with the lastest ubuntu-version.[]("http://ubuntuforums.org/showthread.php?t=2041693")

---

### Post by cortman on 2012-08-14
I'm sorry I couldn't help much more; but there are many, many people on this forum with way more knowledge on this than me; maybe one of them will give you the right advice.
The last thing I can think of is reinstalling glibc++, but otherwise you may be well off installing Ubuntu server 12.04.

---

### Post by crs0328 on 2012-08-16
My issue isn't with GLIBCXX_3.4.11, but I'm having the exact same problem with add-apt-repository. python-software-properties is already installed and nothing else is working. No idea why I can't get it to work...

---

### Post by 1stuffy1 on 2012-08-21
> **crs0328 said:**
> My issue isn't with GLIBCXX_3.4.11, but I'm having the exact same problem with add-apt-repository. python-software-properties is already installed and nothing else is working. No idea why I can't get it to work...

I'm on 10.04 now and add-apt-repository works just fine. What version are you on?

---

