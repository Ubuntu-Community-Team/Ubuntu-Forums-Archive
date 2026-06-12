---
title: "Launch Bash script from web page"
date: 2012-08-24
forum: General Help
---

### Post by Jonny87 on 2012-08-24
I am setting a guest account that will run a browser opening a locally stored web page, the web page will be a nice little welcome thing. I also want it to have options to open other apps from that page, as I want to limit every thing else to basically nothing. so I'm guessing it will need to launch a bash script with a command for the app. 

But how can I do this?

the web page won't be on a sever. it's only local.

otherwise could some give me an example of a basic python gui that opens full screen with a welcome message and buttons to run shell scripts or something along those line.

---

### Post by SeijiSensei on 2012-08-25
Any application that the web server opens will be running with the permissions of the user under which the server runs.  In apache on Ubuntu, that user is called "www-data".  If you need to have users save files to private areas like their home directories, this is not going to be an easy thing to implement with a web server.  You might be able to use apache's [suexec]("https://wiki.archlinux.org/index.php/Apache,_suEXEC_and_Virtual_Hosts") features for this, though it creates substantial security issues.

---

### Post by Jonny87 on 2012-08-25
> **SeijiSensei said:**
> Any application that the web server opens will be running with the permissions of the user under which the server runs.  In apache on Ubuntu, that user is called "www-data".  If you need to have users save files to private areas like their home directories, this is not going to be an easy thing to implement with a web server.  You might be able to use apache's [suexec]("https://wiki.archlinux.org/index.php/Apache,_suEXEC_and_Virtual_Hosts") features for this, though it creates substantial security issues.

Except i'm not running it on a web sever. The web page is a local file that is opened in a python-webkit browser when the guest user logs in. the browse is full screen and can't be closed by the user. there is no other interface as it's a restricted Kiosk but I want to make the local web page act as a welcome screen as well as an application launcher for other apps such as a calculator, word processor, etc.

---

### Post by Jonny87 on 2012-08-25
I realize that I'm probably asking the impossible, so can someone at least give me an example of a simple gui interface that can have a welcome message followed by some app buttons that will launch command. That can be full screen and lightweight. 

I don't know much on building gui's. I've used Zenity in the past, but I don't think I can get it to do what it want.

---

