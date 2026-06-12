---
title: "Admin password gone"
date: 2011-10-26
forum: General Help
---

### Post by hartviglarsen on 2011-10-26
Hello people,

I'm new to Ubuntu.. I got it yesterday so I don't really know nothing about it.. yet ;)

Well, when I installed Ubuntu I chose a password for my account.. But I thought it was a waste of time to type everytime I had to log in, since I'm the only one using this laptop.. 

So I removed it..

But now I can't even install programs or do anything.. 

This is how my user settings look:

[IMG]http://designedbyhartvig.dk/login.png[/IMG]

By the way, "Lås op" means "Unlock" incase you didn't knew lol.

When i try to press it, i get this message:

[IMG]http://designedbyhartvig.dk/login2.png[/IMG]

What do i type??

I can't create a new password, install programs or anything..


Please help.
Thanks guys. :)

---

### Post by jnorthr on 2011-10-26
welcome aboard :KS

It may actually take less time to reinstall ubuntu than to fight problems. The system password is ever so necessary to do many things as it is the proof that you are the administrator and know what you are doing (or maybe not?) when it comes to playing with restricted components. 

You can start your research here: [http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/](http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/) to see where/how to change your system password again. It may require you to edit the /etc/passwd file using a text editor program like gedit. Do NOT use word or libreoffice, etc as these programs do funny things with text files and your system will not behave nicely if it cannot read this password file.

If your system is unstable or cannot be logged into, you may need to place a live CD back into your Cd drive and reboot your system from the live CD. Then you can at least use an edit tool to do the job.

---

### Post by papibe on 2011-10-26
Have try just pressing enter?

Also try to get a root prompt by doing:
```
sudo -i
```
It'll ask your password, try enter again. You'll know it's working if you see a # prompt.

Here's another idea. [This]("http://psychocats.net/ubuntu/fixsudo") is a tutorial for recovering from another problem (lock out of the admin group). But as soon as you get into the root prompt you can change your password by running:
```
passwd youruser
```
I hope these ideas help. Tell us how it goes.
Regards.

---

### Post by linuxuser12345 on 2011-10-26
In order to put in his codes from above, you must press "Ctrl Alt T" on your keyboard to open up a terminal, then enter the codes! :)

---

### Post by hartviglarsen on 2011-10-27
Hey guys,

Thanks for the answers.. I just reinstalled Ubuntu though.. That was waay easier :P

---

### Post by nothingspecial on 2011-10-27
Well it would have been easier and quicker to boot into recovery mode but as long as you got it working.......

---

