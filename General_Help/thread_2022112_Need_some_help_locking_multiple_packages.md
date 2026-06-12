---
title: "Need some help locking multiple packages"
date: 2012-07-10
forum: General Help
---

### Post by kansasnoob on 2012-07-10
First of all to understand why I'm doing this look here:

[http://ubuntuforums.org/showthread.php?t=2004848](http://ubuntuforums.org/showthread.php?t=2004848)

And here:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

So I'm working on a script to revert abiword to stable and I think I'm really, really close:

```
sudo apt-get purge abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview libabiword-2.9 libgdome2-0 libgdome2-cpp-smart0c2a libgsf-1-114 libgsf-1-common libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libots0 libtidy-0.99-0 libwv-1.2-4 link-grammar-dictionaries-en ttf-lyx

sudo sed -i s'/precise/oneiric/g' /etc/apt/sources.list

sudo apt-get update

sudo apt-get install abiword

sudo sed -i s'/oneiric/precise/g' /etc/apt/sources.list

sudo apt-get update

sudo apt-get -f install
```

**[COLOR="Red"]BTW I'm only testing so I hope no one just jumps on that![/COLOR]**

Now I need to lock the following packages:

> abiword-common libgdome2-0 libgdome2-cpp-smart0c2a libgsf-1-114 libgsf-1-common libjpeg62 libloudmouth1-0 libots0 ttf-lyx

I know I could do them one at a time with:

> echo <packagename> hold | sudo dpkg --set-selections

And I could certainly add each package to the script separately but I feel that I'm overlooking something in the man pages. I do that sometimes because I'm old and I have a feeble mind :(

But I know the forums are the place to ask any question when you're stumped :)

Is there a way to lock all of those packages in one command :confused:

BTW I'm tired so my previous attempts may have just been due to a typo :oops:

Here's what I get when I try multiple packages:

```
lance@lance-desktop:~$ echo abiword-common libgdome2-0 libgdome2-cpp-smart0c2a libgsf-1-114 libgsf-1-common libjpeg62 libloudmouth1-0 libots0 ttf-lyx hold | sudo dpkg --set-selections 
[sudo] password for lance: 
dpkg: error: unexpected data after package and selection at line 1
lance@lance-desktop:~$ 

```

Thanks in advance.

---

### Post by Vaphell on 2012-07-10
i couldn't make it to work either
**edit:** i managed to do that but it's not too convenient in your case - it works only if <package> hold are on separate lines. It works that way because **--get-selections** spits data in this format
```
 echo $'aaa hold\nbbb hold' | sudo dpkg --set-selections
```

i guess you will have to use a for loop

```
for p in abiword-common libgdome2-0 libgdome2-cpp-smart0c2a libgsf-1-114 libgsf-1-common libjpeg62 libloudmouth1-0 libots0 ttf-lyx; do echo $p hold | sudo dpkg --set-selections; done
```

---

### Post by kansasnoob on 2012-07-10
> **Vaphell said:**
> i couldn't make it to work either
**edit:** i managed to do that but it's not too convenient in your case - it works only if <package> hold are on separate lines. It works that way because **--get-selections** spits data in this format
```
 echo $'aaa hold\nbbb hold' | sudo dpkg --set-selections
```

i guess you will have to use a for loop

```
for p in abiword-common libgdome2-0 libgdome2-cpp-smart0c2a libgsf-1-114 libgsf-1-common libjpeg62 libloudmouth1-0 libots0 ttf-lyx; do echo $p hold | sudo dpkg --set-selections; done
```

I'd never even heard of a "for loop" before :redface:

I'm mentally wiped out ATM but I'll give this a test drive soon.

Many, many thanks.

---

### Post by Vaphell on 2012-07-10
> I'd never even heard of a "for loop" before 

i'll pretend i didn't see that ;-)

---

### Post by kansasnoob on 2012-07-10
> **Vaphell said:**
> i'll pretend i didn't see that ;-)

Sadly I was being honest :D

That did the trick though, although I didn't have the package list quite complete, but I figured that out.

Many, many thanks. I'll have to do some more man reading now :)

---

