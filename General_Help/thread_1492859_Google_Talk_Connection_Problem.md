---
title: "Google Talk Connection Problem"
date: 2010-05-25
forum: General Help
---

### Post by meetParantapa on 2010-05-25
I am using **Ubuntu 10.04**. I tried to connect with **Google Talk account** from** Pidgin** (following instructions available in this forum). But connection failed. Then I tried the same using** Empathy**, **Kopete** and** Psi**. But none of them worked either.
I cannot figure out where the problem is.
Thank you in advance.

---

### Post by Brandon Williams on 2010-05-25
It would help if you could post some details about what your configuration looks like.

In the mean time, the important details from mine are:

    Basic/Login Options/Protocol: XMPP
    Basic/Login Options/Domain:   gmail.com
    Advanced/Require SSL/TLS:     checked
    Advanced/Connect port:        5222
    Advanced/Connect server:      talk.google.com

Some users have firewall problems that prevent using outbound port 5222. They seem to be able to get it working with:

    Advanced/Force old (port 5223) SSL: checked
    Advanced/Connect port: 443

---

### Post by fragos on 2010-05-25
Empathy has a problem with the Google Talk protocol but I can't see why. Adding as a Jabber account does work and you still only need your Google login ID (your Gmail address), and your password.

---

### Post by meetParantapa on 2010-05-26
> **Brandon Williams said:**
> It would help if you could post some details about what your configuration looks like.

In the mean time, the important details from mine are:

    Basic/Login Options/Protocol: XMPP
    Basic/Login Options/Domain:   gmail.com
    Advanced/Require SSL/TLS:     checked
    Advanced/Connect port:        5222
    Advanced/Connect server:      talk.google.com

Some users have firewall problems that prevent using outbound port 5222. They seem to be able to get it working with:

    Advanced/Force old (port 5223) SSL: checked
    Advanced/Connect port: 443

I tried with configurations exactly what you have mentioned. I tried with port 5223 and 443 also. But still it is giving network error.

---

### Post by meetParantapa on 2010-05-26
> **fragos said:**
> Empathy has a problem with the Google Talk protocol but I can't see why. Adding as a Jabber account does work and you still only need your Google login ID (your Gmail address), and your password.

I tried to connect using Jabber account also. But I am not sure whether my configurations were correct or not. Will you please let me know the detailed configuration?
Thanks

---

### Post by fragos on 2010-05-26
> **meetParantapa said:**
> I tried to connect using Jabber account also. But I am not sure whether my configurations were correct or not. Will you please let me know the detailed configuration?
Thanks

Make sure Enabled is checked ON

Under Empathy Advanced (these were the defaults for supplied Jabber)
Priority: 0
Port: 5222
All others off or blank

---

### Post by meetParantapa on 2010-05-27
> **fragos said:**
> Make sure Enabled is checked ON

Under Empathy Advanced (these were the defaults for supplied Jabber)
Priority: 0
Port: 5222
All others off or blank

Sorry, it did not work. Same problem is continuing.

---

### Post by fragos on 2010-05-27
Not sure where to go from here. My system works with the very simple configuration setting I mentioned. I made none of the other configuration changes you mentioned.

---

### Post by meetParantapa on 2010-05-27
Actually it was working on ubuntu 9.10 in my previous laptop which was an HP. Recently I bought an DELL Inspiron 1464 and installed Ubuntu 10.04. Here I have installed several chatting softwares (Pidgin (comes by default), Empathy, Kopete, PSI) but none of them are able to connect to my Google Talk account.

---

### Post by phaseman on 2010-08-29
Hello everyone, this is my first post :).
I had the same problem up until 10 mins a go.
I use Ubuntu 10.04 LTS and Empathy 2.30.2 (for IM ). The problem was that I could not connect to my gtalk account using Empathy (always getting message : network error).
This is how "solved" it :

login ID : full gmail email address   
password : *gmail* [I]password
[/I][B]advanced
[/B]encryption required (TLS/SSL) : unchecked
ignore SSL certificate errors : unchecked
Resourse : blank (nothing)
Priority: 1
Server : talk.google.com
Port :443
Use old SSL : **checked**

Hope this helps ;)

Regards,
Marko

---

### Post by Ravenrip on 2011-01-18
Hi Guys,

I also experienced the same...

dont change anything...all you have to do is use complete gmail ID as username...like [email]xyz@gmail.com[/email],if you enter xyz it wont connect

---

### Post by saheel.godhane on 2011-03-13
thanks phaseman...i was having the same problem and it got solved in seconds after using the settings suggested by you...especially i changed the port no.

thanks a lot again...

---

