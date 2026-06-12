---
title: "Evolution Email Issue"
date: 2011-09-20
forum: General Help
---

### Post by hayesc1975 on 2011-09-20
Hello. My first post so please be gentle.

I'm having a massive email issue thats driving me nuts at the moment. I'm running Maverick Meerkat 10.10 on a Dell Latitude D420.

The issue is that I'm trying to configure a POP3/SMTP account on Evolution and I'm getting some very strange results. Basically at the moment it's not sending or receiving emails. It says that it cannot reach the destination POP3. It can. I can ping the address of pop3.hosts.co.uk. It can also ping smtp.namesco.net.

I've done a bit of google research and I've looked at the following areas.

1) I've doubled checked the pop3 and smtp account details. These are correct as confirmed by the ISP and their support team.

2) I've made sure that the evolution network preferences go "direct connection to the internet" rather than "use system defaults". When I changed this earlier, everything fired into life and I received 4 messages and sent 1. Then it stopped and couldn't receive the reply I made to the sent item which was sent to my internet email address.

3) I've tried in Evolution to "forget password" both with the pop3 password check box ticked and untick, plus I've closed and restarted Evolution in addition to hard reboots. I can no longer get Evolution to prompt me for the password. This is where evolution differs to MS Outlook where there is a specific box for the POP3 password.

4) I've tried to delete the keychain and reset the passwords to blank passwords as suggested in another forum thread.

5) I've also tried using kmail (but I get SMTP certificate error messages whilst sending) and thunderbird doesn't seem to have anything but a IMAP outgoing mail box in the default setup and you can only seem to add specific details for the SMTP server in the account settings.

Could it be related to the keychain? I seem to remember it asked me to enter it very soon after entering the POP3 password when prompted for the one and only time. Why doesn't Evolution actually forget the password when you ask it to? Coming from a background in Microsoft IT support I love Ubuntu but I do get a little bit annoyed when the client caches configuration passwords rather than having to specify them along with all the other config details.

Any help or light shedding would be much appreciated.

Chris

---

### Post by dcstar on 2011-09-20
> **hayesc1975 said:**
> Hello. My first post so please be gentle.

I'm having a massive email issue thats driving me nuts at the moment. I'm running Maverick Meerkat 10.10 on a Dell Latitude D420.

The issue is that I'm trying to configure a POP3/SMTP account on Evolution and I'm getting some very strange results. Basically at the moment it's not sending or receiving emails. It says that it cannot reach the destination POP3. It can. I can ping the address of **pop3.hosts.co.uk**. It can also ping **smtp.namesco.net**.
........
Any help or light shedding would be much appreciated.

Chris
This is working:
```
*telnet **pop3.hosts.co.uk** 110*
Trying 85.233.160.80...
Connected to pop3.hosts.co.uk.
Escape character is '^]'.
+OK Namesco MUA Server Ready
*quit*
+OK Logging out
Connection closed by foreign host.
```
This is not:
```
*telnet **smtp.namesco.ne**t 25*
Trying 85.233.160.18...
Connected to smtp.namesco.net.
Escape character is '^]'.
Connection closed by foreign host.
```

---

### Post by hayesc1975 on 2011-09-20
> **dcstar said:**
> This is working:
```
*telnet **pop3.hosts.co.uk** 110*
Trying 85.233.160.80...
Connected to pop3.hosts.co.uk.
Escape character is '^]'.
+OK Namesco MUA Server Ready
*quit*
+OK Logging out
Connection closed by foreign host.
```This is not:
```
*telnet **smtp.namesco.ne**t 25*
Trying 85.233.160.18...
Connected to smtp.namesco.net.
Escape character is '^]'.
Connection closed by foreign host.
```

Thanks for that David. It's now working with Outlook 2007 but still no joy on Evolution. Question is what's causing the SMTP issue on Evolution?

---

### Post by haqking on 2011-09-20
> **hayesc1975 said:**
> Thanks for that David. It's now working with Outlook 2007 but still no joy on Evolution. Question is what's causing the SMTP issue on Evolution?

Whenever i experience SMTP issues but i know the server is working, i change to port 587 instead of 25 if they support it and it generally works. though this could effect relaying

---

### Post by dcstar on 2011-09-21
> **hayesc1975 said:**
> Thanks for that David. It's now working with Outlook 2007 but still no joy on Evolution. Question is what's causing the SMTP issue on Evolution?

I see that SMTP server is only accessible from direct connections to that ISP, so that is why my attempt fails.

As far as your other issues go, the setup instructions look straightforward and they should work if you are putting in the correct information.

Rename the (hidden) .evolution folder in your system and start Evolution to create a fresh profile.

---

