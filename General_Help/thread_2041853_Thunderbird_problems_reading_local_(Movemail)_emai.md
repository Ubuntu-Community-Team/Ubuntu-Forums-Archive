---
title: "Thunderbird problems reading local (Movemail) email"
date: 2012-08-13
forum: General Help
---

### Post by kadstro on 2012-08-13
I am not able to setup a Thunderbird account to read email from my local mail spool.  I'm using Thunderbird 14.0 on Ubuntu 12.04 with current updates. 

I am able to use Thunderbird to read email from the local spool when I am logged in as a different user that appears to be set up similarly but was set up under an earlier version of Thunderbird.

To setup the account for kadstro on computer MyLaptop I do the following in Thunderbird while logged in as kadstro:

0.  With no ~/.Thunderbird directory, start Thunderbird.  The ~/.Thunderbird 
     directory is created.

0.1 Open the error console by selecting Tools/Error Console. 
    Initially it just has the informational message:
        "www.hover.com : server does not support RFC 5746, see CVE-2009-3555"

0.2 Wait a few minutes,  doing nothing in Thunderbird.  Within 5 minutes, 
     several messages appear in the error console: 

       Error: formatURL: Couldn't find value for key: TIME_SESSION_RESTORED
       Source File: resource:///components/nsURLFormatter.js  Line: 131

       Warning: WARN addons.updates: Update manifest for 
           {972ce4c6-7e08-4474-a285-3208198ce6fd} did not contain an updates property
       Source File: resource:///modules/AddonUpdateChecker.jsm Line: 313

       Warning: WARN addons.updates: Update manifest for [EMAIL="globalmenu@ubuntu.com"]globalmenu@ubuntu.com[/EMAIL] 
            did not contain an updates property
       Source File: resource:///modules/AddonUpdateChecker.jsm Line: 313

       Warning: WARN addons.updates: Update manifest for [EMAIL="edsintegration@mozilla.com"]edsintegration@mozilla.com[/EMAIL] 
           did not contain an updates property
       Source File: resource:///modules/AddonUpdateChecker.jsm Line: 313

     Wait 5 more minutes, nothing happens.

0.3 In the Welcome to Thunderbird dialog, click on 
     "I think I'll setup my account later"
     No new messages in error console for 5 minutes 

1.  Select File/New/Other Accounts.
     Get two more messages in error console: 

       Error: An error occurred updating the cmd_sendUnsentMsgs command: 
           [Exception... "Component returned failure code: 0x80004005 
           (NS_ERROR_FAILURE) [nsIMsgAccountManager.defaultAccount]"  nsresult: 
           "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: 
           chrome://messenger/content/mail3PaneWindowCommands.js :: 
           IsSendUnsentMsgsEnabled :: line 1071"  data: no]
       Source File: chrome://global/content/globalOverlay.js Line: 86
     
       Error: An error occurred updating the cmd_sendUnsentMsgs command: 
           [Exception... "Component returned failure code: 0x80004005 
           (NS_ERROR_FAILURE) [nsIMsgAccountManager.defaultAccount]"  nsresult: 
           "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: 
           chrome://messenger/content/mail3PaneWindowCommands.js :: 
           IsSendUnsentMsgsEnabled :: line 1071"  data: no]
       Source File: chrome://global/content/globalOverlay.js Line: 86

2.  In the New Account Setup dialog, accept the default "Unix Mailspool (Movemail)"
     selection and click Next.

3.  In the Identity dialog, change the email address from "kadstro@(none)" to
     "kadstro@MyLaptop" and click Next.

4.  In the Outgoing Server Information dialog, for Outgoing Server enter "localhost",
     leave the Outgoing User Name blank and click Next.

5.  In the Account Name dialog, accept the account name of "kadstro@MyLaptop"
     and click Next.

6.  In the "Congratulations!" verification dialog, check the values and 
     click Finish.

7.  Back at the main Thunderbird window, select the new account, 
     kadstro@MyLaptop" on the left
     and click Email/Read Messages in the main area.
     Get one more message in the error console:

       Error: Error opening Inbox for server: TypeError: aFolder is null
       Source File: chrome://messenger/content/msgAccountCentral.js Line: 296

     Nothing else happens.


There are emails waiting to be read in /var/mail/kadstro.

Any suggestions?

---

