---
title: "ssh &amp; sudo - best practices"
date: 2009-11-10
forum: General Help
---

### Post by gforster on 2009-11-10
I have a network of 30+ computers that I administer. For many things I can simply ssh and run a command or do so from a script. This works on anything that doesn't require a sudo password. I can of course, enable the root account/password and ssh into the root accounts, but I know that can be dangerous. 

Is there a way to put the password into the scripts so that I can send even a simple sudo apt-get update && sudo apt-get upgrade command to 30+ computers without being promted for the password?

---

### Post by undecim on 2009-11-10
If you are doing regular updates, you can turn on automatic updates.

If there is any command you run regularly you can set up cron jobs on the remote machines.

You can also use the "expect" command to enter passwords with a script, but having passwords stored as plaintext on your local machine is a bad idea.

You might be able to set up expect to process all machines while only having to type a password once (if all the passwords are the same), but I don't know. you would have to look at the manual for that.

Also, a litte off-topic, but with 30+ ubuntu computers on the same network, you should look at setting up an apt-cacher server if you haven't already.

---

