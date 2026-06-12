---
title: "How to be able to create dir in FireFTP"
date: 2010-07-05
forum: General Help
---

### Post by ozstar on 2010-07-05
Hi,

Is there a way I can get root permision when using fireftp to transfer files from my shared Linux host server to my Linux 10.4 desk?

I can connect with FirefTP oklay but when I wanted to create a dir on the desktop, it said 'unable to create try a different name'.

No matter what name I tried I got the same answer so I guess it is because I am not there as 'root'.

How do I do this?

The sites on the desktop are in var/www/site/

I just also noticed it will not save anything I try and download.

Thanks

oz :-)

---

### Post by ozstar on 2010-07-06
Welll I decided to download to my /Home/Public/ directory which it did and also allowed me to create a directory.

This means I now have to move all these sites across to the ww dir and that I cannot update them from the online host.

Can I somehow gain permission to ftp from an online server to my ubuntu desktop server?

oz

---

### Post by crichard on 2010-07-06
Once I've used FireFTP addon but the problem is I could n't upload the hidden files (Eg:- .htaccess_to_use_later), So, I switched to Nautilus Fire Transfer. In Nautilus Select  File -> Connect to Server.. & choose the service type then, enter relevant data & connect... That's it :) One good thing is it allows tabbed browsing :)

---

### Post by ozstar on 2010-07-06
Thanks.

I do not have an option in 'Type' except the word Custom.

It does not allow any input and when I enter the url it says must enter server name.

What am I doing wrong here?

oz

---

### Post by crichard on 2010-07-06
> **ozstar said:**
> Thanks.

I do not have an option in 'Type' except the word Custom.

It does not allow any input and when I enter the url it says must enter server name.

What am I doing wrong here?

oz

It's strange. You supposed to get many options as "Service Type" like [LIST][*]SSH[*]FTP (with login)[*]Public FTP[*]Windows share,[*]WebDAV[*]Secure WebDAV (HTTPS)[*]Custom [/LIST]

I need few more details, what kind of FTP are you going to use? FTP or SFTP? 
If it's a FTP,Can you able to select FTP (with login) as your "Service Type"? If you feel it's difficult then, simply open your home directory and press Ctrl+L on your keyboard, then enter your ftp details on that location bar,  Use the same format as shown below,

```
ftp://username@ftp.server.com
``` 

For example, my website's ftp server name is ftp.0ccultist.com. Hence, I've to enter [ftp://myusername@ftp.0ccultist.com](ftp://myusername@ftp.0ccultist.com)  So enter your FTP details provided by your hosting account.
Press Enter, You will be asked for a password to connect with the server.

---

