---
title: "why won't the HOSTS file work?"
date: 2011-08-23
forum: General Help
---

### Post by nrundy on 2011-08-23
I used gksu gedit /etc/hosts to modify the hosts file. But it won't work. 

Here's an example of what I put:

127.0.0.1     [www.facebook.com](www.facebook.com)


yet I can still connect to facebook.com with web browsers and when I ping facebook it does not come back with 127.0.0.1

Anybody know how to make this work?

---

### Post by An Sanct on 2011-08-23
This looks just like [the thing here.]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-block-unwanted-website-in-ubuntu-linux/") It has to work. did you restart the service (or the machine) afterwards?

---

### Post by nrundy on 2011-08-23
yeah, I tried restarting the computer afterwards.

It's wierd. I don't understand why its not working. I just tried it on Win7 and it worked fine. Why won't it work on ubuntu?

---

### Post by sanderj on 2011-08-23
Look at /etc/nsswitch.conf, especially the line with "hosts": it determines which lookup-method should be used first: /etc/hosts or DNS ...

---

### Post by dandnsmith on 2011-08-23
Sounds like the hosts file isn't being given priority.
I suggest that looking up dns resolution, and checking resolv.conf might reveal something.
I haven't got a system to hand on which I can check.

Looks like someone else got there while I was thinking.

---

### Post by mike555 on 2011-08-23
put this in host file (note spaces- you may need to use tab key)

# Block Facebook
127.0.0.1	 [www.facebook.com](www.facebook.com)
127.0.0.1 	facebook.com
127.0.0.1 	static.ak.fbcdn.net
127.0.0.1 	[www.static.ak.fbcdn.net](www.static.ak.fbcdn.net)
127.0.0.1	 login.facebook.com
127.0.0.1	 [www.login.facebook.com](www.login.facebook.com)
127.0.0.1 	fbcdn.net
127.0.0.1 	[www.fbcdn.net](www.fbcdn.net)
127.0.0.1 	fbcdn.com
127.0.0.1 	[www.fbcdn.com](www.fbcdn.com)
127.0.0.1 	static.ak.connect.facebook.com
127.0.0.1 	[www.static.ak.connect.facebook.com](www.static.ak.connect.facebook.com)

---

### Post by Habitual on 2011-08-23
> **nrundy said:**
> yeah, I tried restarting the computer afterwards.

It's wierd. I don't understand why its not working.

Clear your browser cache too?

---

### Post by nrundy on 2011-08-23
I have tried clearing my browser cache, yes.

@sanderj:  I checked /etc/nsswitch.conf
the hosts line read "hosts:  files dns"
so files is before dns.

@dandnsmith: resolv.conf shows my dns servers. not sure what I'm looking for here. 

this is a PITA

---

### Post by papibe on 2011-08-23
By any chance are you using Dnsmasq? or Do your router has enable Dnsmasq? (default if you are using DD-WRT)

Just a thought,
Regards.

---

### Post by mike555 on 2011-08-23
did you hit the "tab" key between the numbers and names? that is important....

---

### Post by hawthornso23 on 2011-08-23
Is your browser IPv6 enabled?

---

### Post by angry_johnnie on 2011-08-23
in my case, what worked was [this]("http://ubuntuforums.org/showthread.php?p=4622552").  post #8, to be more specific.

---

### Post by nrundy on 2011-08-24
> **papibe said:**
> By any chance are you using Dnsmasq? or Do your router has enable Dnsmasq? (default if you are using DD-WRT)

Just a thought,
Regards.

I don't think so. I don't even know what DNSmasq is. Is it something that is on by default?

---

### Post by nrundy on 2011-08-24
@Mike555: Yes, I hit the tab key after inputting 127.0.0.1

@Hawthornso: No, my system is only set for IPv4.

---

### Post by nrundy on 2011-08-24
> **angry_johnnie said:**
> in my case, what worked was [this]("http://ubuntuforums.org/showthread.php?p=4622552").  post #8, to be more specific.

my /etc/hosts.conf file shows exactly like post 8 of the thread you linked.

---

### Post by linkageless on 2011-08-24
I agree the most likely explanation is that the hosts file isn't being used so check the /etc/nsswitch.conf and /etc/host.conf

Try testing with another browser or another sanity check you can do is try ```
telnet www.facebook.com 80
```
You should see what IP has been resolved when it's 'Trying' to connect.

