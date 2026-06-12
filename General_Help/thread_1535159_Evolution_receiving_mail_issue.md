---
title: "Evolution receiving mail issue"
date: 2010-07-20
forum: General Help
---

### Post by M4he on 2010-07-20
Dear ubuntu community,

I'm missing an (imo) important feature in Evolution.

When I boot up linux, it logs me in automatically. Then it asks for the keyring password to enable my WLAN connection, since it's password protected. Therefore there's no available internet connection until I type in the password. I've set Evolution to start when I log in. Therefore it tries to receive e-mail as soon as I log in.
The problem is, the receiving of e-mails fails because my WLAN isn't activated instantly and Evolution prompts me to type in the passwords for my 3 e-mail accounts, which is very annoying.
I've been looking for an option to disable the automatic receiving of e-mails at startup but I found nothing. (any other e-mail program I used so far had such an option)

For short: Evolution should not receive e-mails at startup but after the adjusted interval (I've set the receiving interval to 20 minutes).

Is this possible?

Thanks in advance!

---

### Post by J V on 2010-07-20
If you have an encrypted home (Or don't really care about security) set the password for your keyring to blank so it will get the wifi pass instantly... You could also change the startup command for evolution to wait a few seconds first... ("sleep 10" for example)

---

### Post by M4he on 2010-07-20
Thanks for the tip with the keyring! I wanted to get rid of the password request at startup anyway.
How do I use the sleep command? "sleep 5 evolution" (without the quotes) doesn't seem to work.

---

### Post by ajgreeny on 2010-07-20
```
sleep 10; evolution
``` will do it but only for 10 secs.  For a longet time you need to specify minutes as ```
sleep 10m; evolution
```
See **man sleep** for more, though it's not very revealing, and gives no examples.

---

### Post by M4he on 2010-07-20
In startup applications I changed the command to:
```
sleep 10; evolution
```but it's not working. It simply doesn't start.

---

### Post by ajgreeny on 2010-07-20
> **M4he said:**
> In startup applications I changed the command to:
```
sleep 10; evolution
```but it's not working. It simply doesn't start.
Very odd!

Try the command in terminal to see what happens, and what error message, if any, are generated.  The command certainly works OK here, as I have just tried it, though I don't use evolution for my mail.  I do, however use the sleep option for another startup application command, **sleep 10; conky**

---

### Post by M4he on 2010-07-20
It's working in the terminal. However, it doesn't work with the startup applications nor with a starter on the desktop. Very odd indeed...

---

### Post by dcstar on 2010-07-21
> **M4he said:**
> It's working in the terminal. However, it doesn't work with the startup applications nor with a starter on the desktop. Very odd indeed...

Of course not, they are **not** shell environments so shell commands will not work - they are simply launchers.

Make a shell script with those commands and launch that.

---

### Post by ajgreeny on 2010-07-21
Silly me!!   I must have gone brain dead for a while there.

Of course you need it as a script which you link to in Startup Applications.  This is how I do it for conky, but I was just not thinking quick enough, as happens from time to time.

---

### Post by M4he on 2010-07-21
No problem ajgreeny =)
I made a shell script and it's working now, thanks guys!
I'll mark this as solved.

Thanks for all your efforts!

---

### Post by J V on 2010-07-21
Hmm, last time I checked some basic bash was allowed in launchers - something like "sleep 10 && evolution" rather than ";"

---

### Post by ajgreeny on 2010-07-21
> **J V said:**
> Hmm, last time I checked some basic bash was allowed in launchers - something like "sleep 10 && evolution" rather than ";"
Not on my machine, it doesn't.  Or not for my conky launch at least, for which I normally use a shell script, (the one I forgot about earlier).

---

