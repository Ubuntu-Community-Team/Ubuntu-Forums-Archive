---
title: "Snort problem - please help"
date: 2011-10-11
forum: General Help
---

### Post by boeckelr on 2011-10-11
Hi everyone,

I am trying to install Snort 2.9.1.1 on Ubuntu 32bit 10.043.  This is something I have done literally dozens of times.

However, this time, for whatever reason, I am running into a couple of big problems.  

First of all, Snort and its helper program DAQ require libpcap>=1.0.  The problem is that Ubuntu installs by default libpcap0.8.  

I have tried to remove libpcap0.8, and then install by source libpcap-1.0.0 - but I cant get it to work.

I am not a Linux expert, but I have been able to get around and get things done in the past.

NOTE:  This problem occurs in other distros too - I have tried CentOS and FC15 with the same issues.

BTW I have read EVERY Snort install guide that I have been able to get ahold of...and have posted to Snort listserv.  

Could someone please go thru and tell me how to successfully get rid of libpcap0.8, and then put libpcap-1.0.0 into Ubuntu 10.043 32bit? 

I also know that it is possible to keep libpcap0.8 installed....but then also compile libpcap-1.0.0 in a different place like /opt, and then point the programs that need it like DAQ and Snort to it - someone from the Snort listserv showed me how - but it doesnt work because his syntax was wrong.  If that is an easier solution, then please feel free to show me that, 

This is driving me crazy and wasting alot of time.  I need to get this install running.  

Thank you so much,
Mike

---

### Post by bodhi.zazen on 2011-10-12
If you are going to run snort, what is wrong with apt-get install snort ?

If you are going to compile from source, most often the problem is with dependencies. So it may not be so easy to simply rip out libpcap and compile 1.0 from source.

At any rate, if you want help you will need to start posting error messages.

If you are installing packages outside the repositories you will be on your own or on the snort mailing list.

---

### Post by Dangertux on 2011-10-12
Mike,

This should help you, I tested this in a 10.04.3 LTS Server VM 32 bit. I'm not sure why you're getting libpcap errors it compiled just fine with the stock libpcap libs, the only thing I can think is you might not have had libdumbnet installed. Hopefully this remedies your situation , like I said I tested it , but if you get any errors with this procedure please post back .

[http://dangertux.wordpress.com/2011/10/12/compiling-snort-2-9-1-1-daq-0-62/](http://dangertux.wordpress.com/2011/10/12/compiling-snort-2-9-1-1-daq-0-62/)

Good luck :-)

---

### Post by boeckelr on 2011-10-12
Hi Dangertux,

Thank you so much for going to the trouble of setting it up yourself.  Sometimes I am amazed at how nice and helpful some of the people on forums like this can be, and this is one of those times.

I am going to start working on this after lunch and I will definitely get back to you once I get it set up.  

Take care,
Mike

---

### Post by Dangertux on 2011-10-12
> **boeckelr said:**
> Hi Dangertux,

Thank you so much for going to the trouble of setting it up yourself.  Sometimes I am amazed at how nice and helpful some of the people on forums like this can be, and this is one of those times.

I am going to start working on this after lunch and I will definitely get back to you once I get it set up.  

Take care,
Mike

Mike,

No problem, I hope it helps -- the biggest issue I encountered was the libdumbnet-dev dependency,  installing it via the Snort documentation's  (from source) method did not work, so I found installing it from repos solved the build errors I was getting.

Hopefully this works out, if not I'm sure we can figure out what is up :-)

Regards,
Adam

---

