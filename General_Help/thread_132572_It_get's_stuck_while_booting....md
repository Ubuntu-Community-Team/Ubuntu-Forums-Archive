---
title: "It get's stuck while booting..."
date: 2006-02-18
forum: General Help
---

### Post by hibatsu on 2006-02-18
Yesterday evening I installed gnomad 2.8.2 by compiling it from source. I changed something for the hotplug (maybe that's the cause, no idea...) and today when trying to boot I get the following errors:

```

* Cannot find initrd device!
...
* t_console_fd: Inappropirate ioctl for device

```

And at "Setting up ICE socket directory" he get's stuck...
Any idea what I can do?

---

### Post by Harry_Sack on 2006-02-18
Hello.

I think this ha shappened to me before *** well.

When I had this problem it was the permissions of the .ICEauthority-file in my home-dir.
I think you can try something like "sudo chown yourname:yourname /home/yourname/.ICEauthority"

or

"sudo chmod 755 /home/yourname/.ICEauthority"

Maybe that will work?

Without the quotes.

Oh, and when you get to the login screen, you choose failsafe terminal and type these commands.

I don't think they can do much harm, I've done them MANY times.

So Long.

Big Beer Drinker

---

### Post by Harry_Sack on 2006-02-18
ahh, I was not permitted to write ***. HowBoring.
FUCKASSSHITMOTHERFUCKER     \\:D/

---

### Post by hibatsu on 2006-02-18
Well my problem is that I don't even get to the login screen.
It freezes right at the

"* Setting up ICE socket directory        [ok]"

---

### Post by Harry_Sack on 2006-02-18
Well I suppose you could try recovery mode then. It doesent matter where you type it, as long as you're logged in. On the grub menu choose recovery mode. Even if you have to go blind folded you have to DO IT

---

### Post by hibatsu on 2006-02-18
Recovery mode doesn't work either. Would a live cd work?

---

### Post by Harry_Sack on 2006-02-18
oooh never seen that before. i'm a noob too you know. So you're moving further in to enemy territory then. I have no idea. With a live cd yoiu could back up everything and reinstall.    :cry:

---

### Post by hibatsu on 2006-02-18
I've got a knoppix dvd, but somehow I can't write any files, neither on my ext 3 nor on my fat transfer partition. Unfortunately my laptop has only got one cd drive so I can't burn my data on cd's either? How can I get writing permissions with the live dvd so I can transfer from the ext 3 to the fat partition?

Or is there any hope to solve the problem differently?

---

### Post by Harry_Sack on 2006-02-18
don't even  know if I know more about this than you,  but i've hd troubles with knopppix kanotix *** well. try the root terminal in the menu, and run konqueror from there. try that. i've found that often ubuntu live cd      works best with goog old sudoo etc., but im not very knowledgable. im sorry i have to sleep too, haven't slept due to compiling prokyon last night, so that's 36 hours+ im drunk *** well. but i recieve mail if you write anything so good luck until then     :-k

---

