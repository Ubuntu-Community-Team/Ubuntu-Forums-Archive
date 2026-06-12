---
title: "To ssh ..... or to not ssh..... that is the question.  (and also how)"
date: 2010-08-26
forum: General Help
---

### Post by spydeyrch on 2010-08-26
If you want to skip the long intro/rant and get to the actual part where  I ask for help, skip down to the send set of dashes. :)

-----------------------

Ok,  so for a little background, take a look at [this thread.]("http://ubuntuforums.org/showthread.php?t=1343980")

I  had their system beautifully setup. It was wonderful! They were using  Windows XP, had MSE (Microsoft Security Essentials), I also installed  steady state and had it configured wonderfully where they were protected  from anything negative happening. The mother had requested that I limit  her daughter's access to certain websites, which I did. She also  requested that I limit the amount of time and the time of day that the  internet/computer is accessible, which I did.

I had also set up a  VPN connection from my computer to her network. This allowed me to  access her computer via the VPN and use either RDP or VNC to  manage/administer the computer. I would use either RDP or VNC from  either my win7 or Ubuntu system, didn't matter which as both worked  fine.

The current issue is that after a few months of everything  working smoothly, the mother fell to the daughter's constant whining and  complaining. So the mother asked me to remove the steady state and  internet monitoring/managing software. So I did but I warned her that  her system was going to start to have issues eventually.

A little  later, due to the continual whining of the daughter, I was asked to  remove MSE because it "blocked access to some cool sites". In the "epic"  words of the daughter: "It keeps saying that the site is known to  infect computers but my friends visit it all the time and their  computers are fine...." So I firmly warned the mother about the effects  of removing MSE, but in the end it is her computer and so I removed it.

At  that time, I disabled the VPN between our networks so that nothing  could even remotely try to travel between hers and mine.

Then the  mother asked me to change her daughter's account from a user to an  admin account, but the catch was that I change the mother's from an  admin account to a user account!!! My jaw dropped! I spoke with the  mother for like 45 mins explaining what that means and the consequences  of everything else up to that point and then also changing user rights.  She didn't care. So I did it. I did it not because she asked me too but  because I think that it will teach them a lesson in computer management  and it will help them see. I washed my hands and walked away, knowing  that soon events would take place that would cause them to ask me to fix  it again.

Well it did to some degree. After like 6 months, they  called me over to their house and started complaining that their  computer was running slow, was not working like before, and that I had  done something to it to make it not work properly.

I reminded the  mother that I explained to her that this would eventually happen  because she allowed her daughter to make it happen.

I scanned the  machine for malware and found ........ no joke......... more than 6,000  pieces of malware!!!!!! Virii, trojans, fake virus scanners, worms, etc  etc. You name it, they had it!!

So the mom finally accepted the  fact that they had led to their computer's own destruction and failure.

I  told her the only thing that I would do is install ubuntu on the  machine and that neither of them would have admin rights to it. That I  would admin it remotely and would block certain websites. She didn't  like the idea of ubuntu but I told her tough, learn to use it, or go buy  your own copy of XP/Vista/7 and install it yourself and manage it  yourself.

So we agreed on ubuntu.  :D


-------------------------------------

Here  is where I need some help.  First off, sorry about the long intro/rant.  It is very frustrating when people just don't get it!!!

Ok, so  previously I was administering their computer remotely via two different  ways but they each basically did the same thing:

1.) Because it  was a windows based system, I installed no-ip.com's client software on  their system. It allowed me to assign a domain to their dynamic IP. Via  that domain, I could then use VNC or RDP directly and gain access to  their computer.

2.) Or I would use a VPN to connect, via the  domain, and then tunnel  through the VPN using VNC or RDP to gain access to their machine.

Pretty  simple setup actually. A little slow and laggy but it was ok for what  was needed.

But that was a windows based system. Due to what I  explained above in my rant, they are going to switch to an Ubuntu based  system.

no-ip.com has a linux client available but I really don't  want to mess with it. I would rather use their router's dyndomain  feature instead.

I also would like to use SSH instead of VNC or  RDP.

Is it advisable to continue to use a VPN to connect our two  networks and then SSH, or could I just use the ssh command with whatever  their domain is, to connect?

Example:

```


ssh  -X user@domain.com


```

