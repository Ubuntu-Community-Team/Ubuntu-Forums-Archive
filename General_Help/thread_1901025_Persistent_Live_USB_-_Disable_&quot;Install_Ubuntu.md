---
title: "Persistent Live USB - Disable &quot;Install Ubuntu&quot; Wizard?"
date: 2011-12-27
forum: General Help
---

### Post by Valiante on 2011-12-27
Hi all.

I just made a persistent live USB via usb-creator-gtk to use on an old laptop with no hard drive, for general browsing, etc.  All works well, changes are saved across sessions, etc - trouble is it's still showing the "Install Ubuntu" wizard on every boot.  Anyone know how I can disable this?

Cheers,

Valiante. :)

**_EDIT:_**  This is on the latest version (11.10), not 6.06 Dapper.  I created my profile 4 years ago and don't seem to be able to edit this again until I've made 50 posts.

---

### Post by C.S.Cameron on 2011-12-28
Some people prefer the opening screen made by an Unetbootin install.
I recall adding a new user in users and groups might also fix this.
Or you could do a Full install to USB.

---

### Post by Valiante on 2011-12-28
> **C.S.Cameron said:**
> Some people prefer the opening screen made by an Unetbootin install.I'm not sure what that is, but I'll look it up - thanks.

> **C.S.Cameron said:**
> Or you could do a Full install to USB.I considered that, but decided against it as a side-note on the [tutorial]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Method_1:_Installing_Ubuntu_directly_to_USB_drive_from_installer_CD") mentioned that "*This will use the USB drive for /tmp, which will cause extra wear on the flash memory.*"

> **C.S.Cameron said:**
> I recall adding a new user in users and groups might also fix this.I'll certainly give that a try and let you know, thanks.

---

### Post by Valiante on 2011-12-28
> **C.S.Cameron said:**
> I recall adding a new user in users and groups might also fix this.
Unfortunately that didn't work.  All that happened was, after displaying the "Install Ubuntu" wizard as before, it then showed me a login screen with the new account listed.  I could then either login with the new account, or click "Other" and manually enter the "Ubuntu" username with no password (the default live session account).  If I enable auto-login on the new account it still displays the wizard, then logs in afterwards.

So thanks for the suggestion, but I'm still seeking a solution.

---

### Post by C.S.Cameron on 2011-12-29
> considered that, but decided against it as a side-note on the tutorial mentioned that "This will use the USB drive for /tmp, which will cause extra wear on the flash memory."

I do not believe that you will find anyone on this site that has ever worn out a flash drive by running Ubuntu from it, (persistent or Full).

A flash drive is good for over 10000 writes.
At 10MB/s it takes 16GB/10MB/s = 0.444 hours to fill a 16GB drive.
Or 0.444h*10000/8h/wd = 555 work days to wear one out, (if you are writting to it full time, 8 hours per day).

See also:
[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

---

### Post by Valiante on 2011-12-30
> **C.S.Cameron said:**
> A flash drive is good for over 10000 writes.
At 10MB/s it takes 16GB/10MB/s = 0.444 hours to fill a 16GB drive.
Or 0.444h*10000/8h/wd = 555 work days to wear one out, (if you are writting to it full time, 8 hours per day).

See also:
[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

Interesting article.  Despite the 10k write estimate, it turns out he was able to write over 30 millions times per block before the drive failed, and even then he was still able to read his data, so not a total loss.

That aside, I've started to find Ubuntu a little bloated, even if much more user friendly than Puppy (what I was using previously).  I've tried Lubuntu to slim things down somewhat and, though it boots much quicker now, I'm struggling to get everything to work.  Several apt-get attempts have failed where they worked fine in full Ubuntu.

So in summary, I'm no better off that I was before with Puppy.  I think, alas, I am going to end up down the same road I always do when I attempt to use Linux...  and that's to get a 2nd hand hard disk and install Windows. :(

---

### Post by sakraft1 on 2012-01-13
I too would like to do away with the Installation window on startup, if anyone is still looking for a solution.

---

### Post by Valiante on 2012-01-13
> **sakraft1 said:**
> I too would like to do away with the Installation window on startup, if anyone is still looking for a solution.

The solution has already been given:

> **C.S.Cameron said:**
> Or you could do a Full install to USB.

I just decided not to go with it because I find Ubuntu too bloated for my needs vs hardware capabilities, so I've gone back to Puppy, despite it being harder to find working packages for.

If you do a full install with the USB as your target, it should no longer run as though it's a Live CD and won't show the install wizard on startup.  HTH.

---

