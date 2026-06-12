---
title: "Can't read my hotmail in Ubuntu"
date: 2011-05-29
forum: General Help
---

### Post by rva1945 on 2011-05-29
Since a couple of days, I can't read my Hotmail mail. I log in and I see that I have N new unread messages, but when I go to the inbox, the list appears but I can't access to any email. Not even those emails I have already read.

When I place the cursor on any subject, the arrow turns to a hand, I mean, it detects that it's a link, in the status bar instead of the link it says "Javascript:;", but it doesn't respond to the clicks. The same happens with the folders at the left. The mouse clicks don't work there.

Of course I can navigate to any other site, yahoo mail, whatever.java or not java.

The problem happens in Firefox, Chrome, and even in IE in the Windows XP Virtual machine. I tried with my wife's hotmail account with the same results. The people I know that have Hotmail can read their emails with no problem.

I tried disabling the SPI firewall in the wireless router, and the FLOOD and DoS fltering, but to no avail.

I wonder if anyone had the same problem, as it even happens in the Windows virtual machine -ubuntu being the host, does it have something to do with Ubuntu or any update?

---

### Post by cmcanulty on 2011-05-29
There was an old thread on this. Go to in firefox edit-preferences-advanced-network-clear offline storage

---

### Post by rva1945 on 2011-05-29
Ok, but what about IE in Windows?

Well I triend to clear the offline storage in Firefox, I click on Clear Now, but it seems as if nothein happens, no messages no nothing.
And it still won't work.

---

### Post by linuxinstalledfromhdd on 2011-05-29
Try running bleachbit to clear out everything.

sudo apt-get install bleachbit

sudo bleachbit

---

### Post by lemonchicken on 2011-05-29
tor browser?
If javascript's working to some extent you can right click the message and 'view message source'.

---

### Post by Frogs Hair on 2011-05-29
There was a message from Hot Mail about changes users would have to make if using certain email clients and mobile devices last week . I don''t   if this has anything to do with your current problem . I have moved my mail to a different provider , but still have a Hot Mail account .

---

### Post by Frogs Hair on 2011-05-29
Here is the message I received.

Hi,

 You are receiving this note because you have connected to Hotmail from devices such as smartphones or programs like Mac Mail and Mozilla Thunderbird. These smartphones and programs often include an option that automatically deletes messages from Hotmail after they are downloaded (they often use the "POP3" protocol). Because this option is sometimes selected accidentally, we've made some updates to Hotmail to make sure those messages aren't deleted automatically unless you tell us otherwise. 

 What's changing? 
 When we detect that another program wants to delete Hotmail messages, instead of just deleting them, we will move them into a temporary POP folder on url for safe keeping until you tell us what you'd like to do. 


 What do you need to do? 
 Depending on how you'd like messages to show up when you access Hotmail on the web, please take one of the following actions: 
If you want to delete messages from the web version of Hotmail after they are downloaded to your program, sign in to url and choose "POP and deleting downloaded messages" on the Options page.
If you'd like to see your messages on both your Hotmail inbox at url and on your smartphone or program, open the program that's downloading the messages and go to its POP settings. Look for a "delete messages from the server" option and turn it off.
Please note that this does not affect smartphones or programs that connect to Hotmail in other ways (e.g. smartphones with Exchange ActiveSync, Microsoft Outlook with Outlook Hotmail Connector, or Windows Live Mail). 

 Questions? 
 Visit the Windows Live Solution Center. 


 Thank you for using Windows Live Hotmail. 

 Sincerely, 

 The Hotmail Team 

 As part of this new offer, Microsoft may provide feature tips and product information, but there will continue to be no third party advertising. 
 Microsoft respects your privacy. To learn more, please read our online Privacy Statement. 
Microsoft Corporation
 One Microsoft Way
 Redmond WA 98052 


	 
  		  


.

---

### Post by silex89 on 2011-05-29
Have you thought about using a client to fetch your messages to your HDD?, I would highly suggest you to use Mozilla Thunderbird, it's wizard to manage accounts is just awesome. It's just a matter of put your username and your password and Thunderbird does all for you. You don't even have to edit the configuration because the program resolves the best ports and servers to receive and send your e-mails


Best Luck :D

---

### Post by rva1945 on 2011-05-29
But my problem is not with deleting files. The problem is, or, was because now it seems to be fixed (not by me, I had given up the fight), that the list of emails appear but I couldn't access to any, not even to the folders.

I repeat, now it seems fixed, but who knows if forever...I'm considering using Evolution Mail. But first I'll have to delete hundreds of emails because it's taking a while for Evolution Mail to sync local folders.

Thanks

---