I really haven't ever used ssh  and don't know too much about it. I am looking for some basic  tips/pointers about it. I know that with the '-X' parameter it will give  me a visual session of the server computer (the mom's computer) but  other than that, I don't really know too much more about it. I have read  some of the online docs and info and they were helpful but a more,  human response sometimes is the best.

Also, in the off chance  that I am connected to the admin account on the mother's machine via ssh  and if the connection severs/fails, will my session on her computer end  at the same time? I am concerned that if it is not, and it is still  open, then the daughter/mother might have access to admin rights. But I  guess that it all depends on if ssh opens the account on the desktop the  same way that RDP does, right?

So as you can see, I am a little  confused and need some clarification. Thanks!!!!

-Spydey ;)

---

### Post by silverglade00 on 2010-08-26
> Also, in the off chance that I am connected to the admin account on the mother's machine via ssh and if the connection severs/fails, will my session on her computer end at the same time? I am concerned that if it is not, and it is still open, then the daughter/mother might have access to admin rights. But I guess that it all depends on if ssh opens the account on the desktop the same way that RDP does, right?

They will not be able to see anything. It is somewhat like a web server where you can't hook up a monitor and watch all 12 million of your users browse your website.

---

### Post by spydeyrch on 2010-08-26
Thanks silverglade00 for the response. I was hoping that it would work somewhat like that. That is good. 


Anyone else have any pointers?

I forgot to mention that I have a second machine at my house that I can mess around with and try to work out the kinks before going over and actually setting it up on the mother's machine.

Ideas anyone?

-Spydey :)

P.S. what about the code that I had inserted? Would I be able to connect without a VPN by using their domain?

```


ssh -X user@domain.com


```

Any thoughts?

---

### Post by pricetech on 2010-08-26
Just make sure the SSH server is running on their computer and that port forwarding is set up in the router.

I have to say though, I'm wondering if you're ready to be their admin if you have to ask how to set up SSH.

---

### Post by silverglade00 on 2010-08-26
Also, ssh -X will let you use GUI programs. It will pop up the program on your computer instead of the computer it is logged in as. They won't see a thing. It will look just like any of your other windows except it will be laggy. Once you start using ssh, you will really get to know the command line and find yourself in the Terminal more because some things are just faster that way.

---

### Post by Lars Noodén on 2010-08-26
> **spydeyrch said:**
> 
So we agreed on ubuntu.  :D


Excellent.  

I would recommend learning your way around the shell eventually, it saves a lot of time and effort.  

When the ssh connection breaks, you are logged out, unless you've gone to other lengths to prevent that.  So if you log in using **ssh -X** for GUI or **ssh** for regular shell and the connection breaks, you are logged out.  If you are tunneling VNC over SSH then the person sharing stays as they are and the visitor loses the connection.  

The first account set up by ubuntu gets admin privileges, you might make a second account without admin privileges and let her use that and give sudo privileges to kpackage or synaptic only.  

If you need to walk her through admin tasks, then you can both use the admin account.

---

### Post by spydeyrch on 2010-08-26
> **pricetech said:**
> Just make sure the SSH server is running on their computer and that port forwarding is set up in the router.

I have to say though, I'm wondering if you're ready to be their admin if you have to ask how to set up SSH.

Setting it up and port forwarding via the routers is not difficult at all. I do it all the time with other windows machines via vnc, vpn, rdp, etc. But I have just never used ssh and thought that it would be a great opportunity to use it and learn from it. I have read around and seen that the majority of people say it is more secure then vnc/rdp.

Setting it up (install settings, access, etc) I don't need help with. Just thought that asking for any pointers, ideas, thoughts on how to do things more efficiently based upon other user's experiences would be a good idea. I always like to research as much as I can before I dive into something so that I have at least a reference and am prepared if something happens.

And you know what, it may be true that I am a novice at administrating an ubuntu machine, being as I don't have as much experience, but with windows, I have plenty. ;) I am not too worried though. thanks for your concern. :)

[quote=silverglade00]
Also, ssh -X will let you use GUI programs. It will pop up the program  on your computer instead of the computer it is logged in as. They won't  see a thing. It will look just like any of your other windows except it  will be laggy. Once you start using ssh, you will really get to know the  command line and find yourself in the Terminal more because some things  are just faster that way. 	[/quote]

