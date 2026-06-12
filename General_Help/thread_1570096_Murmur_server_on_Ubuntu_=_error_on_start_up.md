---
title: "Murmur server on Ubuntu = error on start up"
date: 2010-09-07
forum: General Help
---

### Post by Hattrix on 2010-09-07
HELP !!!!

I've tried searching everywhere and I can't find any detailed help on  setting up my murmur server. This is my first attempt doing anything within Ubuntu.

Here are my issues:

I'd like help with the murmur.ini setup. I'm having a hard  time getting the server to start up in Ubuntu. I have a wireless router  in the mix as well. It looks like I can get the SuperUser password set  and have murmur see the correct ini for it's settings, but I get an  error when i finally try to start the server. The error says:
   
  
  **"Server: TCP Listen on xxx.xxx.x.x:64738 failed. The address is not available"**
   
  
   I'm confused as to what IP I need to point murmur to. I've tried a bunch of IPs with nothing working.
   
  
[LIST]
[*]Should I be using the IP of the server (the laptop  I'm running murmur on)?
[*]Should it be pointing to the IP of the wireless  router (192.168.2.1) that connects the server (laptop) to the internet?
[*]Should the IP be the dynamic IP that I get from my ISP?
[/LIST]
   Here are the lines of code from the ini file:
   
  
   [I]# Specific IP or hostname to bind to.
 # If this is left blank (default), murmur will bind to all available addresses.
 host=[/I]
   
  
    My ISP gives me a dynamic IP but I'll deal with DynDNS later if I  want the server running 24/7. For now I just want the server to start up  and be able to get to it from Mumble.
   
  
  I'd like to know what PORT to bind it to. I read that 64738 is the  default port that murmur uses, but then I read something about ICE  needing murmur to use port 6502. Now I'm confused. I've tried both with  no success. I have no idea what ICE is or how it affects murmur. The ICE  line in the ini was commented out, so I don't know if that's an issue  or not. Here is that line of code from the ini for the port:

   
  
  [I]# Port to bind TCP and UDP sockets to
 port=[/I]
 

LASTLY, here is how I'm starting the server. Maybe I'm doing something wrong there. In the terminal screen in Ubuntu I type:
   
  
   *murmud -supw [thesuperpassword]*
  
   
  
   *murmurd -ini /home/Hattrix/murmur.ini*
  
   
  
   *murmurd -v*
   
  
   *murmurd -fg*
   
  
   The last statement generates the error I listed above in bold.
  
    Thank you very much for taking the time to read / answer!


 Hattrix

---

### Post by Hattrix on 2010-09-08
I got it running!

I kept ALL defaults in the murmur.ini file except for the Welcome Message which I changed. I left the IP blank (default) and the port as 64738 (default). This Murmur server is running on a laptop, connected via wireless router on my home network.

I started the Murmur server from the terminal:

*murmurd -supw superuserpassword*   [enter]

*murmurd -fg -v*   [enter]

The server stared and showed that it was listening!

To connect from Mumble, I gave my friends the dynamic IP that I'm getting from my ISP and the port 64738. They connected the first time with no issues.

I connected to it (while on my Win7 PC on my home network) by using the IP of the server **within** the network (192.168.2.4). I got in with no issues and the 3 of us chatted and played games for 3 hours.

To log in as the "superuser" from the Mumble client you need to use the actual name "superuser" (without the quotes) when you log into the server. The server will then ask you for the password that we had set when we started the server (see above superuserpassword). I now had admin access and ton of other options to mess with within the client. The only thing is that you can't chat when you log in as superuser....you are muted automatically and I couldn't find a way around that.

I hope that anyone who find this info, find it helpful!

):P

---

### Post by Nocturnal7x on 2011-02-03
hi,

I have the murmur server running, I can log in as a regular user.  But when I try to log in as superuser, and use the password I set, it says "wrong password for registered users"

when I type 

```
murmurd -supw my password
```

it tells me

```
superuser password set on server 1
```

so what is wrong?

I then run the server with

```
murmurd -fg -v
```

any ideas?

---

### Post by Karl Naylor on 2011-06-16
> **Nocturnal7x said:**
> I have the murmur server running, I can log in as a regular user.  But when I try to log in as superuser, and use the password I set, it says "wrong password for registered users"
I had this problem and resolved it by specifying the full path to my .ini file when changing the password:

sudo murmurd **-ini /etc/mumble-server.ini** -supw the_password

I haven't the experience with Murmur to understand why this is, but I notice that without the -ini specification, it was attempting to read an ini file from /home/karl/.murmurd/, which doesn't even exist. The server is picking up my port number and server password from /etc/mumble-server.ini.

My best guess is that the .ini file specifies a location for whatever file the password is to be stored in, and the server is picking that up and looking for the password in a different place than it was stored in. Sounds like a bug but I'm not confident enough in my interpretation to go log it. Anybody more experienced want to comment on this?

---

