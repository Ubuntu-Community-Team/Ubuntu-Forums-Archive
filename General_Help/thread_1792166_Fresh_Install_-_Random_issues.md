---
title: "Fresh Install - Random issues"
date: 2011-06-27
forum: General Help
---

### Post by breNTx22 on 2011-06-27
I consider myself a novice but i've been using Ubuntu (on and off) since Ubuntu 7. Yet again, i'm trying to make the switch from Windows to Ubuntu but it's not an easy one. I ran into a few problems so far.

1) Ubuntu Software Center will not open 

2) Banshee - Every time I go to add my music folder (on my QNap NAS) it closes/crashes without any error.

3) I don't agree with the visual changes in Ubuntu 11, how can I make it look more like Ubuntu 10?

4) How do I permanently add my QNap NAS (network drive)? I can go to "Network" and it's there and then I can right click it and go to "Send to" and select "Desktop" but that only seems to make that shortcut for that session.

I've done some googling and I haven't found any solutions yet. Any help would be appreciated.

---

### Post by nzjethro on 2011-06-27
> **breNTx22 said:**
> I consider myself a novice but i've been using Ubuntu (on and off) since Ubuntu 7. Yet again, i'm trying to make the switch from Windows to Ubuntu but it's not an easy one. I ran into a few problems so far.[/CLOSE]

Good for you, hopefully we can make you Windependent.

> 1) Ubuntu Software Center will not open 
This is quite a broad problem. How are you attempting to open the USC, GUI or from the terminal? I recommend running
```
sudo apt-get update & apt-get -f install
```
Then try open USC from the terminal, and post back any error messages it gives you.

[QUOTE]
3) I don't agree with the visual changes in Ubuntu 11, how can I make it look more like Ubuntu 10?

Fair enough, they're not for everyone, and as you'll see on here, there is a fair few people like you. When you are logging in to 11.04, you should see at the bottom of your screnn a drop-down (well drop-up) menu with the different environments you can boot into. Select "Ubuntu Classic" for a nice 10.10 looking environment.

> 
4) How do I permanently add my QNap NAS (network drive)? I can go to "Network" and it's there and then I can right click it and go to "Send to" and select "Desktop" but that only seems to make that shortcut for that session.

Sorry, no idea what a QNap NAS is, But I'm sure someone on here has dealt with it before.

---

### Post by breNTx22 on 2011-06-28
> **nzjethro said:**
> [QUOTE=breNTx22;10988667]I consider myself a novice but i've been using Ubuntu (on and off) since Ubuntu 7. Yet again, i'm trying to make the switch from Windows to Ubuntu but it's not an easy one. I ran into a few problems so far.[/CLOSE]

Good for you, hopefully we can make you Windependent.


This is quite a broad problem. How are you attempting to open the USC, GUI or from the terminal? I recommend running
```
sudo apt-get update & apt-get -f install
```Then try open USC from the terminal, and post back any error messages it gives you.



Fair enough, they're not for everyone, and as you'll see on here, there is a fair few people like you. When you are logging in to 11.04, you should see at the bottom of your screnn a drop-down (well drop-up) menu with the different environments you can boot into. Select "Ubuntu Classic" for a nice 10.10 looking environment.



Sorry, no idea what a QNap NAS is, But I'm sure someone on here has dealt with it before.

Thank you for the response.

1)
This is the error I get:

"[1] 2273
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

[1]+  Stopped                 sudo apt-get update"


4) A QNap NAS is a type of network storage. QNap is a brand (another common brand is "Drobo"). NAS is "Network Attached Storage".

[http://en.wikipedia.org/wiki/Network-attached_storage](http://en.wikipedia.org/wiki/Network-attached_storage)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822107034](http://www.newegg.com/Product/Product.aspx?Item=N82E16822107034)

---

