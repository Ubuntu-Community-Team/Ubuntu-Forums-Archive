---
title: "Using Ubuntu as an Appliance"
date: 2009-06-30
forum: General Help
---

### Post by flandercan on 2009-06-30
Hi, All 

Im sure this question has been batted around before but im struggling to find an answer. 

I am trying to build a VM appliance however I will be using either jeOS or Ubuntu and I would like the server to boot and run an application without displaying the login prompt. 

The information displayed will be simple stats, output from perl or php scripts running cli , counts etc, and maybe f1 for help etc. 

Can this be done? 

Hope thats clear

Thanks 
Paul

---

### Post by t4thfavor on 2009-06-30
Using a gui, you could setup auto login, and then auto execute the program, or I have heard of a kiosk mode that only displays one app, and no way out of it.

without gui, I am not sure, but if someone wanted to do it once, I'm sure its possible to do.

---

### Post by decoherence on 2009-06-30
I did this by putting the commands I wanted to run in /etc/rc.local. When the machine boots, the commands run as root. Works perfectly, but it's a headless setup -- no user interaction at all, and no displaying information (all it did was capture video, compress it and save it to a network share.)

This setup could work for you if you use another machine to read and display the information. But if you need the output to be viewed on the same machine, you might have to find another solution.

It's an interesting question. I'll try a couple of things with my setup and get back to you.

UPDATE:
AAAAHHHH the hard drive just died on that machine!

anyway.... I think you should check out mingetty which has an auto-login feature for the command line. There's also rungetty, which might be even better suited (not sure if it does auto-login, though)

---

### Post by flandercan on 2009-06-30
Thanks for the replys , I have found on another forum users pushing output to /dev/tty so will investigate this a bit further. 

thanks

---

### Post by t4thfavor on 2009-06-30
Serial terminal? dunno how that works, keep us informed.

---

### Post by flandercan on 2009-07-01
ok a simple test might point to a solution. 

root@JeOS:~# bash -c "tail -f /var/log/messages" > /dev/tty2 &

Switch to tty2 ctrl+alt+f2 (This took me a min to work out in VM!) I had to do (ctrl+alt+space-space+f2  !! lol).

Then logged in over ssh and run 

root@JeOS:~# cat /var/log/dmesg >> /var/log/messages

And the output did indeed appear on tty2.


So im now thinking that if I create a perl, php or bash terminal app that displays the info I need to see, then use decoherence advise to start bash output to tty2 

That should do the trick although I will have no input to the app as its simply output ...hmm 

thanks

---

