---
title: "Gmail/Yahoo Mail does not work in Firefox/Chrome in 10.04"
date: 2010-05-05
forum: General Help
---

### Post by jatanr on 2010-05-05
Hi Everyone,

This is my first post and I am sorry if I am posting in the wrong section.

Lucid Lynx rocks!!! My office VPN was setup in less than 5 minutes. Was never able to set it up in my earlier (now erased) Win7.

OK, I am having a very strange issue with browser based Gmail and Yahoo Mail. Whenever I login to either of  the two mail systems, (using either Chrome of Firefox) I cannot read any of my emails. I am able to login, but in Yahoo Mail, I cannot see anything in the bottom pane when I select any email from the Inbox. In Gmail, when I click on a conversation, it does not open and after some time it says there may be an issue with the connection etc (which is not the case).

I am not sure what I am missing. My internet connection is working fine. I am able to login to all other websites.

There are no add-ons in my Firefox. I am using the 64-bit version.

Thanks and will appreciate any help on this.

---

### Post by ki4anr on 2010-05-05
Are you using a secured connection with your browser (SSL)? I had this situation come up when my gmail account was setup to only to connect with a secure connection. In Firefox,Go to Edit>>Preferences>>Security Tab>> (under Warnings) >> click settings>> Make sure the "I'm about to view a page with low-grade encryption" is checked. See if that helps...

---

### Post by jatanr on 2010-05-06
Thanks for your reply. I am not using a secured connection for either Gmail or Yahoo Mail. But I will check your suggestion tonight (IST) after I reach home and will see if it helps.

Thanks.

---

### Post by jatanr on 2010-05-08
> **ki4anr said:**
> Are you using a secured connection with your browser (SSL)? I had this situation come up when my gmail account was setup to only to connect with a secure connection. In Firefox,Go to Edit>>Preferences>>Security Tab>> (under Warnings) >> click settings>> Make sure the "I'm about to view a page with low-grade encryption" is checked. See if that helps...

Hi checked that I am not using secured connection for gmail. Also, the check box that you suggested is already checked in my case.

Any thing else I can try?

---

### Post by ki4anr on 2010-05-08
Jatanr,

