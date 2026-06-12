---
title: "Azureus DHT &amp; NAT Firewalled problem!!!"
date: 2006-04-10
forum: General Help
---

### Post by exodus on 2006-04-10
hi ppl,

i've been using ubuntu for a while.. i like it..

i installed azureus with automatix.. it works fine... but i have the above mentioned problem...

both my NAT & DHT is firewalled.. i've been readin around and am not able to figure out wat the problem is...

btw i have a zyxel prestige 660 router which is configured to portfoward all ports for a particular ip.. 192.168.1.1

it works like a charm in windows(which i dont like).. how can i get rid of this problem..

i've also enabled the uPnP options in my router and azureus... but it says uPnP has failed...

i get average d/l speeds...

any help will be appreciated.... btw i'm a newbie ;)

---

### Post by exodus on 2006-04-10
oh u should also know that when i do other d/ls like update s/w or somethin.. i get maxed out.. so my connection is fine..

only got problems with torrents...

---

### Post by babyhuey on 2006-04-10
I believe this might be your problem. After you've installed java, you must set it up as the default java client.

sudo update-alternatives --config java

once you run this you will want to pick Sun's Java.

I believe thats the command. You'll find more details in the ubuntu wiki about installing java.

---

### Post by exodus on 2006-04-10
thx babyhuey for yer reply...

but my sun java is already the default java client...

---

### Post by exodus on 2006-04-11
thx ppl.. problem solved.. it jus started workin outta de blue...

---

### Post by sml on 2006-04-29
Any idea how?

I am sure the problem is not my router but mhy xubuntu install. No other distros have this problem with azureus which I have tried.

---

### Post by kupajava on 2006-04-29
You know that this is a Gnome forum right?  if you are using something other than gnome you should post in the correct forum.  More likely to get a correct response there.

---

### Post by mstlyevil on 2006-04-29
[QUOTE=kupajava]You know that this is a Gnome forum right?  if you are using something other than gnome you should post in the correct forum.  More likely to get a correct response there.[/QUOTE]

There is no Xubuntu forum so the gnome forum is the right place for Xubuntu questions. There will be a Xubuntu section when Dapper is released.

---

### Post by kupajava on 2006-04-29
my bad

---

### Post by SoulSmasher on 2008-01-29
i had similar issue with azureus which i downloaded from ubuntu software depot. then i manually downloaded 3.0.4.2 and no issue remains :)
if ur azureus version is old, try updating,
(btw, new vuze style is pretty cool though :) )

---

