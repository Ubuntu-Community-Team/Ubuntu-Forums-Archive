---
title: "HP Pavilion dv2000 shuts down or log out by itself on Ubuntu 9.10"
date: 2010-04-01
forum: General Help
---

### Post by pgonzamailcn on 2010-04-01
Hi all,

Thanks in advance for your time.

My computer, a four year old HP Pavilion dv2000 running with Ubuntu 9.10 since half a year ago, sometimes shut downs and sometimes gets me to a black screen where I can read in the first line: “Ubuntu 9.10 pablo-laptop tty1” and in the second line: “login pablo-laptop:”. In the second case, sometimes (only) it allows me to log in, taking me to the login screen that appears after switching on the[COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]computer[/SIZE][/FONT][/COLOR][COLOR=#000000]. [/COLOR]After logging in on that screen it initiates the computer but all the programs I had opened are closed and I have lost the information. This has been happening to me since long ago but never asked in forums. It is quite annoying and I would be happy to solve it.
[COLOR=#000000]
Do you think it ca be the [/COLOR][COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]CMOS[/SIZE][/FONT][/COLOR][COLOR=#000000] battery?

This other thing (check the link below) happened to me not long ago and some people suggested it could be the [/COLOR][COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]CMOS battery:[/SIZE][/FONT][/COLOR]
  
[http://www.linuxquestions.org/questions/linux-laptop-netbook-25/ubuntu-9-10-hp-pavillion-2000-seems-have-collopsed-792559/](http://www.linuxquestions.org/questions/linux-laptop-netbook-25/ubuntu-9-10-hp-pavillion-2000-seems-have-collopsed-792559/)
  

  I provide attached dmesg and /var/log/messages output. I do not understand very much the dmesg output (and actually I think it is quite long) but I think there is something strange happening at 276.528973. You can look in the attachment. I think it may be related with the low memory space in my disk. Now it is about 800MB. Actually when starting the laptop it always pop out a warning about the low memory space. Do you think the reason is the low memory and so when Vbox starts request more memory than available?


  Thanks for all.
  
Have a good day. All the best,

Pablo

---

### Post by kushal.kumaran on 2010-04-01
The messages look like it's going to suspend itself.  Is it possible the laptop ran out of battery?

---

### Post by pgonzamailcn on 2010-04-01
Hello kushal.kumaran,

No, that can not be. It happend even when the laptop plugged to the elcetricity.

Best,

Pablo

---

