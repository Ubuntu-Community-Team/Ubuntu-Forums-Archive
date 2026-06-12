---
title: "SSH Tunnel to browse internet"
date: 2011-04-05
forum: General Help
---

### Post by tomfpotter on 2011-04-05
I am a noob so please be patient with me!

I have ubuntu 10.10 server (there is no gui) on one box (IP 192.168.1.103 on my LAN). On my windows machine I set up a tunnel in Putty: Source Port: 8080; Destination: 192.168.1.103:8080; Local; Auto; I then connect to my ubuntu server with Putty.

I then set my Firefox browser Tools->Options->Advanced->Network->Settings to "Manual Proxy Configuration. I set HTTP Proxy:127.0.0.1 and Port:8080; I select SOCKS v5; I then select "Use this proxy server for all protocols". When I then try to browse the internet I get a message that the server was closed while trying to access the internet. I have a feeling there is something not set up correctly on my server. If I change the tunnel Destination to 192.168.1.103:80 I get my apache website on my server (I have apache2 installed) for any website I go to (as expected). Do I need to create a listener for port 8080 on my server or open port 8080 (Neither of which I know how to do).

By the way, I have OpenSSH on my server (which works correctly). I have also successfully set up Samba and CUPS on my server.

Thanks in advance for your help!

- Tom

---

### Post by Fire_Chief on 2011-04-05
It appears that you have not configured a proxy server on your Ubuntu server system. So when your client connects to port 8080 on the server (via SSH tunnel), the server is not listening on that port and also doesn't know to redirect that traffic out to the Internet.

You may want to look at this site for a basic squid setup on Ubuntu
[http://beginlinux.com/blog/2010/04/ubuntu-10-04-squid-proxy/]("http://beginlinux.com/blog/2010/04/ubuntu-10-04-squid-proxy/")

For a more advanced setup (with AV and content filtering) see
[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection]("http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection")

Cheers!

---

### Post by tomfpotter on 2011-04-05
Thanks a ton! I will try that when I get home tonight. 
I was reading this site [https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html) when I set up the ssh tunnel. The site left me with the impression that I did not need to set up squid (which I don't want to do if I can avoid it!). Did I mislead myself (that would not be a first)?

---

### Post by Fire_Chief on 2011-04-05
Ah...ok. So I think the problem in your existing setup is PuTTY. It is creating the tunnel that is described in option 2 (Squid proxy) instead of the ssh connection in option 1 (note the destination address/port specification in option 2).

In PuTTY's SSH main section, tick the box for Enable Compression.
In the Tunnels section, enter 8080 for the source port but do not enter a destination. Choose Dynamic instead of Local and leave Auto setting selected. Click Add.

You should see a new entry in the forwarded ports box that says D8080

Save this and connect with PuTTY. Then see if your web browser can get out to the Internet through the tunnel.

For reference: I pulled this info from [http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html#config-ssh]("http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html#config-ssh")

Cheers!

---

### Post by tomfpotter on 2011-04-05
I changed all things you mentioned. Now I don't get any warning I just get an empty page - no warnings - nothing. Any thoughts?
- Tom

---

### Post by Fire_Chief on 2011-04-06
Hmm...not sure what's up there. For additional reference, I found this straightforward article on doing this exact setup.

[http://www.dotcomunderground.com/blogs/2008/12/11/putty-ssh-tunnel-to-hide-ip/]("http://www.dotcomunderground.com/blogs/2008/12/11/putty-ssh-tunnel-to-hide-ip/")

Review that and verify your settings. If it's still not working, let us know and we'll go from there.

Cheers!

Edit: Oh...just to double check. Your Ubuntu box can get to the Internet, right?

---

### Post by tomfpotter on 2011-04-06
Thanks. I will read over that.
I am pretty sure my box can get to the internet as I have downloaded things (like subversion) from the internet that did not come with Ubuntu 10.10 server.

---

### Post by Fire_Chief on 2011-04-06
Ok, that's promising. :)

I did just test this setup locally from a Windows 7 desktop with Putty to a linux box running SSH. It worked perfectly. I did login to the SSH session as root but that should not make a difference in this case.

Cheers!

---

### Post by tomfpotter on 2011-04-06
Awesome!
I changed it to be EXACTLY like the site and it worked. I worked my way backwards to find my problem - for some reason it does not like that I set the http proxy to 127.0.0.1 and port to 8080. If I don't set the http proxy but set everything else it works fine!
Thanks for your help! 
Is there anyway to give you points on the forum or something for helping me out - I'm new here so I don't know how it works (maybe I should read the noob section!).
- Tom

---

### Post by Fire_Chief on 2011-04-07
Nah, not really a points system here. This site is just about helping each other out. :) I appreciate the sentiment though.

You may want to mark the topic as [SOLVED] though so that others can use this thread to get it working as well. For more tips and such, I recommend reading the Ubuntu Forums Code of Conduct and FAQ (under the Forum Help link at the top of the page).

Cheers!

---

