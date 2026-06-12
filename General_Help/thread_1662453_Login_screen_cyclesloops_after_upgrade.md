---
title: "Login screen cycles/loops after upgrade"
date: 2011-01-08
forum: General Help
---

### Post by danselic on 2011-01-08
I was running 10.04 until yesterday, when it occured to me that I could upgrade to 10.10. So I went to Software Center, set it to get normal releases and left it to do its job. The upgrade appeared to go without a hitch and I rebooted.

The login screen appeared. But just before I could click on my username and enter my password, the screen went blank and a second later the login screen was back. But then just before I could click... you get the idea.

Undeterred, after half a minute of frantic clicking I did manage to click on my username and get the password prompt. This time, the login screen didn't go anywhere. Yay.

To cut a long story short, this is now my standard logon procedure. 

However, the plot thickens. I appears that instead of 10.10, I ended up with 11.04, Natty Narwhal, which 'was released in April 2011'.

I've already spent hours on this and other fora and tried many of the solutions suggested to no avail. 

My question therefore is this:

If I download an .iso of Maverick and install it over my current version, will it leave my data unharmed AND reset everything so that it works again? 

Thanks.

---

### Post by Rubi1200 on 2011-01-08
Are you also using Windows or just Ubuntu?

The information about 11.04 is a bug.

If you run this in the terminal it will show you the correct version:

```
cat /etc/*release
```Also post the computer specifications.

Are you able to boot into recovery mode or older kernels?

Thanks.

---

### Post by danselic on 2011-01-08
Yeah, a bug apparenly. Issuing the command you suggested reports the version as 10.10.

I have an MSI GX623 laptop: C2D 2GHz, ATI Mobility Radeon 4670, 4GB RAM.

I am running the latest version of the proprietary ATI drivers.

Haven't tried older kernels but the one time I tried recovery mode, there wasn't any looping.

---

### Post by Rubi1200 on 2011-01-08
Couple of things to try;

either boot into recovery mode or to the regular entry and choose Safe Graphics mode.

Whichever works, try these commands to reconfigure the Xorg server.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg

```
Reboot.

If this does not help, we can investigate further.

---

### Post by danselic on 2011-01-08
Many thanks, Rubi1200, that appears to have done the trick!

---

### Post by Rubi1200 on 2011-01-08
No problem, you are more than welcome :)

---

