---
title: "Installing an Instant Messenger"
date: 2009-12-11
forum: General Help
---

### Post by bevboy0223 on 2009-12-11
Sigh.  Trying very hard to install empathy or pidgin or any other instant messenger client, and nothing works.  I cannot connect.  

At best I get a network error when I try to connect with my yahoo id in empathy.  I know what my id and password are.  I can log on to yahoo.ca with the id and password and I connect.  But I don't know what the server is supposed to be under the advanced options.  I have no idea what the port number is supposed to be.  And I don't know if knowing those things will even fix the problem I am having.  

Is there any documentation on how to configure this software that will explain everything I need to know?  

Thanks.

Bev
:(

---

### Post by Leppie on 2009-12-11
I don't know empathy, but pidgin should be able to connect to yahoo without prompting you for the server. Are you trying to connect from home, or are you in a business environment (hence, most probably behind a firewall or proxy)?

If you don't have pidgin already installed, you can install it using synaptic or in a terminal:
```
$sudo apt-get install pidgin
```

---

### Post by bevboy0223 on 2009-12-11
I tried pidgin, kopete, and several other im clients.  Nothing has worked.  

I am at home.  On a wireless network.  I try to connect to my yahoo id.  It just sits there.  It will not connect.  I see the advanced stuff about servers and ports.  Do I leave those blank?  But that won't make a difference either.  

Is there a really fundamental basic list of things I have to do with a given im client?0

Been working on this for hours.  Very tired.  Very frustrated.

Bev

---

### Post by Leppie on 2009-12-11
Usually when I start using pidgin on a new machine, I only select the connection type (yahoo in your case), put in my userid and password and connect.
Have you tried deleting the profile and recreating it?
Otherwise could you attach some screen shots?

---

### Post by bevboy0223 on 2009-12-11
Just reinstalled pidgin.  My yahoo id is still there.  It says it is disabled, whatever that means.  I try to re-enable it.  It takes me to another screen.  Now it says the account is locked, whatever that means.  I can use the account on yahoo.ca.  I can use it on my blackberry.

---

### Post by Leppie on 2009-12-11
If this the first time you're trying to connect with yahoo messenger from home using wireless, it may be that you have to unblock port 5050 on it.

Also, in pidgin you only need your id (the part before the @) and not the whole email address.

---

### Post by bevboy0223 on 2009-12-11
Now we're getting somewhere!!  How do I unblock or open up a port?  Is that through my wireless router admin software?

---

### Post by fluffman86 on 2009-12-11
sounds like a problem with trying to use the .ca address. Sign up for a new addy on .com and see what happens. 

Also, what version of Ubuntu are you using? Over the summer, yahoo changed their servers and old versions of empathy, pidgin, etc. can't talk to them. If you are using Ubuntu 9.04 (Jaunty Jackalope) or earlier, then you need to check for updates to pidgin to make sure that this bug is fixed.

for the ports issue: [http://www.portforward.com](http://www.portforward.com)

---

### Post by Leppie on 2009-12-11
> **bevboy0223 said:**
> How do I unblock or open up a port?  Is that through my wireless router admin software?

Yes, you have to access the wireless router. Often ports can be enabled under a "services" menu. Some routers already have a whole bunch of apps predefined there.

---

### Post by joes7 on 2009-12-11
Download Wine. Afterwards, install any MSN, say Windows Live Messenger.
```

Wine > [http://www.winehq.org](http://www.winehq.org)
Windows Live Messenger > [http://www.get.live.com](http://www.get.live.com)

```

---

### Post by bevboy0223 on 2009-12-11
I opened up port 5050 in my wireless router.  I am running 9.10.  I downloaded pidgin moments ago through the resource center.  

It still doesn't work.  It says the account is disabled.  I try to enable it in pidgin (version 2.6.2), and it says the account is disabled.  Repeat.  

I was just im'ing with my cousin through the yahoo.ca website.  Worked like a charm.  Why on earth can't i configure something that everyone says is dead simple like pidgin?  I am beyond frustrated now.  

Yes, I logged off my yahoo id before i left the yahoo website.

Bev

---

### Post by bevboy0223 on 2009-12-11
It still doesn't work.  How do I open up a port?  It's asking me to  type in the application name.  I just type in "pidgin"?  Then, port 5050?  I have zero experience in doing this and can't find any documentation anywhere.  

Help!

Thanks.

Bev

---

### Post by Leppie on 2009-12-11
> **bevboy0223 said:**
> How do I open up a port?  It's asking me to  type in the application name.  I just type in "pidgin"?  Then, port 5050?

That's basically it.
What userid are you using in pidgin? You need to leave the @yahoo.ca / @ymail.ca part (e.g. use bevboy0223 if your account is bevboy0223 at yahoo dot ca).

---

### Post by bevboy0223 on 2009-12-11
Still not working.  Been working on this for hours.  Feel like a complete fool as everyone says this is an easy thing to do.  

Here's the screen shot from my router.  

Thanks for putting up with me.

Bev

---

### Post by fluffman86 on 2009-12-12
no, not port triggering, port forwarding.  There's a difference.

Do basically the same thing, but you want to forward the port to your internal ip.  Right click network manager > connection information to find out what it is.

---

### Post by bevboy0223 on 2009-12-12
My gosh, I think it worked that time!!!  I can't believe it.  

My cousin is offline now, but at least I see that he is offline.  

Thank you for your help, everyone.  

I just need more people to chat with now!!

Bev

---

### Post by Leppie on 2009-12-12
So what did the trick for you in the end? (your solution might help others with the same kind of problem)

---

