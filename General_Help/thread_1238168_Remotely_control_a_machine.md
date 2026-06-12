---
title: "Remotely control a machine"
date: 2009-08-12
forum: General Help
---

### Post by porchrat on 2009-08-12
Hi all, long time no post :)

I'm looking for ideas on the best way to remotely control a machine.

I was thinking of using something like VNC through SSH, but I have no experience with VNC and am not sure if it is the right way to go. I would also like to have SSH so as to avoid snooping as I may end up sending sensitive information to the remote machine.

Does anyone have any suggestions?

I would like to be able to remotely control the desktop and not just have shell like SSH gives you. This is mainly for the purpose of updating the machine periodically.

Also my internet connection is rather slow (384kbps down and 64kbps up) and I was wondering if that would be sufficient for VNC to operate through. It seems to work fine for SSH, but I imagine there is a far larger amount of data to be transferred when graphics are involved and I don't know what that will do to response times.

Again, any past experiences or suggestions would be most appreciated.

---

### Post by P4man on 2009-08-12
You already have SSH set up? Then you can have your cake and eat it :)

```
ssh -c -X user@host
```

Then you just start any graphical program you want on the host, eg nautilus. If you want the entire desktop, type "startx" (I think).

---

### Post by t0p on 2009-08-12
If you want to do file transfers and other file management stuff, you can use the graphical file manager over ssh by going to **Places > Connect to Server** and clicking the appropriate options.

There's info on how to use X (graphical interface) over ssh [here]("http://blog.thembid.com/2007/06/23/how-to-access-your-ubuntu-remotely/").  It's a little old, but mostly still relevant.  But a better solution may be [NX]("http://www.nomachine.com/") - click the link and check for the free version.

---

### Post by tomBorgia on 2009-08-12
I got "Unknown cipher type '-X'" when trying this but removed the "-c" bit and it worked... couldn't get X to start but nautilus / rhythmbox seemed to work ok.

Thanks.

---

### Post by t0p on 2009-08-12
> **tomBorgia said:**
>  couldn't get X to start but nautilus / rhythmbox seemed to work ok.

Nautilus and rhythmbox are both graphical programs (ie they work through a gui).  So, if they work, that means X has started.

---

### Post by tomBorgia on 2009-08-12
Yep of course... I meant startx (i.e. getting the window manager running)... which I think would take more fiddling!

---

### Post by porchrat on 2009-08-12
Awesome thanks everyone so much for the responses so far. I had forgotten that ssh had the X component.

The last time I used ssh I avoided X as I was worried about the load it would place on my tiny internet connection.

If this sort of thing can be done through ssh then that should be sufficient.

ssh is not setup currently as I haven't yet put the machine together, but I am relatively familiar with setting it up. I am just not familiar with how the X components of ssh function.

How exactly would it work though, for example if I wanted to start nautilus on the remote machine I would type "nautilus" into the ssh terminal. Would a nautilus window then appear on my local screen that I could interact with? I assume that one can only open one gui at a time?

This would be desirable as I don't wish to transfer the data required to display an entire desktop environment and would like very much to get away with just transferring the data required to display a single gui window.

Also does all the processing get done on the remote machine, or is some handled by the local machine? I just ask because I worry about the load on my internet connection, my cap is rather small as well.

---

### Post by longtom on 2009-08-12
I consider myself as somewhat...clumsy when it comes to things like that.

But this:  [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

was even easy enough for me.  I remotely control Windows and Linux PCs at will, without needing to jump through hoops.

It has my seal of longtom proofed....

---

### Post by P4man on 2009-08-12
IIRC I got it working once using just ssh and .. dont remember, "gnome-session" instead of startx, but it involved quite a bit of tinkering, and i dont quite remember.

t0p's suggestion for using freeNX is worth checking out though:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by porchrat on 2009-08-12
Also another thing is that this will probably be occurring between two Hardy Heron installations as so far it is the most stable recent LTS release I have encountered. I doubt this would be an issue, but in case people needed some additional information.

---

