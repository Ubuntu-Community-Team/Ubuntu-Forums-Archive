---
title: "how can i stop ubuntu from useing the swap drive"
date: 2006-04-23
forum: General Help
---

### Post by cosmoshell on 2006-04-23
how can i stop ubuntu from useing the swap drive??
dont ask why I dont like to use swap.

---

### Post by Ensnared on 2006-04-23
I really can't see any reason why you'd want this, but if you're sure then you can just comment out (or delete) the line from /etc/fstab that looks sort of like this:
```
/dev/hda6   none             swap       sw         0      0
```

I believe that's enough to prevent Ubuntu from seeing and using the swapdrive. The "hda6" bit will likely be different for you, but the rest should be as shown above.

---

### Post by Jason_25 on 2006-04-23
```

sudo swapoff -a

```
will cause it to stop using swap immediately.

---

### Post by r3m0t on 2006-04-23
[QUOTE=cosmoshell]how can i stop ubuntu from useing the swap drive??
dont ask why I dont like to use swap.[/QUOTE]
Sorry, I can't resist. Why can't you use swap? Windows has swap too, you know.

---

### Post by cosmoshell on 2006-04-23
[QUOTE=r3m0t]Sorry, I can't resist. Why can't you use swap? Windows has swap too, you know.[/QUOTE]

you see the computer ubuntu is installed on has a 1 gb harddrive and i realy dont have any space on my disk to waste with the right settings and programs it 
doesent run out of ram. and windows on the other hand it doesent use swap it uses a pageing file witch I tend to lower the size of.

---

### Post by paritybit on 2006-04-23
It is a great mystery. I was thinking that maybe he is curious about seeing what happens without swap in Linux... Who knows.... Maybe he is paranoid and doesn't trust his memory getting written to swap in case someone can read it....

---

### Post by Ensnared on 2006-04-23
[QUOTE=cosmoshell]windows on the other hand it doesent use swap it uses a pageing file witch I tend to lower the size of.[/QUOTE]
Linux can also use a swap-file (e.g. just like Windows) instead of a partition. If you want to set that up instead, here's how.

First, create the file - 128MB in this case (131072k), created in /var:```
sudo dd if=/dev/zero of=/var/swapfile bs=1024 count=131072
```
Set the permissions:```
sudo chmod 600 /var/swapfile
```
Make it a swapfile:```
sudo mkswap /var/swapfile
```
Activate it:```
sudo swapon /var/swapfile
```
And add it to fstab with the following line:```
/var/swapfile swap swap defaults 0 0
```

Only difference is, the file is constant rather than dynamic as is default in Windows, but I atleast always set my swapfile to a constant size in Windows as well. Makes it easier to know how much space is actually available, and it (supposedly) improves performance somewhat. It sure helps with limiting disk fragmentation :)

Oh, and this is a pretty old way of doing it - there may be more streamlined ways these days, but this is pretty much how I did it ages ago.

---

### Post by enopepsoo on 2006-04-23
Ensnared: Wow.

Cosmoshell: I feel that I should add that Ubuntu probably partitioned swap space when you installed, in which case it would probably be easier to just set up the system with no swap partition to begin with.

---

### Post by cosmoshell on 2006-04-23
[QUOTE=paritybit]It is a great mystery. I was thinking that maybe he is curious about seeing what happens without swap in Linux... Who knows.... Maybe he is paranoid and doesn't trust his memory getting written to swap in case someone can read it....[/QUOTE]
hmm actualy on one of my other computers i encrypted the swap space.

---

### Post by paritybit on 2006-04-23
Well making a swap partition doesn't use a lot of space. I have a computer with 1gig of hdd, I use about 60meg for my swap with 72meg of ram, works pretty well.

---

### Post by cosmoshell on 2006-04-23
[QUOTE=paritybit]Well making a swap partition doesn't use a lot of space. I have a computer with 1gig of hdd, I use about 60meg for my swap with 72meg of ram, works pretty well.[/QUOTE]

i realy dont see why you need to have swap when you have over 500 mb ddr ram i dont do anything heavy with it and it still seems to run instintly fast.

---

