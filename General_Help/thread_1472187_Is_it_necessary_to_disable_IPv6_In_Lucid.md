---
title: "Is it necessary to disable IPv6 In Lucid?"
date: 2010-05-04
forum: General Help
---

### Post by inameiname on 2010-05-04
Okay so on WebUpd8 website, ([http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)), I found a way to disable IPv6 and I was hoping to get a little more of an understanding of if I should or not from comments there, but unfortunately I haven't gotten enough to say let's do that. So I figured I might get a better understanding on here.

I am not very familiar with IPv6, but to my understanding its a newer thing that's rarely found currently with ISPs, but can be a security issue now.

So should I disable it?

---

### Post by plucky on 2010-05-04
> **inameiname said:**
> Okay so on WebUpd8 website, ([http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)), I found a way to disable IPv6 and I was hoping to get a little more of an understanding of if I should or not from comments there, but unfortunately I haven't gotten enough to say let's do that. So I figured I might get a better understanding on here.

I am not very familiar with IPv6, but to my understanding its a newer thing that's rarely found currently with ISPs, but can be a security issue now.

So should I disable it?

I think the default for ipv6 is ignore.If you right click on the network icon and select **edit connections**,then select your connection and edit,the setting for ipv6 should say **ignore**.

Good Luck

---

### Post by inameiname on 2010-05-04
Actually it's enabled. At least for me. I did a clean install of Lucid, and using what that site gave me: 
cat /proc/sys/net/ipv6/conf/all/disable_ipv6

1 being disabled, and 0 being enabled, mine was 0.

But thanks for the info on how to check that using a gui, not the terminal. :)

---

### Post by 3rdalbum on 2010-05-04
Ubuntu 10.04's support lifetime is 3 years on the desktop and 5 years on the server. By the end of its support lifetime, we must all be using IPv6 otherwise there won't be enough IP address space for everyone.

---

### Post by inameiname on 2010-05-04
Oh I see. So with that in mind, you're saying it's best to just keep it enabled and be done with it? Despite what I read others say about how keeping it enabled slows their connection down, I don't seem to find anything slower, so really it's just the security issue I guess.

---

### Post by Linuxforall on 2010-05-04
Actually its not causing any slowdown issues like before and it can also be disabled in firefox as well.

---

### Post by inameiname on 2010-05-04
Oh so it can just be disabled in firefox and left enabled in ubuntu as it is and that's that? If so, I know how to do that in about:config in firefox.

---

### Post by psylem on 2010-07-13
> **3rdalbum said:**
> Ubuntu 10.04's support lifetime is 3 years on the desktop and 5 years on the server. By the end of its support lifetime, we must all be using IPv6 otherwise there won't be enough IP address space for everyone.

Ever heard of NAT? The world will keep dragging it's feet with IPv6 because switching over costs money and in reality we don't actually need it. Some IP addresses host hundreds of thousands of websites perfectly well. The only thing I can think of that you really need a unique IP address for is SSL.

---

### Post by dcstar on 2010-07-14
> **3rdalbum said:**
> Ubuntu 10.04's support lifetime is 3 years on the desktop and 5 years on the server. By the end of its support lifetime, we must all be using IPv6 otherwise there won't be enough IP address space for everyone.

I've been hearing panic claims about IP4 addresses running out since about 1998.

---

### Post by WorMzy on 2010-07-14
> **dcstar said:**
> I've been hearing panic claims about IP4 addresses running out since about 1998.

Hah, I was about to say that. :P

---

### Post by 3rdalbum on 2010-07-14
> **psylem said:**
> Ever heard of NAT?

Yes, I'm familiar with NAT. Have you heard about mobile broadband and mobile phones? Those are one IP address per person.

---

