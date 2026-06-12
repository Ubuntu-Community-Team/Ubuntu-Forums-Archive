---
title: "CrossOver - MS Outlook 2007 - Exchange"
date: 2010-03-29
forum: General Help
---

### Post by YankeeFan on 2010-03-29
Greetings all-
Sorry if this is in the wrong section.  I wasn't exactly sure where to post it.

I have the latest version of Ubuntu installed on my Windows XP machine in a dual boot setup.  I installed Crossover software in Ubuntu to allow me to install and use Microsoft Outlook while in Ubuntu.

The installations went fine, but I have a problem connecting to out exchange server.  During my email account setup in Outlook, there is the option to enter the username and the exchange server name.  When I click "check username" the setting for the exchange server change to the exact (correct) name of our exchange server.  So, I know it must see the server in order to get the name correct.

When I complete the setup, I get prompted to log into the account on the exchange server.  This is the problem.  I enter my password and it just flashes and prompts me for the password again, and again, and again....  I know the password is correct and entered correctly.

I was hoping someone out there may have been through this or might know what I need to do to get this to work.  Note: Excel works fine, but Word does not.  Probably Word is tied to Outlook and it prompts me for the password on exchange.

Thanks for any help.
YankeeFan--

---

### Post by labinnsw on 2010-04-05
I believe when you log on to your network on your computer, you have access for all applications for that session. If I am right, then the password that you may need to supply would be your Ubuntu administration password. 

Which version of Office are you using? Up to 2007, Word should work out of the box.

---

### Post by Mark Phelps on 2010-04-05
Unless someone else knows for a fact that this CAN be done, the info at the WinHQ site implies that it can NOT.  See the ratings on the link below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=34]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=34")

---

### Post by labinnsw on 2010-04-06
Some stuff work on Crossover but not on wine. [http://www.codeweavers.com/compatibility/browse/name/?app_id=2841](http://www.codeweavers.com/compatibility/browse/name/?app_id=2841)

---

### Post by greenchilli on 2010-05-20
I've have Outlook working on Ubuntu Lucid through Crossover.

I had this same issue where the connection to Exchange asked me for password even though the credentials seemed correct. The problem is not with the password being incorrect. The problem is with the user name.

To make this work you need to enter your user name with the domain name of your network in front. i.e.

Domain login details: bob.segar

Try this instead: domainname.com\bob.segar

It should work...:P

---

