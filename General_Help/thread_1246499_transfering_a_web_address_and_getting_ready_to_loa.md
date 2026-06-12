---
title: "transfering a web address and getting ready to load a site"
date: 2009-08-21
forum: General Help
---

### Post by krraleigh on 2009-08-21
I hate to ask this question, but being the really new guy I am trying to assess what steps are taken to transfer a web address to my new configured server along with the hows and wherefores of loading my database, and letting the internet know that my address isn't at go daddy anymore but at rackspace.
 
Is there a newbie kind of article for this?
 
Thank You
Kevin

---

### Post by Jerry.S on 2009-08-21
You need to let the DNS servers know were to point the public to your server. Go back to GoDaddy and under your account there is a place for DNS and that is were you need to point your domain name with go daddy to your DNS servers, that point to your web server. 

If you dont have a public DNS server go over to [www.zoneedit.com](www.zoneedit.com) and set up an account for free( you can host 5 sites) and point zone edit to your server and then point godaddy to zone edit. It should thake about 24 hr to populate in the server sometimes sooner.

---

### Post by hockman5 on 2009-08-21
You need to change your name server at whoever you registered your domain with, to the new host.

---

### Post by tgeer43 on 2009-08-21
This doesn't seem to be an Ubuntu question at all but you may have better luck in the [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") forum. There's lots of good info there.

tgeer

---

### Post by krraleigh on 2009-08-24
I appreciate the help
 
Once I transfer using the name server how do I setup my www folder on my intrepid server so that I have separate folders for each web address? I mean right now my server address is 123.123.123 example, but I need a unique address or something for each different web address that I host right? Lots of questions, but the questions are not focused enough for me to start searching the net for the right information.
 
Can you advise?
 
Kevin

---

### Post by Jerry.S on 2009-08-24
It is done in the Apache conf. file. Your best bet is to google for "How to set up two domains under apache" it it out there. I did it about a year ago but I just don't remember enough to explain it to you.

p.s. dont forget to setup port fowarding in you router if you have one.

---

