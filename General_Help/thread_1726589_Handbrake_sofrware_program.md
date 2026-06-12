---
title: "Handbrake sofrware program"
date: 2011-04-11
forum: General Help
---

### Post by trixman on 2011-04-11
hi ,  a friend of mine is interested in downloading this program. Does anybody know if its worthwhile. She is looking to convert her old DVD'S to put into itunes so she can view them on her tablet.

also the program is not in the ubuntu library. is it ok to download this program from its page.

thanks

:P

---

### Post by Enigmapond on 2011-04-11
Handbrake is a good programme but there are many that will do the deed. However, there might be a problem in copying DVD's due to licences but you can give it a shot..

```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update && sudo apt-get install handbrake
```

---

### Post by Grenage on 2011-04-11
> **trixman said:**
> hi ,  a friend of mine is interested in downloading this program. Does anybody know if its worthwhile. She is looking to convert her old DVD'S to put into itunes so she can view them on her tablet

I use it for the same purpose, and it works well.

---

### Post by trixman on 2011-04-11
> **Grenage said:**
> I use it for the same purpose, and it works well.

thanks. is it ok to download the program from therre webpage.
i always download software from ubuntu library.

;)

---

### Post by Enigmapond on 2011-04-11
If you run the commands I posted, it will install...or just add the repo & update and it will be in the software centre. It's not in the main repos. You need to add the repository...by just installing the .deb, you won't receive updates to the programme.

---

### Post by Grenage on 2011-04-11
> **trixman said:**
> thanks. is it ok to download the program from therre webpage.
i always download software from ubuntu library.

;)

Yes it's ok, but Enigmapond's advice would be the way I'd go; it's much easier handling software via a repo.

---

### Post by howefield on 2011-04-11
That repository looks to have version 0.9.4 whereas the latest release is 0.9.5

I'd use the repository detailed here..

[https://edge.launchpad.net/~stebbins/+archive/handbrake-releases](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases)

Your mileage may vary :)

---

### Post by Enigmapond on 2011-04-11
> **howefield said:**
> That repository looks to have version 0.9.4 whereas the latest release is 0.9.5

I'd use the repository detailed here..

[https://edge.launchpad.net/~stebbins/+archive/handbrake-releases](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases)

Your mileage may vary :)

Thanks for that...that's actually the one I meant to post I just edited my post with the proper one.. :)

---

### Post by flipper T on 2011-04-11
try k9copy, it has ripped everything i have thrown at it

---

### Post by trixman on 2011-04-11
> **flipper T said:**
> try k9copy, it has ripped everything i have thrown at it

can i convert the dvds to a file to show them on my tablet with this program.

and is it the same as the program handbrake ?


thanks

---

### Post by flipper T on 2011-04-11
yes it does

when you use it, use the "k9copy assistant"

this will walk you through the process

---

