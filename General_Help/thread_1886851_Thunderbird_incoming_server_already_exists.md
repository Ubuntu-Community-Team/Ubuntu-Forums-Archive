---
title: "Thunderbird: incoming server already exists"
date: 2011-11-25
forum: General Help
---

### Post by jonnyboysmithy on 2011-11-25
I'm using thunderbird 3.1.15 on ubuntu 11.04 and I'm trying to add another mail account. I go through the account setup process, it correctly detects the incoming and outgoing mail servers but then when I click 'Add mail account' I get the error 'incoming server already exists'. What can I do about it?

---

### Post by jonnyboysmithy on 2011-11-27
Anyone??

---

### Post by pretty_whistle on 2011-11-27
You may fix it by restarting the computer and then trying to do it.  But first delete the account info you were entering so after the restart it can start from the beginning.

I have Thunderbird and I'm not getting what you got.

---

### Post by bluexrider on 2011-11-27
You should use the HELP button at the top of Thunderbird 
While in Thunderbird F1


[http://support.mozillamessaging.com/en-US/kb/faq-changing-imap-pop?s=incoming+server+already+exists&as=s](http://support.mozillamessaging.com/en-US/kb/faq-changing-imap-pop?s=incoming+server+already+exists&as=s)


                        This tutorial will show you how to configure a new account for POP access (rather than IMAP). 
1. Select **Tools | Account Settings... | Account Actions | Add Mail Account **. 

     [IMG]http://support.mozillamessaging.com/media/uploads/gallery/images/2011-03-14-10-07-37-02d73d.png[/IMG]   


2. Enter your username (check with your mail provider; it is your full email address) and password and click **Continue**. 

     [IMG]http://support.mozillamessaging.com/media/uploads/gallery/images/2011-03-14-10-05-41-f58c3c.png[/IMG]   

3. Thunderbird will attempt to configure your accounts settings automatically using IMAP. Click **Stop**. 

     [IMG]http://support.mozillamessaging.com/media/uploads/gallery/images/2011-03-14-10-05-40-baf297.png[/IMG]   

4. Enter your account details as follows:  
 
[LIST]
[*] Username: Enter your full email address (or whatever your email  provider recommends, usually your full email address, although  sometimes just the part before the "@").
[*] Incoming: Enter your incoming email provider's server (usually "[mail.yourmailprovider.com]("http://mail.yourmailprovider.com/")" or "[pop.yourmailprovider.com]("http://pop.yourmailprovider.com/")", for example  "[mail.argontech.net]("http://mail.argontech.net/")").
[*] Outgoing: Enter your outgoing mail provider's server (usually "[mail.domainname.com]("http://mail.domainname.com/")" or "[smtp.domainname.com]("http://smtp.domainname.com/")").
[*] Select "POP" from the drop-down list to the right of the  incoming mail server name (the row labelled "Incoming:" in the  screenshot). **This is important because if IMAP is selected you won't be able to change it to POP later!**
[*] Incoming port number: This depends on the email provider.
[*] Outgoing port number: This depends on the email provider.
[*] Incoming security: This depends on the email provider.
[*] Outgoing security: This depends on the email provider.
[/LIST]
 5. Once these settings have been entered, click **Manual Setup...** 

     [IMG]http://support.mozillamessaging.com/media/uploads/gallery/images/2011-03-14-10-07-42-ac07d5.png[/IMG]   . 

You may get an error message that says that the SMTP account already exists. Clear the message. 
6. Click on **Cancel** to exit the Account Settings  dialog. Re-open the Account Settings page and you will see that your new  account has been created.  Also please check your Outgoing Server  (SMTP) is correct for this account (at the bottom of the screenshot). 

     [IMG]http://support.mozillamessaging.com/media/uploads/gallery/images/2011-03-14-10-07-39-ef92ce.png[/IMG]   


7. Check that your incoming and outgoing mail is working correctly.  **If everything is ok (i.e. you can send and receive email and see  your old emails; note that some email providers may not give you access  to all of your emails or all your email folders; check with your mail  provider) and you accidentally created an IMAP account**, then delete the accidentally created IMAP account as follows: open **Tools | Account Settings...**, select the accidentally created IMAP account with the IMAP server setting, then select **Account Actions|Remove Account** from the drop-down list underneath the account list on the left.  
For more information about account connection information, see [Configure an account]("http://support.mozillamessaging.com/en-US/kb/configure-an-account").

---

### Post by pretty_whistle on 2011-11-27
> **jonnyboysmithy said:**
> I'm using thunderbird 3.1.15 on ubuntu 11.04 and I'm trying to add another mail account. I go through the account setup process, it correctly detects the incoming and outgoing mail servers but then when I click 'Add mail account' I get the error 'incoming server already exists'. What can I do about it?
You're supposed to click "add email account" in the beginning, *not* after you've already entered in the new account info.  Just click "ok" when done instead.

---

### Post by jonnyboysmithy on 2011-11-29
Thanks! That solved it, its working the way it should be now.:D

---

