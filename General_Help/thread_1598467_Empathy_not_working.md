---
title: "Empathy not working"
date: 2010-10-16
forum: General Help
---

### Post by onemanclapping on 2010-10-16
Hi!

I installed the new Ubuntu but Empathy seems to be always "crashing" when using MSN.

It doesn't freeze, you can navigate through the contacts, go to Preferences, see the Logs, etc, but you cannot open new chat windows nor recieve any chat messages - I asked people to send me messages and I received nothing...

I quit Empathy and start it again, but then it doesn't even load the contact list. The only way to get it ruunning again (for a few minutes) is to reboot the computer.

Does anyone else have this problem, know how to solve it or somewhere else better where I can ask this question?

Thanks in advance.

---

### Post by onemanclapping on 2010-10-21
Apparently, the problem is only with MSN accounts. I've added my Facebook and GTalk accounts and they are working.

But the MSN account does not work at all. It starts connecting and does not move from that point!

Some debug points:

- Tried adding another different MSN account, also does not work.

- Tried connecting the account in a web service (works) and without disconnecting, connect it with empathy: empathy makes the web service go down, saying the account is being used somewhere else. But empathy is still stuck at connecting.

- Tried the inverse thing: while logging in at Empathy, tried logging in at the web service. The following message appears at empathy: This resource is already connected to the server.

- Tried rebooting (obviously) and the "workaround" killall telepathy-butterfly. Neither work.

- Tried uninstalling and reinstalling the empathy package - same...

So, any ideas?

---

### Post by onemanclapping on 2010-10-21
SOLVED: [http://ubuntuforums.org/showpost.php?p=10003289&postcount=17](http://ubuntuforums.org/showpost.php?p=10003289&postcount=17)

---

### Post by b.charles.gagne on 2011-06-08
Digging back an old post but.. I get the same : ressource already connected to server error when trying to load empathy...

And i've checked and the line of code has been corrected to IME since i'm in natty narwhal...

---

### Post by lifelike27 on 2011-06-08
I've been getting the same problem as well on 11.04 64bit.

Odd this problem pops up after such a long time...

I've tried using Pidgin and it works on that. So it's only an Empathy problem.

---

### Post by linuxinstalledfromhdd on 2011-06-08
You can try using the latest testing PPA for empathy:

[http://ubuntu-tweak.com/source/telepathy-ppa/](http://ubuntu-tweak.com/source/telepathy-ppa/)

---

