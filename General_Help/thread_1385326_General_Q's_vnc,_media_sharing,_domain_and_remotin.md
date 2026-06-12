---
title: "General Q's vnc, media sharing, domain and remoting"
date: 2010-01-19
forum: General Help
---

### Post by jessy722 on 2010-01-19
Ok Got Ubuntu 9.10 working with Compiz on mediocre PC, creamed my pants it was great. 
Looking for a recommendation. For a media sharing client which supports trans coding and is compatible with xbox and ps3. (I have a linksys dma2200 aswell but doubt that will be compatible with anything piece of crap)
Looking into mediaTomb but would like a experienced users input

I have vnc setup on my Ubuntu pc, viewing it/remoting from a windows 7 pc, the visual elements are laggin like bawlz with the windows 7 pc on Nband and Ubuntu 10/100 ethernet. Would an RDP client give me an improvement? what client would you recommend?
I had it setup before to log remotely from an external network(but currently can't remember), I have a dynamic IP, but own some domains as well exp: bluntforce.ca, could this domain be used to log onto my server rather than using a dynamic ip map thing like dyndns or freedns
what will I need to route Ubuntu wise and router wise?

I was fighting with my server(LAMP)
apache2
mysql
php5

to have judmedia.tv work on my local network(to point to server). Is there an easy way of doing this? I tried creating and changing the dbs files in bind with no luck  


Thanks In Advance!!

---

### Post by Chris Musampa on 2010-01-19
For remote access I highly recommend FreeNX, much less laggy than vnc whether using locally or over the internet and has windows and linux clients.
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by jessy722 on 2010-01-19
Thanks and was just recommend by my prof to toss Realvnc and try tightvnc.

---

### Post by jessy722 on 2010-01-20
just tried tightvnc with no luck now going to try freeNX

should I remove vnc11 and tightvnc?
 I think I know the code command for removing tight
sudo apt-get remove tightvncserver
but what about the default vnc in ubuntu would that cause the lag issues I'm having remoting from a windws pc  to ubuntu.

could my local network be the cause? Im running a linksys 610wrt

---

### Post by jessy722 on 2010-01-20
*bump*
something up with my local network... FreeNx won't ever work just crashes on the windows pc. Do I need to port forward anything on my local side to get a good vnc connection working? 

what do I need to do to set and or remove all the x11vnc and tightvnc crap back to default?

And would I mess anything up for future vnc stuff, if I remove x11vnc(cause its a default prog)?
-would removing the two vncs remove the config files I changed. 

There was an odd warning I recieved when installing freenx, though the code was scrolling fast I later found out that ubuntu is listening to 127.0.0.1. port 631

---

