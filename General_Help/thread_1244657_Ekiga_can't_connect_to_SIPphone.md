---
title: "Ekiga can't connect to SIPphone"
date: 2009-08-19
forum: General Help
---

### Post by onlineapps on 2009-08-19
I'm having a real issue setting up Ekiga with my SIPphone.com (Gizmo5) account.

I set up Ekiga to use the following fields:

Name: onlineapps
Registrar: proxy01.sipphone.com (I also tried proxy01.sipphone.com:5060)
User: 1747******* (also tried onlineapps, my username)
Authentication User: 1747******* (also tried onlineapps, my username)
Password: blah (no, that's not my real password ;) )
Timeout: 3600
Enable Account: <checked>

Ekiga reports that my status is "Registered".

However, when I call "Echo test" (sip:500@ekiga.net) or "Conference room", it picks up for about a split second, then hangs up and reports in the status bar, "Call completed". Ekiga also didn't detect an incoming call.

Anyone have any idea what's wrong?

Ekiga's log: [http://pastebin.com/f45b54a0e](http://pastebin.com/f45b54a0e)

---

### Post by jonobr on 2009-08-19
hello

the only way to be really sure whats going on is to do a trace of the call.

Assuming the registration is working, then what you could do is capture a network trace as follows

```
sudo tcpdump -w trace.pcap -i any -s 1600 port 5060
```

hit enter,

make a call, when it drops,
stop the trace, you should have a file called trace.pcap.
If you could post it here it could show whats wrong.

---

### Post by onlineapps on 2009-08-19
I attached trace.pcap.zip. Thanks.

---

### Post by jonobr on 2009-08-20
Hello

The trace was very useful

If you download a program called wireshark from synpatic you can see whats going on your self.

Heres what I see,

You issue the invite, (thats the request to make a call)
The proxy returns with an error 407 which and you send an ack (acknowledgement) to the proxy.

The document that will help you out here is RFC3261 and tells you how the whole thing works,
its kind of detailed and a lot of reading but the most applicable section for you is this


> 21.4.8 407 Proxy Authentication Required

   This code is similar to 401 (Unauthorized), but indicates that the
   client MUST first authenticate itself with the proxy.  SIP access
   authentication is explained in Sections 26 and 22.3.

   This status code can be used for applications where access to the
   communication channel (for example, a telephony gateway) rather than
   the callee requires authentication.


What this means is that the sip client registers with the registrar ok.
It sends its info and the registrar registers the device (your initial post indicates this works). If registration failed, you would have gotten an error 401.

Then it goes to place a call. Here it uses the proxy to place the call.
The proxy receives the call info and then asks you to authenticate again to place the call( thats what the 407 means)
You send back an ack with the authentication info, i see that in the packet,

The problem is, nothing seems to happen after that, there are no more packets.
Its like the proxy possible drops the call.

This makes me think that the proxy is not happy with your authentication information, and makes me think either the registration didnt really work in the first place, or the proxy is not setup with your info to correctly authenticate you.

The other piece of info is that calls cant reach you, thats almost an indication that registration is incorrect.


To elimnate point 1, I would ask you to shut down Ekiga, start your trace again.
Start Ekiga, and then make a call. Stop the trace and repost.

Thanks

---

### Post by onlineapps on 2009-08-20
Update: At Launchpad, one of the developers told me that unless you register with ekiga.com, you won't be able to use the echo service :P

---

### Post by jonobr on 2009-08-20
You know what,

its a bad day you dont learn something new,

Thanks for the information.

I had not thought of this as anything other then a calling problem

---

