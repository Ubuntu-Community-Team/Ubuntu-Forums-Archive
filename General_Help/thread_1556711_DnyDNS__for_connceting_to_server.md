---
title: "DnyDNS  for connceting to server"
date: 2010-08-19
forum: General Help
---

### Post by wannabegeek on 2010-08-19
hi all,
I just got my ssh working to connection to my home server and hoping to finish this stage of the project by getting Dyndns working. It has worked in the past for me with a password.  But not sure that it is now.

My router is running dd-wrt and I set up the DynDNS stuff there.
I also created port forwarding for ssh key access only in sshd_config.

```
ssh -p XXX lucky@smokeblunts.ath.cx [code]
works from home behind same router as server. I tried ssh to another computer outside,
then ssh to my server with the same command as above: Here is output.
[code] th123-13:dcuneo% ssh -p 3555 lucky@smokeblunts.ath.cx
warning: Authentication failed.
Disconnected; no more authentication methods available (No further authentication methods available.).
th123-13:dcuneo% 

```not sure what to do now...? Firewall issue ?
tia,
wbg


EDIT:  I am only allowing keys so, the authorized key file is not accessible. I could make this test work possibly by adding my pub key to the account I am trying  to login from (remote outside one)...

---

### Post by Morrad on 2010-08-19
Promised I'd be back ;)

I have run dd-wrt on an old linksys myself, and I can testify that these settings have worked in the past for myself.

Please check the dynamic dns settings menu from within your router, and make sure they match the settings on the following dd-wrt wiki link.  (You may want to try both the preset DynDNS setting and the custom setting if you run into problems).

 [http://www.dd-wrt.com/wiki/index.php/DDNS_-_How_to_setup_Custom_DDNS_settings_using_embedded_inadyn_-_HOWTO#DynDNS](http://www.dd-wrt.com/wiki/index.php/DDNS_-_How_to_setup_Custom_DDNS_settings_using_embedded_inadyn_-_HOWTO#DynDNS)

You'll also want to make sure that you have Port Forwarding set up to forward the correct ssh port on your server.

Both port forwarding and dyndns must be set up for you to be able to access your machine.

If it doesn't seem to be working, please include the output of 

```
ssh -vp 3555 lucky@smokeblunts.ath.cx
```

and

```
sudo nmap -p 3555 smokeblunts.ath.cx
```

Note: If you decide to change the exposed port (3555), obviously change that in the commands as well.

---

### Post by Morrad on 2010-08-19
Now that I've read your edit, it sounds like you're on the right track.

If you still have problems after getting the pubkey authentication set up, try the stuff in my previous post.

---

### Post by wannabegeek on 2010-08-20
thanks a ton Morad, it seems to work, needs further testing ... :)

I'm using DSL now which I know has a slow upload speed. If I switch to broadband,
is a server like mine a decent way to host a web page ? I've never build a web page and think its
time I try. I don't expect to have a lot of traffic, however it would be cool to have my resume up there though.

thanks
wbg

---

### Post by Morrad on 2010-08-20
> **wannabegeek said:**
> 
I'm using DSL now which I know has a slow upload speed. If I switch to broadband,
is a server like mine a decent way to host a web page ? I've never build a web page and think its
time I try. I don't expect to have a lot of traffic, however it would be cool to have my resume up there though.


For simple pages with low traffic, even what you have now should be just fine.  If you're wanting to host a ton of pictures yourself or other bandwidth intensive things, then yes, you'll need a fatter pipe, or use another service to host the media files.

I run a tiny wall-wart server from home.  It hosts two blogs (one with static files, and one using Wordpress) with my upload speed capped at about 50kB/s.  Any pictures I include are hosted on Flickr, Facebook, or some other service so that people browsing my site don't have to download those files through my slow connection.  You can see what I have set up below.

[http://jason.the-graham.com/about/stats](http://jason.the-graham.com/about/stats)

Bear in mind that for most people their ISP agreement prohibits them from hosting a server through their home connection, but unless you end up on Digg or Slashdot they don't seem to care, in my experience.

---

