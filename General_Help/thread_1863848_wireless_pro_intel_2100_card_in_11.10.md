---
title: "wireless pro intel 2100 card in 11.10"
date: 2011-10-18
forum: General Help
---

### Post by bzzzzz on 2011-10-18
I feel a bit daft because I've installed several linux OS on different machines and have always managed to get my wireless network card to work.  This time however I'm stumped.

I'm fairly sure there's an easy solution, but please can someone help.

I have an Intel Pro Wireless 2100 inbuilt wireless card on my laptop.  

I've just installed 11.10 on to the machine.

I downloaded the intel drivers - which are for linux - I thought this would make things easier rather than ndiswrapper, but not so far.

The files are called ipw2100-1.3-p.fw, ipw2100-1.3.fw and ipw2100-1.3-i.fw

I just don't know how to get the card to find these and turn on.

Thanks for helping out an old fool

---

### Post by bzzzzz on 2011-10-18
Ok solved this myself

But for anyone else 

You need to go to terminal and type

sudo gedit /etc/NetworkManager/NetworkManager.conf

change the file so that it says

"managed=true" on the bottom line

Then in the terminal also type

sudo killall NetworkManager

and your away ... :)

---

### Post by gavila on 2011-10-31
How did you find out about this?

---

### Post by bzzzzz on 2011-10-31
Sorry I said I worked it out, but I searched through the following websites starting with this one.

[http://www.highgeekvalue.com/2011/10/linuxtip-wireless-network-card-not.html](http://www.highgeekvalue.com/2011/10/linuxtip-wireless-network-card-not.html)

I then used this

[http://ubuntuuserblog.blogspot.com/2011/08/re-network-manager-broken-after-latest.html](http://ubuntuuserblog.blogspot.com/2011/08/re-network-manager-broken-after-latest.html)

I tried and failed with several other things but it's working now :)

---

