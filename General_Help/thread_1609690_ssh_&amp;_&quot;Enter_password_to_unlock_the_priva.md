---
title: "ssh &amp; &quot;Enter password to unlock the private key&quot;"
date: 2010-10-30
forum: General Help
---

### Post by jeeves on 2010-10-30
Since upgrading to Meerkat, I have been getting a pop-up window with the message "Enter password to unlock the private key" every time I attempt to *ssh into a server that does NOT use password authentication.* I know some people like the remember password "feature", but I prefer just a plain unadulterated ssh session in a terminal. Does anyone know how to stop this message? So far I have unsucessfully tried:

[LIST]
[*]running **gconftool-2 --set /apps/gnome-keyring/daemon-components/pkcs11 --type bool "0"**

[*]running **gconftool-2 --set /apps/gnome-keyring/daemon-components/ssh --type bool "0"**

[*]commenting out "**use-ssh-agent**" in /etc/X11/Xsession.option

[*]running sudo sysv-rc-conf and looking for a "seahorse" daemon to deselect (never found one!)
[/LIST]

None of the above worked - and I was sure to log out and back in before testing the behavior.

---

### Post by hwttdz on 2010-10-30
What's the output of ssh -v user@host (I wonder if it might tell you exactly what it's doing when it prints that message)?

---

### Post by llamabr on 2010-10-30
You have a server somewhere on the internet which accepts ssh without a password?  What's the IP?

---

### Post by jeeves on 2010-10-31
> **llamabr said:**
> You have a server somewhere on the internet which accepts ssh without a password?  What's the IP?

What I meant is I disabled password authentication in the sshd_config file on the server  machine and am instead using Public Key Authentication.:)

hwttdz - thanks for the "ssh -v" tip but the debug messages are not shedding any more light on this. Interestingly enough, if I login to my system without using the GUI I don't experience this problem with SSH.

---

### Post by jeeves on 2010-10-31
May have a possible fix here. If no negative untended consequence  show up after a few days I will mark this thread as SOLVED. 

The fix for fellow Xubuntu users is to **Applications > Settings > XFCE4 Settings Manager > Sessions and Startup** and click on the "Advanced" tab. From there you want to *uncheck* "**Launch GNOME services on startup**" I rebooted, to apply the setting, but you could probably just log out and back in again.

I don't use the gnome keyring daemon for network connections or anything, so this solution seems to work for me  so far.

If you are a regular Ubuntu user where it may not be good idea to disable Gnome services you could try some of the suggestions here:

[[COLOR="Blue"]Gnome Keyring SSH Agent[/COLOR]]("http://live.gnome.org/GnomeKeyring/Ssh")

Another less convenient work-around is to preceed you SSH command with **SSH_AUTH_SOCK=0** So logging into a server becomes:

**SSH_AUTH_SOCK=0 ssh user@server**

*No idea what the security implications are for using SSH_AUTH_SOCK=0*

---

### Post by uzusan on 2011-11-11
I was having a similar issue to this after upgrading to 11.10 and kept getting the Enter passphrase for /home/username/.ssh/id_rsa: 

I found out that running ssh-add readded my keys and now i dont get that message anymore. This may also work for the gnome keyring.

---

### Post by nothingspecial on 2011-11-11
Thanks for the input. :)  But old threads need to stay underground.

Closed.

---

