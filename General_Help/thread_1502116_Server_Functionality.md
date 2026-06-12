---
title: "Server Functionality"
date: 2010-06-05
forum: General Help
---

### Post by simonw2008 on 2010-06-05
[COLOR=black]Newbie so sorry if very basic questions. [/COLOR][COLOR=black]

[/COLOR][COLOR=black]I need a server for a small business. I don’t want to pay Bill Gates any more money and I worked with SVR5.4 about 15 years ago so I'm sure I can pick Ubuntu up, but before I dive into using and learning Ubuntu Server I just want to check it can do everything I need. [/COLOR][COLOR=black]

[/COLOR][COLOR=black]The company has 4 Windows Vista Pro PC’s and 1 Windows 7 Pro laptop currently in a very simple Microsoft workgroup with one of the desktops acting as a file server. Its horrible because you have to have the same usernames and passwords on all the PC’s to get the file sharing working seamlessly. Also its impossible to easily control who can access what. Mail currently is handled by a third party.[/COLOR][COLOR=black]

[/COLOR][COLOR=black]I want to install Ubuntu Server on a fairly powerful old desktop and use it for permission based file serving but I'm not sure is if Ubuntu Server can act as the domain controller and handle user accounts in the same way as a Windows Active Directory DC. Can Ubuntu act as the DC with Windows PC’s joining an Ubuntu domain and then handle file permissions based on the logged on users id and group membership?[/COLOR][COLOR=black]

[/COLOR][COLOR=black]On the same single server I also will want to run DNS, DHCP etc. – and also if possible a mail server. Does the mail server which comes with Ubuntu work with MS Outlook?[/COLOR][COLOR=black]

[/COLOR][COLOR=black]When I come to install Ubuntu there is an option for Enterprise Cloud – what’s that please.[/COLOR][COLOR=black]

[/COLOR][COLOR=black]Sorry if drawn out and if I've posted this on the wrong forum but thanks if you can help me.[/COLOR][COLOR=black]

[/COLOR][COLOR=black]Simon[/COLOR][COLOR=black][/COLOR]

---

### Post by wojox on 2010-06-05
Check this out Simon [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html")

That should answer most of your questions. :)

---

### Post by simonw2008 on 2010-06-05
Thanks - I was just after a yes or no really rather than "read the manual".

---

### Post by jerome1232 on 2010-06-05
Well only you can really determine if Ubuntu will meet your needs

I think these two sections will be of particular interest to you, just do a quick browse over them and see if that is what you have in mind

Windows Networking: [https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html](https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html)
Email Services: [https://help.ubuntu.com/10.04/serverguide/C/email-services.html](https://help.ubuntu.com/10.04/serverguide/C/email-services.html)

Also these sections

DHCP Server: [https://help.ubuntu.com/10.04/serverguide/C/dhcp.html](https://help.ubuntu.com/10.04/serverguide/C/dhcp.html)
DNS Server: [https://help.ubuntu.com/10.04/serverguide/C/dns.html](https://help.ubuntu.com/10.04/serverguide/C/dns.html)

---

### Post by sgosnell on 2010-06-05
The short answer is yes.  The long answer is that it will require some knowledge to set it up, so you need to read all that stuff anyway.  

Just set up the server using the guides, and things should work.  I'm not running a business, but I have an extra netbook set up at home as a server, and it works fine with the Windows machines around.  Most servers in the world run Linux of some flavor, so it's certainly possible, and in reality, not that hard.  You do need to do some research on the technical aspects, though.

---