If another browser works, is it possible the browser is set to use a proxy?

---

### Post by nrundy on 2011-08-25
I wonder why this isn't working?

It's a mystery that's dogging me.

---

### Post by gmargo on 2011-08-25
> **mike555 said:**
> did you hit the "tab" key between the numbers and names? that is important....
From the **hosts(5)** man page: "Fields of the entry are separated by any number of blanks and/or tab characters."

BTW, mike555's facebook list from post #6, added to my /etc/hosts, worked immediately for firefox and command line.

---

### Post by nrundy on 2011-08-26
> **gmargo said:**
> From the **hosts(5)** man page: "Fields of the entry are separated by any number of blanks and/or tab characters."

BTW, mike555's facebook list from post #6, added to my /etc/hosts, worked immediately for firefox and command line.

I inputed the info precisely. 127.0.0.1 and then Tab key and then site.

I'm having the same problem over here:  [http://ubuntuforums.org/showthread.php?p=11190535#post11190535](http://ubuntuforums.org/showthread.php?p=11190535#post11190535)  A webpage is not displaying correctly. Some folks can replicate it. But many others cannot. Uggg!

---

### Post by augnix on 2011-09-28
This is a "feature":

[https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/736149](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/736149)

Depending on what resolver library your application uses, you may or not be checking /etc/nsswitch.conf or /etc/hosts.

The bind tools ( host, dig ) use libresov which does not bother checking nsswitch or hosts.

Google Chrome seems to check /etc/hosts.

If you run "strace" on the application, you can get a better idea of what it is doing for example:

strace -f -s 500 -o tmp host example.com

I hope that helps.

--Augie

---

### Post by nrundy on 2011-09-30
> **augnix said:**
> This is a "feature":

[https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/736149](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/736149)

Depending on what resolver library your application uses, you may or not be checking /etc/nsswitch.conf or /etc/hosts.

The bind tools ( host, dig ) use libresov which does not bother checking nsswitch or hosts.

Google Chrome seems to check /etc/hosts.

If you run "strace" on the application, you can get a better idea of what it is doing for example:

strace -f -s 500 -o tmp host example.com

I hope that helps.

--Augie

Hey, thanks so much for this. I really don't understand hardly anything you said, nor what is in that bug report. But it appears that Hosts is indeed not working by design. Kind of a bummer not being able to use it.

---

### Post by SeijiSensei on 2011-09-30
That bug report has nothing to do with the problem the OP has.  The bug submitter is complaining about the behavior of the "host" command which ignores, as it should, the /etc/hosts file.  The host command is used to query DNS servers and retrieve pertinent records.  It doesn't have anything to do with local name resolution.

@nrundy
I didn't see any answer to the question of whether you are using a proxy of some kind.  I'm using (K)ubuntu 10.10, and both /etc/nsswitch.conf and /etc/host.conf have the proper entries by default:

/etc/nsswitch.conf
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

/etc/host.conf
```
order hosts,bind
multi on
```

(In addition, the comment in /etc/host.conf says the order directive is only used by older versions of the C library.  I can confirm that it's not used in 10.10; I removed the order line in /etc/host.conf and could still ping hosts by their names in /etc/hosts.)

---

### Post by nrundy on 2011-10-01
> **SeijiSensei said:**
> That bug report has nothing to do with the problem the OP has.  The bug submitter is complaining about the behavior of the "host" command which ignores, as it should, the /etc/hosts file.  The host command is used to query DNS servers and retrieve pertinent records.  It doesn't have anything to do with local name resolution.

@nrundy
I didn't see any answer to the question of whether you are using a proxy of some kind.  I'm using (K)ubuntu 10.10, and both /etc/nsswitch.conf and /etc/host.conf have the proper entries by default:

/etc/nsswitch.conf
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

/etc/host.conf
```
order hosts,bind
multi on
```

(In addition, the comment in /etc/host.conf says the order directive is only used by older versions of the C library.  I can confirm that it's not used in 10.10; I removed the order line in /etc/host.conf and could still ping hosts by their names in /etc/hosts.)

No, I don't use a proxy. don't like proxys.

My intention was to use the hosts file to block certain websites. Since it's not working, perhaps there's a better way to do this? Any ideas?

---

