---
title: "getting suspend to work in customized ubuntu 10.04 install"
date: 2010-06-26
forum: General Help
---

### Post by Helios747 on 2010-06-26
Hello,

I've done an Ubuntu 10.04 CLI install and installed the packages I wanted for a desktop environment.

In a vanilla Ubuntu install, closing the laptop lid gets Ubuntu to go into suspend properly.

In my setup, closing the lid triggers nothing. How do I get it to trigger a suspend?

---

### Post by _Mark_ on 2010-06-26
You probably haven't installed the power management stuff

Have no clue what it maybe called but a search for power in synaptic, you should be able to work out what you need

---

### Post by kerry_s on 2010-06-26
check that you have "acpi-support".

---

### Post by Helios747 on 2010-06-27
I did not have acpi-support installed kerry, however installing it and starting it in init.d doesn't trigger a suspend when I close the lid.

---

### Post by kerry_s on 2010-06-27
hmm, here's what i have under acpi.

---

### Post by Helios747 on 2010-06-27
Yeah, I have those packages installed, but closing the lid does nothing at all. It's weird.

I'm wondering if it's because I have a MacBook 5,1 and vanilla ubuntu has some special tweak to get that working properly on Apple hardware.

I guess it's not TOO big of an issue, because I found a script on the internet that throws my laptop into suspend mode, however when I come out of it, I can't seem to get back into Openbox... Or a virtual terminal. Whee.

I might just have to settle for turning the lappy off. heh.

---

### Post by kerry_s on 2010-06-27
yeah, you didn't say it was a mac, thats pretty important info.
see if any of this helps->
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid)

---

### Post by Helios747 on 2010-06-27
Well that's funny.

It says suspend is support is supported OotB.


Ah well, I'm probably missing some important tweak. This is helping me narrow what to search for on google though! :p

If I find anything that works I will post back with what I did.

---

### Post by dino99 on 2010-06-27
just search into synaptic: hibernate seem to be your boy

---

### Post by _Mark_ on 2010-06-27
> **Helios747 said:**
> Well that's funny.

It says suspend is support is supported OotB.


Ah well, I'm probably missing some important tweak. This is helping me narrow what to search for on google though! :p

If I find anything that works I will post back with what I did.

Have you actually gone into Power Management and configured what action you want when the lid is closed?

---

### Post by Helios747 on 2010-06-27
Thank you for all of your help! I was able to get it working. Here is what I did


```
sudo apt-get --no-install-recommends install hibernate gnome-power-manager
```

I used the no install recommends switch because I am using openbox and if it wanted to install gobs of gnome stuff I didn't need.

I then ran

```
gnome-power-preferences
```

and configured it to my liking, restarted, and shutting the laptop threw it into suspend! Thank you!

---

