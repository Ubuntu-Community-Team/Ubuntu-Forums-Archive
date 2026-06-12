---
title: "Opening Mathematica via SSH X-window Sporatically Quits All Programs and Logs Me out"
date: 2011-07-27
forum: General Help
---

### Post by maberib on 2011-07-27
Hi everyone,

I use Mathematica 7.0 through my school's SSH server.  This involves:
-loading their font server via "xset fp+ tcp/c1.ucalgary.ca:7100"
-connecting to the SSH server via "ssh -X [email]useruser@servername.ca[/email]"
-entering my password
Then I choose to run Mathematica via ". use mathematica 7" then to load the GUI "mathematica".

Sometimes, and only sometimes, the screen goes to the error in the attached picture, stays there for about 5 seconds, brings me to the login screen.  When I log in again, all of my applications that were running, open folders, and my terminal windows are closed.

I've even tried going through the procedure with the same applications open -- sometimes it dies, sometimes it works fine.

Any thoughts?

---

### Post by Nagarjuna Asam on 2011-08-04
Same with me. I doing a remote login through ssh using x11 forwarding and opening a GUI software called sde . My computer logs off as soon as I open it. However, other GUI applications like tecplot_sv work nicely.

I am using this command to remote login:
>ssh -XY ee735_1@10.107.106.37

And then when I say
>sde

It starts opening a GUI window , and immediately my systems logs off, and all my programs running on my system are closed.

Someone please help.

---

