---
title: "No graphic interfce from SSH"
date: 2010-10-18
forum: General Help
---

### Post by runningpig001 on 2010-10-18
Hello, all

I am having an annoying problem with ubuntu 10.04.
with SSH, I get connected to a linux server. The command line works well.
But I can NOT get a graphic interface from it.
For example:

################################################## #############
me@power:~$ ssh -Y me@123.456.789.3
me@123.456.789.3's password:

[me@master]#gedit abc.f

(gedit:23385): Gtk-WARNING **: cannot open display:

[me@master]#matlab
Warning: Unable to open display '123.456.789.223:0.0'. You will not be able to display graphics on the screen.

< M A T L A B >
Copyright 1984-2007 The MathWorks, Inc.
Version 7.5.0.338 (R2007b)
August 9, 2007

Warning: Name is nonexistent or not a directory:
/usr/local/matlab/toolbox/readgrib.

To get started, type one of these: helpwin, helpdesk, or demo.
For product information, visit [www.mathworks.com](www.mathworks.com).

################################################## #####################
where 123.456.789.3 is the server's ip and 123.456.789.223 is my ip.

According to some ppl's suggestion, I have changed my ~/.ssh/config file to

############
GSSAPIAuthentication no
ForwardX11 yes
############

but it does not help.

The OS I am working with is ubuntu 10.04
the GNOME version is 2.30.2

So any suggestion please?
Thank you!


&#65339;SOLUTION&#65341;just comment one line in the .cshrc file in my home folder in the server
#setenv DISPLAY 123.456.789.223:0.0

it's said this line is not needed for linux system trying to connet to the server.

---

### Post by huotte on 2010-10-18
Hi,

Did you try running ssh with the -X option? This enables X11 forwarding in the client. It is not always enabled default.

Hope this helps.

<ED>

---

### Post by runningpig001 on 2010-10-18
> **huotte said:**
> Hi,

Did you try running ssh with the -X option? This enables X11 forwarding in the client. It is not always enabled default.

Hope this helps.

<ED>

Hi, huotte

I tried it too, it did work either...

thank u for you reply

---

### Post by standingfire on 2010-10-18
Check your ssh_config and sshd_config files.
If you are jumping across as root, that sometimes does not work so well either.
These files would be in /etc/ssh

---

### Post by runningpig001 on 2010-10-18
> **standingfire said:**
> Check your ssh_config and sshd_config files.
If you are jumping across as root, that sometimes does not work so well either.
These files would be in /etc/ssh

I tried that before, it did not work

but i have solved the problem  thank you all the same!

---

