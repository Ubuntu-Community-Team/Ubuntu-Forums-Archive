---
title: "Tunnel X through gateway"
date: 2009-07-21
forum: General Help
---

### Post by Perplexed555 on 2009-07-21
Hi,

I am trying to tunnel from my home computer, through a gateway, to a third computer.

I want to forward X11 so that I can open programs installed on the third computer on my home computer. For general context, the third PC is at work and is definitely set-up appropriately as I am aware other people do this.

I can ssh on the command line to get to the third computer without problem, apart from X11 forwarding.

I have tried the steps described here:
[http://www.cyberciti.biz/faq/proxycommand-ssh-session-internal-host-through-gateway/](http://www.cyberciti.biz/faq/proxycommand-ssh-session-internal-host-through-gateway/)

But the nc file doesn't exist in that directory (am running jaunty 9.04).

Sorry if there are answers elsewhere, but I'm new to this and don't even know if there is a proper term for what I am trying to achieve that I can search for.

Thanks in advance.

---

### Post by Perplexed555 on 2009-07-22
Bump.

> **Perplexed555 said:**
> Hi,

I am trying to tunnel from my home computer, through a gateway, to a third computer.

I want to forward X11 so that I can open programs installed on the third computer on my home computer. For general context, the third PC is at work and is definitely set-up appropriately as I am aware other people do this.

I can ssh on the command line to get to the third computer without problem, apart from X11 forwarding.

I have tried the steps described here:
[http://www.cyberciti.biz/faq/proxycommand-ssh-session-internal-host-through-gateway/](http://www.cyberciti.biz/faq/proxycommand-ssh-session-internal-host-through-gateway/)

But the nc file doesn't exist in that directory (am running jaunty 9.04).

Sorry if there are answers elsewhere, but I'm new to this and don't even know if there is a proper term for what I am trying to achieve that I can search for.

Thanks in advance.

---

### Post by Perplexed555 on 2009-07-25
> **Perplexed555 said:**
> Bump.

```

home> xhost +localhost
home> ssh -C -R 6099:localhost:6000 tom@red
Password: ********
red> ssh -C -R 6099:localhost:6099 tom@blue
Password: ********
blue> ssh -C -R 6099:localhost:6099 tom@black
Password: ********
black> export DISPLAY=[127.0.0.1:99]("http://127.0.0.1:99/")
black>

```

Tried this sort of thing, but no joy.

Any pointers?

---

### Post by Perplexed555 on 2009-07-27
If no pointers, can anyone suggest terms to search Google with that might direct me towards some useful information? Is there some sort of jargon for this?

Thanks.

---

### Post by zarqoon on 2009-07-27
I have done this by using the -Y option while connecting.
```
 ssh -Y user@host 
```
-X should work too but in some cases does not.

I did not have to export anything a application started would just appear on my local x screen.

---

### Post by Perplexed555 on 2009-07-27
> **zarqoon said:**
> I have done this by using the -Y option while connecting.
```
 ssh -Y user@host 
```-X should work too but in some cases does not.

I did not have to export anything a application started would just appear on my local x screen.

Hi,

Thanks for the response.

Having had a read of man ssh, I don't think -Y will help in this situation. I don't think X11 is enabled/available on the gateway, so I must push traffic through from my computer to the destination computer, tunneling through the gateway to forward X11.

...I think. But, I thought my attempt shown would do something like this. But, it didn't work.

---

### Post by zarqoon on 2009-07-27
I used it to connect to a machine at my university and i had to hop over another host too. That worked just fine. Of course if this middle host has no x server installed that could be a problem. The Gateway host I used has no x server running, just checked that. But i think it has all the libs installed.

If i just do this
```

ssh -Y user@gatewayhost

```
ann then from there
```

ssh -Y user@workhost

```
I can start whatever i want and get the window on my screen.
it does not work if I use -X

Just read the link you posted have you tried to make a tunnel like the last guy in the comments proposed?
```

ssh -fgNL 2202:somelan.example.com:22 user@gateway.example.com
ssh -Xp 2202 user@localhost

```

---

### Post by Perplexed555 on 2009-07-28
```

ssh -Y user@gatewayhost
ssh -Y user@workhost

```This doesn't work for me - it was the first thing I tried. :)

```

ssh -fgNL 2202:somelan.example.com:22 user@gateway.example.com
ssh -Xp 2202 user@localhost

```I tried this, but it tells me the address is already in use.

---

### Post by zarqoon on 2009-07-28
Have you tried using some other port?
just use some random high number other than 2202

---

### Post by Perplexed555 on 2009-07-29
> **zarqoon said:**
> Have you tried using some other port?
just use some random high number other than 2202

Hm yes. All the ones I've tried (randomly chosen, more than a dozen) have told me the bind address is already in use.

Starting to think I may as well just SCP files, locally edit them, then put them back through the gateway. I guess this may be a better solution anyway considering it's a shared gateway and tunneling large amounts of X11 data is going to clog it up a bit.

But purely from an academic point of view, I'd be interested to know if what I was previously trying to achieve is possible...

---

