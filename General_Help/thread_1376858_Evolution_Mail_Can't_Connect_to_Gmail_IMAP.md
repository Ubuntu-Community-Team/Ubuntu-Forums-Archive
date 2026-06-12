---
title: "Evolution Mail Can't Connect to Gmail IMAP"
date: 2010-01-09
forum: General Help
---

### Post by Amagineer on 2010-01-09
I'm on a fresh Ubuntu 9.10 x86_64 install and I'm trying to configure Evolution to grab my email from Gmail using IMAP.

For receiving mail my server is set to imap.gmail.com:993 and my user name is [email]___@gmail.com[/email]

I'm using SSL and the authentication type is "Password"

If I click the "Check for supported types button, the "Please wait. Querying server for a list of supported authentication mechanisms." window pops up, but it never finishes.

When I try to sync my mail, evolution doesn't ask for my password, and the send and receive mail window displays my account as "Scanning folders in "IMAP server imap.gmail.com" indefinitely.

Running Evolution from the terminal doesn't seem to print any IMAP related errors only
```
** (evolution:5565): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
```

POP works fine, but that isn't really an option.

Can anyone give me a hand?

---

### Post by dcstar on 2010-01-10
> **Amagineer said:**
> I'm on a fresh Ubuntu 9.10 x86_64 install and I'm trying to configure Evolution to grab my email from Gmail using IMAP.

For receiving mail my server is set to imap.gmail.com:993 and my user name is [email]___@gmail.com[/email]

I'm using SSL and the authentication type is "Password"

If I click the "Check for supported types button, the "Please wait. Querying server for a list of supported authentication mechanisms." window pops up, but it never finishes.

When I try to sync my mail, evolution doesn't ask for my password, and the send and receive mail window displays my account as "Scanning folders in "IMAP server imap.gmail.com" indefinitely.

Running Evolution from the terminal doesn't seem to print any IMAP related errors only
```
** (evolution:5565): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
```

POP works fine, but that isn't really an option.

Can anyone give me a hand?

Turn off SSL and see what happens.

---

### Post by sigixv on 2010-01-10
did you disable pop and enable imap in gmail settings in the webmail using your browser?

According to gmail.com the settings you use should work unless you are downloading your entire gmail box instead of only the headers. I personally use pop, my read mails simply go into the "all messages" folder, so i do not know how to set a "download headers only"-thing in evolution...

---

### Post by Amagineer on 2010-01-10
My IMAP is enabled and my POP is disabled from the GMail web interface so that shouldn't be the cause of the problem.

And turning off SSL made no difference.

---

### Post by dcstar on 2010-01-11
> **Amagineer said:**
> I'm on a fresh Ubuntu 9.10 x86_64 install and I'm trying to configure Evolution to grab my email from Gmail using IMAP.

For receiving mail my server is set to imap.gmail.com:993 and my user name is [email]___@gmail.com[/email]
.........
Can anyone give me a hand?
See if you can manually connect to the server:
```
telnet imap.gmail.com 993
```

---

### Post by Pijar on 2011-12-16
I have the same situation - in Gmail configuration IMAP is enabled, Evolution says it tries to connect to imap.gmail.com, I also use 993 port to connect, according to Google instructions, and nothing happens. I haven't been asked for my password either. I can telnet to imap.gmail.com 993. I use 11.10 amd64.

---

### Post by Pijar on 2011-12-16
OK, it started to work - and it's not easy to say why it did.

I installed tshark to monitor packets between my station and imap.gmail.com. When I tried to use Evolution to check the Gmaul account, I saw only triple handshake packets (SYN, SYN-ACK, ACK) on imaps and nothing else. When I tried to check available password mechanisms I had a bunch of SSLv3 packets, as it was supposed to happen. I tried also to:

$ openssl s_client -connect 74.125.79.109:993

and it also presented nice SSL exchange. So I entered Preferences once again and I unmarked the "Remember password" field. It didn't change anything. Then I tried to go offline using the tiny icon in the down-left corner - but to no avail, I could keep on clicking and the icon stayed in the online mode. So I tried to go offline using the menu option but it didn't work as well. So I closed Evolution and opened it again. And it started working - I was asked form password and after entering it Evolution connected to Gmail service and synchronised. It seems that there is some problems with refreshing configuration and status in Ubuntu's Evolution and it's better to exit and enter and check the configuration.

The working configuration is: port 993, SSL encryption mechanism, and "password" password mechanism option.
[COLOR=#0000FF][/COLOR]

---

