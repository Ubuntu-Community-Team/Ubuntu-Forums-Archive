---
title: "Using Thunderbird with Sendmail"
date: 2006-02-25
forum: General Help
---

### Post by Ingla on 2006-02-25
Hello.

In my continuing attempt to switch completely to Linux, I'm trying to achieve a function that I use under Windows with no problem...sending e-mails from my desktop, bypassing my ISP's smtp server and that of my web hosting company.

The reason is simply that both of them have very low sending limits which don't allow me to send to my mailing list of a couple hundred recipients (at least not legally).

On Windows, I use two programs for this purpose. One is GroupMail, which allows me to write a text message and attach an HTML file, which the program combines into a mulitpart message that can be viewed in the appropriate format by each recipient...just like a message created in an e-mail client. The program also maintains mailing list and I can send the message to a given list with a click.

Groupmail is configured to pass the messages to a program called PostCast Server, which is a desktop smtp server. It mails to the recipients and can be configured to alter the helo handshake as I wish. This is necessary because some recipient servers check the reply-to address against the sender's domain ID and reject messages where the two don't match. Obviously, my machine name doesn't match the domain of my return address, so I have to make it appear as if I'm using my host's smtp address. That way, messages get through and any replies go to my address at my host and are received in the usual manner via an e-mail client.

I'm trying to find a way to do all this on Linux. However, I'm not able to find software for the purpose.

Someone told me that sendmail can do the job and that I can send from Thunderbird via sendmail.

So far, I haven't been able to get this to work. I'm running Ubuntu 5.10. Sendmail seems to be present, as I get this:
-----------------------------------------------------------------------
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 localhost.localdomain ESMTP Sendmail 8.13.4/8.13.4/Debian-3; Sat, 25 Feb 2006 20:23:30 +0200; (No UCE/UBE) logging access from: localhost.localdomain(OK)-localhost.localdomain [127.0.0.1]
Connection closed by foreign host.
------------------------------------------------------------------------
I don't really know what this means, except that sendmail is there. I don't understand the part about "no access" or about the connection being closed by "foreign host".

I made an additional smtp in Thunderbird, called localhost, and set it as default. However, Thunderbird seems still to be using my ISP's smtp server (which I have not removed from the list). I don't know why that would be the case unless sendmail isn't working or isn't configured properly.

Can anyone help with this?

Thanks.

---

### Post by Ingla on 2006-02-26
Did I just get unlucky and post this when no one was online, or is there nobody who uses Thunderbird to send via sendmail?

---

### Post by nix4me on 2006-02-26
My guess is that most people have not used sendmail at all.

My only advice is sendmail documentation and google.

nix4me

---

### Post by dcstar on 2006-02-27
[QUOTE=Ingla]Did I just get unlucky and post this when no one was online, or is there nobody who uses Thunderbird to send via sendmail?[/QUOTE]
Do a "man postfix" as Sendmail is a frontend to that package in Ubuntu.

You can also search for various postfix items in the forum, there are various HOWTOs on setting up mail servers.

---

