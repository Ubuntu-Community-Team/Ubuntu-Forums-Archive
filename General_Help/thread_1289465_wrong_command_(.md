---
title: "wrong command :("
date: 2009-10-12
forum: General Help
---

### Post by Xen0n on 2009-10-12
Hey. i accedently typed > mv /* .. because i would move the content folders in a subdir. and now, nothing works. i think i moved the whole system somewhere.... how do i get it back? :/ it was on my ubuntu server

---

### Post by Giblet5 on 2009-10-12
If you weren't root (uid = 0) then that command gave you a bunch of permissions errors.

Otherwise, it should have yielded command syntax errors since /. and /.. are the same physical directory. Hence, attempting to move /etc to /etc, etc. ;)

I'm not going to try it to see what it will do, but you might have some reinstalling to do........

---

### Post by Giblet5 on 2009-10-12
I looked at your command again.....

Where were you when you executed this command line?

If you were in your home directory (eg, /home/bob), SOME of that stuff got moved to /home and you got errors trying to move /home to a subdirectory of itself.

That would be a reinstall.

---

### Post by Xen0n on 2009-10-12
Sigh, -_-
It is a rented server so i'll have to pay for it ._.
i can't even connect to the server now -_-

---

### Post by Giblet5 on 2009-10-12
Yeah, sshd and pals aren't where they're supposed to be.

Advice: use the sudo command v su root and double-check every command you run as root before you ever type it in.

(We have ALL done this before)

---

### Post by PowerSource on 2009-10-12
once i typed somehting that gave the normal user all the rights to the /usr folder.
unfortunately root wasn't able to write there anymore X(

---

### Post by SPr on 2009-10-12
> **PowerSource said:**
> once i typed somehting that gave the normal user all the rights to the /usr folder.
unfortunately root wasn't able to write there anymore X(
ROFLMAO.

I did the same but for the command being recursive. Thank God for backups. (I remember now. It was a subdirectory and lower directories of /etc not /bin. I can't remember what I wanted to acheive though.)

Checking the commands before hitting enter only works if you don't hit enter too soon.

To the OP:
Bad luck and I hope you can get it fixed without too much expense. mv doesn't preserve ownership etc so moving the files and directories back won't help :(

---

