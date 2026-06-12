---
title: "Why do I get asked for a password before I can use wireless internet?"
date: 2010-06-29
forum: General Help
---

### Post by sastusbulbas on 2010-06-29
Every time I boot up Ubuntu I am asked for a password which I have to enter before I can access the internet, why and can I switch it off and have permanent wireless connection which works automatically when I boot up Ubuntu?

---

### Post by jeicrash on 2010-06-29
If your wireless connection requires wep/wpa key then this is stored in your key ring. This is why your being asked for password.

Getting rid of this step may be possible by removing the current network manager, installing "network" and setting all options manually via the config files or by a startup script.

I like the option of needing a password, it means people are less likely to just jump on my box and start downloading junk.

Jei.

---

### Post by 7Lj3)(P38J on 2010-06-29
> **jeicrash said:**
> If your wireless connection requires wep/wpa key then this is stored in your key ring. This is why your being asked for password.

Getting rid of this step may be possible by removing the current network manager, installing "network" and setting all options manually via the config files or by a startup script.

I like the option of needing a password, it means people are less likely to just jump on my box and start downloading junk.

Jei.


Jei
you may be right, but it is so annoying. It's one of the most horrible thinga about Ubunt. No one wants to be constantly asked for the password in order to acess/install anything. Windows never asked us such, so Ubuntu shouldn't as well. Period.

---

### Post by GlazedWicker on 2010-06-29
This was happening to me as well. For some reason right clicking on the wireless icon, going to edit connections and then saving the settings for my network got rid of the problem.

---

### Post by techunit on 2010-06-29
Ok if you are automatically being logged in then the keyring isn't being automatically started so you must enter the key ring when your full logged in. there is a way around this... I believe if you set your computer to require you to log in then you will get options on the keyring when it asks for a password again.

---

### Post by Chronon on 2010-06-29
> **crolidge said:**
> Jei
you may be right, but it is so annoying. It's one of the most horrible thinga about Ubunt. No one wants to be constantly asked for the password in order to acess/install anything. Windows never asked us such, so Ubuntu shouldn't as well. Period.

This is a big reason that Windows is more susceptible to malware.

---

### Post by jeicrash on 2010-06-30
I agree that passwords can be annoying, but without them another app could do whatever it wanted without you knowing it was trying to access root level privileges.

One easy way is just to remove the pass key from your wireless. Although this is even worse then having to type a short password each time. I keep my main user account pass simple on my personal computer. Ubuntu is easy enough to setup I'm not worried about many people going crazy on it.

---

### Post by stinkeye on 2010-06-30
You can solve this by clicking on the NetworkManager Applet > edit connections > wireless > edit.
In the bottom left hand corner you'll see a box ...**Available to all users**
[SIZE="6"]**TICK IT**[/SIZE]

---

### Post by 7Lj3)(P38J on 2010-07-01
> **jeicrash said:**
> I agree that passwords can be annoying, but without them another app could do whatever it wanted without you knowing it was trying to access root level privileges.

One easy way is just to remove the pass key from your wireless. Although this is even worse then having to type a short password each time. I keep my main user account pass simple on my personal computer. Ubuntu is easy enough to setup I'm not worried about many people going crazy on it.

you're right Jei, I didn't think about that. But of course it would be highly unsafe.

---

### Post by jeicrash on 2010-07-01
No more unsafe then the 90% of computers running MS windows with no login password at all. 
Disabling the key ring would be just as unsafe.

---