Yes, I am aware that the -X parameter will give me a GUI on my end of the connection but will it only be the program that I am running on the server end that is viewable in the window? Or is it going to show me a "desktop", as if I was physically at the machine, and from there I would have access to the gui menus, etc.

I guess that I am basing my questions off of previous experience with RDP and VNC.

Thanks for the clarification.  :D

-Spydey :KS

---

### Post by spydeyrch on 2010-08-26
> **Lars Noodén said:**
> Excellent.  

I would recommend learning your way around the shell eventually, it saves a lot of time and effort.  

When the ssh connection breaks, you are logged out, unless you've gone to other lengths to prevent that.  So if you log in using **ssh -X** for GUI or **ssh** for regular shell and the connection breaks, you are logged out.  If you are tunneling VNC over SSH then the person sharing stays as they are and the visitor loses the connection.  

The first account set up by ubuntu gets admin privileges, you might make a second account without admin privileges and let her use that and give sudo privileges to kpackage or synaptic only.  

If you need to walk her through admin tasks, then you can both use the admin account.

Thanks for the input. Yeah, I would say that I am not extremely versed with the shell yet, but I manage to get around fine on my home system in the shell. At home I have a triple boot system currently but it is always changing. ;)

Home:

Win7 Pro x64
Ubuntu 10.04 x64
Mint 9 x64

I have been experimenting with ubuntu since 2005, on and off. I haven't really used it as a primary os until 9.04 and even more heavily now with 10.04.  So I know my way around the shell for basic things but for more advanced things, I am still learning. ;)

As far as the admin rights go, yes, I was already planning on not giving them admin rights, except for synaptic for updates and installing program that they may want.

After reading your post, I have a few more questions about ssh. Hopefully you don't mind me asking. :(

So from your brief description, to try and compare apples to apples as much as possible, it almost appears that ssh can be used as a vpn can. Meaning that it can be used to link to separate private networks together. Yet it appears that I could also use ssh directly, as rdp and vnc could. Am I correct in understanding that?

I guess I am going to test a bunch of things first on my network here at home to understand it better. :D

-Spydey :KS

---

### Post by Lars Noodén on 2010-08-27
> **spydeyrch said:**
> ... but with windows, I have plenty. ;) 

That's a liability with computers, but curiosity and a interest in [hacking](http://catb.org/jargon/html/H/hacker.html) will overcome that and get you up to speed quickly.  

> **spydeyrch said:**
> ...will it only be the program that I am running on the server end that is viewable in the window? Or is it going to show me a "desktop", as if I was physically at the machine, and from there I would have access to the gui menus, etc.


X11 is based on a client server architecture.  The server is the display you see on your computer with access to the local mouse, keyboard and other devices.  The client is the application you choose to run, such as firefox, konqueror or thunar.  The connection is via TCP/IP.  Using ssh with forwarding, you are [forwarding the client-server connection](http://docstore.mik.ua/orelly/networking/firewall/ch08_16.htm) over the net to another computer.  

So you could forward, IIRC, either a desktop environment or a window manager.  Any latency in the connection will be a pain and obviously the less traffic you have to forward, the faster it will feel.  You will get faster results, just forwarding individual applications.  My recommendation is that the shell be used for sysadmin tasks, since it is more robust, less affected by slow network connections, secure, and scriptable.  

Here is a case in point, regarding the UI, using adding the closed source,but open standard, package Opera.  If you use the shell:
[list]
 [*] log in 
 [*] add *deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free* to */etc/apt/sources.list*
 [*] download and install the repository key for Opera *wget -O -  [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -*
 [*] refresh the package database *sudo apt-get update*
 [*] install Opera *sudo apt-get install opera*'
[/list]
Now consider how you would write out instructions for the same task using the GUI and kpackage or synaptic instead.  

To be sure, you'll  need the GUI to help walk them through various end-user tasks, but not for sysadmin.

---

### Post by spydeyrch on 2010-08-27
Awesome! Thanks for that example. I went online and did some more research. I found a few tuts that are fairly simple to follow and a good resource for future reference. I think that is pretty clear now. I appreciate your help and patience. ;)

Now I just have to test a few things on my local network and work out the kinks. Thanks again!  :D

-Spydey :KS

---

