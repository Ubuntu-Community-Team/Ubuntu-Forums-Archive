---
title: "Evolution mail not able to send to certain external ISP e-mail accounts"
date: 2006-03-31
forum: General Help
---

### Post by maxsteiner on 2006-03-31
Hello,

  I have a strange problem that is occurring on our computers with Ubuntu Hoary Hedgehog installed.

  These computers are located in various schools in our city and are set to send and receive e-mail from our server here in our main office that has Ubuntu - Breezy Badger installed with HULA.  These e-mail client computers send and receive messages using Evolution Mail.

  The people using these client computers, can send to recipients who have two specific internal domains, in our company, but not to any domains that are external and are configured on seperate ISPs.  When they try to send to these e-mail addresses,they receive a **<RCPT to address [email]xxxxxxxx@xxx.xx[/email] failed - cause unknown>** error.

  They can, however, receive messages from these external ISP e-mail addresses with no problem on their UBUNTU - Hoary Hedgehog computers.

  I can, however, send and receive messages to these external ISP e-mail addresses by connecting to http://<e-mail server address>:8080 and logging on with various e-mail accounts that we have set up on our HULA server.

  One more thing I need to mention, these computers are set up with local accounts that do not have "sudo" priviledges and Firestarter is installed to only allow Port 25 to be used internally and externally.  We have not given them access to surf on the internet.

  We have ruled out the possibility that the schools' firewalls may be interfering because these computers can not even send messages to the schools staff e-mail addresses which are not blocked on their firewalls.

  Any advice that you can offer would be greatly appreciated.

  Thanks in advance

  Regards,

  Max Steiner

---

### Post by maxsteiner on 2006-04-10
Hello again,

  I configured Thunderbird and am able to send messages to any external ISP e-mail account.

  Evolution does have more features, including a calendar, and I would prefer using this application if it is possible.

  Do you have any ideas why Evolution would give a RCPT error when trying to send messages to certain e-mail domains when Thunderbird does not have this problem?

  Thanks

  Max Steiner

---

### Post by rajan on 2007-02-10
Hey Max,
 I hope this isn't too late for you, but I had the same problem and I found a fix for it and posted it here:

[http://www.ubuntuforums.org/showthread.php?p=2134791](http://www.ubuntuforums.org/showthread.php?p=2134791)

rajan

---

