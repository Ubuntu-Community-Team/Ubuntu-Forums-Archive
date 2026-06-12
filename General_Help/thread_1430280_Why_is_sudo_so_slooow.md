---
title: "Why is sudo so slooow?"
date: 2010-03-15
forum: General Help
---

### Post by t0p on 2010-03-15
I've got an EeePC 701 with Jaunty installed.  It's set up with / mounted on the 4GB SSD and /home on a 4GB SD card that is permanently mounted in the built-in card reader.

When I issue a *sudo* command in terminal, there is a pause of 8 seconds after password input before the command is performed.  Once I've issued a *sudo* command, I can issue another within the 15 mins? of authorization without a delay.  But if I change to a fresh terminal, so I must input the password again, *sudo* again takes 8 seconds.

The delay is clearly due to a bottleneck in authorization somewhere.  I though maybe it's because I've got /home mounted on a USB interface.  But this didn't happen when I had Intrepid installed on the exact same hardware configuration.  It also doesn't happen if I run Karmic from a live USB stick.

Any ideas as to what's causing this?  And possible fixes?

---

### Post by kerry_s on 2010-03-15
did you do the /etc/hosts tweak?

127.0.0.1	localhost	your-computer-name

also, run "gksu-properties" & disable the grab, that will help with the gui root stuff.

---

### Post by t0p on 2010-03-15
Thanks for the tips kerry_s, unfortunately that hasn't done the job.  Anything else?

---

### Post by kerry_s on 2010-03-15
> **t0p said:**
> Thanks for the tips kerry_s, unfortunately that hasn't done the job.  Anything else?

nothing off the top of my head, i assume you skipped making a swap partition, so that stuff should be kept in ram. possible there's read speed issues.

---

### Post by anaconda on 2010-03-15
those small and cheap SSD disk are really slow to start reading. 
the delay might be just the delay for starting to read data from your SSD

I am not kidding!

I once tried to run my (old) acer aspire one from an external usb-hd, and it was really fast.. compared with the performance from the 8GB SSD disk..

You could make a RAM disk and copy some important executables to it.. tohose would start really fast..

---

### Post by t0p on 2010-03-15
> **anaconda said:**
> those small and cheap SSD disk are really slow to start reading. 
the delay might be just the delay for starting to read data from your SSD


But would that explain why I get the delay when supplying the password to authorise *sudo*?  I haven't noticed an appreciable delay for other tasks.  True, the EeePC is generally slow, but I've always put that down to the Celeron M 900MHz processor.  The EeePC is also slow when running other OSes.  But this delay with *sudo* authentication seems to be an issue with this installation alone.

> **anaconda said:**
> 
You could make a RAM disk and copy some important executables to it.. tohose would start really fast..

I shall look into that.  But if anyone else has suggestions as to the *sudo*authentication delay, I'd love to see them!

---