Not sure if this is what is going on my friend, but inside of the gmail and yahoo settings there is a setting to only use the [https://(Secure](https://(Secure) http). If your gmail is set to this ( I dont use yahoo, sorry) then if you have those checked it will not let you see your mail. Can you get into your Gmail account settings? If you can check whether or not the secure settings are on or off. If this is not the case then it might be a browser issue. Do you have a friend who has internet and tried to sign on to your email with their computer? What version of Firefox are you using? What about Chrome? Try to focus on getting one browser to work first, Firefox would be the one I would try to focus on.

---

### Post by Good_Newz on 2010-05-08
Yes I do have the same problem. I also cannot login into gmail. No problem if I use windows. I have tried with both chrome and firefox under linux. My issues started about 2 days ago. Under the updates there is nothing suspicious? I have no clue what it might be.

---

### Post by Good_Newz on 2010-05-08
Also I cannot login into launchpad.

---

### Post by ki4anr on 2010-05-08
This is more information about Google's use of HTTPS connection. I don't know whether this is what is happening, but its worth looking into:

[Quote from Google Help]

Changing the HTTPS setting

We've recently made the 'Always use https' setting the default behavior in Gmail (the default used to be http). Here's some background: If you sign in to Gmail via a non-secure Internet connection, like a public wireless or non-encrypted network, your Google account may be more vulnerable to hijacking. Non-secure networks make it easier for someone to impersonate you and gain full access to your Google account, including any sensitive data it may contain like bank statements or online log-in credentials. Accordingly, we enable the 'Always use https' option in Gmail by default. HTTPS, or Hypertext Transfer Protocol Secure, is a secure protocol that provides authenticated and encrypted communication.

To disable or re-enable this feature in Gmail:

   1. Sign in to Gmail.
   2. Click Settings at the top of any Gmail page.
   3. Set 'Browser Connection' to 'Don't use https' or 'Always use https.'
   4. Click Save Changes.
   5. Manually change the URL to [http://mail.google.com](http://mail.google.com) to start accessing Gmail via http.

Please note that selecting 'Always use https' will prevent you from accessing Gmail via HTTP (Hypertext Transfer Protocol). If you trust the security of your network, you can turn this feature off at any time.

If you use a public computer to check your email, it's also important to end each of your Gmail sessions by clicking Sign out at the top of any Gmail page and to close all Gmail browser windows.

---

### Post by ki4anr on 2010-05-08
More information on Loading issues of Gmail in Firefox:


Symptoms:
After clicking Sign in, you see 'Loading...' or 'This seems to be taking longer than usual' and may be redirected to our basic HTML version. You might see a blank white page.

Cause:
A conflict with software on your computer, browser cache that needs to be cleared, or a temporary problem on the Gmail server.

Solution:
First, we recommend that you upgrade to the most recent stable version of your browser. You can find information on the latest stable version of your browser by searching your browser's Help Center, often times accessible by clicking the 'Help' menu near the top of the browser window.

If you're using the most recent stable version of your browser, follow the instructions below in the order provided. If they don't resolve your issue, you'll have a chance to report the problem to Gmail.

Internet security, firewall can prevent Gmail from working correctly.


We suggest seeing if a browser extension or toolbar may be causing the problem. Browser extensions and toolbars are intended to enhance browser functionality, but they can interfere with Gmail.

Clearing your browser's cache and cookies can resolve many issues in Gmail. Select your browser below for instructions.



   1. Log out of Gmail and close all other open browser windows.
   2. Click the Tools menu at the top of your browser and select Clear Private Data...
   3. Select the Cookies and Cache check boxes.
   4. Click Clear Private Data Now.

In Firefox 3.5+ for PCs:

   1. Click the Tools menu.
   2. Click Clear Recent History.
   3. Expand the details.
   4. Select the Cookies and Cache check boxes.
   5. Click Clear Now.



If clearing your browser's cache and cookies didn't fix the problem, visiting the secure site may resolve the issue.

Gmail offers an encrypted site for extra security. Because browsers and security applications are more likely to trust encrypted data, visiting Gmail through its encrypted login will often resolve issues caused by that software.

Please try logging in to Gmail via [https://mail.google.com](https://mail.google.com).

---

### Post by Good_Newz on 2010-05-08
Ok, I solved my cannt login to gmail problem. Restart YOUR router. I have netgear. It started causing all kinds of weird problems(most on linux, no problems on windows) in the past couple of days. So unplug it from the power source then wait 10s and plug it in again. Hope this helps.

---

### Post by ki4anr on 2010-05-08
Good_Newz,

I was about to mention that if the above solution didn't work. Thanks for bringing that up to the forum!


Jatanr,

Are you connecting with a router who has a firewall? What type of connection are you using, wireless or wired? Are you sharing the connection with others like a open wireless or shared connection? Any of those along with a hard restart of the network router might be the cause. Good_Newz has a great iadea about rebooting the router.

Kev
ki4anr

---

### Post by jatanr on 2010-05-09
Hi ki4ranr,

I tried all the combinations. In gmail settings, I chose "Always use https" and tried... didnt work. Then I chose "Don't always use https". Didn't work. I always keep getting the stupid error popup "Some Gmail features have failed to load due to an Internet connectivity problem blah blah blah".

I have a wireless as well as wired connection. I use a router along with a modem. I have a winXP laptop on which everything works like a charm. I have a desktop ubuntu 10.04 on which I see this issue. 

Oh... btw, I just reinstalled ubuntu again this morning... vanilla... and then started firefox (without any plugins) but still I see the same issue.

I have restarted the router and modem also, but still a no-go.

This is quite frustrating...

Thanks for your help guys... anything else I can do??

---

### Post by jatanr on 2010-05-09
I think it is something to do with my network settings in Ubuntu. I am trying to connect to twitter using gwibber, but am not able to see any messages. I am able to add the twitter account in gwibber without any errors, but I do not see any new messages. Posting a new message also does not post anything to my twitter page.

My latest experience with Ubuntu has been teribly disappointing :(

---

