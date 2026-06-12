---
title: "Package manager trying to connect to wrong IP address"
date: 2009-08-25
forum: General Help
---

### Post by Hibbo on 2009-08-25
Hello hello,

For a while now, my package manager has not been working.  I've done some searching on here and played about a bit, and I noted that when I run it from the CLI I get 
```
 sudo apt-get update
0% [Connecting to 192.168.0.1 (192.168.0.1)]
```

This is not my IP address and I'm guessing it isn't where the repositories are!  I do use my laptop on a lot of different networks, so I'm guessing that this IP address may have once been a router I was connected to.  The preferences tab says 'direct connection to internet' and the /etc/apt/apt.conf file is empty, but it still tries to connect to this address.

What is going on?

Cheers

---

### Post by i.r.id10t on 2009-08-25
Something in /etc/hosts?  What DNS servers are you using?

---

### Post by running_rabbit07 on 2009-08-25
Are the proper repositories checked in the Software Sources menu?

---

### Post by Hibbo on 2009-08-25
> **i.r.id10t said:**
> Something in /etc/hosts?  What DNS servers are you using?

Hi,

I can't see any mention of 192.168.0.1 in there.

My primary DNS is 10.10.0.1 

I am currently on hotel WiFi.

When I am at home everything is set by DCHP (cable broadband), all other internet functionality is fine.

---

### Post by Hibbo on 2009-08-25
> **running_rabbit07 said:**
> Are the proper repositories checked in the Software Sources menu?

Yes.  I have also tried changing from the UK server to the main server, it still tries to connect to 192.168.0.1....... :confused:

---

### Post by Hibbo on 2009-09-20
Can anyone help with this or point me to a guide please?

This install is dead in the water if I can't get this working... :(

---

### Post by t0p on 2009-09-20
Have you got things set to use a proxy server?  Or has the hotel wireless you're using been set up to use a proxy?  That ip address is a non-public facing one, ie it belongs on a lan somewhere.  192.168.0.1 is the number I use for the ip address of my desktop computer in my home network.  It is *not* a public internet address.

---

### Post by Hibbo on 2009-09-20
I've told synaptec that it's a 'direct connection to the internet'.  I don't think I've got a proxy set up anywhere, as all other internet access is fine.

I'm aware that 192.168.0.1 is not a public IP address, but how do I change things so synaptec connects to the right place?

Cheers.

---

### Post by Hibbo on 2009-09-22
How do I get apt to connect to the correct place?

C'mon people, I'm in my hour of need here!

If I can't get this working then I think I'm going to have to do a complete reinstall....... :(

---

### Post by Hibbo on 2010-05-16
Can anyone help me with this?  I've searched and searched and checked everything that's been suggested, but it still won't connect :(

```
sudo wget http://superb-east.dl.sourceforge.net/sourceforge/rarcrack/rarcrack-0.2.tar.bz2
--2010-05-17 02:31:29--  http://superb-east.dl.sourceforge.net/sourceforge/rarcrack/rarcrack-0.2.tar.bz2
Connecting to 192.168.0.1:8080... failed: No route to host.

```

---

### Post by jeremyMb on 2010-05-28
Try going to the System>Preferences>Network proxy and select  'Do Direct Connection' selection if you are not using a proxy server. If you are using a proxy server select either of the remaining two. After that click on 'Apply System-Wide' button. Try to reload the package manager again.

---

### Post by Ter0 on 2010-06-27
I'm having similar problems.. at home location I cannot get apt-get to work..
apt-get tries to connect some 192.168... address, which is not "in range" of my home network address.

I'ma n00b yes.. ;)

---

### Post by the_pod on 2012-09-14
same issue.  Extremely frustrating.

Hoping this has been solved somewhere....

fwiw, mine is trying to connect to 192.168.1.1, which is my home IP range and where initial install was performed.  

 But I'm not there.  Not sure why it would be looking there, or why this would be "stuck".

Sigh.

---

