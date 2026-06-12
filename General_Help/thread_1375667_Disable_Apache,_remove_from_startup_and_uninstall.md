---
title: "Disable Apache, remove from startup and uninstall"
date: 2010-01-08
forum: General Help
---

### Post by kabeza on 2010-01-08
Hi guys
I'm having a little problem because I've installed xampp, but can't start it because it seems there's already an apache installation in my ubuntu

I've confirmed this by browsing to [http://127.0.0.1](http://127.0.0.1) , and by doing 
px ax | grep apache

[http://justpaste.it/wf](http://justpaste.it/wf)

[B]Now I'd like to know how to stop this apache, remove from startup, and uninstall safely so I use xampp's apache instead.
[/B]
Thanks,

---

### Post by AlexDudko on 2010-01-08
To stop apache just run in terminal
> sudo apache2ctl stop
To remove from startup run in terminal
> sudo chkconfig apache2 off
To uninstall run
> sudo apt-get remove apache2

---

### Post by kabeza on 2010-01-08
Alex
I've executed your commands, and here is the result. I guess there're some problems

[http://justpaste.it/wj](http://justpaste.it/wj)

---

### Post by AlexDudko on 2010-01-08
Firstly, do as prompted
> sudo apt-get update

Secondly, chkconfig is likely not installed, so run
> sudo apt-get install chkconfig

Apache service is started/stoped/restarted by command
> sudo apache2ctl stop/start/restart

You can see whether apache2 process is running by executing command
> ps -e | grep apache2
(if there is output - the process is running).

---

### Post by kabeza on 2010-01-08
Cool

1. I got no output so I guess it was closed

2. installed chkconfig, executed the sudo chkconfig apache2 off and got this
[http://justpaste.it/wl](http://justpaste.it/wl)

3. I still get the message regarding package apache2 is not installed so it won't be removed.

I don't know what software installed apache without my knowledge, but I'm beginning to think that NetBeans PHP edition installed it silently... but can't find an option in netbeans settings to remove that.

Thanks

---

### Post by AlexDudko on 2010-01-08
Well, perhaps, apache really is not installed in your system.
Can you show the output of command
> netstat --tcp --listening --program

---

### Post by kabeza on 2010-01-08
here it is
[http://justpaste.it/wm](http://justpaste.it/wm)

Apache now seems to be stopped, now doing some research for removing it and use only xampp's apache

---

### Post by AlexDudko on 2010-01-08
OK, from all of the above I can presume that apache is **not** installed and **nothing** is running on port 80 (the default for a web server). That means, apache shouldn't block your xampp start.

How do you start xampp and what errors do you receive?

---

### Post by kabeza on 2010-01-08
I start it using

sudo /opt/lampp/lampp start

and I got errors that por 80 was blocked.

---

### Post by AlexDudko on 2010-01-08
Do you see a start page in [http://localhost](http://localhost) ?
Can it be that your xampp is already running?

---

### Post by kabeza on 2010-01-13
> **AlexDudko said:**
> Do you see a start page in [http://localhost](http://localhost) ?
Can it be that your xampp is already running?

Yes, I see a starting page at [http://localhost](http://localhost)
But this start page is not xampp's start page
I see "It works..." which is apache's default page. Instead, xampp's starting page has a menu, logo, etc.

For now, I've solved the problem by doing this each time PC starts

**1)** sudo apache2ctl stop
**2)** sudo /opt/lampp/lampp start

So I'll keep researching about how to remove that apache installation that is running "as service", and then I'll make xampp start automatically

---

### Post by abid_naqvi83 on 2010-04-02
I had the exact same problem. The apache2 server was running in the background even though I had removed its package. To fix it I executed the following command:

sudo apt-get autoremove

and it removed all the free-hanging dependencies for apache2. Restarted the computer and apache2 had vanished and Xampp was starting up correctly showing the correct page in [http://localhost/](http://localhost/)

---

### Post by kabeza on 2010-04-02
thanks abid_naqvi83. Will try once I reach d office

---

### Post by connermcd on 2010-05-06
> **abid_naqvi83 said:**
> I had the exact same problem. The apache2 server was running in the background even though I had removed its package. To fix it I executed the following command:

sudo apt-get autoremove

and it removed all the free-hanging dependencies for apache2. Restarted the computer and apache2 had vanished and Xampp was starting up correctly showing the correct page in [http://localhost/](http://localhost/)

Thanks for this!!!!

---

