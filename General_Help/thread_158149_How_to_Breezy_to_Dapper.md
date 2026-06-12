---
title: "How to Breezy to Dapper ?"
date: 2006-04-10
forum: General Help
---

### Post by krypto_wizard on 2006-04-10
What steps are required to change from Breezy to Dapper ?

Is it just changing the /etc/apt/source.list and dist-upgrading or there is something more to it.

My current Breezy is messed because of some Gnome and KDE issues. It wont let me goto Gnome. I also upgraded KDE to 3.5.2 from 3.4.3 but it still shows the old one.

I tested Dapper once and it wasn't bad. Any comments ??

thanks

---

### Post by aysiu on 2006-04-10
[QUOTE=krypto_wizard]What steps are required to change from Breezy to Dapper ?

Is it just changing the /etc/apt/source.list and dist-upgrading or there is something more to it.[/QUOTE] Yes. That's all you do. I don't know if that'll solve your KDE/Gnome problems, though.

---

### Post by krypto_wizard on 2006-04-10
where can i find the correct source.list for Dapper ?

Is there a place on forums where you have access to the most recent and up to date repos.

Thanks

[QUOTE=aysiu]Yes. That's all you do. I don't know if that'll solve your KDE/Gnome problems, though.[/QUOTE]

---

### Post by rabidphage on 2006-04-10
I think you should replace all occurances of "breezy" to "dapper" in your sources.list file. Thats what I did.
Then do sudo apt-get update 
and sudo apt-get dist-upgrade

It broke my install though, Probably due to xconf issues ](*,) 

imho the sources.list depends on your specific needs.
I don't think there is "a" sources.list file

---

### Post by taurus on 2006-04-10
And don't forget that Dapper is not even beta.  It's more like alpha so if it breaks your system, then it breaks your system althought Dapper Flight 6 runs fine on my HP laptop!  ;)

---

### Post by joshrobinson on 2006-04-10
[QUOTE=taurus]And don't forget that Dapper is not even beta.  It's more like alpha so if it breaks your system, then it breaks your system althought Dapper Flight 6 runs fine on my HP laptop!  ;)[/QUOTE]

dapper is pretty darn stable.. i havent had a crash or any problems really

only thing is that some programs dont work on it yet, or need dependencies that arent easy to get a hold of

automatix as of right now doesnt work

---

### Post by greenpenguin on 2006-04-10
Dapper is a lot more stable than it was at Flight 1 :) Most crashes I get are to do with XGL - apart from that I only have 1 prob with my Dapper install :D.

---

### Post by Engnome on 2006-04-10
I havent tried dist-upgrade myself because there seems to be so many people that have broken their install, maybe on a fresh breezy but not if you used it to long. 

I have to agree with previous posters, tried breezy. Had many annoying bugs, stuff that didnt and lots of crashes, but all that stopped when i did a fresh dapper install.  Maybe thats something for you?

---

### Post by aysiu on 2006-04-10
I just did a dist-upgrade of Breezy to Dapper today, and it went flawlessly. I couldn't believe it, since my dist-upgrade from Hoary to Breezy totally screwed up my xorg and something about locales...

---

