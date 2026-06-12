---
title: "What step do I take next?"
date: 2011-11-26
forum: General Help
---

### Post by bignixs on 2011-11-26
I have followed this tutorial on how to Set Up and Configuring a DNS Server in Ubuntu and I got stuck on part 4 towards the end .


Here is the tutorial :

[http://www.youtube.com/watch?v=H8phIakC-Jk&feature=related](http://www.youtube.com/watch?v=H8phIakC-Jk&feature=related)


when I use the command nslookup myhostname I get 

server: 192.168.1.110
address: 192.168.1.110 #53


Non-authoratative answer:

Name: myhostname
Address: 184.106.31.166

Name: myhostname
Address: 204.232.162.92

What am I doing wrong? How would I point my nameservers from another host to my ubuntu's nameservers?

---

### Post by bluexrider on 2011-11-26
never have liked u-tube tutorials so no help from here

This may help [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by blueridgedog on 2011-11-26
Other than posting a link to a tutorial, can you summarize what you are trying to do and what is not working?

---

### Post by bignixs on 2011-11-26
Ok, can anyone see this?


[http://bizguys.5-on-it.com/](http://bizguys.5-on-it.com/)

If so then please post what it says.

If you cannot see then I will answer your questions

---

### Post by uRock on 2011-11-26
Your link is broken.

---

### Post by oldtimer7777 on 2011-11-26
Don't accept 3rd party requests. Flag them if they keep this up for much longer.

> **bignixs said:**
> Ok, can anyone see this?


[http://bizguys.5-on-it.com/](http://bizguys.5-on-it.com/)

If so then please post what it says.

If you cannot see then I will answer your questions

---

### Post by bignixs on 2011-11-27
> **uRock said:**
> Your link is broken.

Hi, I am trying to set up my Ubuntu server correctly, and by broken you mean you cannot see? If so then how would I fix this?

---

### Post by lisati on 2011-11-27
Is your website on a dynamic IP address by any chance? If so, you might need to update the DNS records that point to it.

---

### Post by bignixs on 2011-11-27
> **lisati said:**
> Is your website on a dynamic IP address by any chance? If so, you might need to update the DNS records that point to it.


I am using 192.168.1.110

---

### Post by lisati on 2011-11-27
> **bignixs said:**
> I am using 192.168.1.110

That won't work for us mere mortals outside your network. Your link was broken when I checked.

---

### Post by bignixs on 2011-11-27
> **lisati said:**
> That won't work for us mere mortals outside your network. Your link was broken when I checked.


Ok, I tried to configure my router to user port forwarding, not sure if it was a success, I can now access the server at:

[http://96.41.82.107/](http://96.41.82.107/)

Are you able to see or is it still blank? If you can see text then please copy and paste the text in your post as a verification.

Should I do DMZ or ?

I can screenshot my modems/routers config if you cannot view.

I asked my current host(not connected to my home server) and they can tell me what text appears, so I know they can see it. But I asked someone else and they said they get a blank page and cannot connect error, so I do not know if it works.

---

### Post by oldtimer7777 on 2011-11-27
Never accept a 3rd party request anywhere on the Internet like this one.

You are asking for trouble for yourselves if you do.   

There are test forums dedicated to just this sort of thing they are trying to do, but they are in the wrong place for this. Sorry.

> **bignixs said:**
> Ok, I tried to configure my router to user port forwarding, not sure if it was a success, I can now access the server at:

[http://96.41.82.107/](http://96.41.82.107/)

Are you able to see or is it still blank? If you can see text then please copy and paste the text in your post as a verification.

Should I do DMZ or ?

I can screenshot my modems/routers config if you cannot view.

I asked my current host(not connected to my home server) and they can tell me what text appears, so I know they can see it. But I asked someone else and they said they get a blank page and cannot connect error, so I do not know if it works.

---

### Post by bignixs on 2011-11-27
> **oldtimer7777 said:**
> Never accept a 3rd party request anywhere on the Internet like this one.

You are asking for trouble for yourselves if you do.   

There are test forums dedicated to just this sort of thing they are trying to do, but they are in the wrong place for this. Sorry.

This is a help site right? Shouldn't you be helping rather than annoying? You could have told me to post in the test forums you are making this very difficult, I am supposed to be receiving help *sigh* ](*,)


Anyways here are my router/modem settings Any help is appreciated, I just want to get this ting set up:

[IMG]http://www.prohosta.com/port2.png[/IMG]

[IMG]http://www.prohosta.com/port.png[/IMG]

---

### Post by oldtimer7777 on 2011-11-27
Cisco, nice router..   They have a tech support phone number to help you get this configured, and they can even ping it for you to test it.

Free, better, and precise. 

> **bignixs said:**
> This is a help site right? Shouldn't you be helping rather than annoying? You could have told me to post in the test forums you are making this very difficult, I am supposed to be receiving help *sigh* ](*,)


Anyways here are my router/modem settings Any help is appreciated, I just want to get this ting set up:

[IMG]http://www.prohosta.com/port2.png[/IMG]

[IMG]http://www.prohosta.com/port.png[/IMG]

---

### Post by bignixs on 2011-11-27
> **oldtimer7777 said:**
> Cisco, nice router..   They have a tech support phone number to help you get this configured, and they can even ping it for you to test it.

Free, better, and precise.


they charge $30-$75 per phone call I believe, was going to call them yesterday, but did not want the charge

---

### Post by oldtimer7777 on 2011-11-27
> **bignixs said:**
> they charge $30-$75 per phone call I believe, was going to call them yesterday, but did not want the charge

When someone purchases a router like the one you are running, they can call the free tech support phone number that is listed on their web site, and they will provide you with a real person to help walk you through the process of getting that configured correctly.  Try to speak with someone in Level II tech support at Cisco, if at all possible. They can tell you what you want to do very quickly.

---

### Post by bignixs on 2011-11-27
> **oldtimer7777 said:**
> When someone purchases a router like the one you are running, they can call the free tech support phone number that is listed on their web site, and they will provide you with a real person to help walk you through the process of getting that configured correctly.  Try to speak with someone in Level II tech support at Cisco, if at all possible. They can tell you what you want to do very quickly.


Ok, thanks will do. So I assume my current settings are incorrect?

---

### Post by bignixs on 2011-11-27
> **oldtimer7777 said:**
> When someone purchases a router like the one you are running, they can call the free tech support phone number that is listed on their web site, and they will provide you with a real person to help walk you through the process of getting that configured correctly.  Try to speak with someone in Level II tech support at Cisco, if at all possible. They can tell you what you want to do very quickly.

According to them I have it configured correctly, I had a few friends test and they said it was good, but now how would I install a SSL?

---

### Post by oldtimer7777 on 2011-11-27
> **bignixs said:**
> According to them I have it configured correctly, I had a few friends test and they said it was good, but now how would I install a SSL?

This is will get you up-to-date on that:

[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

and 

[https://wiki.auckland.ac.nz/display/BeSTGRID/Enabling+SSL+on+Apache2++%28Ubuntu+10.10%29](https://wiki.auckland.ac.nz/display/BeSTGRID/Enabling+SSL+on+Apache2++%28Ubuntu+10.10%29)

---

### Post by bignixs on 2011-11-27
> **oldtimer7777 said:**
> This is will get you up-to-date on that:

[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

and 

[https://wiki.auckland.ac.nz/display/BeSTGRID/Enabling+SSL+on+Apache2++%28Ubuntu+10.10%29](https://wiki.auckland.ac.nz/display/BeSTGRID/Enabling+SSL+on+Apache2++%28Ubuntu+10.10%29)


ok thank you

---

### Post by oldtimer7777 on 2011-11-27
> **bignixs said:**
> ok thank you

You are welcome and make sure to mark this thread as solved when you are done here.

---

### Post by bignixs on 2011-11-27
> **oldtimer7777 said:**
> This is will get you up-to-date on that:

[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

and 

[https://wiki.auckland.ac.nz/display/BeSTGRID/Enabling+SSL+on+Apache2++%28Ubuntu+10.10%29]("https://wiki.auckland.ac.nz/display/BeSTGRID/Enabling+SSL+on+Apache2++%28Ubuntu+10.10%29")

In this tutorial they are self signing, how would I put in my geotrust signed info

[https://wiki.auckland.ac.nz/display/BeSTGRID/Enabling+SSL+on+Apache2++%28Ubuntu+10.10%29](https://wiki.auckland.ac.nz/display/BeSTGRID/Enabling+SSL+on+Apache2++%28Ubuntu+10.10%29)

Just seen your post and will do

---

