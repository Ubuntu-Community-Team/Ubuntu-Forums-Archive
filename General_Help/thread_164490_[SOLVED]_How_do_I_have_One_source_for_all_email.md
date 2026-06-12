---
title: "[SOLVED] How do I have One source for all email"
date: 2006-04-22
forum: General Help
---

### Post by pappo on 2006-04-22
I have a network with three PC's.
1 Ubuntu, and 2 XP machines.
Does anyone know how to setup my network so all the mail I pull down from my ISP mail server is in one common spot.
I want to point all three PC's at one spot to retrieve mail, and only have the mail go away when one of the PC's deletes it.
Is that something Ubuntu could do ?

Regards

---

### Post by Ensnared on 2006-04-22
Best way to do this (imho) is to set up fetchmail on your Ubuntu-box and run an IMAP-server on it where the clients can connect and read mail from anywhere on the network, using any mail-program that supports IMAP (all modern mail-clients do this). The good thing with IMAP is the mail is stored on the server, so you'll be able to access your own mailfolders no matter where you log on from :)

I have this set up on my own network with courier-imap, fetchmail, maildrop, spamassassin and postfix. I've forgotten how exactly I set it up though as I did it ages ago while my server was running Red Hat 9.0, so I pretty much just used apt to install the packages and copied over all my configuration-files from Red Hat. But it should be pretty straight forward, and a google-search or two will get you a long way.

I'll be happy to answer any questions about it though, but right now I'm too tired to start digging around in my own config and writing up some detailed instructions (it's 3:30AM here) - I'll see what I can do tomorrow if nobody else comes up with something better first ;)

---

### Post by Mustard on 2006-04-22
I'm sure its possible.  The practicalities of how to do it would be beyond me though.  I often set up my email clients (on other linux installs) to not delete the mail on the server when they download so that I am assured of finding my email still on the mail server when I use my main linux email client.  As for the one common storage point, I think that's where my knowledge would fail.  I would assume you would want a standard client interface to make it easy.

---

### Post by cilynx on 2006-04-22
I would fetch the mail off of your ISP with the Ubuntu box and have it running an IMAP server.  I use courier, personally.  From there, you can use any machine that can talk to the Ubuntu machine as an IMAP client.  The wonder of IMAP is that changes take place on the server instead of the client.  Also, if you run Mozilla Thunderbird, you can run multiple clients concurrently and they update to each other's changes.  (Evolution does not yet support this setup.)

---

### Post by AndyCooll on 2006-04-22
The proper way is probably as ensnared says.

What I have is a box which is a file server. My file server is always switched on. It also has a partition where my /home directory is stored. Using NFS in my /etc/fstab I always mount this on my "Home" directory on all my other Linux boxes. So whichever pc I use on my home network whenever I logon I see the same "Home" folder. And when I open up Thunderbird it's using the same profile and hence opening up with the same e-mails.

When I ran XP I actually mapped "My Documents" to this /home partition on the server too. And from there I redirected the XP Thunderbird profile (in documents and settings) to look at the /my documents/.mozilla-thunderbird folder. 

This isn't as neat as ensnared's approach, but setting up an e-mail server has always looked to be a pfaff to me and this "dirty" method has so far worked fine for me.

:cool:

---

### Post by jonny on 2006-04-24
Just finished doing it... and it works like a dream.  I thought that I'd got lost a few times in the process, but I've just completed a successful test :grin: 

I followed [this guide from the wiki]("https://wiki.ubuntu.com/MailServer") and it worked perfectly.  As has been said above, you want to set up your mail clients to use IMAP, not POP, as that's a server-based system.

The only layer of complexity is that the guide assumes that you have your own domain name and that you want to send / receive mail from your Linux user name at that address (ie [email]yourlinuxname@yourdomainname.com[/email]).  I found it easier to get myself a free domain name from dyndns.org and to use that when I was completing all the settings - I guess that your router can handle dynamic DNS; most can these days.  When that's working, you can start to fiddle about with using fetchmail to pull mail from your existing email accounts.

If you follow the section of the guide on configuring Squirrelmail, you'll even be able to access your email from anywhere in the world, but make sure that you're careful with security, though.  I might be wrong, but I somehow think that would all be much more difficult and expensive under Windows.

---

