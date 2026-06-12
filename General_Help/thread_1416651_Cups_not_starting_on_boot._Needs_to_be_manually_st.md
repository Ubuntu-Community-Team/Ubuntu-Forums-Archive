---
title: "Cups not starting on boot. Needs to be manually started."
date: 2010-02-26
forum: General Help
---

### Post by eqqfooyoung on 2010-02-26
I am running Ubuntu 9.10, and every time the computer starts, cups does not appear to be running. I have to run the following from the command line:
```
sudo /etc/init.d/cups start
```
After cups is started, printing works fine. Does anyone know how I can get cups to start on it's own when the computer boots?

---

### Post by joeyknuccione on 2010-02-26
Go to:

System > Preferences > Main Menu

In that do:

Determine which subsection, and click on it

With subsection highligten, click "New Item" in the upper left

Give it a name, enter the command, and any comments.

Click "Close" and it should start the next time you boot.

---

### Post by eqqfooyoung on 2010-02-26
> **joeyknuccione said:**
> Go to:

System > Preferences > Main Menu

In that do:

Determine which subsection, and click on it

With subsection highligten, click "New Item" in the upper left

Give it a name, enter the command, and any comments.

Click "Close" and it should start the next time you boot.

joeyknuccione,

Thank you for the response, but I'm pretty sure that is just going to add a launcher to my main menu, right? I would prefer if cups would just start up on it's own without me having to go into my menu.

If it is any help, cups use to start on it's own when the computer booted up. I'm not sure exactly when it stopped because this is not my computer and they are not sure when it stopped working either. I'm guessing that this started after a software update was run, but I have no specific evidence of that.

Any other ideas?

---

### Post by joeknoodle on 2010-02-26
Doh! Do this...

System > Preferences > Startup Applications

In that do:

Click on "Add" at the right.

Enter name, command, and maybe a comment.

Close out and it should start on your next boot.

---

### Post by eqqfooyoung on 2010-02-27
That doesn't seem to work either. I tried adding:
```
/etc/init.d/cups start
```
and...
```
sudo /etc/init.d/cups start
```
I don't think this is working because cups needs to be started as root and there is no way to authenticate.

Something else interesting to note is that I just installed openssh-server on this computer as well and it does not start on it's own either. This is compounding the issue because I am troubleshooting remotely.

Is there some sort of an init.d log that i can check to see if there are errors somewhere?

---

### Post by joeknoodle on 2010-02-27
I'm sorry I can't be much more help, being an amateur and all.

You might try to take permanent ownership of the cup file in question...

Since it is a potential security issue to do so, I'll leave it to you to sort out the proper chown command for that.

Sorry I can't be more help.

---

### Post by eqqfooyoung on 2010-02-27
Well I finally got it fixed and ssh is starting on boot now too. Luckily I came across this bug listing:

bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520

I was missing the following from my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
```

After rebooting everything started working again.

---

### Post by klausner on 2010-03-10
> **eqqfooyoung said:**
> 
I was missing the following from my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
```

After rebooting everything started working again.

My /etc/network/interfaces file was completely empty. This solved my cupsd problem too!=D>

P.S. You might want to mark the thread "Solved", so others can find it.

---

### Post by shafin on 2010-03-15
> **eqqfooyoung said:**
> Well I finally got it fixed and ssh is starting on boot now too. Luckily I came across this bug listing:

bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520

I was missing the following from my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
```

After rebooting everything started working again.
Thanks a lot, I had manually edited my /etc/network/interfaces file before, and now was having problems, goes on to show that manually editing configs can have very far reaching consequences, who knew that editing a network file would stop your printing?

---

### Post by martalli on 2010-05-18
> **eqqfooyoung said:**
> Well I finally got it fixed and ssh is starting on boot now too. Luckily I came across this bug listing:

bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520

I was missing the following from my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
```

After rebooting everything started working again.

I had the same problem afterupgrading my Kubuntu 9.10 to 10.04.  CUPS was starting up fine in 9.10, but would not work in 10.04.  I am not sure about ssh or sshd in my case, but I found that the "iface lo inet loopback" was missing in my /etc/network/interfaces too.

---

