---
title: "How do I install Java?"
date: 2009-08-10
forum: General Help
---

### Post by lisabrown715 on 2009-08-10
When trying to download Java to my laptop it tells me-

 **To install the Linux (self-extracting) file**                                                                                                                   Follow these instructions:

[LIST=1]
[*]At the terminal: Type:
    **su**
[*]Enter the root password.
[*]Change to the directory in which you want to install. Type:
    **cd <directory path name>**
    For example, to install the software in the /usr/java/ directory, Type:
    **cd /usr/java/**
[/LIST]
When I type in the only password I've ever used it tells me 

Authentication Failure

I don't know what I am doing wrong.  I tried passwd username and it tells me to type in my old password and then new password and it tells me it is unchanged, so why doesn't it work as the root password?

---

### Post by snowpine on 2009-08-10
(edit) See michy99's post below for an even better way of installing Java...

Ubuntu is a little different than other Linux distros, and those instructions weren't written specifically for Ubuntu. Instead of 'su', try:

```
sudo -i
```

Then enter your regular user password when prompted and continue with the tutorial. (There is no root password in Ubuntu.)

---

### Post by michy99 on 2009-08-10
The easiest way to install java is through the repositories. Install the sun-java6-jre and sun-java6-plugin through Synaptic Package Manager or using apt-get in a terminal.

---

### Post by aysiu on 2009-08-10
To install Java, just paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install sun-java6-plugin
``` When prompted for a password, enter *your* password.

There is no root password in Ubuntu.

---

### Post by lisabrown715 on 2009-08-10
Thanks for the help!

---

