---
title: "VMWare and AOL Radio"
date: 2006-06-24
forum: General Help
---

### Post by josys36 on 2006-06-24
Howdy folks!

I moved completely to Ubuntu a few weeks ago and right now I am having only one issue.

I run Windows XP under VMWare Player, because there are a few applications that don't work in Linux. All works perfect except for AOL radio. For some reason the audio gets static at random times, and for an unknown reason. I have tried everything I already know about VMWare settings, and Ubuntu settings, but this still happens.

I have downloaded VMWare Server, but have not installed yet to see if this happens there as well. I will try this next week.

The funny part is that I can run AOL Radio under Firefox using Wine. From here it seems to work OK for now, but I would like to get this audio issue fixed in VMWare Player. 

If anyone has any suggestions I would be most greatfull.

Thanks!

Jason

---

### Post by josys36 on 2006-06-27
Well I switched from VMWare Player to VMWare Server, but the issue is still happening. This is also happening for any .MP3 file. So with that in mind, it must not be network related and just be sound related.

Has anybody else had these types of issues? Right now I am running AOL radio under Firefox using wine, but that can be choppy sometimes. Although it does work.

Thanks!

Jason

---

### Post by josys36 on 2006-07-02
Well I just might have found the issue. The problem seems to be with the clock in the windows guest. I found others out there that have had the same issue. One test that can be ran is try to play a MIDI file. If the file plays slower ( mine was about 50% slower) then you may have this problem.

Right now I could not find a workaround for windows guests with a linux host. I found some workarounds for linux guests, but windows guest still appear to be a mystery. With vmware tools installed you can keep the clock correct, but this is not real time. 

Thanks!

Jason

---

### Post by josys36 on 2006-07-07
Well I have AOL Radio working fine under Wine. So for now I guess I will have to wait for VMWare to fix the issue with player.

Jason

---

### Post by josys36 on 2006-08-04
I just upgraded to a T60 from my T43. The T60 has a dual core processor and VMWare seems to love this quite a bit. I no longer have the processor clock issue at all.

Jason

---

### Post by easyease on 2006-08-04
just out of interest, have you not tried any shoutcast net radio staions? they are very easy to recieve under linux.....you can even get live 365 stations with streamtuner.

---

### Post by josys36 on 2006-08-04
The main reason I use AOL radio is because they have one station I cannot find anywhere else. I fully understand that for linux there are better options then AOL, but I just can't seem to find the station I like any where else.

Jason

---

### Post by pdxsam on 2006-10-20
How did you accomplish it through Wine?  Aol Radio wants to use a web browser as the platform.

---

### Post by josys36 on 2006-10-20
> **pdxsam said:**
> How did you accomplish it through Wine?  Aol Radio wants to use a web browser as the platform.

I just installed FireFox under Wine. It works great and this solved the AOL radio problems. In fact I still use this solution to this day. Even though AOL Radio works rather well in my VM using VMWare Server. Server fixed a lot of the issues I was having.

Jason

---

### Post by pdxsam on 2006-10-20
Thanks  I'll give that a whirl.

---

### Post by des4ij on 2006-10-20
did u try using Qemu instead of vmware...

---

### Post by josys36 on 2006-11-01
> **pdxsam said:**
> Thanks  I'll give that a whirl.

How did that work out for you? Be warned that I could not install 2.0 Firefox using Wine. The install told me that I did not have enough disk space to install. 

Jason

---

### Post by AnRkey on 2007-04-04
I see that AOL radio uses UVOX to stream. I am looking into a UVOX player and will post my findings.

Ex of stream: XM Flight 26 >> [uvox://firehose-bbnm.stream.aol.com/stream/22212]("uvox://firehose-bbnm.stream.aol.com/stream/22212")

Hope this helps a bit :)

---

### Post by AnRkey on 2007-04-29
I tried to get XM streams to work on my box but it seems that the only player that they work on is Winamp.

I did find Songbird ([http://www.songbirdnest.com](http://www.songbirdnest.com)) which works really nicely and lists loads of online radio stations to take your mind of AOL radio.

Ciao

AnRkey

---

### Post by josys36 on 2007-06-14
Really AOL radio works fine as long as you run it under WINE with Firefox.

Jason

---

