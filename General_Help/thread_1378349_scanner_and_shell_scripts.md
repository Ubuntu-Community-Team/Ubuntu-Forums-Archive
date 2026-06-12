---
title: "scanner and shell scripts"
date: 2010-01-11
forum: General Help
---

### Post by caue.rego on 2010-01-11
I've got a HP all in one printer and I want a simple way to scan with it connected to the server.

I've made a shell script that does the job and scan to overwrite a default file. Unfortunately this is still not enough.

I wonder how I can run it without needing to ssh into the server.

Best option would be by pressing the printer "scan" button.

But I'd also enjoy being able to do it through local HTTP, no passwords asked.

Anyone can help?

---

### Post by mocoloco on 2010-01-12
[This]("http://www.linux.com/archive/feature/59138") info is old but may still be useful, I would guess it would still work.  I used scanbuttond a few years ago but haven't had need to try and set it up again.

---

### Post by caue.rego on 2010-01-12
Thanks for the response, **mocoloco**.

It seems very promising, but ...

I've been trying for the last hour or so to make it work. There's a lot to read and not much to do. I've configured it, used make and make install. I can't make it run. It says:
> Unable to load backend library "/usr/local/lib/libscanbtnd-backend_meta.so"!


Which is a compiled and most likely the main file.

---

### Post by JBAlaska on 2010-01-12
You need to run ldconfig, I think.

---

### Post by caue.rego on 2010-01-12
> **JBAlaska said:**
> You need to run ldconfig, I think.

From this doc: [http://en.gentoo-wiki.com/wiki/Scanner_buttons_and_one-touch_scanning](http://en.gentoo-wiki.com/wiki/Scanner_buttons_and_one-touch_scanning) you are probably right. But I'm still clueless on how to do that.

And now there's that another option, the KScannerButtons, which was made on top of HP and is newer, thus a better chance of success. But I can't even make "make install" work on that one.

---

### Post by caue.rego on 2010-01-12
Well, I got some progress with scanbuttond, and it just can't find my scanner! :(

It was just running "ldconfig" on the same directory where I finished off the "make install" before.

> 
/var/log/debug:Jan 12 15:00:33 bs00-server scanbuttond: running scanner initialization script...
/var/log/debug:Jan 12 15:00:33 bs00-server scanbuttond: initialization script executed.
/var/log/debug:Jan 12 15:00:34 bs00-server scanbuttond: rescanning devices...
/var/log/debug:Jan 12 15:00:34 bs00-server scanbuttond: no supported devices found. rescanning in a few seconds...
/var/log/debug:Jan 12 15:00:36 bs00-server scanbuttond: rescanning devices...
/var/log/debug:Jan 12 15:00:36 bs00-server scanbuttond: no supported devices found. rescanning in a few seconds...


Trying my luck now with KScannerButtons.

---

### Post by caue.rego on 2010-01-12
Well, I hope someone who gets here hoping to solve their similar issue will have better luck than I.

The clues here are more than enough to try two different solutions that may work with other devices.

KScannerButtons also didn't work with my device:
> 
$ sane-nb-buttons --debug
Scanning for devices ...
hpaio:/usb/Officejet_J4660_series?serial=BR976FF0DD052W Hewlett-Packard Officejet_J4660_series all-in-one
Device has no buttons, bye...


I'm still left with the last hope of doing this: [http://en.gentoo-wiki.com/wiki/Scanner_buttons_and_one-touch_scanning#Your_Scanner_Isn.27t_Supported](http://en.gentoo-wiki.com/wiki/Scanner_buttons_and_one-touch_scanning#Your_Scanner_Isn.27t_Supported) or actually coding some solution.

Unfortunately I've got no time or enough knowledge (to reduce time needed) to go that far. For now, I'm obligated to give up on this path. :(

Any other ideas on how I could remotely and easily trigger the script?

My only other idea would be installing lampp (which seems complicated enough), opening some HTTP port, making a PHP script to run the shell commands (or script) all just for what should be done with a single scanner button press.

---

