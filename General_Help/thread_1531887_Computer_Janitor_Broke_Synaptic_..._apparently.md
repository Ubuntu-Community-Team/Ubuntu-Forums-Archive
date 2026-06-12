---
title: "Computer Janitor Broke Synaptic ... apparently"
date: 2010-07-15
forum: General Help
---

### Post by russki_drewski on 2010-07-15
I just ran Computer Janitor on my computer and I think it broke Synaptic.

The program was cleaning up some files, but then it froze halfway through and I had to force it to quit. Since then, I can't open Synaptic package manager, the Ubuntu Software Center, nor Computer Janitor itself. When I do they either freeze and I have to force them to quite or they just don't show up on the screen, but they're stuck running in the background because System Monitor reports the processor is running at 100% and so I have to go in manually and kill the bad processes running in the background. Restarting doesn't change anything.

Does anyone know how I could fix this?


Running Lucid Lynx on a HP dc7100, P4 3.2 Ghz, 2gb RAM.

---

### Post by Cavsfan on 2010-07-15
I don't much about how to fix your system, I am sure someone else will. but I believe that
that program can cause some serious problems as you are experiencing. I believe I heard that said in this forum.

I use Bleachbit to clean my system you can get it from Synaptic.
I enter in a terminal "sudo bleachbit" rather than running it as root.
You just want to double check what options are set when you run it.

And I have never had a problem using it either. You can even set it to clean your 
free space.

Someone with more knowledge than I will be along to help you shortly...

---

### Post by Cavsfan on 2010-07-15
You could try these commands:
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get dist-upgrade (this is only for when a kernel is available I believe)

With these 3 commands you do not need Update Manager.
In fact these are better because they will tell you what is going to be done before hand.

---

