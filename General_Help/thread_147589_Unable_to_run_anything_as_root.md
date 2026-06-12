---
title: "Unable to run anything as root"
date: 2006-03-20
forum: General Help
---

### Post by teoryn on 2006-03-20
Whenever I try to run anything that requires root (i.e. any sudo command in terminal, most anything under System>Administration>, etc) I am prompted for the password, which I enter correctly (it complains if it's wrong), but then nothing happens usually. In the case of a couple things like System>Administration>Services a tab on the bottem bar appears with the text "Starting Services", but that then closes a few seconds later.

Thanks in advance,
Kevin

---

### Post by IYY on 2006-03-20
What happens if you try to run a console command using sudo? For example, "sudo echo hello world". Does it just hang? Or does it finish execution without doing anything?

---

### Post by Beowolf on 2006-03-20
Hi Kevin,

Is your username the first one that was created during installation? Only that one has  access to sudo AFAIK.

---

### Post by teoryn on 2006-03-20
Running "sudo echo hello world" I am prompted for my password and then nothing happens.

And yes, I am on the first and only username I created during installation.

---

### Post by RavenOfOdin on 2006-03-20
That happened to me a month or so ago too.
Are you in the "admin" user group? (Under System > Administration > "Users and Groups" > Groups > admin > Properties in GNOME, or /etc/group in terminal.)

---

### Post by teoryn on 2006-03-20
RavenOfOdin, I am unable to open System > Administration > Users and Groups.

---

### Post by RavenOfOdin on 2006-03-20
[QUOTE=teoryn]RavenOfOdin, I am unable to open System > Administration > Users and Groups.[/QUOTE]

Then boot into recovery mode as root and open up /etc/group.

Find the line in it that says:

adm: x:4:

and make it like this:

adm: x:4:<your username here>

Then reboot to normal mode and see if it worked.

---

### Post by teoryn on 2006-03-20
The line adm:x:4:kevin was in /etc/group already, and it's still behaving the same.

---

### Post by RavenOfOdin on 2006-03-20
Ugh.

Sorry dude, you'll have to wait for someone else to chip in on this, seeing as I'm all out of ideas.

---

### Post by FLeiXiuS on 2006-03-20
Did you enable the root account?

---

### Post by teoryn on 2006-03-20
Just tested this:

I can do "su root" enter my password, and I'm able to work as root in a terminal.

I guess that means I enabled the root account.

---

### Post by FLeiXiuS on 2006-03-20
[QUOTE=teoryn]Just tested this:

I can do "su root" enter my password, and I'm able to work as root in a terminal.

I guess that means I enabled the root account.[/QUOTE]
I thought so :-P.  Yes, it's more security efficient to have this account disabled as there is really no need for it with sudo capabilities.  SUDO will give that specific user fake root access.  

```
$ su root -c "passwd -d root"
```

That should remove the password for the root account.  Afterwards gnome may be a little sketchy about the password indifference.  I'd reccomend a re-login!

---

### Post by teoryn on 2006-03-20
sweet, thank you, I'll try that.

---

### Post by teoryn on 2006-03-20
I reinstalled ubuntu, incase I messed up somewhere there. I used the 'expert' mode (both this and last time) since I was having problems with the installer hanging on installing grub. It went fine, and I was in the same situation as before, so I ran ```
$ su root -c "passwd -d root"
``` but I'm still getting the same problem as before, apps just won't open.

Also new this time there's and icon in the upper right telling me 69 updates are available, but it won't do anything thing other than pop up a selection of options when I right click it (none of which work).

---

