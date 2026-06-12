---
title: "Cannot send mail in php using sendmail, exim nor postfix."
date: 2009-07-21
forum: General Help
---

### Post by infocom on 2009-07-21
Hi

I wondered if anyone knows how to fix this issue... I cannot send email using php mail with sendmail, exim nor postfix. Tried installing all 3 separately and updating php.ini path for each one, restarting apache but still no joy. I have seen many others with same issue and different solutions, none working for me. 

Smtp port 25 is open.I can telnet an external server.  

Is there a definitive guide on how to setup mail on ubuntu? 

Thanks

---

### Post by Janeway on 2009-07-21
Hi,

I think that cannot work not having an aditional mail server running, what I would not recommend. If you want to upload the php site to a provider, you should not care.

Otherwise you have to get a mail server running on you system and write it into the php.ini.

Regards
Janeway

---

### Post by infocom on 2009-07-22
I got it working now.

Firstly, @Janeway I thought using something like sendmail, postfix or exim4 IS a mail server???? 

Anyway, I decided to go with exim, seemed this had most positive reviews online. 

I checked exim mainlog (/var/log/exim4/mainlog) when it failed, I had the following error:-
```
socket bind() to port 25 for address 127.0.0.1 failed: Address already in use
```

The problem was even though sendmail was uninstalled when exim installed, "sudo netstat -napt|grep 25" still showed sendmail as LISTEN on port 25! So I had to kill this process then did a "sudo apt-get purge sendmail" but dont know if any of this helps. 

Once sendmail was not runnning on port 25 I reconfigured exim.....

Using configuration section here (did not go onto the do the rest, looked too complicated as usual, why oh why): [https://help.ubuntu.com/community/Exim4](https://help.ubuntu.com/community/Exim4)

When I ran the configure command from above (sudo dpkg-reconfigure exim4-config) I chose to use a Smarthost with no local mail. Then when it asked me for the domains to use I used my own web host SMTP server.

Then using this website ([http://articles.techrepublic.com.com/5100-10878_11-6053844.html](http://articles.techrepublic.com.com/5100-10878_11-6053844.html)) I added the SMTP Auth into the /etc/exim4/passwd.client file: ```
target.mail.server.example:login:password
```

Then I restarted and now its working. 

// BOF RANT SECTION
For info my PHP project was originally developed on Windows. I just installed a sendmail for windows program and I can send email just fine. 5 minutes it took me. Why is Linux still so far behind? I have been trying to use Linux for 10 years and keep giving up, its unbelievable how it STILL requires so much technical command prompt configuration. The latest release of Ubuntu is the first time everything installed OK which is why I want to move to using it for this development. I keep saying it when I come here for help, but Linux/Ubuntu will NEVER be a suitable operating system for non technical people until things like this are sorted out with suitable GUIs for people to configure things. Rant over, back to programming. :)
// EOF RANT SECTION

---

