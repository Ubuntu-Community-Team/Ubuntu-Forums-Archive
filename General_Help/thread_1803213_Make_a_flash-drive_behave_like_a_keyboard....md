---
title: "Make a flash-drive behave like a keyboard..."
date: 2011-07-13
forum: General Help
---

### Post by amithaba on 2011-07-13
Not sure where to post this but here it goes anyway...

I am verry curious whether it is possible to make a flashdrive behave like keyboard. I recon there must be some good reasons not to. Because I can imagine some situations where this comes in verry handy... Like this one:

For my job I have to login +-30 windows pcs with different usernames and different random passwords.

For example a script that executes gives login tab password enter
and readies the next login for the next computer.
This way I could just plug the flashdrive in, let type, plug it out and continue.

I could log in the whole classroom without typing anything.

I have googled and tried, but I haven't found anything... yet...
Any thoughts?
Cheers

---

### Post by Mark Phelps on 2011-07-13
The result you want is reasonable but your request is faulty.

A flash drive is a storage device; a keyboard is a data entry device.  They have totally different functions.

However, what you could do is create a BASH script that will do the logins, save that script to the USB drive, plug in that drive, and run the script.

Unfortunately, it's been a LONG time since I did anything in BASH.  So, I can't provide you the code needed to do this. Sorry.

---

### Post by HermanAB on 2011-07-13
Yes and no...

You cannot make a regular off the shelf flash drive behave like anything other than a flash drive, since it is controlled by a little hardware chip which only does one thing.

However, you could build a a device that could behave like anything if you give it some smarts.  So if you get a little Linux based microcontroller with a memory card and stuff it into a tobacco tin yourself then it could potentially act like any kind of USB device.

---

