---
title: "email spam bot??"
date: 2010-09-24
forum: General Help
---

### Post by choochoousmc on 2010-09-24
I have Unbuntu 10.04lts  Use Thunderbird email
Lately I have noticed that I am getting email from people in my address book.
At least it appears that way.
I check the properties and headers and the correct return address of the sender is there.
But the person really didn't send the email.
The email normally has  just a  web link url in it, that I know is a spam link.

I have the default antivirus installed and run it regularly.
But I don't think it is designed to find this type of bot problem.
I'm not sure if I am infested or if several people in my address book are infected.
I wrote them and told them of the problem. Couple of them said other people have notified them of the same thing. I suggested they get help from their ISP in getting the BOT removed from their system.

What linux product can I use to determine if my address book / computer has been
compromised and get rid of this bot in case I am infected?

---

### Post by Joe of loath on 2010-09-24
If you're getting spam from them, but they're not getting any from you, it's their problem. AFAIK the only spambots for Linux run on mail servers, so it's pretty much impossible to be infected yourself.

---

### Post by lisati on 2010-09-24
It could be [malware]("http://lisati.homelinux.com/wiki/index.php/Malware") of some kind on a mutual acquaintance's machine. 

You can't trust the "From" or "Reply-to" email addresses as a source of information on the origin of the offending email. A more reliable source is the last "Received" header in the email. 

There are a number of tools available online to help you analyse the email's headers. I use the [Spamcop]("http://spamcop.net") reporting service to analyse incoming spam and figure out who to send a response to (if any).

---

