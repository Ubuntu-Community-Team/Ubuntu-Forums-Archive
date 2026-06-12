---
title: "Need Help with Several Things (Samba, DNS, Config Files)"
date: 2011-08-22
forum: General Help
---

### Post by jlacroix on 2011-08-22
Hello again everyone. I didn't know where to post this because I need assistance with several things, and I didn't feel the need to flood the forum with a bunch of questions so I thought I'd consolidate my questions into one post. If this is in the wrong place, I apologize.

First, a little background. I have a home lab (so to speak) with five Linux machines, a single Windows machine, and a Mac. I use Samba shares on each, because I do a lot of stuff with servicing clients Windows machines, so that's why I use Samba. So, with that in mind, here are my questions:

1.) On my Linux machines, I have to add all the other Linux machines to /etc/hosts in order to browse samba shares. If I do not do this, the Linux machines will time out when trying to view them. Is this normal? My Windows machine can see all the Linux shares without doing this.

2.) I thought about DNS on a Linux server to solve number 1 (every time I add or remove a Linux machine, I have to edit /etc/hosts on EACH machine) but I cannot seem to find a tutorial online that I can understand. Is there a simple DNS howto specifically for LAN DNS? A sample config file for DNS used in a LAN would be awesome. (Note: I tried dnsmasq, and come to the conclusion that it is not compatible with my network).

3.) On each machine, I store a lot of config files, that are made the same between each machine on purpose. Is there a Linux based server application that can push config files to machines from one central source, rather than me editing config files manually on each machine? It seems the more computers I get my hands on, the more work I have to do managing them and I'm trying to simplify my work a bit.

I know these questions may be a little on the strange side but I'm studying to become a Linux Administrator some day (I currently support Windows machines) and I'm trying to learn all I can by configuring systems in my lab.

---

### Post by skinnyquiver on 2011-08-22
> **jlacroix said:**
> Hello again everyone. I didn't know where to post this because I need assistance with several things, and I didn't feel the need to flood the forum with a bunch of questions so I thought I'd consolidate my questions into one post. If this is in the wrong place, I apologize.

First, a little background. I have a home lab (so to speak) with five Linux machines, a single Windows machine, and a Mac. I use Samba shares on each, because I do a lot of stuff with servicing clients Windows machines, so that's why I use Samba. So, with that in mind, here are my questions:

1.) On my Linux machines, I have to add all the other Linux machines to /etc/hosts in order to browse samba shares. If I do not do this, the Linux machines will time out when trying to view them. Is this normal? My Windows machine can see all the Linux shares without doing this.

2.) I thought about DNS on a Linux server to solve number 1 (every time I add or remove a Linux machine, I have to edit /etc/hosts on EACH machine) but I cannot seem to find a tutorial online that I can understand. Is there a simple DNS howto specifically for LAN DNS? A sample config file for DNS used in a LAN would be awesome. (Note: I tried dnsmasq, and come to the conclusion that it is not compatible with my network).

3.) On each machine, I store a lot of config files, that are made the same between each machine on purpose. Is there a Linux based server application that can push config files to machines from one central source, rather than me editing config files manually on each machine? It seems the more computers I get my hands on, the more work I have to do managing them and I'm trying to simplify my work a bit.

I know these questions may be a little on the strange side but I'm studying to become a Linux Administrator some day (I currently support Windows machines) and I'm trying to learn all I can by configuring systems in my lab.
1.)In your samba config you can set your resolve order for your names
   name resolve order = lmhosts host wins bcast #<-example

2.)For dns i would say look into bind and webmin (webmin provides a front end to easily configure a lot of services)

3.)What i would advise is using a repository service such as mercurial and checking in and out the config files.

---

### Post by jlacroix on 2011-08-22
> **skinnyquiver said:**
> 1.)In your samba config you can set your resolve order for your names
   name resolve order = lmhosts host wins bcast #<-example

2.)For dns i would say look into bind and webmin (webmin provides a front end to easily configure a lot of services)

3.)What i would advise is using a repository service such as mercurial and checking in and out the config files.
Thank you so much! 

I consider #1 solved now. I did as you suggested, then commented out a server in my hosts file, and samba browsing still worked. Before, if I commented out a server, I wouldn't be able to see any of the files underneath that share.

As for number 2 (DNS) that was also a brilliant suggestion, I installed webmin before but never thought to use it as a means to set up DNS. However, it still seems to be a bit above me. Is there an easy way to say something like "172.16.254.100 = saturn" to my entire network?

Finally, for number 3, I never used mercurial before. However, I started thinking that maybe it would be easier for me to write a shell script, or use Unison. However, with Unison I'm not sure how to tell it to sync only particular files, and I'd probably have to run Unison under root. Maybe I should go with a shell script?

---

### Post by skinnyquiver on 2011-08-22
> **jlacroix said:**
> Thank you so much! 

I consider #1 solved now. I did as you suggested, then commented out a server in my hosts file, and samba browsing still worked. Before, if I commented out a server, I wouldn't be able to see any of the files underneath that share.

As for number 2 (DNS) that was also a brilliant suggestion, I installed webmin before but never thought to use it as a means to set up DNS. However, it still seems to be a bit above me. Is there an easy way to say something like "172.16.254.100 = saturn" to my entire network?

Finally, for number 3, I never used mercurial before. However, I started thinking that maybe it would be easier for me to write a shell script, or use Unison. However, with Unison I'm not sure how to tell it to sync only particular files, and I'd probably have to run Unison under root. Maybe I should go with a shell script?

#2 I am unaware of any way to do that we use a custom script to manage dns here. It is based off of the mac address.

The best option for #3 would be puppet or cheif now that i think about it but that can get complex

---

