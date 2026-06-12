---
title: "what does apt-get install -f exactly do?"
date: 2010-10-01
forum: General Help
---

### Post by davidvandoren on 2010-10-01
I know when something during install goes wrong, you'll see the message ```
apt-get install -f
```

In my first Ubuntu installation I executed this command and from there the system was getting more and more problems. 

On this current installation I had an update error as well but did not execute this command instead I ran ```
sudo apt-get update
```

then ```
sudo apt-get upgrade
```

got a lot of dependency error messages but no upgrade.

I then opened the update manager again and there where two packages which previously failed to install. 
I clicked install and everything went fine. 


So My question when should I run this command? and What does it exactly do?

---

### Post by QIII on 2010-10-01
From the man page:

```
**-f** **--fix-broken** Fix; attempt to correct a system with broken dependencies in  place. This option, when used with install/remove, can omit any packages  to permit APT to deduce a likely solution. Any Package that are specified must completely  correct the problem. The option is sometimes necessary when running APT  for the first time; APT itself does not allow broken package dependencies to exist on a  system. It is possible that a system's dependency structure can be so  corrupt as to require manual intervention (which usually means using ***dselect**(8)* or **dpkg --remove** to eliminate some of the offending packages). Use of this option together with **-m** may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.
```Many questions can be answered by 

```
man foo
```

In your case

```
man apt-get
```

But to be honest, unless you know what the instructions mean they can sometimes be hard to understand.  Those who maintain man pages sometimes pre-suppose that you will understand the answer because it is very obvious to them.  That's human nature.  But you can always ask for clarification here!

---

### Post by wojox on 2010-10-01
Open your terminal and

```
man apt-get
```

It's an option to --fix-broken.

---

