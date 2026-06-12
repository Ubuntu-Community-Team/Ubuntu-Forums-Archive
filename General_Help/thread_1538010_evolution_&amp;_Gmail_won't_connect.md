---
title: "evolution &amp; Gmail won't connect"
date: 2010-07-24
forum: General Help
---

### Post by donach on 2010-07-24
I've spent ages trying to get evolution & Gmail to talk to each other. Whenever I press Send/receive it tries then I get 'Error while Scanning folders in "IMAP server imap.gmail.com" '. I've tried changing the ports etc, deleting the account from evolution and redoing it. I've looked thru various forums and walkthroughs. I've checked that the right password is stored in the keyring. I'm sure all my settings are right, but evolution can neither sync with my inbox nor send emails.
I have synced my google contacts and calendar with evolution, however.
I use my Gmail on a variety of devices so I don't want to use POP and in any case SMTP isn't working either.
I'm running ubuntu 10.04 on an acer 5738 thru a not particularly fast ADSL connection.

---

### Post by robbienam on 2010-09-10
I had had the same error message as you: Error while scanning folders in "IMAP server imap.gmail.com" and the solution in the following thread worked for me too:

[http://ubuntuforums.org/showthread.php?t=869632](http://ubuntuforums.org/showthread.php?t=869632)

Specifically, either when first setting up your gmail account within Evolution, or after it has been created, select your gmail account from the panel at left within the Evolution mail main page, then open the menu Edit->Preferences, which should bring up a new window. Within the new window select your gmail account again and click on the Edit button at right within the window. This will bring up a new window with many tabs. Select the Receiving Mail tab and make sure that under Security you have selected Use Secure Connection: "SSL encryption". I had originally set up my gmail account within Evolution to use "TSL encryption" for receiving and sending mail, and this produced the error message above (same as yours).

I have not tested sending mail yet. I still have Sending Mail set to TSL encryption, which may need to be changed as well, though I'm not sure about that.

The tutorial below was also helpful:

[http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml](http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml)

---

### Post by robbienam on 2010-09-10
Following up on my first response above, after a couple rounds of testing I repeatedly found that I could not send mail with "SSL encryption" selected under Sending Mail options, but could send with "TSL encryption" selected. This is the opposite of what I found for Receiving Mail (see my first response above for details).

In summary, the settings which are working for me  for gmail IMAP account within Evolution are as follows:

Following detailed menu instructions in above response,

Under "Receiving Mail" tab, choose "SSL encryption"

Under "Sending Mail" tab, choose "TSL encryption"

Hope this helps

---

### Post by donach on 2010-09-12
That doesn't work for me. I'd tried all SSL, TLS and no encryption, nothing seemed to work. At present its on SSL encryption.

---

### Post by nabsha on 2010-11-13
Dears,

I have followed all the tips and done all the tricks to use evolution with gmail but nothing seems to be working at the moment for me...

This is what I have already done

1. Enabled IMAP in gmail
2. Able to telnet to imap.gmail.com
3. configured account in Evolution/Thunderbird/Kmail a zillion times with settings defined in various logs. But without any luck.

Any assistance is appreciated.

Thanks.

Here is the logs from evolution which goes in the endless loop.



Get folder info(0x8662100:imap://ulta.current@imap.gmail.com/, '<null>') =
< 0 >
Camel SQL Exec:
INSERT INTO folders VALUES ( '.#evolution/Junk', 13, 0, 0, 0, 0, 0, 0, 0, 0, 0, NULL ) 
Sync for vfolder '.#evolution/Junk': 0 secs
Camel SQL Exec:
DELETE FROM folders WHERE folder_name = '.#evolution/Trash'
Camel SQL Exec:
INSERT INTO folders VALUES ( '.#evolution/Trash', 13, 0, 0, 0, 0, 0, 0, 0, 0, 0, NULL ) 
Sync for vfolder '.#evolution/Trash': 0 secs
Camel SQL Exec:
DELETE FROM folders WHERE folder_name = '.#evolution/Trash'
Camel SQL Exec:
INSERT INTO folders VALUES ( '.#evolution/Trash', 13, 0, 0, 0, 0, 0, 0, 0, 0, 0, NULL ) 
Sync for vfolder '.#evolution/Trash': 0 secs
Camel SQL Exec:
DELETE FROM folders WHERE folder_name = '.#evolution/Junk'
Camel SQL Exec:
INSERT INTO folders VALUES ( '.#evolution/Junk', 13, 0, 0, 0, 0, 0, 0, 0, 0, 0, NULL ) 
em_junk_sa_finalize
Sync for vfolder '.#evolution/Junk': 1 secs

---

